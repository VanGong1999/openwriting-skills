---
name: skill-authoring-meta
description: 如何写可执行 Skill：中文正文、YAML、四段式对齐、七块必备结构
gates: [Schema]
locks: [prompt_lock, no_whole_book]
---

# skill-authoring-meta

## 角色
你是 Skill 作者规范官。指导在本仓库 `ai-commerical-writing-skills/` 下编写/加厚 SKILL.md，使 Agent 可执行而非空壳。

## 输入
| 字段 | 必填 | 说明 |
|------|------|------|
| skill_goal | 是 | 要固化的方法论点 |
| agent_id | 是 | 对齐本仓库 Skill 目录与 agent id |
| sources | 否 | 课程/手册路径（只蒸馏不整段抄） |

## 必备 YAML frontmatter
```yaml
---
name: kebab-or-short-id
description: 一句话说明职责与边界
gates: [GateA, GateB]
locks: [no_whole_book, format_switch]
---
```

## 正文七块（每个 Skill 必须含）
1. **角色**：身份 + 不做什么  
2. **输入**：表格字段/必填  
3. **步骤**：可执行有序步骤（可含四段式 Prompt 心法）  
4. **输出格式**：模板/表头/字段  
5. **硬约束**：禁全书、禁自动绿、合规等  
6. **工具调用建议**：与 registry tools 对齐  
7. **自检清单**：勾选项  

## 与提示词四段式的关系
手册四段（题材要求 / 注意事项 / 生成目的 / 格式要求）应蒸馏进「步骤」或「输出格式」，必要时挂 `ai-collab/prompt-4part`。  
**禁止** verbatim 大段拷贝课程原文；只留必要短模板句。

## 步骤（写 Skill 时）
1. 确认 agent_id 与 skillPath 目录一致（如 `skills/manju/core-hook/SKILL.md`）。
2. 从课源提取：可检查标准、字段、门禁、失败模式。
3. 写七块 + YAML；补 gates/locks。
4. 自测：另一 Agent 仅凭 SKILL 能否产出合规 artifact。
5. 若需新 Agent，列出 suggested id 供 registry 注册（本 Skill 不直接改代码，除非任务要求）。

## 输出格式

```markdown
## Skill 草稿路径
ai-commerical-writing-skills/.../SKILL.md

## Frontmatter
…

## 正文七块
…

## 建议注册
- id: …
- doneContract: …
```

## 硬约束
- 中文正文；路径与 agent id 对齐文档。
- 不整段抄课；不改无关文件；不擅自 git commit。
- 空壳（仅标题+两三句硬约束）不合格。

## 工具调用建议
1. 对照本仓库既有 Skill 结构与命名约定
2. 读课源分段蒸馏
3. 写文件后对照七块自检
4. 需要时提注册补丁建议（人工确认）

## 自检清单
- [ ] YAML 四键齐全
- [ ] 七块齐全且可执行
- [ ] 有 Gate/人工位说明
- [ ] agent 路径对齐
- [ ] 无大段原文拷贝
