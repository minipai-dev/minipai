# Robot Definitions

机器人定义：MJCF / URDF、关节命名、限位、默认姿态。

每个机器人一个子目录，供 `minipai.make("<name>")` 解析。

计划支持：

- `biped_v1` —— MiniPAI Biped V0.1（12 DOF）
- `microduck` —— 兼容验证
- `qmini` —— 兼容验证

支持第三方机器人是刻意设计：**软件不绑定单一硬件**。
