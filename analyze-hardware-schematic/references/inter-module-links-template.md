# Inter-Module Links Template

Use this template after the module-level analysis is substantially complete.

```md
# [项目名 / Project Name] 模块间链接关系

## 模块清单 / Module List
| 模块 | 角色 | 主要输入 | 主要输出 |
| --- | --- | --- | --- |
| 电源模块 | [role] | [inputs] | [outputs] |
| MCU 模块 | [role] | [inputs] | [outputs] |

## 电源链路 / Power Chains
- [Only summarize links already supported in module analysis.]

## 参考电位与基准链路 / Reference Chains
- [AGND, ACOM, VREF, AREF, midpoint, etc.]

## 控制与通信链路 / Control and Communication Chains
- [I2C, SPI, UART, enable pins, reset paths, chip-select paths.]

## 关键信号输入输出链路 / Critical I/O Chains
- [Measurement inputs, actuator outputs, external interfaces.]

## MCU 交互关系 / MCU Interactions
| 模块 | MCU 资源 | 证据 | 置信度 |
| --- | --- | --- | --- |
| [module] | `I2C1_SCL`, `ADC_IN3` | `[evidence]` | 已确认 |

## 待确认跨模块关系 / Unresolved Cross-Module Links
- [Only include links that are not fully closed.]

## 冲突摘要 / Conflict Summary
- [Summarize only real conflicts that affect system interpretation.]
```

## Rules

- Do not invent a system-level relationship that was not already supported at module level.
- Mark unresolved cross-module chains explicitly instead of silently omitting them.
