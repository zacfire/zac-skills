# zac-skills

> Personal skill collection for Claude Code — 按生活/工作领域分类，不只是开发。

## Structure

```
skills/
├── RESOLVER.md           -- 触发词到 skill 的路由表
├── dev/                  -- 开发（think / check / hunt / design / health）
├── writing/              -- 写作（write polish，未来: makerlog / official-blog / research-note）
├── product/              -- 产品（未来: research / decide / service-design）
├── life/                 -- 生活（未来: reading / watching / reflection）
└── meta/                 -- 跨领域工具（read / learn）
rules/
├── chinese.md            -- 禁用 AI 中文模式
└── english.md            -- 英文写作规则
scripts/
└── verify-skills.sh      -- 结构校验
```

## 当前状态

**v0.1 — 骨架 + Waza 8 技能**

直接搬运 [tw93/Waza](https://github.com/tw93/waza) 的 8 个 skill 作为起点：

| 板块 | Skill | 出处 | 状态 |
|---|---|---|---|
| dev | think | Waza | 原版，待 Zac 化 |
| dev | check | Waza | 原版，待 Zac 化 |
| dev | hunt | Waza | 原版，待 Zac 化 |
| dev | design | Waza | 原版，待 Zac 化 |
| dev | health | Waza | 原版，待 Zac 化 |
| writing | write | Waza | 原版，待 Zac 化 |
| meta | read | Waza | 原版，待 Zac 化 |
| meta | learn | Waza | 原版，待 Zac 化 |

## Skill vs Script vs Rule 判断

判断新能力属于哪层（来自 Waza 的核心方法论）：

| 问题 | YES → | NO → |
|---|---|---|
| 需要 AI 判断、适应、追问？ | **Skill** | Script / Rule |
| 同样输入总是同样输出？ | **Script / Rule** | Skill |
| 依赖用户项目环境？ | **Skill** | Script / Rule |
| 是查找、列表、状态检查？ | **Script / Rule** | 大概是 Skill |
| 行为随对话上下文变化？ | **Skill** | Script / Rule |

原则：如果在 SKILL.md 里写 "if X then Y" 枚举，那应该是 script。如果在 shell 脚本里写 "agent 应该有好判断"，那部分应该是 skill。

## 演进路径

**v0.1（now）**：搬 Waza 8 技能，先用起来
**v0.2**：product 板块——写第一个 Zac 独有的方法论 skill（研究外部项目）
**v0.3**：writing 板块——把 makerlog / official-blog 从芦苇 repo 迁过来
**v0.4**：life 板块——阅读/观影/反思方法论
**v1.0**：所有 dev/writing skill 都经过 Zac 化改造，不再是 Waza 原版

## License

MIT
