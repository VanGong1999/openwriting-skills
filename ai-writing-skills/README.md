# 写作 Skills（19 个 · Claude Code / Codex · 可独立分发）

从多门写作课蒸馏合并。遵循 [Agent Skills](https://agentskills.io/specification)（`name` + `description`）。

**自包含**：上线只需打包本目录下 19 个 skill 文件夹，**不需要**课程 `notes/` / `讲义/` / `录音稿/`。

## 体裁路由

| 需求 | Skill |
|------|-------|
| 好故事标准、梗概、十五步/节拍质检 | `story-fundamentals` |
| 人物、反派、团队、延迟满足识人 | `character-craft` |
| 画面、转场、POV、外貌、流畅、电影叙事 | `narration-craft` |
| 长篇网文、男女频、打斗、大纲爽点、番茄 | `web-novel-craft` |
| 盐选短篇通用流程 | `short-story-salt` |
| 盐选垂直：科幻/历史/悬疑/萌燃/富兰克林 | `short-genre-verticals` |
| 竖屏短剧、漫剧、充值钩子 | `short-drama-manhua` |
| 喜剧（长剧元素 + 短剧喜剧） | `comedy-writing` |
| 电影/长剧、Pilot | `screenwriting-longform` |
| 拉片打点、前史工作簿 | `screenplay-analysis` |
| 公众号爆文 | `new-media-viral` |
| 小红书入局与万赞笔记 | `xiaohongshu-ops` |
| 带货文案 FABE/模板 | `commercial-content` |
| 审查/广告法/题材红线自检 | `compliance-content` |
| 短视频三角定位与 3-2-4 | `short-video-angles` |
| 视频小说 30 秒制作链 | `video-novel-production` |
| 卡文、拖延、训练、同人边界 | `writer-practice-unblock` |
| AI 辅助、Prompt、去 AI 味 | `ai-writing-workflow` |
| 变现路径、投稿、接活总图 | `monetization-career` |

**冲突原则**：短剧「解压 > 审美 > 故事」；长剧「故事与节拍优先」；网文「期待感 + 日更」；新媒体「情绪 + 打开率」。

## 安装（19 个）

```bash
ROOT="/绝对路径/到/skills"
SKILLS="story-fundamentals character-craft narration-craft web-novel-craft short-story-salt short-genre-verticals short-drama-manhua comedy-writing screenwriting-longform screenplay-analysis new-media-viral xiaohongshu-ops commercial-content compliance-content short-video-angles video-novel-production writer-practice-unblock ai-writing-workflow monetization-career"

mkdir -p ~/.claude/skills ~/.agents/skills
for s in $SKILLS; do
  ln -sfn "$ROOT/$s" ~/.claude/skills/$s
  ln -sfn "$ROOT/$s" ~/.agents/skills/$s
done
```

Claude Code：`/skill-name`　·　Codex：`$skill-name`

## 口径

收入/流量口播 = **经验口径，非保证**。不确定标 **【待核实】**。
