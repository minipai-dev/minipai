# MiniPAI ServoBench

**国产智能舵机可复现的 Physical AI Benchmark。**

这是项目第一个值得开源的工程，它回答：

> ¥100 左右的国产 Smart Servo，能不能被准确建模并实现稳定 Sim2Real？

这个问题决定 ¥2999 整机是否成立。

```text
测量数据 → Actuator Model → MuJoCo Config → RL Training → Sim2Real
```

## 原始数据是资产

`data/` 下的原始 CSV **入库**。Benchmark 的可信度取决于开放原始数据与多人独立复现，
不接受只给图表和结论。

🚧 测试协议 `protocol.md` 将于 Week 3（09/15–09/21）随自动化框架一起发布。
