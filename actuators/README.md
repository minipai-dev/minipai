# Actuator Models

执行器模型，每款一个 YAML。**由 ServoBench 实测辨识产出，不是厂标参数。**

```text
actuators/
├── feetech_sts3032.yaml
├── feetech_sts3036.yaml
├── dynamixel_xl330.yaml
└── minipai_x1.yaml
```

## 内容

position / velocity / current / voltage / temperature / load / backlash /
latency / step response / bandwidth / deadband / continuous torque / thermal

这些参数直接灌入 MuJoCo，是 Sim2Real 成败的关键。

🚧 候选型号清单 `candidates.md` 正在核价与询价中，完成后发布。
