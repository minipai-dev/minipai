# MiniPAI Sim

MuJoCo 仿真环境与 MJCF 模型。

## 目标体验

```bash
uv run minipai demo walk
```

一行命令，电脑上出现一台可运行的仿真机器人 —— **无需真机**。

## 约定

- 不绑定单一机器人：同时支持 MiniPAI Biped / Microduck / Qmini
- 模型几何与 `hardware/` 的 CAD **同源生成**，禁止手工二次建模
- 执行器参数来自 `actuators/*.yaml`（ServoBench 实测），不用厂标宣传值
