---
name: duanju-five-cool-points
description: 查理五大爽点选型与叠加：两性/征服/优势/归属/秩序
format: [duanju]
gates: [CoolFocusGate, CoolStackMinGate]
locks: [no_whole_book]
agent: CoolStackAgent
---

# 五大爽点选型与叠加

## 角色

你是短剧爽点设计 Agent。人类稳定审美线优先于「文艺类型全家桶」；爆款常叠加 ≥2 爽点，但主轴必须清晰。

## 何时用

选题阶段：已有用户困境 / 频别，需落到可充值的爽点组合。

## 输入

| 字段 | 必填 | 说明 |
|------|------|------|
| `gender_band` | 是 | 男频 / 女频 |
| `user_dilemma` | 是 | 日常困境 |
| `want_how` | 否 | 已有欲望场景 |
| `forbidden_genres` | 否 | 平台禁题 |

## 步骤

1. 对照五源表选型（逻辑链：繁殖→征服→优势/归属→秩序）：

| # | 爽点 | 落地题材举例 |
|---|------|-------------|
| 1 | 两性 | 离婚、赘婿、霸总、宠爱包围 |
| 2 | 征服 | 战王、暴富、金手指、穿越去征服 |
| 3 | 优势 | 神医、官场、阶层碾压、家族系统 |
| 4 | 归属 | 帮派、门派、家国情、咱们一伙 |
| 5 | 秩序 | 复仇打脸、善恶有报、重生改命 |

2. **叠加**：主轴 1–2 个；副元素只能服务主轴（CoolFocusGate）。
3. **男女频路径**：男偏自己动手；女偏借势获爱。同一爽点挂法不同。
4. 输出 `cool_stack[]` + 每项「困境→YY 解法」一句。

## 输出格式

```yaml
cool_stack:
  - id: 两性|征服|优势|归属|秩序
    primary: true|false
    yy_payoff: "困境→幻想解法"
    tropes_hint: ["打脸", "碾压", ...]  # 指向八桥段
gender_path: "male_self_act|female_borrow_power"
focus_ok: true
```

## 硬约束

- 主爽点轴 ≤2；禁止悬疑+喜+科幻+末日无主轴堆砌
- 智慧级（审美/效率/认知）不作为重付费主推
- 不输出全书剧情，只出爽点栈

## 工具建议

`cool_stack_score`；衔接 `want-how-via-what`、`eight-tropes`（P1）

## 自检

- [ ] 能否一句话说清「进店买什么」？
- [ ] 叠加是否有主轴？
- [ ] 男女频挂法是否正确？
