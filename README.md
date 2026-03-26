# Information Pages Repository

複数のプロジェクト向けプライバシーポリシー、サポートページ、法務文書をホストする汎用リポジトリです。

GitHub Pages で公開されています: https://okasy.github.io/information/

## 📋 ホスト中のプロジェクト

### My QR Reader
- [プライバシーポリシー](https://okasy.github.io/information/myqrreader/privacy.html)
- [サポート](https://okasy.github.io/information/myqrreader/support.html)

*新しいプロジェクトを追加する場合は、[CONTRIBUTING.md](CONTRIBUTING.md) をご参照ください。*

## 📁 リポジトリ構造

```
information/
├── docs/
│   ├── index.html              # ドキュメント一覧（GitHub Pages用）
│   └── {project-name}/
│       ├── privacy.html        # プライバシーポリシー
│       ├── support.html        # サポートページ
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

- [GitHub リポジトリ](https://github.com/okasy/information)
- [GitHub Pages](https://okasy.github.io/information/)

## 📄 ライセンス

各プロジェクトのドキュメントはプロジェクト固有のライセンスに従います。
