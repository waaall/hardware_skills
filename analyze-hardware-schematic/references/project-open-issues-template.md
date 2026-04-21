# Project Open Issues Template

Use this file to maintain a project-level list of unresolved items, conflicts, and user action items.

```md
# 项目级待确认与冲突清单 / Project Open Issues

| 问题项 | 截图证据 | BOM/总体文档/辅助证据 | 影响 | 当前处理 | 需要用户确认的内容 |
| --- | --- | --- | --- | --- | --- |
| [issue] | `[01_xxx.png]` | `bom.md: U12 = ...` | [impact] | 暂停下结论 | [question] |
```

## Include These Categories

- unresolved cross-module links
- screenshot vs BOM conflicts
- screenshot vs architecture-note conflicts
- unreadable or missing screenshot evidence
- naming inconsistencies
- missing files that block closure

## Rules

- Keep this list project-level, not module-local.
- Do not duplicate routine local uncertainty that does not affect the main chain.
- If an item blocks safe interpretation, say so directly in the `影响` field.
