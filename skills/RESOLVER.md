# zac-skills Resolver

触发词到技能的路由表。Claude Code 通过每个 SKILL.md 的 `description` 自动匹配，这份文档是给人看的集中索引。

> **Read the skill file before acting.** 多个技能都可能匹配时，都读。它们设计成可串联。

---

## 按生活领域分类

### 🛠️ Dev（开发板块）

对着代码工作时用。

| 触发 | 技能 |
|------|------|
| 新功能 / 架构决策 / "怎么设计" / "应该用什么方案" | `skills/dev/think/SKILL.md` |
| UI / 组件 / 页面 / 视觉界面 / 前端 | `skills/dev/design/SKILL.md` |
| 实现完成 / 合并前 / "review 一下" / "看看这段代码" | `skills/dev/check/SKILL.md` |
| review issue / PR / triage / 批量处理 | `skills/dev/check/SKILL.md` (Triage Mode) |
| 报错 / 崩溃 / 测试失败 / 行为异常 / "为什么不工作" | `skills/dev/hunt/SKILL.md` |
| Claude 忽略指令 / hook 失灵 / MCP 异常 / 配置审计 | `skills/dev/health/SKILL.md` |
| 开发者视角 prose（PR / release notes / issue 评论）润色 | `skills/dev/write/SKILL.md` |

### ✍️ Writing（写作板块）

输出非开发类长文时用。

**待建**：
- `skills/writing/makerlog/` — MakerLog 开发日志
- `skills/writing/official-blog/` — roseau.app 官方博客
- `skills/writing/research-note/` — 研究笔记输出
- `skills/writing/publish-blog/` — 发布到 Quaily

### 📦 Product（产品板块）

做产品判断时用。

**待建**：
- `skills/product/research/` — 外部产品/项目研究方法论
- `skills/product/decide/` — 产品决策（要不要学 X 的做法）
- `skills/product/service-design/` — 芦苇服务设计

### 🌱 Life（生活板块）

个人体验/消费沉淀时用。

**待建**：
- `skills/life/reading/` — 阅读批判性记录
- `skills/life/watching/` — 观影/观剧记录
- `skills/life/reflection/` — 复盘/反思

### 🔧 Meta（跨领域工具）

| 触发 | 技能 |
|------|------|
| 消息含 URL / PDF 路径 / "看一下这个" / "总结这个" | `skills/meta/read/SKILL.md` |
| 深度研究陌生领域 / 六阶段研究到成稿 / 素材沉淀成文章 | `skills/meta/learn/SKILL.md` |

---

## Disambiguation（歧义消解）

多个技能都可能匹配时按以下规则：

1. **最具体优先**：`/design` 比 `/think` 更具体（仅限 UI 决策）
2. **URL 按内容类型二次分流**：URL → 先 `/read` → 长文研究再接 `/learn`
3. **改错 vs review**：代码已交付 → `/check`；代码跑不通 → `/hunt`
4. **配置异常 vs 代码错误**：Claude 不听话 / hook 不触发 → `/health`；用户代码抛异常 → `/hunt`
5. **长文产出 vs 润色**：从零到成稿 → `/learn`；已有稿子要改 → `/write`
6. **兜底**：模糊时读两个 SKILL.md 的 "Not for" 段排除法；还是模糊就问用户

---

## Chaining（常见串联）

```
新功能 → /think (设计方案) → 实现 → /check (review) → 合并
报错 → /hunt (诊断) → 修复 → /check (验证) → 提交
研究长文 → /read (抓取) → /learn (深度研究) → /dev/write (润色成稿)
```
