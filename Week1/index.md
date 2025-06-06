# 目录

## 第一周任务： 重复码入门与量子纠错基本概念

**本周目标与学习重点：**理解经典与量子错误的区别，初步掌握纠错的基本思想。学生将学习简单的重复码(repetition code)原理，了解如何通过冗余编码来检测和更正比特翻转错误。重点在于理解经典三比特重复码如何检测单比特错误，以及量子情况下测量所带来的挑战和解决方案（例如利用奇偶校验测量而非直接测量编码位
状态）。

**涉及的量子计算概念：**比特翻转错误（X错误）的概念；经典纠错与量子纠错的异同；测量对量子态的扰动；奇偶校验（parity）检查的思想。将介绍逻辑比特（编码在多个物理比特上的信息）与物理比特的区别。

**推荐的工具**：QuTiP用于模拟简单量子态演化和测量。学生可使用QuTiP构建3量子比特的态并应用门操作。若无现成量子电路模块，可手动实现CNOT等门。也可仅用Python基础库处理比特翻转的逻辑（例如用0/1表示态，模拟错误发生和纠
错）。可实现的编程任务/小实验：实现3比特重复码纠错流程的模拟。具体任务包括：

a. 编码：将一个逻辑比特（|0⟩ 或 |1⟩）编码到3个物理比特，例如通过两个CNOT门将第一个比特复制到第二、第三个比特上，得到 |000⟩ 或 |111⟩状态。
b. 引入错误：随机选择一个物理比特施加一次 X 操作（比特翻转），模拟单比特错误。
c. 错误检测：模拟测量奇偶校验，例如检查比特1和2是否相同，以及比特2和3是否相同。这相当于测量两个稳定子（stabilizer） 和的结果，获取综合征信息(syndrome)。注意，这种奇偶校验测量并不会直
接获取每个比特的值，从而避免对量子信息的破坏thepaper.cn。
d. 错误更正：根据综合征判断哪一个比特发生了翻转，并对其施加X操作纠正错误。
e. 验证：测量3个物理比特，验证纠错后得到的逻辑比特状态是否与初始一致。



## 阅读资料：

### 理论学习

