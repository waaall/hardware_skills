# `analyze-hardware-schematic` 使用说明

这份文档不是重复 `SKILL.md` 的规范定义，而是用一个实际工作流的角度说明这个 skill 怎么用。

## 这个 Skill 适合做什么

适合在下面这些情况下使用：

- 原理图太大，不适合一次性整体阅读
- 用户已经把原理图按模块拆成截图资料
- 目标是做保守、证据驱动的硬件文档分析，而不是自由发挥式总结

典型用途包括：

- 生成模块级设计文档
- 梳理模块间连接关系
- 找出未闭合或冲突的链路
- 根据截图和 BOM 修订已有硬件文档

## 最小输入

正式调用前，至少准备这些输入：

- 一份总体架构说明
- 按模块组织的原理图截图文件夹
- 一份 BOM 文档，通常是 `bom.md`
- 如果要做修订模式，可额外提供已有文档

如果这些输入不完整，或者质量不够，skill 应该先停在输入验收阶段，而不是直接开始写结论。

## 推荐的资料组织方式

一个比较实用的目录结构可以是这样：

```text
project-materials/
├── overview.md
├── bom.md
├── module-index.md
├── mcu-pin-map.md
├── interface-map.md
├── power/
│   ├── 01_acdc-input.png
│   ├── 02_24v-protection.png
│   └── 03_24v-to-5v.png
├── analog-input/
│   ├── 01_sensor-input.png
│   └── 02_signal-conditioning.png
├── mcu/
│   ├── 01_mcu-power-reset.png
│   └── 02_mcu-interfaces.png
└── existing-docs/
    ├── power.md
    └── inter-module-links.md
```

## 输入准备要点

准备资料时，建议遵守这几个规则：

- 截图文件名要有顺序，也要能体现功能
- 网络名、引脚名、位号必须清晰可读
- BOM 里的 `RefDes` 要能和截图中的位号对应起来
- 总体说明要交代板卡用途、主要模块和关键模块间连接

比较好的截图命名示例：

- `01_power-input.png`
- `02_24v-to-5v.png`
- `03_mcu-i2c-links.png`

不太好的命名示例：

- `image1.png`
- `test.png`
- `final-final.png`

## 调用示例

调用时，最好明确告诉 Codex 输入位置、分析顺序和输出要求。

示例：

```text
Use $analyze-hardware-schematic to analyze the materials under ./project-materials.

Read overview.md first, then inspect each module folder in filename order, and use bom.md as the source of part identity and parameters.

Work in fresh-document mode. Produce:
1. one module document per module
2. one inter-module relationship document
3. one project-level open issues document

Do not guess unclear links. If critical links are missing or unreadable, stop after the intake check and list the gaps.
```

## 修订模式示例

如果项目里已经有旧文档，建议在提示里明确说明要进入修订模式：

```text
Use $analyze-hardware-schematic to revise the hardware design documents in ./project-materials/existing-docs based on the schematic screenshots and bom.md.

Preserve supported conclusions, replace unsupported statements with evidence-backed wording, and collect unresolved items separately.
```

## 预期输出

正常情况下，这个 skill 应输出最多三类结果：

- 模块级文档
- 模块间关系文档
- 项目级待确认/冲突清单

每条重要结论最好都能回挂到证据，例如：

- 截图文件名
- 关键 `RefDes`
- 关键网络名
- 置信度标签

## 不适合的场景

下面这些任务不应该默认用这个 skill：

- PCB layout review
- SI/PI 仿真类任务

## 实际使用建议

- 先从一个板子、几个边界清晰的模块开始
- 保持总体说明和截图目录里的模块边界一致
- 如果资料不是你自己整理的，先要求 skill 做输入验收
- 如果某个跨模块关系很关键，就确保截图里能看到本地链路和跨页或跨模块标签
