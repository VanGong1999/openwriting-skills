# OpenWriting Skills

面向 **Claude Code / Codex / OpenCode** 等 Agent 环境的写作 Skill 合集。按场景拆成三套可独立安装的技能包，覆盖：

- 企业公文与商业文档（含飞书办公集成）
- 通用创作课蒸馏的体裁写作（网文 / 短剧 / 剧本 / 新媒体等）
- 可执行的商业内容生产线（短剧 / 漫剧 / 长篇 / IP 等细粒度 Agent Skill）

**站点：** [https://vangong1999.github.io/openwriting-skills/](https://vangong1999.github.io/openwriting-skills/)



---

## 仓库结构

```
openwriting-skills/
├── README.md                          # 本文件
├── .gitignore
├── AI写作的缺点和问题汇总.md           # 课程口径笔记（可选参考）
├── gongwenwriting-skills/             # 公文 / 商业 / 飞书办公 Skill
├── ai-writing-skills/                 # 通用创作体裁 Skill（19 个）
└── ai-commerical-writing-skills/      # 商业写作生产线细粒度 Skill（约 134 个）
```

| 目录 | 定位 | 典型用法 |
|------|------|----------|
| [`gongwenwriting-skills/`](gongwenwriting-skills/) | 投标、竞品、新闻稿、内审、技术方案、飞书多维表报告等 | 办公写作 + 飞书自动化 |
| [`ai-writing-skills/`](ai-writing-skills/) | 故事 / 人物 / 网文 / 短剧 / 剧本 / 小红书 / 去 AI 味等 | Claude Code / Codex 独立安装 |
| [`ai-commerical-writing-skills/`](ai-commerical-writing-skills/) | 短剧 / 漫剧 / 男女频长篇 / 结构 / 拆书 / QC 等可执行 Skill；独立仓库见下 | 按目录或 `catalog.json` 检索调用 |

---

## 快速开始

### 1. 克隆

```bash
git clone https://github.com/VanGong1999/openwriting-skills.git
cd openwriting-skills
```

### 2. 按需安装某一套 Skill

**通用创作包（推荐先装）：**

```bash
ROOT="$(pwd)/ai-writing-skills"
SKILLS="story-fundamentals character-craft narration-craft web-novel-craft short-story-salt short-genre-verticals short-drama-manhua comedy-writing screenwriting-longform screenplay-analysis new-media-viral xiaohongshu-ops commercial-content compliance-content short-video-angles video-novel-production writer-practice-unblock ai-writing-workflow monetization-career"

mkdir -p ~/.claude/skills ~/.agents/skills
for s in $SKILLS; do
  ln -sfn "$ROOT/$s" ~/.claude/skills/$s
  ln -sfn "$ROOT/$s" ~/.agents/skills/$s
done
```

Claude Code：`/skill-name`　·　Codex：`$skill-name`

**公文 / 飞书包：** 将 `gongwenwriting-skills/<skill名>` 链到上述 skills 目录即可。

**商业生产线包：** 将 `ai-commerical-writing-skills` 下需要的子目录链入；也可用 `catalog.json` 做索引。

### 3. 配置环境变量（仅本地，勿提交）

涉及飞书或大模型调用时，在 shell / `.env`（已被 `.gitignore` 忽略）中配置，例如：

```bash
export FEISHU_APP_ID="your-app-id"
export FEISHU_APP_SECRET="your-app-secret"

# project-tracker-feishu 报告生成（OpenAI 兼容接口）
export LLM_API_KEY="your-llm-api-key"
export LLM_BASE_URL="https://api.example.com/v1"
export LLM_MODEL="gpt-4o-mini"   # 可选
```

---

## 一、`gongwenwriting-skills` — 公文与商业写作

企业办公向 Skill：从招标响应、竞品分析到飞书多维表周报。

### 飞书能力

| Skill | 说明 |
|-------|------|
| [`feishu-toolkit`](gongwenwriting-skills/feishu-toolkit/) | 飞书办公执行层：日历/会议室、消息、审批、多维表、通讯录、考勤。本地服务默认 `http://127.0.0.1:8002` |
| [`feishu-im-file-send`](gongwenwriting-skills/feishu-im-file-send/) | 将 docx/pdf/xlsx 等作为 **IM 聊天附件** 发送（勿用「只写云文档」冒充已送达） |
| [`project-tracker-feishu`](gongwenwriting-skills/project-tracker-feishu/) | 从飞书多维表读任务数据，生成 6 类管理报告，发群或导出 DOCX |

**启动 feishu-toolkit（摘要）：**

```bash
export FEISHU_APP_ID=...
export FEISHU_APP_SECRET=...
cd gongwenwriting-skills/feishu-toolkit/server
# 可参考 .env.example，不要提交真实 .env
uv run uvicorn feishu_toolkit.main:app --host 127.0.0.1 --port 8002
```

**project-tracker 六类报告：** 周进度简报、月度管理报告、项目节点报告、团队绩效分析、风险预警专报、季度汇报材料。

```bash
cd gongwenwriting-skills/project-tracker-feishu
python3 scripts/batch_generate_feishu.py --app-token <TOKEN> --chat-id <CHAT_ID>
# 或导出 DOCX
python3 scripts/batch_generate_feishu.py --app-token <TOKEN> --docx --output-dir ~/Desktop
```

### 商业与市场写作

| Skill | 用途 | 常见结构 / 产出 |
|-------|------|----------------|
| `bid-proposal-writer` | 投标 / 方案书 | 需求响应、实施计划；`proposal.md` / docx |
| `competitive-intel-writer` | 竞品分析 | SWOT、差距、策略；可选 scorecard |
| `customer-case-study-writer` | 客户案例 | Challenge → Solution → Results |
| `landing-page-writer` | 落地页 | AIDA |
| `product-one-pager-writer` | 产品单页 | FAB |
| `press-release-writer` | 新闻稿 / 公告 | 5W1H |
| `sales-email-writer` | 销售邮件 / 私信 | PAS |
| `market-research-writer` | 行业 / 市场调研 | TAM-SAM-SOM、PESTLE、五力等 |

### 技术与合规

| Skill | 用途 |
|-------|------|
| `tech-design-writer` | 技术方案 / 架构 / ADR / 接口说明 |
| `internal-audit-report` | 内审报告、发现清单、整改建议 |
| `risk-control-weekly` | 风控 / 稽核周报、风险矩阵 |
| `opencode-writer` | 经 OpenCode Bridge 做重文件解析与报告产出（需自备 Bridge） |

---

## 二、`ai-writing-skills` — 通用创作体裁（19 个）

从多门写作课蒸馏，**自包含**：只需本目录下 19 个 skill 文件夹，不依赖课程录音稿 / 讲义原件。详细路由见 [`ai-writing-skills/README.md`](ai-writing-skills/README.md)。

| 需求 | Skill |
|------|-------|
| 好故事标准、梗概、节拍质检 | `story-fundamentals` |
| 人物、反派、团队、识人 | `character-craft` |
| 画面、转场、POV、电影叙事 | `narration-craft` |
| 长篇网文、男女频、大纲爽点 | `web-novel-craft` |
| 盐选短篇通用流程 | `short-story-salt` |
| 盐选垂直：科幻/历史/悬疑等 | `short-genre-verticals` |
| 竖屏短剧、漫剧、充值钩 | `short-drama-manhua` |
| 喜剧（长剧 + 短剧） | `comedy-writing` |
| 电影 / 长剧 / Pilot | `screenwriting-longform` |
| 拉片打点、前史工作簿 | `screenplay-analysis` |
| 公众号爆文 | `new-media-viral` |
| 小红书入局与笔记 | `xiaohongshu-ops` |
| 带货文案 FABE | `commercial-content` |
| 审查 / 广告法 / 题材红线 | `compliance-content` |
| 短视频三角定位 | `short-video-angles` |
| 视频小说制作链 | `video-novel-production` |
| 卡文、拖延、同人边界 | `writer-practice-unblock` |
| AI 辅助、Prompt、去 AI 味 | `ai-writing-workflow` |
| 变现路径、投稿、接活 | `monetization-career` |

**冲突原则（摘要）：** 短剧「解压 > 审美 > 故事」；长剧「故事与节拍优先」；网文「期待感 + 日更」；新媒体「情绪 + 打开率」。收入/流量口播为经验口径，非保证。

---

## 三、`ai-commerical-writing-skills` — 商业内容生产线

细粒度、可执行的 Agent Skill（约 **134** 个，见 [`catalog.json`](ai-commerical-writing-skills/catalog.json)）。每个 Skill 含角色、输入表、步骤、输出格式、硬约束与自检清单。

**独立 GitHub 仓库：** [https://github.com/VanGong1999/ai-commerical-writing-personalagents](https://github.com/VanGong1999/ai-commerical-writing-personalagents)  
（与本 monorepo 中 `ai-commerical-writing-skills/` 目录对应；也可单独 clone 该仓库使用。）

### 模块一览

| 模块 | 内容侧重 |
|------|----------|
| `duanju/` | 短剧：选题、结构、场戏、对白、期待感、合规、交稿包等 |
| `manju/` | 漫剧：核心梗、分集、对白压力、分镜、QA |
| `male_long/` / `female_long/` | 男女频长篇：开篇钩、升级循环、金手指边界、节奏与雷区 |
| `short_novel/` | 短篇：开篇吸睛、章纲上限、正文充实 |
| `structure/` | 大纲 / 节拍 / 爽点模型 / 冲突 / 伏笔账本等 |
| `character/` | 人设七步、Big5、声口、灵魂自检 |
| `topic/` / `ip/` / `swap/` | 选题、世界观、IP 拆解与换元 |
| `kb/` | 拆书参数、情绪曲线、桥段挖掘、知识图谱、报告管线 |
| `quality/` / `qc/` | 去 AI 味、沉浸审计、圣经守卫、逻辑启发式 |
| `orchestrator/` / `memory/` / `_meta/` | 写作编排、章节记忆、Skill 作者规范 |

写作方法论与工具约定可独立使用；**不依赖**本仓库外的私有服务。

---

## 安全与贡献约定

1. **禁止**把真实 `LLM_API_KEY`、`FEISHU_APP_*`、群 `chat_id`、多维表 `app_token` 写入任何已跟踪文件。
2. 示例 ID 一律用占位符（如 `oc_xxx`、`bascnXXXXXXXXXXXXXXX`）。
3. 本地 `.env`、`.venv`、`.DS_Store`、日志已由 [`.gitignore`](.gitignore) 忽略。
4. 修改 Skill 时保持中文可执行结构；商业生产线 Skill 建议对齐 `_meta/SKILL.md` 的七块结构。

---

## 相关文档与仓库

| 资源 | 链接 |
|------|------|
| 本仓库（合集） | https://github.com/VanGong1999/openwriting-skills |
| 商业写作生产线（独立仓） | https://github.com/VanGong1999/ai-commerical-writing-personalagents |
| 通用创作路由 | [`ai-writing-skills/README.md`](ai-writing-skills/README.md) |
| 商业 Skill 包说明 | [`ai-commerical-writing-skills/README.md`](ai-commerical-writing-skills/README.md) |
| 商业 Skill 索引 | [`ai-commerical-writing-skills/catalog.json`](ai-commerical-writing-skills/catalog.json) |
| 飞书 toolkit | [`gongwenwriting-skills/feishu-toolkit/README.md`](gongwenwriting-skills/feishu-toolkit/README.md) |
| AI 写作问题笔记 | [`AI写作的缺点和问题汇总.md`](AI写作的缺点和问题汇总.md) |

---

## License / 使用说明

Skill 文本供 Agent 调用与二次改编；课程口播中的收入、流量数字仅为经验口径。对外发布内容请自行完成合规与事实核验。
