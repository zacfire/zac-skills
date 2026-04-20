# zac-skills

Personal skill collection for Claude Code — 按生活/工作领域分类。

## Structure

```
skills/
├── RESOLVER.md           -- 触发词到 skill 的路由表
├── dev/                  -- 开发板块
├── writing/              -- 写作板块
├── product/              -- 产品板块（待建）
├── life/                 -- 生活板块（待建）
└── meta/                 -- 跨领域工具
rules/                    -- 无判断的硬规则
scripts/                  -- 结构校验
```

## Skill vs Script vs Rule

| 问题 | YES → | NO → |
|---|---|---|
| 需要 AI 判断、适应、追问？ | **Skill** | Script / Rule |
| 同样输入总是同样输出？ | **Script / Rule** | Skill |
| 依赖用户项目环境？ | **Skill** | Script / Rule |
| 是查找、列表、状态检查？ | **Script / Rule** | 大概是 Skill |
| 行为随对话上下文变化？ | **Skill** | Script / Rule |

## Commit Convention

`{type}: {description}` — types: feat, fix, refactor, docs, chore

## Credits

dev/、writing/write、meta/read、meta/learn 的初始版本来自 [tw93/Waza](https://github.com/tw93/waza)（MIT）。
