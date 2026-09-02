# Reinforcement Learning

训练环境、reward、PPO、Domain Randomization。

## 流程

```text
修改 Reward → 重新训练 → 仿真验证 → 导出 ONNX → 部署真机
```

## 约定

- checkpoint 与 log 不入库（见 `.gitignore`）；**导出的 ONNX 策略入库**
- Domain Randomization 范围应有依据，来自 ServoBench 实测离散度
- 提交策略时附训练曲线与复现命令
