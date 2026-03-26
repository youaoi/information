# 新規プロジェクトの追加ガイド

このリポジトリに新しいプロジェクトのドキュメントを追加する方法を説明します。

## ステップバイステップ

### 1. ディレクトリ構造の作成

プロジェクト用ディレクトリを `docs/` に作成します：

```bash
mkdir -p docs/{your-project-name}
```

ディレクトリ名はプロジェクト識別子として使用します（例: `myqrreader`, `myapp`, `awesome-tool`）

### 2. テンプレートをコピー

```bash
# プライバシーポリシー
cp templates/privacy-template.html docs/{your-project-name}/privacy.html

# サポートページ
cp templates/support-template.html docs/{your-project-name}/support.html
```

### 3. 内容を編集

各HTMLファイルを開いて、以下の部分をプロジェクト固有の内容に編集します：

#### プライバシーポリシー (`privacy.html`)
- `<title>` タグ内のアプリ名
- データ収集・利用方針
- 連絡先情報
- 最終更新日

#### サポートページ (`support.html`)
- `<title>` タグ内のアプリ名
- よくある質問と回答
- トラブルシューティング情報
- お問い合わせ先

### 4. スタイル（オプション）

テンプレートには基本的なスタイルが含まれています。必要に応じて調整できます：

```css
body { max-width: 800px; margin: 0 auto; padding: 24px 16px; }
h1 { font-size: 1.8em; }
h2 { font-size: 1.2em; border-bottom: 1px solid #e5e5ea; }
```

### 5. 全言語対応（推奨）

テンプレートはデフォルトで日本語・英語のバイリンガル対応になっています。

- **日本語ブロック**: `<h1>プライバシーポリシー</h1>` の後のセクション
- **英語ブロック**: `<hr>` で区切られた下部のセクション

単一言語のみの場合は、不要な部分を削除してください。

### 6. コミット＆プッシュ

```bash
git add docs/{your-project-name}/
git commit -m "Add documentation for {your-project-name}"
git push origin main
```

GitHub Pages が自動的にデプロイされます。

### 7. README.md を更新

[README.md](README.md) の「ホスト中のプロジェクト」セクションに新規プロジェクトへのリンクを追加します：

```markdown
### Your Project Name
- [プライバシーポリシー](https://okasy.github.io/information/{your-project-name}/privacy.html)
- [サポート](https://okasy.github.io/information/{your-project-name}/support.html)
```

## 📋 チェックリスト

新規プロジェクト追加時の確認項目：

- [ ] `docs/{your-project-name}/` ディレクトリを作成
- [ ] `privacy.html` と `support.html` を追加
- [ ] プロジェクト固有の内容を編集完了
- [ ] HTML の `<title>` タグを更新
- [ ] メタデータ（最終更新日など）を更新
- [ ] ダークモード対応を確認
- [ ] モバイル表示を確認
- [ ] 外部リンクが正しいか確認
- [ ] README.md に追加
- [ ] コミット＆プッシュ

## 📐 技術要件

### 必須事項
- ✅ HTML5 形式
- ✅ UTF-8 エンコーディング
- ✅ `<meta name="viewport">` 設定
- ✅ 言語属性 (`<html lang="ja">` など)
- ✅ インラインCSS（外部ファイル不可）

### 推奨事項
- ✅ ダークモード対応 (`@media (prefers-color-scheme: dark)`)
- ✅ レスポンシブデザイン
- ✅ バイリンガル（日本語・英語）
- ✅ セマンティックHTML5

### 非推奨
- ❌ 外部CSS/JavaScript
- ❌ iframe や Flash
- ❌ 大きな画像ファイル
- ❌ クライアント側のリダイレクト

## 🔗 テンプレート変数

テンプレートには以下のプレースホルダーが含まれます（カスタマイズが必要な部分）：

- `[App/Product Name]` - アプリケーション名
- `[Your Company/GitHub Issues URL]` - 問い合わせ先
- `[month/year]` - 最終更新日
- セクション内容 - データ収集方針など

## ❓ よくある質問

**Q: プライバシーポリシーのみでよい？**  
A: はい、プロジェクトに必要なページだけ追加してください。

**Q: 複数言語対応は必須？**  
A: いいえ。単一言語でも構いません。テンプレートから不要な部分を削除してください。

**Q: HTTPS は対応している？**  
A: はい、GitHub Pages はすべてのリポジトリで HTTPS をサポートしています。

**Q: SEO 対策は？**  
A: これらは法務ドキュメントのため、SEO 対策は最小限にしています。必要に応じてメタデータを追加できます。

## 📧 質問・問題

リポジトリの Issues で質問や問題報告ができます。
