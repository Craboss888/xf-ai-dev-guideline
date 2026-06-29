# 配置「每轮自检 hook」——给 AI 执行的指令

> 前提：本 skill 已装在 `~/.claude/skills/xf_ai_develop_guideline/`。
> 用途：把本 skill 自带的每轮自检脚本，配成 Claude Code 的 stop hook，让每轮回复结束时自动提醒自检。

请按以下步骤帮我配置（逐步做，遇到拿不准先问我，别擅自绕路）：

1. **找脚本 + 加权限**：脚本在 `~/.claude/skills/xf_ai_develop_guideline/hook/` 下（名字含「每轮自检」、是个 `.sh`）。确认它存在；若文件名是中文、担心路径编码，先重命名为英文（如 `self_check_hook.sh`）；用 `chmod +x` 加可执行权限。
2. **先备份**：改 `~/.claude/settings.json` 之前，先复制一份备份。
3. **追加 Stop hook**：在 settings.json 的 `hooks.Stop` 里**追加**一条 command，用 bash 执行该脚本的**绝对路径**。若已有别的 Stop hook，**保留它们、只追加，别覆盖**。
4. **格式查官方**：hook 配置的字段格式**以 Claude Code 官方文档为准，别凭记忆拼**；拿不准先查、或问我再动。
5. **验证**：配完告诉我要不要重开会话生效，并触发一次让我确认它真的工作。

---

> 若这台机器不允许改 `settings.json`：不必配 hook——`SKILL.md`「每轮自检」一节已把同样的清单写成规则，你照着每轮自觉过一遍即可（效果覆盖到，只是不自动）。
