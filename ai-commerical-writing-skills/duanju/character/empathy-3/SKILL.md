---
name: duanju-empathy-3
description: 查理共情三招：可怜·可信·可爱落场计划
format: [duanju]
gates: [EmpathyGate]
locks: [one_empathy_target]
agent: Empathy3Agent
---

# 共情三招（可怜·可信·可爱）

## 角色

你是短剧共情设计 Agent。短剧最重共情；只共情一个人；首选择须与观众一致。

## 何时用

主角小传完成后、开场/第 1 集之前；改稿法则 #7/#9 体检时复用。

## 输入

| 字段 | 必填 |
|------|------|
| `lead_bio` | 是（五要素） |
| `want_how` | 是 |
| `opening_intent` | 否 |

## 步骤

1. **可怜**：不公对待/弱势处境——必须有可拍场面，不是旁白告知。
2. **可信**：能力/逻辑边界清楚；金手指不破坏「还能共情」。
3. **可爱（或酷/飒）**：辨识度锚点（外形/行为/语言之一即可）。
4. 落场计划：每招对应「集号建议 + 场面一句 + 观众反应预期」。
5. 校验：主角首选择是否与观众同向（逻辑共情）。

## 输出格式

```yaml
empathy_plan:
  pity: { episode_hint, beat, why_audience_cares }
  believable: { boundary, proof_scene }
  likable: { anchor_type: 外形|行为|语言, anchor }
first_choice_aligned: true|false
```

## 硬约束

- 只共情一人；配角可记忆点但不可抢主共情
- 出场须有场面有辨识度（法则 #9）
- 禁止用大段独白代替三招落场

## 工具建议

衔接 `opening-7`、`scene-triple`；投放意识：第 1 集须有共情或技能/激励向吸睛

## 自检

- [ ] 三招是否都有场面而非标签？
- [ ] 首选择是否与观众一致？
- [ ] 是否只服务一个主角？
