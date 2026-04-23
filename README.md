# 🎵 楽譜アプリ

音声で曲名を話すと、Google DriveからPDFを検索して全画面表示するWebアプリです。
同名の音声ファイルがあれば、楽譜と一緒に再生することもできます。

---

## 使い方

1. [アプリを開く](https://olivesoap2000-cell.github.io/MusicScoreApp/)
2. **「Googleでログイン」** をタップ
3. マイクボタンをタップして曲名を話す（例：「荒城の月」）
4. 楽譜（PDF）が全画面で表示される
5. **×ボタン** で最初の画面に戻る

---

## 音声再生機能

### 動作フロー

1. PDFを開くと、同じ名前の音声ファイル（MP3 / M4A / WAV等）をGoogle Driveで自動検索
2. 見つかれば画面下部に再生バーが表示される
3. ▶ボタンで再生、■ボタンで停止
4. プログレスバーをタップしてシーク可能
5. PDFを閉じると自動で停止

### 注意点

- Drive内にPDFと同じ名前の音声ファイルがある場合のみ再生バーが表示されます
  - 例：`Fur_Elise.pdf` → `Fur_Elise.mp3` を自動検索
- 音声ファイルが見つからない場合は再生バーは表示されません

---

## ファイルの置き方（各ユーザー共通）

ログインすると**自分のGoogle Drive全体**からPDF・音声ファイルを検索します。
フォルダの場所は問いません。ファイル名に曲名を含めてください。

```
Google Drive（各自）
├── 荒城の月.pdf
├── 荒城の月.mp3      ← 同名の音声があれば再生バーが表示される
├── Fur_Elise.pdf
├── Fur_Elise.mp3
└── （サブフォルダでもOK）
```

---

## 初回セットアップ手順（開発者向け）

### 1. Google Cloud Console の設定

#### Google Drive API を有効化
1. [Google Cloud Console](https://console.cloud.google.com) にアクセス
2. 「APIとサービス」→「ライブラリ」
3. 「Google Drive API」を検索して有効化

#### OAuth 同意画面の設定
1. 「APIとサービス」→「OAuth同意画面」（Google Auth Platform）
2. アプリ名・サポートメールを入力して作成
3. 「対象」→「**アプリを公開**」でGoogleアカウントを持つ全員が使用可能になる

#### OAuth クライアント ID の作成
1. 「APIとサービス」→「認証情報」→「認証情報を作成」→「OAuthクライアントID」
2. アプリの種類：**ウェブアプリケーション**
3. 「承認済みのJavaScript生成元」に以下を追加：
   ```
   https://olivesoap2000-cell.github.io
   ```
4. 作成されたクライアントIDを `index.html` の `CLIENT_ID` に設定

### 2. GitHub Pages の設定

1. リポジトリの「Settings」→「Pages」
2. Branch：`main` / Folder：`/ (root)` → Save
3. 公開URL：`https://olivesoap2000-cell.github.io/MusicScoreApp/`

---

## 仕様

| 項目 | 内容 |
|------|------|
| 対象ユーザー | Googleアカウントを持つ全員 |
| 検索対象 | ログインユーザー自身のGoogle Drive全体 |
| 検索対象ファイル | PDF（楽譜）・MP3/M4A/WAV等（音声） |
| 音声認識 | Web Speech API（日本語） |
| PDF表示 | Google Drive プレビュー（全画面） |
| 認証 | Google OAuth 2.0 |
| ホスティング | GitHub Pages |

---

## 動作環境

- **推奨ブラウザ**：Safari（iOS / iPadOS）、Chrome
- インターネット接続が必要です
- 音声認識にはマイクの使用許可が必要です
