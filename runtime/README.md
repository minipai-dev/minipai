# MiniPAI Runtime & Robot HAL

ONNX Runtime 推理 + Robot HAL 实现。**这是项目最关键的差异化层。**

## 目标：上层不绑定任何品牌舵机

```python
robot.state()

robot.joints.position
robot.joints.velocity
robot.joints.effort

robot.imu.orientation
robot.imu.angular_velocity

robot.command(position)
```

下层可以是 Feetech / Dynamixel / CAN Actuator / Qmini / Microduck-compatible /
MiniPAI / Simulator —— 上层代码不变：

```python
robot = minipai.make("biped_v1")        # 真机
robot = minipai.make("sim:biped_v1")    # 仿真
```

这就是 **Sim2Real by Design**。接口定义见 🚧 `docs/adr/0002-robot-hal.md`。
