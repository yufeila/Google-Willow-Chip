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