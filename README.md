<div align="center">

# MiniPAI

**Open Physical AI for Everyone**

人人都能训练自己的机器人。

```text
$3000?
No.

¥3000.
```

[参与贡献](CONTRIBUTING.md) ·
[许可](LICENSING.md) ·
Manifesto 🚧 ·
V0.1 PRD 🚧

</div>

---

## MiniPAI 是什么

一套让普通 AI 开发者用 **3000 元以内**进入 Physical AI 的开放平台：
国产硬件 + 仿真 + 强化学习 + Sim2Real + Robot HAL + 开发者社区。

**不是**遥控机器人，**不是**动作组编程，**不是**玩具。

```text
Sensors → Observation → Neural Policy → Joint Targets → Physical Robot
```

你能做的是：

```text
修改 Reward → 重新训练 → 仿真验证 → 导出 Policy → 部署真机
```

## 与「又一台开源双足」的区别

低成本开源小型双足本身已经不是空白（Microduck、Unitree Qmini、青龙 Mini 都在）。
MiniPAI 多的是三层：

| | 内容 |
|---|---|
| **ServoBench** | 国产智能舵机的可复现 Physical AI Benchmark + 自动参数辨识，产出可直接用于仿真的 Actuator Model |
| **Robot HAL** | 上层不绑定任何品牌舵机，`sim:` 与真机同构，Sim2Real by Design |
| **社区** | 没有真机也能参与：装上就能训练，提交 Demo |

## 现在的状态

> 目录已就位，代码尚未落地。
> 当前正在进行 90 天 MVP 验证（Day 0 = 2026-09-01，Demo Day = 2026-11-30）。

90 天要回答两个问题：

1. **¥100 左右的国产 Smart Servo，能不能被建模并跑通 Sim2Real？** → 由 ServoBench 回答
2. **上层能不能做到 sim 与真机同构？** → 由 MiniPAI Sim + Robot HAL 回答

进度见 [Projects 看板](https://github.com/orgs/minipai-dev/projects)。

## 目标体验

无真机，先跑仿真：

```bash
uv run minipai demo walk
```

有真机之后，上层代码不变：

```python
robot = minipai.make("sim:biped_v1")   # 仿真
robot = minipai.make("biped_v1")       # 真机
```

## Reference Robot：MiniPAI Biped V0.1

| 项 | 目标 |
|---|---|
| DOF | 12（每腿 5 + 头部 2） |
| 高度 | ~280 mm |
| 重量 | ≤1 kg（理想 750–900 g） |
| 主控 | RK3566 Linux SBC + STM32/GD32/ESP32 运动控制 |
| 传感 | 6 轴 IMU + CSI 相机 |
| BOM | ≤¥2000 |
| 制造 | 普通 FDM 3D 打印，M2/M3 标准件，无 CNC、无碳纤 |

Hardware MVP 六项：Stand / Walk / Turn / Push Recovery / Fall Detection / Get Up
—— 全部由 Policy 驱动，不使用预设动作组。

## 仓库结构

```text
minipai/
├── hardware/     # STEP / STL / 装配 SOP / 打印参数 / BOM
├── firmware/     # Motion Board：Servo Bus / IMU / 安全层
├── runtime/      # ONNX Runtime + Robot HAL 实现
├── sim/          # MuJoCo / MJCF
├── rl/           # 环境 / reward / PPO / Domain Randomization
├── robots/       # biped_v1, microduck, qmini …
├── actuators/    # servo_*.yaml（Actuator Model）
├── servobench/   # 测试框架 / 协议 / 原始数据
├── examples/
└── docs/         # manifesto / prd / adr / research
```

## 参与

现在最需要两个方向的核心 Contributor：

- **Mechanical** — Link Design、配重、结构优化、公差、关节集成
- **RL / Locomotion** — Reward Engineering、Actuator Identification、Domain Randomization、PPO、Sim2Real

参与方式见 [CONTRIBUTING.md](CONTRIBUTING.md)，详细角色说明 🚧 编写中。

不写代码也能参与：买一款国产舵机、按 ServoBench 协议跑一遍、提交数据，就是对 Benchmark 的直接贡献。
（测试协议 🚧 Week 3 随框架一起发布）

## 许可

- 软件（`runtime/` `sim/` `rl/` `servobench/` `firmware/` `examples/`）：[Apache-2.0](LICENSE)
- 硬件与机械（`hardware/`）：[CERN-OHL-P-2.0](hardware/LICENSE)
- 文档（`docs/`）：[CC BY 4.0](docs/LICENSE)

详见 [LICENSING.md](LICENSING.md)。
