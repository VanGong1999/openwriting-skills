# AI Commercial Writing Skills

商业内容生产线细粒度 Agent Skill（短剧 / 漫剧 / 长篇 / IP / 拆书 / QC 等）。

**独立仓库：** [https://github.com/VanGong1999/ai-commerical-writing-personalagents](https://github.com/VanGong1999/ai-commerical-writing-personalagents)

本目录也会随 [openwriting-skills](https://github.com/VanGong1999/openwriting-skills) 一并分发。

## 内容

- 约 **134** 个可执行 Skill，索引见 [`catalog.json`](catalog.json)
- 每个 Skill 含：角色、输入、步骤、输出格式、硬约束、自检清单
- **不含** API 密钥、飞书会话 ID、个人隐私或私有服务凭证

## 主要模块

| 模块 | 侧重 |
|------|------|
| `duanju/` | 短剧选题、结构、场戏、对白、交稿 |
| `manju/` | 漫剧核心梗、分集、对白、分镜 |
| `male_long/` / `female_long/` | 男女频长篇节奏、金手指、雷区 |
| `short_novel/` | 短篇开篇与章纲 |
| `structure/` / `character/` / `topic/` | 结构、人设、选题 |
| `kb/` | 拆书与知识库报告 |
| `quality/` / `qc/` | 去 AI 味、逻辑与质检 |
| `orchestrator/` / `memory/` / `_meta/` | 编排、记忆、作者规范 |

## 使用

将需要的子目录链到 Claude Code / Codex skills 目录，或按 `catalog.json` 检索后 `skill_read`。

```bash
# 示例：仅安装短剧相关
ln -sfn "$(pwd)/duanju" ~/.claude/skills/duanju-commerical
```

## 安全

- 禁止把真实密钥、群 ID、多维表 token 写入本仓库
- 示例一律用占位符
- 本包为写作方法论与流程 Skill，不依赖外部私有「写作工作流」服务
