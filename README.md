# 🎵 楽譜アプリ

音声で曲名を話すと、Google Driveの楽譜フォルダからPDFを検索して全画面表示するWebアプリです。

---

## 使い方

1. [アプリを開く](https://olivesoap2000-cell.github.io/MusicScoreApp/)
2. **「Googleでログイン」** をタップ
3. マイクボタンをタップして曲名を話す（例：「荒城の月」）
4. 楽譜が全画面で表示される
5. **×ボタン** で最初の画面に戻る

---

## 初回セットアップ手順

### 1. Google Cloud Console の設定

#### Google Drive API を有効化
1. [Google Cloud Console](https://console.cloud.google.com) にアクセス
2. 「APIとサービス」→「ライブラリ」
3. 「Google Drive API」を検索して有効化

#### OAuth 同意画面の設定
1. 「APIとサービス」→「OAuth同意画面」（Google Auth Platform）
2. アプリ名・サポートメールを入力して作成
3. 「対象」→「テストユーザー」に自分のGmailアドレスを追加

#### OAuth クライアント ID の作成
1. 「APIとサービス」→「認証情報」→「認証情報を作成」→「OAuthクライアントID」
2. アプリの種類：**ウェブアプリケーション**
3. 「承認済みのJavaScript生成元」に以下を追加：
   ```
   https://olivesoap2000-cell.github.io
   ```
4. 作成されたクライアントIDを `index.html` の `CLIENT_ID` に設定済み

---

### 2. Google Drive の楽譜フォルダ

- フォルダID：`1Yo2IyNy3-bbbphlISM3QJRIGdv_gv1iP`
- このフォルダおよびサブフォルダ内のPDFを検索します
- ファイル名に曲名を含めてください（例：`荒城の月.pdf`）

---

### 3. GitHub Pages の設定

1. リポジトリの「Settings」→「Pages」
2. Branch：`main` / Folder：`/ (root)` → Save
3. 公開URL：`https://olivesoap2000-cell.github.io/MusicScoreApp/`

---

## 注意事項

- **ログインできるのはテストユーザーに登録されたアカウントのみ**です
- 検索されるのは**ログインしたユーザー自身のGoogle Drive**です
- 音声認識には **Safari（iOS/iPadOS）** または **Chrome** を推奨します
- インターネット接続が必要です

---

## 技術仕様

| 項目 | 内容 |
|------|------|
| 音声認識 | Web Speech API（日本語） |
| ファイル検索 | Google Drive API v3 |
| PDF表示 | Google Drive プレビュー（iframe） |
| ホスティング | GitHub Pages |
| 認証 | Google OAuth 2.0 |
