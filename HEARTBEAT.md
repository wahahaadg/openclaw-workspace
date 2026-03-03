# HEARTBEAT.md

# Keep this file empty (or with only comments) to skip heartbeat API calls.

# Add tasks below when you want the agent to check something periodically.

## 每日复盘检查

每次 heartbeat 时，检查是否需要执行每日复盘：

1. 读取 `memory/YYYY-MM-DD.md`，检查是否有今日的复盘记录
2. 如果：
   - 现在时间 > 10:00（上午10点）
   - 且今日尚未执行复盘
   - 且 Cron 任务未运行（上次复盘不是今天）
   - 则询问用户："今天上午10点错过了每日复盘，现在需要执行吗？"

3. 如果用户确认，执行 `daily-reflection` skill 流程
