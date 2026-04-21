# hardware_skills

这个仓库用来开发和沉淀面向硬件场景的 Codex skills。

目标不是收集泛化提示词，而是把原理图分析、设计理解、文档整理这类真实硬件工作，抽象成可复用、可扩展、证据边界清晰的 skill。

## 当前状态

目前仓库里只有 1 个 skill：

- `analyze-hardware-schematic`
  用于基于模块化原理图截图、BOM 和总体说明，做保守、证据驱动的硬件设计分析，并输出模块级文档、模块间关系文档，以及待确认/冲突清单。

## 目录结构

```text
.
├── analyze-hardware-schematic/
│   ├── SKILL.md
│   ├── USAGE_ZH.md
│   ├── agents/
│   └── references/
└── plans/
```

- `analyze-hardware-schematic/`：当前已有的硬件 skill 主目录。
- `USAGE_ZH.md`：给出这个 skill 的实际使用教程和输入组织示例。
- `agents/`：与 skill 配套的代理配置。
- `references/`：模板、证据规则、停止条件、检查清单等参考资料。
- `plans/`：skill 设计和拆解过程中的计划文档。

## 这个仓库的方向

我希望这里逐步沉淀一组真正能服务硬件开发流程的 skills，例如：

- 原理图模块分析与文档生成
- 模块间连接关系梳理
- BOM 与原理图一致性检查
- 引脚/接口映射整理
- 设计审查辅助

## 设计原则

- 以硬件实际工作流为中心，而不是写成通用聊天模板
- 尽量基于可见证据输出结论，避免补猜
- 支持从零生成文档，也支持修订已有文档
- 每个 skill 尽量保持独立目录，便于单独演进

## 如何使用

从仓库层面看，比较合适的文档结构通常是两层：

- 根目录 `README.md` 负责说明仓库定位和 skill 列表
- 每个 skill 自己的目录里提供一份可直接照着用的教程

当前这个 skill 的示例教程见 [analyze-hardware-schematic/USAGE_ZH.md](analyze-hardware-schematic/USAGE_ZH.md)。

## 安装方式

这个仓库当前采用的是更偏 `Codex` 的 skill 组织格式。

### 安装到 Codex

本地开发时，最直接的方式是把某个 skill 目录复制或软链接到 `~/.codex/skills/` 下。

示例：

```bash
mkdir -p ~/.codex/skills
ln -s /path/to/hardware_skills/analyze-hardware-schematic ~/.codex/skills/analyze-hardware-schematic
```

之后重启 Codex，让它重新加载 skill。

如果这个仓库后续发布到 GitHub，也可以在 Codex 里通过内置的 skill installer 从仓库地址安装。官方参考：

- [Using skills in Codex](https://developers.openai.com/codex/skills)
- [Create custom skills in Codex](https://developers.openai.com/codex/skills/create-skill)

### 用于 Claude Code

这一部分建议写得保守一些。

当前这个仓库结构和 `Codex` 是直接匹配的；对于 `Claude Code`，更合适的写法是“兼容或迁移方式”，而不是直接声称和 Codex 一样原生安装。

比较稳妥的说明方式是：

- 如果你的 Claude 环境支持 Agent Skills 风格目录，可以把 skill 放到 `~/.claude/skills/<skill-name>` 或 `<project>/.claude/skills/<skill-name>`
- 如果没有这类约定，建议把这个 workflow 改造成 `.claude/commands/` 或 `.claude/agents/` 下的项目级命令或子代理

Claude Code 官方参考：

- [Set up Claude Code](https://docs.anthropic.com/en/docs/claude-code/getting-started)
- [Claude Code settings](https://docs.anthropic.com/en/docs/claude-code/settings)

## 后续扩展约定

如果继续新增 skill，建议保持类似结构：

- `SKILL.md`：定义 skill 的用途、输入、流程和输出要求
- `USAGE.md / USAGE_ZH.md`：说明实际如何组织输入、如何调用、预期输出是什么
- `references/`：存放模板、规则和检查清单
- `agents/`：存放该 skill 的代理配置
- `plans/`：记录该 skill 的设计方案或迭代计划

这个仓库目前还很小，但会围绕“硬件分析与文档自动化”这个方向持续扩展。
