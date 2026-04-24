# zac-skills 执行规划

> 来源: 2026-04-25 会话，规划下一阶段任务
> 上下文会话 ID: `9c3798e2-2f3e-402e-8739-409a4d9fb6eb`

## 当前状态（v0.1）

- 骨架完整：dev / writing / product / life / meta 五板块 + RESOLVER.md + scripts/verify
- Waza 8 skill 原样搬入 dev/ 和 meta/，待 Zac 化
- writing/ 板块空（只有 README）
- product / life 板块空

## 优先级排序

### P0 — writing/makerlog 迁移 + 瘦身（紧急，效果直接影响日常博客写作）

**背景**：
- 原版博客提示词在芦苇项目 `/Users/zac/CLAUDE.md`，4/4 迁移到 skill 时被改成指针（无备份，home 不是 git repo）
- 迁移后的 skill `/Users/zac/.claude/skills/write-makerlog/skill.md` 从原版 **37 行膨胀到 313 行**
- 原版（4/4 迁移前）备份在芦苇项目：`docs/blog/makerlog/ORIGINAL-PROMPT-2026-03-22.md`（从 3/22 会话 JSONL 里恢复出来的）
- 用户实测反馈："skills 效果非常不好"

**膨胀了什么（必须砍）**：
1. 20+ 条五阶段 Checklist（A1-E4）
2. 10 条 Voice 规范（V0-V10，带✅❌对比举例）
3. 6 种句式分类表 + 强制交替
4. 强制"工程格言 ≤25 字" / 强制 1400-1800 字 / 强制"具体数字 ≥ 3 个" / 强制"技术细节段 ≥ 3 个"
5. 强制每个 ## 小标题是具体事件名

**原版的特点（必须保留）**：
- 流程只有 3 步（回顾素材 → 写作 → 保存）
- 第一人称"我"视角，但不强制 AI 视角
- 内容方向 8 种可选但明确"选 1-2 个展开，不要面面俱到"
- 结构/长度/风格全部自由发挥
- 人文视角是"真的有共鸣时才写，一篇最多一次"
- 没有 Checklist、没有 Voice 规范、没有句式分类表

**三种修复方案（跟用户讨论过）**：
- **温和**：Checklist 砍到 5 条核心，Voice 规范挪附录
- **中等**：接近原版 40 行，保留"AI 视角"和"隐私红线"两条现代化补充
- **激进**：直接用 ORIGINAL-PROMPT 替换，一字不改

**用户倾向（从上下文推断）**：中等方案——因为他明确说 skill 效果差，但也保留了 4/14 的调整痕迹说明不是全盘否定

**执行步骤**：
1. 读 `/Users/zac/Xcode/AI assiant/docs/blog/makerlog/ORIGINAL-PROMPT-2026-03-22.md`（原版）
2. 读 `/Users/zac/.claude/skills/write-makerlog/skill.md`（当前膨胀版）
3. 读 `/Users/zac/Xcode/AI assiant/docs/blog/makerlog/writing-reflection.md`（活文档，**这个不要合并到 skill 里**，保留在芦苇项目做跨篇回顾记录）
4. 按中等方案合成新版写入 `/Users/zac/zac-skills/skills/writing/makerlog/SKILL.md`
5. 确认用户认可后，更新 `/Users/zac/.claude/skills/write-makerlog/skill.md` 指向新版（或软链接）

**关键红线**：
- 不要把 writing-reflection.md 的内容搬进 skill——那是活文档，每 5 篇更新一次，skill 不该追着它变
- AI 视角要求（"涉及用户时用 'Zac 给我看了...'"）保留——博客定位变了，这是合理补充
- 隐私红线（不暴露提示词原文 / 内部函数名 / 定价）保留——这是现代化必需

### P1 — writing/official-blog 迁移

当前在 `/Users/zac/.claude/skills/write-official-blog/skill.md`（4/4 版本，没被改过）。

**不需要瘦身**——这个版本是原版，效果没问题。直接搬到 `/Users/zac/zac-skills/skills/writing/official-blog/SKILL.md`。

### P1 — writing/publish-blog 迁移

发布到 Quaily 的流程 skill，当前在芦苇项目或全局 skill 目录。直接搬。

### P2 — dev/ 板块 Zac 化

Waza 6 个 dev skill（think / check / hunt / design / health / write）原样搬入，待改造。

**改造原则**（用户明确说过）：
- 先用 Waza 的逻辑跑一段时间
- 跑的过程中发现问题或不合自己用法的，再一个一个改
- 不要一开始就大改

**优先改造候选**（从用户现有工作流推断）：
1. `design` — 用户对 UI 设计有强意见（参考 pbakaus/impeccable、getdesign），可能最先想 Zac 化
2. `write` — 开发语境的 prose，可能跟 writing/ 板块有重叠，需要划清边界

### P2 — meta/ 板块 Zac 化

Waza 2 个 meta skill（read / learn）。read 已被用户提到想 Zac 化（具体原因在 4/24 会话里，需要翻 session）。

### P3 — product / life 板块填充

**product 板块候选**（从芦苇项目提炼）：
- `research` — 竞品/产品研究规范（当前在 `docs/research/` 散落）
- `decide` — 决策记录（芦苇核心产品理念"可溯源决策链"的工作流版）
- `service-design` — 服务三条纪律（`memory/feedback_service_design_discipline.md`）

**life 板块候选**：
- `reading` — 读书记录
- `watching` — 影视记录
- `reflection` — 个人反思

这些都是芦苇项目里已有的习惯，提炼成 skill 就是了。

## 执行建议

**如果是单个 agent 一次性推进**：
- 只做 P0（writing/makerlog 瘦身迁移）
- P0 做完让用户实测一天的博客写作体验，反馈 OK 再往后推

**如果是多个 agent 并行**：
- Agent A: P0 writing/makerlog（关键路径，需要最仔细）
- Agent B: P1 writing/official-blog + publish-blog（纯迁移，低风险）
- Agent C: P3 product 板块骨架（从芦苇项目提炼，参考资料全在 repo 里）

**不建议同时做的**：
- P2 dev Zac 化——用户明确说"先用 Waza 原版跑一段"，别抢跑
- 任何涉及修改 `/Users/zac/.claude/skills/` 下现有 skill 的操作——先在 zac-skills repo 里做好，用户确认再同步

## 参考资料地图

| 资源 | 位置 | 用途 |
|---|---|---|
| 原版博客提示词 | 芦苇 `docs/blog/makerlog/ORIGINAL-PROMPT-2026-03-22.md` | makerlog skill 瘦身的黄金标准 |
| 当前膨胀 skill | `/Users/zac/.claude/skills/write-makerlog/skill.md` | 对照看砍什么 |
| 官方博客 skill | `/Users/zac/.claude/skills/write-official-blog/skill.md` | 直接搬 |
| 写作反思活文档 | 芦苇 `docs/blog/makerlog/writing-reflection.md` | **不搬**，留在芦苇做跨篇回顾 |
| Waza 原 repo | https://github.com/tw93/waza | dev/ + meta/ 的源 |
| 芦苇项目 | `/Users/zac/Xcode/AI assiant/` | product / life 素材来源 |

## 上下文会话索引

用户 4/24 和 4/25 两天在不同会话里讨论了 zac-skills：

- `40ea690d-a09e-4ab3-91b0-139de78462a2.jsonl` （4/24，43 次提到 waza，最完整的讨论）
- `9c3798e2-2f3e-402e-8739-409a4d9fb6eb.jsonl` （4/25，本规划产生的会话）

需要更多上下文时优先翻 4/24 那个会话。
