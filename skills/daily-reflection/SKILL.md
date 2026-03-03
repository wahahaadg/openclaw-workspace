---
name: daily-reflection
description: "每日0点流程：先同步 .openclaw 至 GitHub，再自我复盘与优化。 触发词：每日复盘、nightly review、sync & improve。"
metadata: { "openclaw": { "emoji": "📝", "requires": { "bins": ["git", "curl"] } } }
---

# 每日复盘流程

## 触发条件

当用户说以下任意关键词时触发：
- "每日复盘"
- "nightly review"
- "sync & improve"

## 完整流程

### 1. 备份（优先执行）

进入工作目录并推送到远程仓库。

```
cd ~/.openclaw/workspace
git add .
git commit -m "Daily backup: $(date '+%Y-%m-%d')"
git push origin master
```

**若同步失败，记录报错但继续执行复盘。**

---

### 2. 内省与分析

1. **读数据**：回放当日 `memory/` 与会话记录，对比 `MEMORY.md` 基线。
2. **找问题**：识别理解偏差、低效操作、用户纠正点。
3. **记日志**：将复盘结论（简练）追加到当日 `memory` 文件。

---

### 3. 沉淀与调整

1. **更新记忆**：提炼通用教训入 `MEMORY.md`，删除过时信息。
2. **微调配置**：根据痛点优化 `AGENTS.md`（规则）或 `TOOLS.md`（工具）。
3. **补强能力**（按需）：
   - **缺能力**：搜索 Skill（ClawHub/npm），只列出推荐，**不自动装**。
   - **需自动化**：写 Python/Bash 草稿至 `workspace/skill_drafts/`，**只写不跑**。

---

### 4. 简报输出

输出中文总结：
- **同步**：Git 推送状态
- **复盘**：今日教训与配置变更
- **建议**：推荐的 Skill 或脚本草稿（如有）

**重要**：复盘完成后，必须把简报内容发送到 Telegram：
- 使用 `openclaw message send --channel telegram --target <用户ID> --message "<复盘内容>"`
- 用户ID可在 `channels.telegram.allowFrom` 中找到，或查看日志

---

## 红线（必须遵守）

- **严禁**未经确认安装 Skill 或执行草稿
- **严禁**随意修改 `SOUL.md`
- 评价务必客观犀利，拒绝废话

---

## 注意事项

- 复盘任务可使用 Sonnet 模型降低成本（复盘不需要强推理）
- 建议配合 Cron 定时任务在每天凌晨自动触发
