# Information Pages Repository

複数のプロジェクト向けプライバシーポリシー、サポートページ、法務文書をホストする汎用リポジトリです。

GitHub Pages で公開されています: https://youaoi.github.io/information/

## 📋 掲載プロジェクト

### App

#### My QR Reader
- QRコードをすばやく読み取れるiOSアプリ
- [プライバシーポリシー](https://youaoi.github.io/information/myqrreader/privacy.html)
- [サポート](https://youaoi.github.io/information/myqrreader/support.html)

#### Prompt Gallery
- AIプロンプトを見つけて整理できるiOSアプリ
- [プライバシーポリシー](https://youaoi.github.io/information/promptgallery/privacy.html)
- [サポート](https://youaoi.github.io/information/promptgallery/support.html)

#### Gee Movie Explorer
- Webページで選択した動画を端末に保存し、オフラインで再生できるiOSアプリ
- [プライバシーポリシー](https://youaoi.github.io/information/gee-movie-explorer/privacy.html)
- [サポート](https://youaoi.github.io/information/gee-movie-explorer/support.html)
- [審査用デモ](https://youaoi.github.io/information/gee-movie-explorer/demo.html)

#### Host Cassettes（Mac App）
- macOS向けのhostsファイルマネージャー
- [GitHub リポジトリ](https://github.com/youaoi/hostcassettes)
- [ダウンロード（Releases）](https://github.com/youaoi/hostcassettes/releases)

### Chrome拡張

#### Gmail Unread Tracker
- ログイン済みのGmailアカウントの未読メール件数を表示するChrome拡張機能
- [プライバシーポリシー](https://youaoi.github.io/information/gmail-unread-tracker/privacy.html)
- [Chrome Web Store](https://chromewebstore.google.com/detail/jlmecjjomdibffdlidbgkdnnickphlie)

#### URL Switcher for Developer
- 登録した本番・開発・ローカルなどの環境URLを切り替えられるChrome拡張機能
- [プライバシーポリシー](https://youaoi.github.io/information/url-switcher-for-developer/privacy.html)
- [サポート](https://youaoi.github.io/information/url-switcher-for-developer/support.html)
- [Chrome Web Store](https://chromewebstore.google.com/detail/binkjcibekcnomlpfkbimlejdolahona)

### VS Code拡張
- [okasyのMarketplace掲載一覧](https://marketplace.visualstudio.com/publishers/okasy)

#### Sakana Fugu for VS Code
- sakana.aiのfugu・fugu-ultraをVS Codeのチャットモデルとして利用できる拡張
- [GitHub リポジトリ](https://github.com/youaoi/sakana-fugu-for-vscode)
- [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=okasy.sakana-fugu-for-vscode)

#### Terminal Actions
- サイドバーからワンクリックでターミナルコマンドを実行できる拡張
- [GitHub リポジトリ](https://github.com/okasy/vscode-ext-local-terminal-actions)
- [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=okasy.local-terminal-actions)

*新しいプロジェクトを追加する場合は、[CONTRIBUTING.md](CONTRIBUTING.md) をご参照ください。*

## 📁 リポジトリ構造

```
information/
├── docs/
│   ├── index.html              # ドキュメント一覧（GitHub Pages用）
│   └── {project-name}/
│       ├── privacy.html        # プライバシーポリシー
│       ├── support.html        # サポートページ
│       ├── demo.html           # 審査用デモ（必要な場合）
│       └── terms.html          # 利用規約（オプション）
├── templates/
│   ├── privacy-template.html   # プライバシーポリシー雛形
│   └── support-template.html   # サポートページ雛形
├── CONTRIBUTING.md             # 新規プロジェクト追加ガイド
└── README.md                   # このファイル
```

## 🌐 ページ仕様

### 技術要件
- **形式**: HTML5（単一ファイル）
- **スタイリング**: インラインCSS推奨
- **ダークモード**: `prefers-color-scheme` メディアクエリで対応
- **レスポンシブ**: モバイル対応必須
- **言語**: 日本語・英語（バイリンガル推奨）
- **文字エンコーディング**: UTF-8

### 一般的なページ構成
1. **プライバシーポリシー** (`privacy.html`)
   - データ収集方針
   - 情報の共有・保管方法
   - ユーザーの権利

2. **サポートページ** (`support.html`)
   - よくある質問（FAQ）
   - トラブルシューティング
   - お問い合わせ方法

3. **利用規約** (`terms.html`) - オプション
   - サービス利用条件
   - 責任の制限
   - 契約終了

## 🚀 使用方法

### 新規プロジェクトの追加
1. `docs/{project-name}/` ディレクトリを作成
2. `templates/` からテンプレートをコピー
3. プロジェクト固有の内容に編集
4. コミット＆プッシュで自動公開

詳細は [CONTRIBUTING.md](CONTRIBUTING.md) を参照します。

### ページの更新
1. `docs/{project-name}/` 内のHTMLファイルを編集
2. 変更をコミット
3. GitHub Pages が自動的にデプロイ（数秒～1分）

## 📝 編集のベストプラクティス

- HTMLは単一ファイルで完結（外部CSS/JS不要）
- インラインスタイルを使用
- `<meta name="viewport">` を含める
- 言語を明記する（`<html lang="ja">`）
- セマンティックHTMLを使用（`<h1>`, `<h2>`, `<p>`, `<ul>` など）

## 🔗 リンク集

- [GitHub リポジトリ](https://github.com/youaoi/information)
- [GitHub Pages](https://youaoi.github.io/information/)

## 📄 ライセンス

各プロジェクトのドキュメントはプロジェクト固有のライセンスに従います。
