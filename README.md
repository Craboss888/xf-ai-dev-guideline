<p align="center">
  <img src="assets/banner.png" alt="cc-preflight — 项目起飞前，先把环境配好" width="760">
</p>

# cc-preflight

**项目起飞前，先把环境配好。**

一个 Claude Code skill：新项目开工前敲一次 `/cc-preflight`，它把开发环境一次性配齐——**记忆文件、目录结构、必备装备**——逐项验证、拿证据汇报，然后才放你起飞。

```
你：/cc-preflight
AI：第 0 步 · 侦察……第 1 步 · 记忆文件……
    ✅ CLAUDE.md 已生成（含协作铁律）
    ✅ 目录结构就绪：scripts/ docs/ tests/ …
    ✅ 装备检测：playwright ✓  frontend-design ✓  agent-reach ⚠️ 需重启生效
    preflight 完成，等待任务指令。
```

## 为什么需要它

vibe coding 翻车，多半不是翻在写代码，而是翻在**裸奔开工**：

- 🧠 AI 不知道你的规矩——每个新会话都要从头调教一遍
- 🗂️ 文件越堆越乱——脚本、数据、笔记全在根目录打架
- 🧰 工具没装齐——做到一半发现缺东西，心流打断

cc-preflight 把这些前置工作压缩成一条命令。

## 它做三件事，然后验证

| | 配置 | 内容 |
|---|------|------|
| 1️⃣ | **记忆文件** | 生成项目 `CLAUDE.md`（协作铁律 · 回答方式 · 每轮自检 · 数据安全）+ `开发日志.md` 骨架 |
| 2️⃣ | **目录结构** | `scripts/ docs/ data/ tests/ references/ output/` 按项目类型裁剪——所有东西有明确的家 |
| 3️⃣ | **必备装备** | 按 manifest 清单：检测 → 安装 → 验证（playwright · frontend-design · superpowers · agent-reach · web-design-engineer） |

收尾输出 ✅ / ⚠️ / ❌ 逐项验证清单——**不是「我做了」，而是「你看」**：每条附文件路径或命令输出作证据。

## 核心理念：规则住在 CLAUDE.md，skill 只是安装器

CLAUDE.md 每个会话**自动加载**；skill 只在被调用那一次生效。

所以协作规则（先计划等放行、诚实有据、交付前自检……）不写在 skill 正文里，而是作为「载荷」由 preflight 写进项目的 CLAUDE.md——**装一次，之后每个会话天生守规矩**。

## 三条设计原则

- **仅手动触发** —— frontmatter `disable-model-invocation: true`。环境安装有副作用，不让模型自作主张。
- **幂等** —— 已存在的不覆盖、要改的先备份、拿不准的先问。跑第二遍不会弄坏任何东西。
- **诚实汇报** —— 装不上的（需重启 / 缺权限 / 缺网络）如实标注 ⚠️，绝不谎报已装。

## 安装

```bash
git clone https://github.com/Craboss888/cc-preflight.git ~/.claude/skills/cc-preflight
```

重开 Claude Code 会话，在项目根目录敲 `/cc-preflight`。

## 仓库结构

```
SKILL.md                    编排流程：侦察 → 记忆文件 → 目录 → 装备 → 可选 hook → 验证汇报
templates/
  CLAUDE.md骨架.md           投放载荷：协作铁律 / 回答方式 / 每轮自检 / 数据安全
  开发日志骨架.md
  启动prompt.md              preflight 后的开场模板（含装不了 skill 环境的后备版）
  常用指令.md                过程中随手用的追加指令
manifest/必备装备清单.md      装备清单：每项的用途 / 检测 / 安装指引 / 验证
hook/                       可选：每轮自检 stop hook（脚本 + 配置说明）
```
