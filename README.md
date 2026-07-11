# cc-preflight

开发环境「起飞前检查」的 Claude Code skill——**新项目开工前手动触发一次，把环境配好并逐项验证**，然后才开始真正的开发。

> 前身为 `xf-ai-dev-guideline`（协作守则文档版）。v2 重构为**环境安装器**：规则不再住在 skill 正文里，而是作为「载荷」写进每个项目的 CLAUDE.md（每个会话自动加载），skill 只负责安装与验证。

## 它做三件事（+ 验证）

1. **项目记忆文件**——按模板生成 CLAUDE.md（内含协作铁律、回答方式、每轮自检、数据安全规则）+ 开发日志.md 骨架
2. **目录结构**——`scripts/ docs/ data/ tests/ references/ output/` 按项目类型裁剪，所有东西有明确的家
3. **必备装备**——按 manifest 清单检测 → 安装 → 验证常用 skills / plugins（playwright、frontend-design、superpowers、agent-reach、web-design-engineer）

最后输出 ✅ / ⚠️ / ❌ 逐项验证清单（附证据），宣布 preflight 完成后停下等任务指令。

## 设计原则

- **仅用户手动触发**：frontmatter `disable-model-invocation: true`——环境安装有副作用，不让模型自作主张
- **幂等**：已存在的不覆盖、要改的先备份、拿不准的先问
- **诚实汇报**：装不了的（需重启 / 缺权限 / 缺网络）如实标注，绝不谎报已装

## 安装

```bash
git clone https://github.com/Craboss888/cc-preflight.git ~/.claude/skills/cc-preflight
```

重开 Claude Code 会话后，在项目根目录敲 `/cc-preflight` 触发。

## 结构

```
SKILL.md                     # 编排流程：侦察→记忆文件→目录结构→装备→可选hook→验证汇报
templates/CLAUDE.md骨架.md    # 投放载荷：协作铁律 / 回答方式 / 每轮自检 / 数据安全
templates/开发日志骨架.md
templates/启动prompt.md       # preflight 后的开场模板（含装不了 skill 环境的后备版）
templates/常用指令.md          # 过程中随手用的追加指令
manifest/必备装备清单.md       # 装备清单：每项的用途 / 检测 / 安装指引 / 验证
hook/                        # 可选：每轮自检 stop hook（脚本 + 配置说明）
```
