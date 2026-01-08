# Gigazine Notifier

GigazineのRSSフィードを自動取得し、新着記事をDiscordに投稿するBot。

## セットアップ

### 1. Discord Webhook URLを取得

1. Discordサーバーの設定 → 連携サービス → ウェブフック
2. 「新しいウェブフック」を作成
3. URLをコピー

### 2. Gistを作成（状態保存用）

1. https://gist.github.com にアクセス
2. ファイル名: `gigazine_state.json`、内容: `{}`
3. Secret Gistで作成
4. URLから **Gist ID** をコピー（例: `https://gist.github.com/username/abc123` → `abc123`）

### 3. Personal Access Token (PAT) を作成

1. https://github.com/settings/tokens → Generate new token (classic)
2. スコープ: `gist` のみチェック
3. トークンをコピー

### 4. リポジトリのSecretsを設定

Settings → Secrets and variables → Actions → New repository secret:

| Name | Value |
|------|-------|
| `DISCORD_WEBHOOK_URL` | Discord Webhook URL |
| `GIST_TOKEN` | 作成したPAT |
| `GIST_ID` | 作成したGistのID |

### 5. 有効化

1. リポジトリをGitHubにプッシュ
2. Actions タブで「Gigazine to Discord Bot」を確認
3. 「Run workflow」で手動テスト可能

## 動作

- **毎時0分**に自動実行
- 新着記事のみをDiscordに投稿
- 過去の投稿履歴はGistに保存（重複防止）
