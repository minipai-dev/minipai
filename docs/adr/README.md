# Architecture Decision Records

记录**重要且不易回退**的技术决策：为什么这么选，当时排除了什么，什么情况下应该重新考虑。

写 ADR 的意义在于半年后有人问"为什么用 MuJoCo 不用 Isaac"时，答案不依赖某个人的记忆。

## 命名

`NNNN-短标题.md`，四位序号递增。

## 计划中

| 编号 | 主题 | 计划周 |
|---|---|---|
| 0001 | Sim 技术栈选型（MuJoCo / PPO 库 / ONNX 导出） | Week 2 |
| 0002 | Robot HAL 接口定义 | Week 4 |
| 0003 | Linux ↔ MCU 通信协议 | Week 7 |

模板见 [template.md](template.md)。
