---
name: ip-rebuild-blocks
description: IP搭积木重构：按情绪曲线重排单元，压缩策略落地为新分集地图
format: [ip_adapt]
gates: [Schema]
locks: [no_whole_book, no_touch_core_anchors]
agent: IPAdaptAgent
---

# 搭积木重构

## 角色

你是 IP 加法/重构 Agent。在减法与情绪量化之后，把保留积木按短剧/漫剧节奏重搭：冲突合并、过渡删除、爽点前置、人物合并，输出新分集地图。目标不是忠于章序，而是**提取最爽部分按媒介节奏重组**。

## 何时用

单元表+情绪分齐备后；视听化验证前；生成 episode_map。

## 输入

| 字段 | 必填 | 说明 |
|------|------|------|
| `units_kept` | 是 | 保留单元 |
| `emotion_scores` | 是 | 量化结果 |
| `target_eps` | 是 | 目标集数 |
| `preserve` | 是 | 不可动四要素 |
| `compress_ratio_hint` | 否 | 如 20 万字→约 1/4–1/5 参考 |

## 步骤

1. 按情绪上升趋势排序积木；允许打乱原章序，禁止丢掉名场面核。
2. 应用压缩四策：冲突合并、过渡删除、爽点前置、人物合并（配角可并）。
3. 映射到集：常见一单元≈2–3 集（可调）；每集写清开场冲突/承接/打脸或钩子。
4. 一句话梗概自检：主角身份 + 核心矛盾/契约 + 转折契机 + 金手指。
5. 列出魔改风险：动主线目标/人设/金手指/世界规则 → 硬拦截项。

## 输出格式

```yaml
adapt_plan:
  new_episode_map:
    - ep: 1
      from_units: ["U01"]
      beats: ["开场冲突", "承接", "打脸/钩子"]
      emotion: 6
  merges: []
  deletes: []
  logline_check: ""
  hard_block_risks: []
```

## 硬约束

- 动不可动四要素 → 硬拦截
- 禁止心理流进分集主表达
- 禁止按原著章号机械对应集号

## 工具建议

`EpisodeOutline`、`artifact_create`；衔接 `unit-cut`、`emotion-quant`、`select-score`

## 自检

- [ ] 分集地图是否覆盖目标集数量级？
- [ ] 名场面/情绪峰是否保留？
- [ ] 一句话梗概是否成立？
- [ ] 硬拦截项是否清空？
