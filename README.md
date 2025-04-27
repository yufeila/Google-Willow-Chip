<!--
 * @Author: 杨宇菲 166906656+yufeila@users.noreply.github.com
 * @Date: 2025-04-21 00:25:38
 * @LastEditors: 杨宇菲 166906656+yufeila@users.noreply.github.com
 * @LastEditTime: 2025-04-21 00:57:40
 * @FilePath: /Google-Willow-Chip/README.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%*AE*
-->
# Google-Willow-Chip

# Google Willow Chip: Quantum Error Correction and Real-Time Decoding

This project explores the principles, simulation techniques, and engineering implementation of **quantum error correction (QEC)** through the case study of Google's **Willow chip**, the first system to demonstrate real logical error rate suppression using **surface code**.

## 📌 Project Overview

Quantum computing promises unprecedented computational power, but **quantum bits (qubits)** are fragile and easily disturbed by noise and decoherence. **Quantum Error Correction (QEC)** encodes logical qubits into multiple physical qubits to detect and correct errors without disturbing quantum information.

In 2023, **Google's Willow chip** demonstrated:
- A 105-qubit superconducting processor with distance-7 surface code
- Logical qubit lifetime exceeding physical ones by 2.4×
- Hardware-accelerated real-time decoding using **Fusion Blossom**

This project aims to both understand and simulate QEC workflows, and evaluate Willow’s engineering innovations.

---

## 🎯 Objectives

1. **Theoretical Understanding**  
   Learn how QEC works using **repetition and phase-flip codes**, exploring stabilizers, logical qubits, and surface codes.

2. **Simulation Practice**  
   Implement and test QEC pipelines using Python with:
   - `QuTiP` for quantum state simulation
   - `PyMatching` for MWPM decoding
   - `Fusion Blossom` for real-time, hardware-friendly decoding

3. **Case Study Analysis**  
   Investigate the Willow chip’s design, error suppression results, and decoding architecture.

---

## 🗓️ Project Timeline (6 Weeks)

| Week | Topic                                    | Tools & Goals |
|------|------------------------------------------|---------------|
| 1    | Repetition Code & QEC Basics             | Simulate bit-flip error correction with QuTiP |
| 2    | Phase-Flip Code & CSS Structure          | Explore Z-errors, Hadamard tricks, and phase repetition |
| 3    | Stabilizer Formalism & Surface Code      | Study stabilizer layout, logical ops, and distance |
| 4    | Surface Code Simulation                  | Decode syndromes via MWPM using PyMatching |
| 5    | Scaling & Threshold Behavior             | Vary code distances to observe logical error trends |
| 6    | Google Willow Chip Case Study            | Analyze experimental results, decoding strategy, and limitations |

---

## 🛠 Simulation Tools

| Tool | Purpose |
|------|---------|
| [QuTiP](http://qutip.org/) | Simulate small quantum states, encode repetition codes |
| [PyMatching](https://github.com/oscarhiggott/PyMatching) | Perform minimum-weight perfect matching (MWPM) for surface codes |
| [Fusion Blossom](https://github.com/yazhe-li/fusion-blossom) | Fast real-time decoder used in Willow with sliding-window support |

---

## 🔬 Core Concepts

- **Quantum Errors**: Bit-flip ($X$), phase-flip ($Z$), and combinations.
- **Stabilizers**: Commuting sets of Pauli operators to detect errors.
- **Logical vs Physical Qubits**: Encoded information vs actual hardware bits.
- **Surface Code**: A 2D QEC code that supports high error thresholds and is experimentally scalable.

---

## 👨‍💻 Team Structure

- **Research Lead**: Theory exploration, literature review, writing
- **Simulation Lead**: Code development with QuTiP / PyMatching / Fusion Blossom
- **Presentation Lead**: Timeline, slides, visualization, demo coordination

---

## 📦 Deliverables

- ✅ A 5-minute presentation explaining QEC and Willow chip
- ✅ Python-based simulation report with figures and results
- ✅ Final written report with findings, architecture analysis, and references

---

## 🔗 References

- [Google Quantum AI](https://quantumai.google/)
- [Nature paper on Willow Chip (2023)](https://www.nature.com/articles/s41586-024-08449-y)
- [PyMatching on GitHub](https://github.com/oscarhiggott/PyMatching)
- [Fusion Blossom on GitHub](https://github.com/yazhe-li/fusion-blossom)
- [Surface Code Overview (Fowler et al. PRA 86, 032324)](https://journals.aps.org/pra/abstract/10.1103/PhysRevA.86.032324)

---

## 📁 Repository Structure

