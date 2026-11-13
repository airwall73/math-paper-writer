# math-paper-writer

[![lang-中文](https://img.shields.io/badge/lang-%E4%B8%AD%E6%96%87-red?style=for-the-badge)](README.md)
[![lang-English](https://img.shields.io/badge/lang-English-blue?style=for-the-badge)](README.en.md)

一个让 AI 写出**规范、易读、可核查**的**数学证明**skill 包。
为 GPT 6 Astra 设计，同样适用于其他 LLM 与 agent harness。
它只约束写作与核查流程，**不改变证明逻辑本身**。

## 使用方式

**单次使用 / 网页版**：把 zip 丢给 AI，例如

```
按这个 package 的设定，证明素数有无穷多个
```

或

```
按这个package的设定，重写xxx.tex
```

**长期使用 / Codex 等 agent**：将content文件夹的内容放入**工作区**，AI会自动调用。本 package 由 `AGENTS.md` 和 skill 两部分组成——若工作区已有 `AGENTS.md`，需将两者文本合并。注意一次部署仅作用于**一个工作区**。

## 实际效果示例

同一个引理（取自一篇树上指标随机游动论文的稿件），对比 AI 原生写法与本 skill 约束下的写法。

**使用前**——所有内容压成一段话，定义和估计藏在文字里：

> **Lemma 2.2 (Attachment mixing).** The attachment environment indexed by individual right trees has an exponentially absolutely regular stationary renewal version. A translation-invariant function of $r$ ancestral levels can be localized to $h$ tree indices with exceptional probability at most $Ce^{-ch+Cr}$. The initial renewal environment has bounded density with respect to the stationary version, and admits an exponential coupling to it.

**使用后**——对象先以正式定义给出，结论拆成编号部分，关键估计居中展示并编号，便于交叉引用：

> **Lemma 2.2 (Attachment mixing).** For $j \ge 1$ let $\mathcal{E}_j$ collect the right count $R_j$ and the shapes and spatial marks of the right trees at ancestral level $j$, and let $\nu_r$ be the number of tree indices in the renewal blocks constructed below that meet levels $1,\dots,r$, including the two boundary blocks.
>
> (i) Reindexed by tree index, $(\mathcal{E}_j)$ has a stationary renewal version $(\mathcal{E}^{\mathrm{st}}_j)$ and an exponential coupling to it:
>
> $$\mathbb{P}\bigl(\mathcal{E}_j \ne \mathcal{E}^{\mathrm{st}}_j \ \text{for some } j \ge n\bigr) \le Ce^{-cn}. \qquad (34)$$
>
> In particular it is absolutely regular with exponentially decaying coefficients.
>
> (ii) For $r, h \ge 1$,
>
> $$\mathbb{P}(\nu_r > h) \le Ce^{-ch+Cr}. \qquad (35)$$
>
> Hence a measurable function of $r$ consecutive level environments, applied at any starting level, agrees with a function of at most $h$ tree indices off an event of probability at most $Ce^{-ch+Cr}$, uniformly in the starting level.
>
> (iii) The initial renewal environment has bounded density with respect to the stationary version, and admits an exponential coupling to it.

## 附：防止 AI 偷懒小技巧

GPT 6 Astra 经常按指示前进一小步就停下，可用原生的 `/goal` 功能锁定终点，例如

```
/goal 证明素数有无穷多个
```

## 主要功能说明

### 1. 让 AI 和"自己对账"

参考了 grill-with-docs 的设计理念，但重点不是人机对账，而是让 AI 自我审计：

- 维护一份**符号/术语台账**（`glossary.md`）——每个符号记录含义、类型、定义位置和首次使用处；AI 自创的术语必须有对应符号与锚点，未解决的条目标记为 open
- 每个命题引用了什么，都有精确定理/引理/公式编号指示

### 2. 定义居中展示

重要定义以居中公式展示，不藏在大段文字里。

### 3. 文献溯源 footnotes

对驱动证明结构、关键估计或极限识别的方法，在首次使用处加footnote：

- 直接引用 → 作者、citation key、可核验的章节/定理编号，并在证明中验证条件满足
- 改编 → 说明借用了哪一步、此处改了什么、还需补什么估计
- 类比 / 独立推导 → 说明共享机制或所依赖的标准工具
- 未核实的来源标记为 pending，不假装已查证

### 4. 期刊风格适配

- 内置概率期刊风格样板（基于 AOP、PTRF等概率杂志）：包括摘要与引言的写法、定理位置、proof roadmap、remark 的取舍等
- 可以替换成你指定的期刊、可以加入作者风格（需要些许动手能力，直接让agent从你的arxiv或个人主页抓取，并加入本skill）

### 5. 数学核查流程

- 新写或实质改动的推导**独立检验**一遍；检查渐近展开的适用区域、误差界的一致性、退化与边界情形
- 优先精确算术；依赖计算时给出可复现的脚本/命令
- 数值验证只算证据不算证明；缺口如实标记为 open

### 6. 其他约定

- **只以英文写作**（正文、footnote、台账条目），与其他语言聊天讨论互不干扰
- 编号纪律：局部定义/计算用无编号公式 `\[...\]`，需要稳定交叉引用才给编号；保护已有的公式和定理编号
- 长任务维护检查点（目标、已证结果、未决命题、失败路径、下一步），中断后可无缝续作
- 主要问题未解决时，优先攻坚关键障碍，不沉迷于打磨格式和反复编译
