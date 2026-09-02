# Hardware / Mechanical

机械与电气设计：CAD 源文件、STEP、STL、原理图、PCB、装配 SOP、打印参数、BOM。

**许可与仓库其余部分不同**：本目录为 CERN-OHL-P-2.0，见 [LICENSE](LICENSE)。

## 约定

- CAD 必须提交 **源格式 + STEP + STL** 三者（只给 STL 无法二次修改）
- 改动影响质量/质心时，必须同步更新 `sim/` 中的模型 —— **CAD 与 Sim 同源**
- 紧固件限 M2 / M3 标准件；不依赖 CNC、不依赖碳纤维
- 材料：PLA+ / PETG，普通 FDM 可打印
