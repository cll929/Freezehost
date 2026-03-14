# FreezeHost 自动续期

使用 Playwright + GitHub Actions 每天自动续期 FreezeHost 服务器。

## 配置步骤

### 1. Fork 或上传此仓库到 GitHub

### 2. 添加 Secrets

进入仓库 → Settings → Secrets and variables → Actions → New repository secret：

| Secret 名称       | 内容              |
|------------------|-------------------|
| `DISCORD_ACCOUNT` | Discord 账号，格式 `email,password`，例如 `foo@gmail.com,mypassword` |
| `TG_BOT` | Telegram 推送，格式 `chat_id,bot_token` |
| `GOST_PROXY` | 代理地址，如 `socks5://host:port`，不需要代理留空 |

### 3. 启用 Actions

进入 Actions 标签页，点击 "Enable GitHub Actions"。

### 4. 手动触发测试

Actions → FreezeHost 自动续期 → Run workflow

## 运行时间

每天 UTC 08:00（北京时间 16:00）自动运行。
可在 `.github/workflows/renew.yml` 的 cron 表达式中修改。

## 续期结果说明

| 结果 | 说明 |
|------|------|
| ✅ passed | 续期成功 |
| ⚠️ skipped | 余额不足，待赚够金币后下次自动重试 |
| ❌ failed | 登录失败或未知错误，查看 failure-screenshots |
