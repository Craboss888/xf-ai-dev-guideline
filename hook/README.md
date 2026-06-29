# 每轮自检 hook —— 配置说明

## 它是什么
一个 **stop hook**：每轮回复结束时自动打印一份自检清单（核心验证了没 / 有没有跑偏 / 该记的记了没 / 有没有绕路），避免陷入"代码跑通但没真正解决问题"。

## ⚠️ 重要：hook 不是 skill 的一部分
hook 由 Claude Code 的 **`settings.json`** 配置、由 harness 执行——**不是 skill 或 AI 能自己开启的**。所以这个目录里放的是「脚本 + 配法」，真正生效要你在目标机器上配一次。

## 怎么配
1. 给脚本加可执行权限：`chmod +x 每轮自检hook.sh`
2. 在 `~/.claude/settings.json` 的 `hooks.Stop` 里加一条 command，指向本脚本的**绝对路径**。
   - 格式**参照你环境里已有的 stop hook 配置**（照现成的写最稳，别凭记忆拼）。大致长这样：
     ```json
     { "hooks": { "Stop": [ { "hooks": [ { "type": "command", "command": "bash /绝对路径/每轮自检hook.sh" } ] } ] } }
     ```
3. 重开 Claude Code 会话生效。

## ⚠️ 在受限 / 陌生环境能不能用，先实测
能不能改目标机器的 `settings.json` / 放脚本，往往是未知项：
- **能配** → 配上，让它每轮自动提醒。
- **不能配** → 不依赖它：`SKILL.md` 第三节「每轮自检」已把同样的清单写成规则，靠 AI 自觉每轮过一遍（不如 hook 强制，但内容覆盖到了）。
