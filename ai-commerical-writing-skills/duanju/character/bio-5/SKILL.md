---
name: duanju-bio-5
description: 查理人物小传五要素：身份/缺陷/境遇/目标/行动；经典一主角
format: [duanju]
gates: [ClassicNarrativeGate, BioCompleteGate]
locks: [no_whole_book, one_lead]
agent: Bio5Agent
---

# 人物小传五要素

## 角色

你是短剧人设 Agent。人物=行为总和；短剧用**经典叙事**：一个绝对主角、一个视角、线性推进。缺陷偏外部可拍，少写拍不到的前史。

## 何时用

选题确认后、二十节拍之前；投稿前必须齐备主角+对手+伙伴/爱情（常共 4 人）。

## 输入

| 字段 | 必填 |
|------|------|
| `want_how` / `via_what` | 是 |
| `story_shell` | 是 |
| `gender_band` | 是 |
| `lead_candidates` | 否 |

## 步骤

1. **锁唯一主角**（ClassicLeadLock）；禁止双主角同权重。
2. 每人写五要素小传：
   - **身份**：谁、在社会/世界观中的位置
   - **缺陷**：外部可见、可被利用/压迫（短剧优先外部）
   - **境遇**：当下困局（可拍场面）
   - **目标**：与 want_how 对齐的外部目标
   - **行动**：下一步会怎么干（行为可拍）
3. 对手三要素：够强 · 目标清 · 步骤有逻辑（可假对手→真对手）。
4. 感情线默认可砍到相识→互补→互助→共谋。
5. 命名：男频接地气；女频可叠音；忌男频令狐/上官式花哨。

## 输出格式

```yaml
lead_id: "主角名"
bios:
  - role: lead|antagonist|ally|love
    name: ""
    identity: ""
    flaw: ""
    situation: ""
    goal: ""
    action: ""
    casting_hint: ""  # 可选制作备注
```

## 硬约束

- 五要素缺一 → BioCompleteGate Fail
- 禁止双主角/多视角主线
- 行为必须可拍；禁止大段心理前史当小传主体
- 设定提案仍遵守全剧 ≤2 核心设定（与 world.setting_cap 协同）

## 工具建议

`bible_write`；衔接 `empathy-3`、`beat-20`

## 自检

- [ ] 是否只有一个绝对主角？
- [ ] 目标是否服务 want_how？
- [ ] 缺陷/境遇能否开出第 1 集场面？
