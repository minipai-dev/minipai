# MiniPAI 许可说明

MiniPAI 同时包含软件、硬件设计和文档三类资产。它们的复制/分发/衍生方式不同，
用同一个许可证覆盖会产生歧义，因此分开授权。

## 三类资产

| 范围 | 许可证 | 文件 |
|---|---|---|
| **软件**<br>`runtime/` `sim/` `rl/` `servobench/` `firmware/` `examples/` `robots/` `actuators/` | Apache-2.0 | [LICENSE](LICENSE) |
| **硬件与机械设计**<br>`hardware/`（STEP / STL / CAD / 原理图 / PCB / BOM） | CERN-OHL-P-2.0 | [hardware/LICENSE](hardware/LICENSE) |
| **文档**<br>`docs/` 及仓库根部 `.md` | CC BY 4.0 | [docs/LICENSE](docs/LICENSE) |

## 为什么这样选

**软件用 Apache-2.0。** 与 MIT 类似的宽松度，但多了明确的**专利授权**条款。
机器人领域专利密集，贡献者可能持有相关专利；Apache-2.0 让下游用户不必担心
被贡献者反向主张专利。这也是 LeRobot、MuJoCo 等上游生态的常见选择，便于互操作。

**硬件用 CERN-OHL-P-2.0。** 软件许可证的措辞（"source code"、"object form"、
"compilation"）无法干净地映射到 STEP 文件和实体制造行为，直接套用会留下解释空间。
CERN-OHL 是专为开源硬件写的，`-P` 是其中**最宽松（permissive）**的变体：
允许闭源制造与商业销售，不要求衍生设计开源。

> 为什么不用 CERN-OHL-S（strong reciprocal，要求衍生设计也开源）？
> 因为 MiniPAI 的目标是成为 reference hardware——希望别人拿去改、拿去做产品、
> 拿去做教具，越少摩擦越好。用 S 变体会让商业改版望而却步，与"成为
> Physical AI 的 Raspberry Pi"这个定位相冲突。

**文档用 CC BY 4.0。** 允许自由转载与翻译，只要求署名。
Benchmark 报告需要广泛传播，这是最合适的选择。

## 对使用者意味着什么

你**可以**：

- 商业使用、修改、闭源分发
- 自行制造、改版、售卖 MiniPAI 硬件
- 转载翻译文档与 Benchmark 报告（署名即可）

你**需要**：

- 保留版权与许可声明
- 硬件衍生品需按 CERN-OHL-P 要求标注来源与修改
- 文档转载需署名

你**不能**：

- 使用 MiniPAI 名称或标识暗示官方背书（商标不在开源许可范围内）
- 移除或篡改原始署名

## 贡献者条款

向本项目提交贡献，即表示你同意按上述对应许可证授权你的贡献
（Apache-2.0 §5 的 inbound=outbound 原则）。项目暂不要求签署单独的 CLA。

如果你的贡献包含第三方内容（代码、CAD、数据、图片），必须在 PR 中明确其来源和许可证，
且该许可证需与本项目兼容。**尤其注意**：从竞品仓库复制 CAD 或数据前先确认其许可证，
GPL / CERN-OHL-S 类的强互惠许可与本项目不兼容。

## 商标

"MiniPAI" 名称与 logo 不通过上述开源许可授权。
你可以说"基于 MiniPAI 设计"或"兼容 MiniPAI"，但不能用它命名你的产品或暗示官方认证。
