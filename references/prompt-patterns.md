# 逐页提示词与核查要点

准备任何图形或逐页生成提示词时读取；示例用于约束生成，不是待抄答案。图种不限于本文件列出的例子。

## 单页生成骨架

```text
Use case: photorealistic-natural.
Create ONE full portrait A4 sheet photographed on a neutral tabletop.
Reference images: REAL HANDWRITING ONLY. Match the actual character skeletons,
numerals, Chinese forms, letter proportions, joins, long descenders and stroke
endings closely. Do not substitute a generic messy handwriting font.
Use black fine ballpoint with even faster, more scrawled joins, compressed
letterforms, long loose tails and uneven pressure, while retaining reference
character skeletons. Occasionally add one small natural single-line strikeout
and nearby rewrite, a touched-up stroke or a small insertion. Do not force this
onto every page or obscure final formulas, labels or answers. No teacher marks.
Do not copy old answers, names, IDs, university logos, letterheads or red rules.
Keep question order in readable groups, usually one column. Formula rows must
not be perfectly parallel: selected neighboring baselines differ by about
5 degrees (naturally around 3–6), with slight rising, falling or curved lines.
No mechanical alternating rotations, scattered formulas, or crossing rows.
Camera tilt is separate and must not replace these baseline differences.
Preserve all required parallel/perpendicular/angle relationships inside diagrams.
Keep formulas readable, no typeset math or neat handwriting font.
Full page and all content visible, subtle wrinkles, fine paper texture,
soft window light and realistic edge shadows; no hand, pen, watermark.
Keep question order and readable groups. Use enough space for diagrams.

CONTENT — copy exactly, with natural handwritten fractions and subscripts:
[insert this page's approved equations, values, units and minimal labels]

DIAGRAMS — hand draw:
[explicit objects, positions, edges, connections, directions, dimensions,
scales, axes, construction or logical relationships, and labels for this page]

Do not print these instructions. Tiny page number [page/total] at bottom.
```

把确定内容真正填入提示词，不能保留上述方括号占位词。中文与公式可以混写，公式保留必要括号和单位。页数不固定为两页或三页。

## 各类配图的关系清单

先固定每幅图的结构，再要求手绘外观。以下按实际题目选择，不是绘图能力的限制列表：

| 图种 | 生成前明确 | 成图核对 |
| --- | --- | --- |
| 函数、数据与统计图 | 方程或数据、定义域、坐标、刻度、关键点及图例 | 点位、趋势、极值、交点、单位与数值 |
| 平面与立体几何 | 点线面、相交、平行垂直、可见与隐藏边、尺寸和投影 | 连接、交角、比例要求、虚实线及标注 |
| 力学、运动与装置 | 对象、支撑、运动方向、力的作用点及方向 | 箭头、受力对象、约束、相对位置 |
| 光路与场线 | 光学元件、入射点、法线、传播或场方向 | 入射折射反射关系、先后顺序与箭头 |
| 结构、流程与关系图 | 对象、层次、连接、流程先后、条件分支 | 有向边、分支、标号、遗漏或重复 |
| 化学结构与实验示意 | 原子或器材、键或管路、连接、必要立体关系 | 化合价、键型、结构、装置连接和标签 |
| 电路、相量与波形 | 节点、元件、极性、相位、幅值和分段 | 拓扑、方向、相角、平台及零段 |

不能让模型凭“画一个正确的图”补全关键关系。精确图可先计算或构造参考，再交给图像工具生成手绘纸面；不能通过扭歪图内几何关系来制造行间 5° 的变化。

## 波形

先在纸面内容清单写出分段式或 min/max 表达式，再逐区间描述形状。
- 指出输入与输出是实线还是虚线。重合区间数学上应重合，别生成两条不同幅值曲线。
- 明确平台的纵坐标、起止横坐标；不能把限幅和整流混淆。
- 一周期至少标起点、中点、终点及正负幅值。阈值交点在内容允许时标出。
- 逐条核对：正半周是否保留，负半周是否保留，零段或平台是否持续到正确位置。

## 接线图

用连接关系表述，不依赖模型猜图：
`Ui+ → R → 输出节点；该节点 → 稳压管K；稳压管A → 公共回路Ui−`。
每一元件用明确编号；需要时用 A（阳极）、K（阴极）澄清方向，符号本身也须一致。

发生过的实质性错误：
- 模型把“9V 节点减 3V 节点得到 6V”写对，却将输出端画在 3V 和地之间。
  必须画 Uo+ 接 9V 节点、Uo− 接 3V 节点；两个输出端之间不能画短路线。
  测量箭头与电线要分清，不能把箭头看作导线。
- 增加元件编号时，把正向管下端 K 改成 A。每轮编辑后必须重新看所有 A/K 标签。
- 两个稳压管图形正确却没有编号，无法知道谁是 3V、谁是 9V。编号属于答案。
这些是条件性核查示例，不把 6V 差分电路强加给其他题目。

## 定点编辑骨架

```text
Edit target: this page. Change only question [number], [precise region].
Current error: [what is wrong].
Required correction: [exact text or node-to-node connection].
Preserve other content, handwriting style, layout, paper, lighting and wrinkles.
No extra explanatory text or correction patches.
```

修正后不要假设其余像素或答案绝对不变；复核整页。

## 参考与分发边界

真实照片仅从本机 `assets/local-only/` 使用，不随仓库分发，也不上传到 GitHub 或公开预览。使用前读取 [handwriting-profile.md](handwriting-profile.md)。
`assets/handwriting-reference.png` 是不含学校标识和个人信息的生成示例，可用于没有本地私人参考的环境；它不代表特定人的真实笔迹。