- [Qiskit 教科书 & IBM 学习课程](https://learning.quantum.ibm.com/course/foundations-of-quantum-error-correction/correcting-quantum-errors):  

  IBM 提供了面向初学者的在线教材章节，如*“Correcting Quantum Errors”*，系统讲解了量子错误校正的基本原理和第一个发现的量子码——9比特 Shor 码[learning.quantum.ibm.com](https://learning.quantum.ibm.com/course/foundations-of-quantum-error-correction/correcting-quantum-errors#:~:text=For the next four lessons,as the discretization of errors)。课程从经典的三比特重复码引入（说明如何通过多数表决纠正单比特错误[learning.quantum.ibm.com](https://learning.quantum.ibm.com/course/foundations-of-quantum-error-correction/correcting-quantum-errors#:~:text=Encoding and decoding)），逐步过渡到 Shor 码如何将比特翻转码和相位翻转码级联实现同时纠正 X/Z 错误[learning.quantum.ibm.com](https://learning.quantum.ibm.com/course/foundations-of-quantum-error-correction/correcting-quantum-errors#:~:text=The 9)[learning.quantum.ibm.com](https://learning.quantum.ibm.com/course/foundations-of-quantum-error-correction/correcting-quantum-errors#:~:text=Image%3A Encoding circuit for the,Shor code showing 3 blocks)。教材还强调了**量子错误离散化**这一核心概念，即连续微小扰动可等效为有限集合的 Pauli 错误，从而使纠错成为可能[learning.quantum.ibm.com](https://learning.quantum.ibm.com/course/foundations-of-quantum-error-correction/correcting-quantum-errors#:~:text=on the fundamentals,as the discretization of errors)。这些官方教程配有交互示例和练习题，有助于巩固概念。

- [Quantum Error Correction for Beginners” (初学者指南)](https://ar5iv.labs.arxiv.org/html/0905.2794#:~:text=4.%20IV%20The%203,1%20Systematic%20gate%20errors)：

  Devitt 等人在 2009 年撰写的权威综述[ar5iv.org](https://ar5iv.org/abs/0905.2794#:~:text=Quantum error correction ,error correction for large scale)对量子纠错的理论基础做了通俗介绍，非常适合已有一定量子背景的读者加深理解。文章通过详细实例解释了经典比特错误和量子错误的区别，首先以**3比特码**为起点阐释基本原理，然后介绍了第一个完整的量子纠错码——**9比特 Shor 码**[ar5iv.org](https://ar5iv.org/abs/0905.2794#:~:text=4. IV The 3,1 Systematic gate errors)。文中系统讲解了稳定子Formalism（稳定子规范）在量子纠错中的应用[ar5iv.org](https://ar5iv.org/abs/0905.2794#:~:text=4. IV The 3,1 Systematic gate errors)，并讨论了容错量子计算和阈值定理等进阶主题，是学习稳定子码理论的经典参考之一。

- [Stabilizer Codes and Quantum Error Correction(Chapter 1-3)]()： 

  见Week1/Resources文件夹

### 代码实现

- [Quskit实现3比特比特翻转码电路示例](https://quantumcomputinguk.org/tutorials/quantum-error-correction-bit-flip-code-in-qiskit#:~:text=to%201%20since%20the%20main,qubits%20state%20is%201)

- [IBM Quantum Learning 重复码教程](https://learning.quantum.ibm.com/tutorial/build-repetition-codes)



## 教程视频

- [James Wootton 的量子纠错入门](https://www.youtube.com/watch?v=ZY8PddknCos#:~:text=13,an%20introduction%20to%20the)
- [12 Days of Qiskit” 系列之量子纠错](https://www.youtube.com/watch?v=e-EaIs-Qr78#:~:text=Playing%20with%20Quantum%20Error%20Correction,looking%20at%20the%20hints%2C)
- [Steve Girvin 容错计算讲座](https://www.youtube.com/watch?v=PI8PqARCwWo#:~:text=,Yale)



# Toric Code vs. Surface Code – Key Resources and Differences

## Textbook Chapters and Lecture Notes

- 【Héctor Bombín (2013) – *Topological Codes* (Chapter in *Quantum Error Correction*, eds. D. Lidar & T. Brun)】

  - 网址：https://arxiv.org/pdf/1311.0277
  - 简介：这是 Bombín 撰写的关于拓扑量子纠错码的系统入门章节，收录于《Quantum Error Correction》一书中（剑桥大学出版社出版），可在 arXiv 免费获取。
  - 核心内容：章节首先介绍了环面码（toric code），即在闭合曲面（如环面）上定义的量子码，随后引出具有开放边界的表面码（surface codes，也称平面环面码）；强调在环面码中逻辑算符是不可收缩的闭合回路，而在引入边界后，逻辑算符则变为连接不同边界的开放路径；章节中使用同调理论（homology）形式化描述这些概念，并讨论了错误综合征、码距和容错阈值；其中第4.5节专门探讨了有边界和平面结构下的表面码与无边界环面码的区别。

  ------

  【Error Correction Zoo – Surface Code 条目】

  - 网址：https://errorcorrectionzoo.org/c/surface
  - 简介：Error Correction Zoo 网站上的表面码（Surface Code）条目，系统总结了表面码在不同边界条件下的实现。
  - 核心内容：条目指出在闭合曲面（如环面）上构建的表面码与环面码等价，逻辑比特通过非平凡闭合路径定义；而在引入粗糙边界与光滑边界之后，表面码可以在二维平面上实现，逻辑操作变为连接不同类型边界的开放路径，这种结构兼顾了理论保护能力与实验实现的可行性。

  | 链接                                                         | 指向内容                                                     | 说明                                                         |
  | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | [arxiv.org/pdf/1311.0277](https://arxiv.org/pdf/1311.0277#:~:text=This is the chapter Topological,the written permission of Cambridge) | Bombín 写的《Topological Codes》章节（2013），收录在 *Quantum Error Correction* 一书中 | Bombín 对拓扑量子码的系统介绍，涵盖 toric code 和 surface code |
  | [arxiv.org/pdf/1311.0277](https://arxiv.org/pdf/1311.0277#:~:text=Figure 12%3A A planar toric,85%2C 1%2C 7]]) | 同一篇文档中的 **Figure 12**，展示了 **planar toric code**（平面环面码）的图示 | 具体是图12，展示平面环面码的形态和结构                       |
  | [arxiv.org/pdf/1311.0277](https://arxiv.org/pdf/1311.0277#:~:text=toric code ,3]. This work introduced) | 同一篇文档中的一段内容，解释了 **toric code** 及其首次提出的背景 | 讲述了 toric code 的历史和Kitaev的贡献                       |
  | [errorcorrectionzoo.org/c/surface](https://errorcorrectionzoo.org/c/surface#:~:text=The construction on closed surfaces,6) | Error Correction Zoo 网站，关于 **surface code** 的详细条目  | 特别说明了 surface code 与 toric code 在闭合曲面（如环面）与开放曲面（如平面）上的结构关系 |
  | [errorcorrectionzoo.org/c/surface](https://errorcorrectionzoo.org/c/surface#:~:text=(%2B1),the case of open boundaries) | 同样是 Error Correction Zoo，讲述 **开放边界（open boundaries）** 情况下表面码的变化 | 解释在有开放边界时，surface code 的稳定子和逻辑算符如何变化  |

  

- 【University of Cologne Lecture Notes (Michael Kastoryano, *Quantum Error Correction*, 2019)】

  - 网址：https://www.thp.uni-koeln.de/kastoryano/ExSheets/Notes_v9.pdf
  - 简介：这是由科隆大学 Michael Kastoryano 教授撰写的《量子纠错》讲义，提供了一个适合初学者但保持数学严谨的表面码和环面码学习材料，免费公开发布。
  - 核心内容：在第12章“表面码（Surface Codes）”中，讲义指出环面码是定义在具有周期性边界（torus）上的一种特殊表面码，而平面码是具有开放边界（non-periodic boundaries）版本的表面码；讲义强调由于在实验中难以实现真正的周期性边界，因此通常使用平面表面码；特别指出了逻辑X/Z算符的区别：在环面码中是绕环形成闭合路径，而在平面码中则是连接不同边界的开放路径；讲义还详细展示了边界条件如何影响逻辑比特数量，并通过图29等示意图比较了bulk区域与edge区域的稳定子结构变化。

  | 链接                                                         | 指向内容                                                     | 说明                                                         |
  | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | [thp.uni-koeln.de - Lecture Notes PDF](https://www.thp.uni-koeln.de/kastoryano/ExSheets/Notes_v9.pdf#:~:text=12,we consider a quadrilateral surface) | 讲义**第12章 Surface Codes 开头**，解释 toric code 和 surface code 的基本定义 | 明确 toric code 是 surface code 的一种特殊情况（周期性 vs 开放边界） |
  | [thp.uni-koeln.de - Lecture Notes PDF](https://www.thp.uni-koeln.de/kastoryano/ExSheets/Notes_v9.pdf#:~:text=12,we consider a quadrilateral surface) | 讲义**同一处内容**，强调实验中更实际采用开放边界             | 因为实现环面在实验中太困难                                   |
  | [thp.uni-koeln.de - Logical Operators](https://www.thp.uni-koeln.de/kastoryano/ExSheets/Notes_v9.pdf#:~:text=The X and Z logical,gives a new logical operator) | 讲义中**关于逻辑算符**（X、Z）如何不同的描述                 | toric code 中闭合，surface code 中开放                       |
  | [thp.uni-koeln.de - Figure 29](https://www.thp.uni-koeln.de/kastoryano/ExSheets/Notes_v9.pdf#:~:text=Figure 29%3A Planar codes are,operators%2C and thus this triangular) | 讲义中**Figure 29**，展示了平面表面码的稳定子结构和逻辑算符  | 包括方块格子中 bulk 和 edge 区域的稳定子安排                 |
  | [thp.uni-koeln.de - Stabilizer Overlap](https://www.thp.uni-koeln.de/kastoryano/ExSheets/Notes_v9.pdf#:~:text=stabilizers meet%2C they always overlap,it with the logical operators) | 讲义进一步解释**稳定子和逻辑算符的交叠关系**                 | 特别是不同稳定子在格子边界的连接方式                         |

- 【Eric Dennis, Alexei Kitaev, Andrew Landahl, John Preskill (2002) – *Topological Quantum Memory*】

  - 网址：https://quantumcomputing.stackexchange.com/questions/23681/reference-for-surface-code-error-correction
  - 简介：这是 Dennis、Kitaev、Landahl 和 Preskill 合作发表的一篇具有里程碑意义的论文，发表于 *Journal of Mathematical Physics* 第43卷第4452页，经常被引用为表面码与量子存储基础概念的入门参考。
  - 核心内容：论文以Kitaev提出的环面码为起点，展示了如何通过引入边界（rough 和 smooth boundaries）在二维平面上实现与环面码相同的错误纠正机制，主要研究对象是无孔的平面表面码；内容涵盖了表面码的构造方法及其基本性质，将错误纠正过程映射为统计物理模型，推导了误差阈值，并介绍了如何通过编织缺陷（braiding defects）实现容错逻辑门操作；虽然是研究型论文，但假设读者无需已有拓扑编码背景，因此也是一份非常完整且友好的表面码入门资料。

  | 链接                                                         | 指向内容                                                     | 说明                                                         |
  | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
  | [quantumcomputing.stackexchange.com - Paper Reference](https://quantumcomputing.stackexchange.com/questions/23681/reference-for-surface-code-error-correction#:~:text=Topological quantum memory by Eric,free encoding) | StackExchange上的一则问答，推荐了**Eric Dennis, Kitaev 等人 2002年《Topological Quantum Memory》**这篇论文作为学习表面码的入门资料 | 这里指出，这篇论文从量子存储的角度，建立了平面表面码的直观理解框架 |
  | [quantumcomputing.stackexchange.com - Intuitive Picture](https://quantumcomputing.stackexchange.com/questions/23681/reference-for-surface-code-error-correction#:~:text=develops intuitive description of the,free encoding) | 指向同一页面中一段文字，强调这篇论文**用拓扑直观方式**解释了如何在平面上引入边界，实现与环面码相同的纠错功能（通过 rough 和 smooth 边界） | 特别强调了从 toric code 到 surface code 的转变               |
  | [quantumcomputing.stackexchange.com - Statistical Model](https://quantumcomputing.stackexchange.com/questions/23681/reference-for-surface-code-error-correction#:~:text=properties%2C statistical,to 3D and 4D lattices) | 指向同一页面中另一段文字，提到论文将**错误纠正映射到了统计物理模型**（比如随机绑定能量模型），并且还推广到更高维格子（3D/4D） | 说明论文内容不仅仅局限于2D，还提出了对更高维度的拓展思考     |

- 【Austin Fowler *et al.* (2012) – *Surface Codes: Towards Practical Large-Scale Quantum Computation*】

  - 网址：https://web.physics.ucsb.edu/~martinisgroup/papers/Fowler2012.pdf
  - 简介：这是 Fowler 及其同事撰写的一篇综述性论文，发表于 *Physical Review A* 第86卷第032324号，面向希望理解并应用表面码的实践者，具有很高的工程指导价值。
  - 核心内容：文章首先指出表面码起源于Kitaev提出的环面码，但强调环面几何结构在实际中并非必要，Bravyi、Kitaev、Freedman 和 Meyer随后提出了平面版本的表面码；文章讲解了如何在二维量子比特格子上利用稳定子形式（stabilizer formalism）构建表面码，展示了大型表面码晶格中逻辑比特的形成机制，并讨论了实际工程中的综合征提取电路、容错操作流程等；文中还提供了误差阈值的数值估计，并以教程风格编写，配有大量图示和附录，兼顾了概念理解与工程实现细节，是学习表面码设计与应用的重要资料。

  | 链接                                                         | 指向内容                                                     | 说明                                             |
  | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ |
  | [web.physics.ucsb.edu – Surface codes evolution](https://web.physics.ucsb.edu/~martinisgroup/papers/Fowler2012.pdf#:~:text=on surface codes ,4%2C10) | Fowler论文中，解释**表面码源自Kitaev的环面码**，但**去除了环面几何结构**，并由Bravyi等人提出了**平面版本** | 揭示了 surface code 和 toric code 的演化关系     |
  | [web.physics.ucsb.edu – Conceptual introduction](https://web.physics.ucsb.edu/~martinisgroup/papers/Fowler2012.pdf#:~:text=This article provides an introduction,how logical qubits are physically) | 指向同一篇文章中介绍性的部分：**详细介绍了如何构建表面码晶格，形成逻辑比特** | 是关于如何实际构建大型 surface code 的概念性导引 |
  | [web.physics.ucsb.edu – Surface codes evolution (重复)](https://web.physics.ucsb.edu/~martinisgroup/papers/Fowler2012.pdf#:~:text=on surface codes ,4%2C10) | 重复的指向，还是上面那个**surface codes 演变**的部分         | 强调 planar surface codes 的工程实际性           |

- 【Stephen Simon (Oxford) – *Topological Quantum Lecture Notes* (2021)】

  - 网址：https://topoquantumoxford.files.wordpress.com/2021/04/topological_quantum_book.pdf
  - 简介：这是牛津大学 Stephen Simon 教授撰写的《拓扑量子讲义》，为一部持续更新的自由获取教材（proto-book），从拓扑量子场论与量子存储的视角出发介绍基础概念。
  - 核心内容：在第9章中，讲义以较低的数学物理门槛独立介绍了环面码（toric code），避免直接使用复杂的拓扑量子场论（TQFT）形式化，然后进一步讲解了如何通过“切割”环面构造出平面表面码（planar codes）；虽然整体侧重于任意子性质（anyonic properties）和拓扑序（topological order），但也清晰地阐述了环面码的稳定子结构，并指出在适当边界条件下，平面环面码同样可以编码一个逻辑比特

  | 链接                                                     | 指向内容                                                     | 说明                                                         |
  | :------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
  | Topological Quantum Lecture Notes by Stephen Simon (PDF) | 讲义全文下载链接，作者是 Stephen Simon，Oxford 牛津大学，时间跨度 2016–2021年 | 第9章系统讲解了 toric code，并且以直观、低门槛方式引出表面码构造 |

## Video Lectures

- 【Alexei Kitaev – *Introduction to Surface Codes* (Keynote Talk, YouTube)】

  - 网址：YouTube 搜索关键词：“Kitaev surface codes keynote”（目前无官方固定链接，需要自行检索）
  - 简介：这是环面码发明者 Alexei Kitaev 在某次量子计算大会第二天发表的主旨演讲，向听众直接介绍环面码与表面码的基本概念与核心思想。
  - 核心内容：Kitaev在演讲中首先定义了环面码（toric code），然后展示了如何通过引入边界构造出表面码（surface code），用非常直观的方式讲解了编码中的任意子激发（anyonic excitations）以及拓扑在信息保护中的作用；演讲不仅面向初学者，且包含重要细节，如在环面与平面上稳定子（stabilizers）的排列方式，以及逻辑操作是如何对应到闭合回路或开放弦路径的，从发明者本人角度提供了对表面码工作机制的独特理解。

  | 链接                                | 指向内容                                               | 说明                                                         |
  | :---------------------------------- | :----------------------------------------------------- | :----------------------------------------------------------- |
  | （无具体链接，只是指向YouTube搜索） | **YouTube 搜索关键词**：“Kitaev surface codes keynote” | 可以找到Kitaev亲自讲授环面码与表面码的视频。是Day 2主旨演讲。 |

- 【IBM Qiskit Lecture – *Quantum Error Correction: CSS, Toric & Surface Codes* (YouTube)】

  - 网址：https://www.youtube.com/watch?v=H8ChK5lA0Cw
  - 简介：这是 IBM Qiskit 教育系列《理解量子信息与计算》的一部分，时长约1.5小时，专门讲解 CSS 码、环面码与表面码的关系，面向希望系统入门量子纠错的学习者。
  - 核心内容：讲座从简单的CSS码（Calderbank–Shor–Steane codes）出发，逐步过渡到环面码（toric code）和表面码（surface code），解释了稳定子形式（stabilizer formalism），展示了环面码如何作为在二维晶格上实现的一种特定CSS码，并进一步说明了转变为平面表面码的过程；讲座明确指出表面码是为适配实际硬件（二维排列量子比特带边界）而演变自环面码的；内容覆盖了星型和多边形稳定子的Pauli生成元、综合征提取方法（syndrome extraction）和错误解码器（error decoders），并且以直观易懂的方式兼顾了初学者友好性与技术深度。

  | 链接                                                         | 指向内容                                                     | 说明                                                         |
  | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
  | [YouTube – IBM Qiskit Lecture: "Quantum Error Correction: CSS, Toric & Surface Codes"](https://www.youtube.com/watch?v=H8ChK5lA0Cw) | IBM官方Qiskit频道发布的视频，完整讲座（时长约1.5小时），从CSS码入手，讲到环面码和表面码 | 循序渐进的讲解，适合初学者深入了解稳定子码、表面码构造及其与硬件实现的关系 |

- 【Big Think (2021) – *Progress Towards Quantum Error Correction with the Surface Code*】

  - 网址：https://www.youtube.com/watch?v=2g7E0xHdnJ0
  - 简介：这是 Big Think 发布的一则视频讲座，讲解表面码（surface code）在量子计算工业应用中的重要性，内容偏向高层次概览，数学推导较少。
  - 核心内容：视频重点说明了表面码在实际量子计算硬件开发中扮演的核心角色，讨论了它对提高量子计算容错性（fault tolerance）的关键意义，帮助观众从产业与应用的角度理解表面码的重要地位，是面向广泛受众的入门科普讲解。

  ------

  【Atilla Yurdakul – *Introduction to Toric Code* (YouTube)】

  - 网址：https://www.youtube.com/watch?v=ZB0qZHZHZjg
  - 简介：这是 Atilla Yurdakul 发表的一场学生讲座，专门讲解环面码（toric code）的基础概念及其与拓扑序（topological order）的关系，适合初学者温和入门。
  - 核心内容：讲座详细阐述了环面码中量子比特排列、稳定子测量和逻辑操作的基本原理，同时引入了任意子激发（anyonic excitations）和拓扑保护机制的初步概念，内容清晰细致，适合对拓扑量子纠错感兴趣但尚无深入背景知识的学习者。

  | 链接                                                         | 指向内容                                                     | 说明 |
  | :----------------------------------------------------------- | :----------------------------------------------------------- | :--- |
  | [YouTube – "Progress Towards Quantum Error Correction with the Surface Code" (Big Think, 2021)](https://www.youtube.com/watch?v=2g7E0xHdnJ0) | Big Think 发布的视频，概述了**表面码在工业界的重要性**。内容偏高层次（概念性较强），数学推导较少，适合了解应用背景。 |      |
  | [YouTube – Atilla Yurdakul: "Introduction to Toric Code"](https://www.youtube.com/watch?v=ZB0qZHZHZjg) | Atilla Yurdakul 的学生讲座视频，**详细讲解了环面码的基本概念**，并涉及一点**拓扑序（topological order）**。适合初学者温和入门。 |      |

## Code Repositories and Simulations

- 【Qiskit Topological Codes (GitHub)】

  - 网址：https://github.com/yaleqc/qtcodes
  - 简介：这是由耶鲁大学和IBM联合开发的开源项目 *qtcodes*，在Qiskit框架下实现了拓扑量子码（topological codes）的编码器和解码器，免费向公众开放。
  - 核心内容：项目支持旋转表面码（rotated surface code），这种表面码是实验中常用的平面码变体，并特别指出其理论基础源自环面码（toric code），只是将周期性边界改为开放边界以适应实际硬件布局；仓库内包含多个Jupyter Notebook示例，展示了如何编码逻辑比特、模拟错误综合征（error syndromes）、并应用不同的解码算法，是动手实践环面码/表面码理论与工程实现的优秀入门资源。

  | 链接                                                         | 指向内容                                                     | 说明 |
  | :----------------------------------------------------------- | :----------------------------------------------------------- | :--- |
  | [GitHub – Qiskit Topological Codes (qtcodes)](https://github.com/yaleqc/qtcodes#:~:text=,actual device is much easier) | Yale 和 IBM 联合开发的 Qiskit 拓扑码库，支持旋转表面码，强调其与环面码的关系，并包含Jupyter示例教程 |      |

- 【PanQEC – Topological Code Simulator (GitHub)】

  - 网址：https://github.com/panqec/panqec
  - 简介：PanQEC是一个由量子纠错领域研究人员开发的综合性Python软件包，用于模拟和可视化拓扑量子纠错码，支持多种拓扑码模型，面向从初学者到进阶研究者的广泛用户群体。
  - 核心内容：PanQEC提供了简洁的接口，允许用户通过定义晶格类型和边界条件快速创建环面码（toric code）、表面码（surface code）及三维拓扑码（3D codes）；内部自动构建奇偶校验矩阵并集成了多种解码器，支持带周期性边界（toric）与开放边界（planar）的二维表面码，同时支持标准方形格子和旋转格子；项目还包含一个交互式网页可视化器，用户可以实时插入错误并观察综合征与任意子对的形成过程，是理解拓扑量子码基本机制和研究误差阈值行为的重要工具。

  | 链接                                                         | 指向内容                                                     | 说明 |
  | :----------------------------------------------------------- | :----------------------------------------------------------- | :--- |
  | [GitHub – PanQEC: Topological Code Simulator](https://github.com/panqec/panqec#:~:text=In its current version%2C PanQEC,implements the following codes) | PanQEC官方GitHub仓库，支持定义2D/3D拓扑码，自动构建奇偶矩阵，内置多种解码器，提供实时错误可视化工具 |      |

- 【“The Toric Code” Simulation (GitHub by nanleij)】

  - 网址：https://github.com/nanleij/The-toric-code
  - 简介：这是由nanleij开发的一个简洁的Python实现项目，专门用于模拟环面码（toric code）及其基础解码过程，面向教学与学习目的开放源代码。
  - 核心内容：项目通过几百行Python代码构建了一个环面上的方形格子，将量子比特置于格子边上，并提供了插入错误和检测综合征的基本函数；实现了两种常见解码器：最小权完美匹配（MWPM）和并查集解码器（union-find decoder）；项目README指出这实际上相当于在环面上实现的表面码，使用Python模拟错误链产生综合征对以及解码器重连综合征的过程，是理解表面码/环面码基本纠错机制并进行小项目练习的良好起点。

  | 链接                                                         | 指向内容                                                     | 说明 |
  | :----------------------------------------------------------- | :----------------------------------------------------------- | :--- |
  | [GitHub – The Toric Code Simulation by nanleij](https://github.com/nanleij/The-toric-code#:~:text=The Toric Code ,find decoder programmed in python) | Python实现的小型环面码模拟器，包含MWPM与Union-Find两种解码器，适合教育用途和初步学习 |      |

Each of these resources will help you understand **how the toric code and surface code are related** and what sets them apart. In summary, the **toric code** is a topological [[n,k,dn,k,dn,k,d]] code defined on a closed surface (a torus) with *periodic boundaries*, typically yielding two logical qubits for a single torus (since a torus has two non-contractible loops)[errorcorrectionzoo.org](https://errorcorrectionzoo.org/c/surface#:~:text=The original planar code on,have been investigated  6). The **surface code** usually refers to the same code idea realized on a planar patch of qubits with *open boundaries* – one needs two types of boundaries (often called *rough* and *smooth*) to mimic the two kinds of loops[errorcorrectionzoo.org](https://errorcorrectionzoo.org/c/surface#:~:text=The construction on closed surfaces,6). This planar version encodes fewer logical qubits (often just one per patch, unless additional holes or boundaries are introduced) but is far easier to implement in hardware[thp.uni-koeln.de](https://www.thp.uni-koeln.de/kastoryano/ExSheets/Notes_v9.pdf#:~:text=In particular%2C the toric code,we consider a quadrilateral surface)[web.physics.ucsb.edu](https://web.physics.ucsb.edu/~martinisgroup/papers/Fowler2012.pdf#:~:text=known as toric codes ,4%2C10). The core stabilizer structure (star **X** stabilizers and plaquette **Z** stabilizers on a 2D grid of qubits) is the same in both cases. We encourage exploring the above textbooks/notes for theory, the videos for intuitive explanation, and the coding resources for practical insight. Each will reinforce the idea that the **surface code is essentially Kitaev’s toric code adapted to a flat geometry**, retaining the topological protection while being compatible with real-world layouts[web.physics.ucsb.edu](https://web.physics.ucsb.edu/~martinisgroup/papers/Fowler2012.pdf#:~:text=on surface codes ,4%2C10)[thp.uni-koeln.de](https://www.thp.uni-koeln.de/kastoryano/ExSheets/Notes_v9.pdf#:~:text=The X and Z logical,gives a new logical operator).

**Sources:**

- Bombín, H. *“An Introduction to Topological Quantum Codes,”* in **Quantum Error Correction** (Ed. Lidar & Brun, CUP 2013) – Ch. 4 on Surface Codes[arxiv.org](https://arxiv.org/pdf/1311.0277#:~:text=Figure 12%3A A planar toric,85%2C 1%2C 7]] code)[arxiv.org](https://arxiv.org/pdf/1311.0277#:~:text=toric code ,3]. This work introduced).
- Kastoryano, M. *Lecture Notes on Quantum Error Correction* – Section 12: Surface Codes (University of Cologne)[thp.uni-koeln.de](https://www.thp.uni-koeln.de/kastoryano/ExSheets/Notes_v9.pdf#:~:text=12,we consider a quadrilateral surface)[thp.uni-koeln.de](https://www.thp.uni-koeln.de/kastoryano/ExSheets/Notes_v9.pdf#:~:text=The X and Z logical,gives a new logical operator).
- Dennis, E. *et al.*, *“Topological quantum memory,”* **J. Math. Phys.** 43, 4452 (2002)[quantumcomputing.stackexchange.com](https://quantumcomputing.stackexchange.com/questions/23681/reference-for-surface-code-error-correction#:~:text=Topological quantum memory by Eric,free encoding).
- Fowler, A. *et al.*, *“Surface codes: Towards practical large-scale quantum computation,”* **Phys. Rev. A** 86, 032324 (2012)[web.physics.ucsb.edu](https://web.physics.ucsb.edu/~martinisgroup/papers/Fowler2012.pdf#:~:text=on surface codes ,4%2C10).
- Simon, S. *Topological Quantum* (Oxford lecture notes, 2021), Ch. 9 (Toric Code).
- **YouTube:** Kitaev Keynote *“Introduction to surface codes”*[youtube.com](https://www.youtube.com/watch?v=M25fBmF9XR0&pp=ygULI3NocnV0aXB1cmk%3D#:~:text=In this Day 2 Keynote%2C,their physical interpretation and); Qiskit Video *“QEC: CSS, Toric & Surface Codes.”*
- **GitHub:** Yale/IBM **Qiskit Topological Codes** (qtcodes)[github.com](https://github.com/yaleqc/qtcodes#:~:text=,actual device is much easier); **PanQEC** Simulator[github.com](https://github.com/panqec/panqec#:~:text=In its current version%2C PanQEC,implements the following codes); **nanleij – The Toric Code** (Python)[github.com](https://github.com/nanleij/The-toric-code#:~:text=The Toric Code ,find decoder programmed in python).