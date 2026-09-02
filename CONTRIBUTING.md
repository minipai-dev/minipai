# 参与 MiniPAI

先说最重要的一条：

> **不需要有真机，也不需要是机器人专家。**

MiniPAI 的仿真先于硬件可用。你有一台电脑就能训练策略、提交 Demo。

---

## 四种参与方式（按门槛从低到高）

### 1. 跑一款舵机，交一份数据 ← 现在最需要

**门槛：一款国产总线舵机（¥50–150）+ 一个 USB-TTL。**

这是当前对项目最直接的贡献。MiniPAI 的第一个技术资产是
《国产 Smart Servo Benchmark 2026》，它的可信度取决于**多人独立复现**。

```text
按 ServoBench 协议跑一遍 → 提交原始 CSV + 你的测试条件 → PR
```

> 🚧 `servobench/protocol.md` 测试协议将随自动化框架一起发布。
> 在此之前想参与的话，可以先在 Discussions 说明你手上有哪款舵机，协议发布后第一时间通知你。

即使你测的型号已经有人测过，**重复测量也有价值**——它验证了协议的可复现性，
也暴露批次差异。请如实记录你的电压、环境温度、负载条件。

### 2. 训练一个策略，交一个 Demo

**门槛：一台能跑 MuJoCo 的电脑。**

```bash
uv run minipai demo walk
```

改 reward、换 Domain Randomization 范围、试不同算法，把结果发到 Discussions。
走得更快、更稳、更省电的策略，都会被收进 `examples/`。

### 3. 文档、翻译、复现报告

跑不通就是 bug。**把你卡住的地方写成 issue，本身就是贡献**——
尤其是 README/Quickstart 里说得不清楚的部分。

英文文档、Benchmark 报告翻译同样欢迎。

### 4. 核心开发

目前最缺两个方向（详细角色说明 🚧 编写中）：

- **Mechanical** — Link Design、配重、结构优化、公差、关节集成
- **RL / Locomotion** — Reward Engineering、Actuator Identification、DR、PPO、Sim2Real

---

## 一条不可协商的原则

> **Locomotion 必须由 Policy 驱动，不接受预设动作组。**

以下形态的行走实现不会被合并：

```cpp
servo.move(...);
delay(...);
servo.move(...);
```

原因不是风格偏好。一旦引入动作组，项目性质就从 Physical AI 平台退化成
传统舵机机器人，`Sensors → Policy → Joint Targets` 这条链就断了。

动作组在**标定、自检、急停归位**里是可以用的——但不能出现在 locomotion 路径上。

---

## 提交流程

1. **先开 issue 或 Discussion**，特别是较大的改动。避免你花了两周，方向却和项目冲突。
2. Fork → 开分支：`feature/xxx`、`fix/xxx`
3. 提交信息：`type(scope): description`
   `type` ∈ `feat` / `fix` / `docs` / `refactor` / `test` / `chore`
   例：`feat(servobench): add step response measurement`
4. 提 PR，说明**动机**（为什么需要）而不只是**内容**（改了什么）
5. PR 描述里请写清你怎么验证的

## 代码规范

| | |
|---|---|
| 行宽 | 120 字符 |
| 缩进 | 4 空格（Makefile 用 Tab） |
| Python | PEP 8 + 类型注解；`ruff` 格式化；虚拟环境 `.venv/` |
| C/C++ | 遵循 MISRA C 关键规则；`snake_case` 变量；`UPPER_SNAKE_CASE` 宏；`#pragma once` |
| 嵌入式 | 避免动态内存；中断处理保持简短；硬件寄存器与中断共享变量用 `volatile` |
| 提交前 | 跑 lint 和测试 |

## 数据与实验的额外要求

MiniPAI 的核心资产是**可复现的测量数据**，所以对数据类 PR 要求更严：

- 原始数据必须一起提交（不接受只给图表和结论）
- 必须记录测试条件：电压、环境温度、负载、采样率、固件版本
- 说明用了哪个协议版本（`servobench/protocol.md` 的 git tag）
- 结论与数据不符时，以数据为准

## 硬件类 PR

- CAD 提交**源格式 + STEP + STL** 三者（只给 STL 无法二次修改）
- 说明打印参数：层高、填充、材料、支撑
- 改动影响质量或质心的，请更新对应 sim 模型 —— **CAD 与 Sim 必须同源**，
  几何漂移会让 Sim2Real 的问题无法归因

## 许可

提交贡献即表示你同意按项目对应许可证授权（软件 Apache-2.0 / 硬件 CERN-OHL-P-2.0 /
文档 CC BY 4.0）。包含第三方内容时必须声明来源与许可证，详见 [LICENSING.md](LICENSING.md)。

## 行为准则

参与本项目需遵守 [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)。

---

## 卡住了？

- 用不起来 / 跑不通 → 开 issue
- 想讨论方向 → Discussions
- 想认领任务 → 看公开看板，在对应 issue 下留言

不确定该不该提某个想法的时候，**提**。宁可被回复「暂时不做」，也别自己憋着。
