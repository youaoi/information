# 新規プロジェクトの追加ガイド

このリポジトリは、アプリや拡張機能の概要・ドキュメント・配布先を一覧で掲載するためのものです。
新しいプロジェクトを追加するときは、配布形式に応じたセクションへ登録してください。

## 掲載セクション

`docs/index.html` と `README.md` には、次の3つのセクションがあります。

- **App**: iOS・macOSなどのアプリ
- **Chrome拡張**: Chrome Web Storeで配布する拡張機能
- **VS Code拡張**: VS Code Marketplaceで配布する拡張機能

## 追加手順

### 1. ドキュメントを作成する

このリポジトリでプライバシーポリシーやサポートページを公開する場合は、プロジェクト用ディレクトリを作成します。

```bash
mkdir -p docs/{project-slug}
cp templates/privacy-template.html docs/{project-slug}/privacy.html
cp templates/support-template.html docs/{project-slug}/support.html
```

プロジェクトに必要なページだけを作成できます。たとえばプライバシーポリシーだけを掲載する場合は、`support.html` は不要です。

#### プライバシーポリシー (`privacy.html`)

- `<title>` と見出しをプロジェクト名に変更
- 取得・利用する情報とその目的を記載
- 情報の共有・保管・削除方針を記載
- 問い合わせ先と最終更新日を更新

#### サポートページ (`support.html`)

- `<title>` と見出しをプロジェクト名に変更
- 機能概要、FAQ、トラブルシューティングを記載
- 問い合わせ先を記載

### 2. アイコンを追加する

カードに表示するアイコンを `docs/product-icons/` に追加します。

- ファイル名はプロジェクト識別子に合わせる（例: `my-project.png`）
- PNGまたはSVGを使用する
- 正方形の画像を推奨
- 外部URLではなく、リポジトリ内の画像を使用する

既存のカードと同じく、`docs/index.html` から相対パスで参照します。

```html
<img class="project-icon" src="product-icons/my-project.png" alt="" aria-hidden="true">
```

VS Code拡張のアイコンで明るい下地が必要な場合は、`vscode-icon` クラスを追加します。

```html
<img class="project-icon vscode-icon" src="product-icons/my-project.png" alt="" aria-hidden="true">
```

### 3. 一覧ページにカードを追加する

`docs/index.html` の配布形式に合う `<section>` 内へ、プロジェクトカードを追加します。

カードには次の情報を含めます。

- アイコン
- プロジェクト名
- 簡潔な概要（`project-description`）
- このリポジトリで公開しているドキュメントへのリンク
- GitHub、App Store、Chrome Web Store、VS Code Marketplaceなどの配布先リンク

概要とリンクの例：

```html
<div class="project-card">
  <div class="project-heading">
    <img class="project-icon" src="product-icons/my-project.png" alt="" aria-hidden="true">
    <h3 class="project-name">My Project</h3>
  </div>
  <p class="project-description">プロジェクトの主な機能を簡潔に説明します。</p>
  <ul class="docs-list">
    <li><a href="my-project/privacy.html" class="docs-link">プライバシーポリシー</a></li>
    <li><a href="https://github.com/owner/my-project" class="docs-link" target="_blank" rel="noopener noreferrer">GitHub リポジトリ</a></li>
  </ul>
  <div class="store-area">
    <a class="store-link" href="https://example.com/download" target="_blank" rel="noopener noreferrer">
      <span class="store-icon" aria-hidden="true">↗</span>
      配布先で見る
    </a>
  </div>
</div>
```

公開状況やバージョンなどの補足ステータスはカードに追加せず、配布先へのリンクだけを掲載します。

### 4. README.mdを更新する

`README.md` の同じ配布形式セクションに、概要と関連リンクを追加します。

```markdown
#### My Project
- プロジェクトの主な機能を簡潔に説明します
- [プライバシーポリシー](https://youaoi.github.io/information/my-project/privacy.html)
- [配布先](https://example.com/download)
```

### 5. 確認してコミットする

```bash
git diff --check
git add docs/ README.md CONTRIBUTING.md
git commit -m "Add documentation for my project"
git push origin main
```

GitHub Pagesは、`main` ブランチへのプッシュ後に自動デプロイされます。

## チェックリスト

- [ ] 配布形式に合うセクションを選択
- [ ] 必要なドキュメントディレクトリを作成
- [ ] 必要なプライバシーポリシー・サポートページを作成
- [ ] HTMLのタイトル、見出し、内容、最終更新日を更新
- [ ] アイコンを `docs/product-icons/` に追加
- [ ] `docs/index.html` に概要とリンクを追加
- [ ] `README.md` に概要とリンクを追加
- [ ] 外部リンクが正しいか確認
- [ ] レスポンシブ表示とダークモードを確認
- [ ] `git diff --check` を実行
- [ ] コミットして `main` にプッシュ

## ページの技術要件

### 必須

- HTML5
- UTF-8
- `<meta name="viewport">`
- 適切な言語属性（通常は `<html lang="ja">`）
- インラインCSS
- 外部リンクへの `target="_blank"` と `rel="noopener noreferrer"`

### 推奨

- 日本語・英語の併記
- セマンティックHTML
- `@media (prefers-color-scheme: dark)` によるダークモード対応
- モバイル画面での表示確認

### 避けるもの

- 外部CSS・外部JavaScriptへの依存
- iframeやFlash
- 不要に大きな画像
- クライアント側のリダイレクト

## テンプレート

- [プライバシーポリシーテンプレート](templates/privacy-template.html)
- [サポートページテンプレート](templates/support-template.html)

質問や問題がある場合は、リポジトリのIssuesで報告してください。
