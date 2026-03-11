# 宿スタ サポートサイト — GitHub Pages 公開手順

本ドキュメントでは、宿スタのサポートページ・プライバシーポリシー・利用規約をGitHub Pagesで無料公開する手順を説明します。

## 含まれるファイル

| ファイル | 内容 |
|---------|------|
| `index.html` | サポートページ（FAQ・お問い合わせフォーム） |
| `privacy.html` | プライバシーポリシー |
| `terms.html` | 利用規約 |
| `style.css` | 共通スタイルシート |

## 公開前に変更が必要な箇所

各ページ内の以下の箇所を、ご自身の情報に書き換えてください。

| 対象 | 現在の値 | 変更先 |
|------|---------|--------|
| メールアドレス | `shukusutaofficial@gmail.com` | ご自身のサポート用メールアドレス |
| 著作権表示の年 | `2026` | 必要に応じて変更 |
| お問い合わせフォームの送信先 | JavaScriptのダミー処理 | Formspree等の実サービスに連携（後述） |

## GitHub Pagesでの公開手順

### 手順1: GitHubリポジトリを作成する

1. [GitHub](https://github.com) にログインする
2. 右上の「+」ボタンから「New repository」を選択
3. 以下の設定でリポジトリを作成する
   - **Repository name**: `shukusta-support`（任意の名前でOK）
   - **Public** を選択（GitHub Pages無料版はPublicリポジトリが必要）
   - 「Add a README file」にチェックを入れる
4. 「Create repository」をクリック

### 手順2: ファイルをアップロードする

1. 作成したリポジトリのページで「Add file」→「Upload files」をクリック
2. ZIPを展開した中の4ファイルをドラッグ＆ドロップ
   - `index.html`
   - `privacy.html`
   - `terms.html`
   - `style.css`
3. 「Commit changes」をクリック

### 手順3: GitHub Pagesを有効にする

1. リポジトリの「Settings」タブを開く
2. 左メニューの「Pages」をクリック
3. 「Source」セクションで以下を設定
   - **Branch**: `main`
   - **Folder**: `/ (root)`
4. 「Save」をクリック
5. 数分後、ページ上部に公開URLが表示される

### 手順4: 公開URLを確認する

公開URLは以下の形式になります。

```
https://{GitHubユーザー名}.github.io/{リポジトリ名}/
```

例：`https://your-username.github.io/shukusta-support/`

各ページのURLは以下のとおりです。

| ページ | URL |
|--------|-----|
| サポート | `https://{ユーザー名}.github.io/{リポジトリ名}/index.html` |
| プライバシーポリシー | `https://{ユーザー名}.github.io/{リポジトリ名}/privacy.html` |
| 利用規約 | `https://{ユーザー名}.github.io/{リポジトリ名}/terms.html` |

### 手順5: App Store Connectに登録する

App Store Connectでアプリ情報を入力する際、以下のURLを設定してください。

| App Store Connect の項目 | 設定するURL |
|-------------------------|-------------|
| **サポートURL**（必須） | `https://{ユーザー名}.github.io/{リポジトリ名}/` |
| **プライバシーポリシーURL**（必須） | `https://{ユーザー名}.github.io/{リポジトリ名}/privacy.html` |
| **マーケティングURL**（任意） | 同上、またはアプリ紹介ページがあればそのURL |

## お問い合わせフォームの実装（任意）

現在のお問い合わせフォームはダミーの送信処理になっています。実際にメールを受信するには、以下のいずれかのサービスと連携してください。

### Formspree（おすすめ・無料枠あり）

1. [Formspree](https://formspree.io/) にアカウントを作成
2. 新しいフォームを作成し、フォームIDを取得
3. `index.html` の `<form>` タグを以下のように変更

```html
<form action="https://formspree.io/f/{あなたのフォームID}" method="POST">
```

4. `handleSubmit` のJavaScriptを削除

### Google Forms（代替案）

1. Google Formsでお問い合わせフォームを作成
2. `index.html` のフォーム部分をGoogle Formsの埋め込みコードに置き換え

## カスタムドメインの設定（任意）

独自ドメインをお持ちの場合、GitHub Pagesにカスタムドメインを設定できます。

1. リポジトリの Settings → Pages → Custom domain にドメインを入力
2. DNSプロバイダーでCNAMEレコードを設定
3. 「Enforce HTTPS」にチェックを入れる

詳細は [GitHub公式ドキュメント](https://docs.github.com/ja/pages/configuring-a-custom-domain-for-your-github-pages-site) を参照してください。
