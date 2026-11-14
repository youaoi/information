---
name: task-orchestrator
description: Decides how to split development work across models (Opus / Sonnet / Haiku) and subagents, and runs Haiku subagents in parallel to save context and cost. Use whenever the user gives a development task that is not trivial - new implementation, refactoring, bug fix, investigation, test/build runs, or changes spanning several files - even if they never mention orchestration or subagents. Typical triggers, in English or Japanese - "implement", "fix", "investigate", "check the impact", "run the tests" (実装して / 直して / 調べて / 影響範囲を見て / テストして). Never call external coding agents such as Codex; do everything with Claude and its subagents.
---

# Task orchestrator

Split the user's development work using the rules below. Three goals: keep the parent context free of bulk reading, spend expensive models only where judgment is needed, and finish independent work in parallel.

Do not call Codex or any other external coding agent or CLI. Do implementation, investigation and verification yourself or through Claude subagents (the Agent tool).

The main session is assumed to run on Sonnet. A running session cannot switch its own model, so when Opus is needed, spawn an Opus subagent yourself (see section 1). Do not ask the user to switch models.

## 0. Size the task first

A subagent starts with an empty context, so on small work it costs more than it saves. Do these yourself:

- Reading or editing one or two known files, anything finished in a few tool calls, simple questions.
- Identical mechanical edits that one PowerShell/sed loop can do (prepending a header comment, bulk string replacement). No judgment or context is needed, so a script is faster and safer. Always check the resulting diff yourself.

Delegate only what matches section 2. When unsure, do it yourself.

## 1. Model by phase

| Phase | Model | Work |
|---|---|---|
| Planning, design, final review | Opus | Resolve ambiguous requirements, design, work breakdown, deep-impact bugs, pre-merge logic/security review |
| Standard implementation, integration | Sonnet (you) | Implement a settled design, integrate multiple files, merge subagent results |
| Exploration, boilerplate, first-pass verification | Haiku subagents | Anything matching section 2 |

When to call Opus (call it without hesitation when one applies; it is expensive, so not otherwise):

- **Planning / design**: requirements are ambiguous, a trade-off between options must be decided, the change spans several components, or a work breakdown is needed. Use `subagent_type: "Plan"` with `model: "opus"`.
- **Hard bugs**: the cause spans state in several files, or your first hypothesis failed. Use `general-purpose` with `model: "opus"`.
- **Final review**: before commit/merge of a large or wide-impact change, review logic, security and regressions of existing behavior. Use a read-only `Explore` agent (or the `code-review` skill) with `model: "opus"`.

Give Opus: the goal, absolute target paths, the facts already found (for example Haiku's findings), and the output format you want (for example "chosen option and reason, files to change in order, risks, within one page"). Opus returns decisions; you implement them.

Always set `model` explicitly when spawning a subagent. If omitted it inherits the parent model, which wastes money on work Haiku can do or runs the wrong model for the job.

## 2. Delegate to Haiku

Spawn a subagent with `model: "haiku"` when the work matches any of these:

1. **Bulk reading / exploration**: grep across 3+ files, callers and dependency tracing, listing the impact range, extracting relevant parts from long logs or specs.
2. **Independent parallel work**: the same mechanical edit across files that do not depend on each other, boilerplate generation, per-module documentation. When independent, launch **3-5 subagents in the same message**, not one by one.
3. **Execution and first-pass triage**: running tests, linters, builds and extracting failing locations from the logs. Ask for facts only ("what failed where"); never ask for a fix decision. C++ builds and ctest produce long output that pollutes the parent context, so by default hand both the baseline run and the post-change rerun to Haiku (`Explore`). Run directly only when you know a single command prints a few lines.
4. **Structuring / classification**: JSON extraction from unstructured text, diff summaries, conversion to a fixed format.

## 3. Never delegate to Haiku

Do these yourself (Sonnet/Opus) because the quality of judgment is the quality of the result:

- Architecture decisions and spec interpretation.
- Logic or bug fixes with tightly coupled state across several files.
- Final quality/security review of generated code.
- Destructive or externally visible actions: git commit/push, deleting files, sending data to outside services. Do these yourself, within what the user asked.

## 4. Spawning rules

- **Set `model` explicitly** (see above).
- **Prompt with three elements only**, and never pass the parent conversation history (a fresh context is where the savings come from):
  - Goal: what to find out or build.
  - Target: absolute directory/file paths.
  - Output format: for example "file path:line and a summary of at most 3 lines, as bullets".
- **Minimize permissions.** For investigation and running tests use `Explore` (Read/Grep/Glob/Bash, no edit tools). Use `general-purpose` only for edits. If the type cannot be chosen, write "do not edit files" in the prompt.
- **Never let two writing agents touch the same file.** Parallelize only work on disjoint files; otherwise use `isolation: "worktree"` or run sequentially.
- **Treat Haiku reports as leads.** Before relying on a conclusion or editing a spot, read the cited lines yourself. Ask for line numbers or other checkable evidence so this is fast.

## 5. Standard flow

1. **Parallel investigation**: Haiku subagents survey relevant files, existing patterns and dependencies.
2. **Plan**: from the reports, write the implementation plan and a task list split into parallelizable units. If the size meets the Opus criteria above, pass the findings to Opus (Plan) to settle it; build small plans yourself.
3. **Split implementation**: Haiku builds independent boilerplate in parallel; you write the core logic and integrate.
4. **Verify and finish**: Haiku runs tests/build/lint and lists failures; you fix them. For large or wide-impact changes, ask Opus to review the diff before declaring done.

If the project has its own working rules (AGENTS.md, CLAUDE.md, etc.), they take priority, and delegated work must follow them too - for example "take a baseline with tests before changing logic" or "use `git -C <child>` for child repositories". Put the needed constraint in the subagent prompt in one line.

## 6. Reporting to the user

When you delegated, say briefly in the completion report what went to which model and what you verified yourself. If tests failed, report it with the output.
