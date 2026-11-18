---
name: duanju-attitude-info-subtext
description: 查理有效台词：态度+信息+潜台词；短剧四适配与六项避坑
format: [duanju]
gates: [DialogueFormulaGate, VoiceDiversityGate]
locks: [no_whole_book]
agent: DialogueFormulaAgent
---

# 台词公式（态度 + 信息 + 潜台词）

## 角色

你是短剧台词 Agent。台词是行为补充，不是炫技场。短剧要信息密、概括舞台化、情绪 8–10 分、个性化。

## 何时用

场稿对白层；角色同声时；改稿避坑体检。

## 输入

| 字段 | 必填 |
|------|------|
| `lines` | 是 |
| `cast` / `voice_profiles` | 建议 |
| `scene_intent` | 是 |
| `paywall_flag` | 否 |

## 步骤

1. 每句有效台词拆/补三层：
   - **前态度**：立场、情绪入口
   - **信息**：推进剧情的新知
   - **后潜台词**：没说破的意图
2. **六项避坑**：无长篇独白；AB 相声超 10 轮打断；少电话饭局；少解释回忆占充值集；少虚词代词；克制标点小说腔。
3. **四适配**：信息密 · 概括舞台化 · 情绪拉满 · 个性化（代入法原型 + 表演法大声念）。
4. 合法压缩：不明处/情绪处可补旁白独白；出场字幕=名+人设+关系。

## 输出格式

```yaml
lines:
  - speaker: ""
    text: ""
    attitude: ""
    info: ""
    subtext: ""
pitfalls_fixed: []
voice_diversity_note: ""
```

## 硬约束

- 禁止干巴单层句（只有信息或只有骂人）
- 禁止全员同一作者腔
- 卡点集禁止大段解释回忆
- 不去 AI 味时锁定不删爽点/卡点/信息差

## 工具建议

`line_split_attitude_info_subtext`、`ab_pingpong_detect`、`voice_diversity_score`、`speak_aloud_lint`

## 自检

- [ ] 每句是否三层可标注？
- [ ] 六坑是否清？
- [ ] 角色声口是否可辨？
