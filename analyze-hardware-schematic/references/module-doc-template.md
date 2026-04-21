# Module Document Template

Use this template for new module documents or when normalizing an existing one.

Headings should follow the user's language. The structure below is the required shape.

```md
# [模块名 / Module Name]

## 输入资料 / Input Evidence
- 总体说明：`[filename]`
- 模块截图目录：`[folder]`
- 相关截图：
  - `[01_xxx.png]`
  - `[02_xxx.png]`
- BOM：`[bom.md]`
- 现有文档：`[optional path]`

## [子模块名 / Submodule Name]

### 关键器件 / Key Parts
| 位号 / RefDes | 型号 | 参数 | 类别 | 来源 |
| --- | --- | --- | --- | --- |
| U1 | [model] | [param] | [category] | BOM |
| R3 | [model] | [param] | [category] | BOM |

### 电路关系分析 / Circuit Relation Analysis
- [Describe the visible chain, direction, and role.]
- [Separate visible facts from inference.]

### 关键关系表 / Key Relationship Table
| 关系描述 | 证据截图文件名 | 关键位号 / RefDes | 关键网络名 | 是否闭环 | 是否跨模块 | 置信度 |
| --- | --- | --- | --- | --- | --- | --- |
| [description] | `[01_xxx.png]` | `U1, R3` | `VCC_5V` | 是/否 | 是/否 | 已确认 |

### 当前可确认的内容 / Confirmed
- [Evidence-backed statements only.]

### 待确认项 / Open Questions
- [Unclosed link or unreadable evidence.]

### 冲突项 / Conflicts
- [Screenshot vs BOM or screenshot vs architecture-note conflicts.]
```

## Writing Rules

- Start each submodule with key parts before analysis.
- Keep part identity separate from topology analysis.
- Do not scatter BOM facts across the entire section.
- Every important claim should be traceable to visible evidence.
