# xf_ai_develop_guideline

一套「用 AI 从 0 解决问题」的 Claude Code skill —— 协作守则。
**方向与验收标准由人来定，AI 负责执行，并随时接受校验。**

## 它管什么

- **5 条铁律**：① 不主动开工（等放行）② 诚实有据、不编造 ③ 交付前自检 ④ 缺权限先问、不绕路 ⑤ 先计划再动手
- **6 步工作流**：对齐验收标准 → 不懂先讲原理 → 出计划 → 先攻最难核心并实测 → 逐步报告 → 卡住先说
- **每轮自检**：核心验证了没 / 有没有跑偏 / 该记的记了没 / 有没有绕路
- **文件管理**：每个项目只维护 `CLAUDE.md`（最重要的）+ 开发日志（细碎过程）
- **测试规范**：每个测试单独文件夹、目标明确
- `templates/`：XML 结构的启动 prompt + 常用追加指令
- `hook/`：每轮自检 stop hook（脚本 + 配置说明）

## 安装

克隆到 Claude Code 的 skills 目录（目标目录名用下划线版，与 skill 名一致）：

```bash
git clone https://github.com/Craboss888/xf-ai-dev-guideline.git ~/.claude/skills/xf_ai_develop_guideline
```

重开 Claude Code 会话后，可 `/xf_ai_develop_guideline` 调用，或按描述自动触发。

## 用法

新任务开始时，先加载本 skill，再用 `templates/启动prompt.md` 开场、填空即可。

---

个人开发方法论，欢迎参考自用。
