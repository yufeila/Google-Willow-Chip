<!--
 * @Author: ����� 166906656+yufeila@users.noreply.github.com
 * @Date: 2025-04-21 00:25:38
 * @LastEditors: ����� 17786321727@163.com
 * @LastEditTime: 2025-04-27 15:45:16
 * @FilePath: /Google-Willow-Chip/README.md
 * @Description: ����Ĭ������,������`customMade`, ��koroFileHeader�鿴���� ��������: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%*AE*
-->
# Google-Willow-Chip

# Google Willow Chip: Quantum Error Correction and Real-Time Decoding

This project explores the principles, simulation techniques, and engineering implementation of **quantum error correction (QEC)** through the case study of Google's **Willow chip**, the first system to demonstrate real logical error rate suppression using **surface code**.

## �9�8 Project Overview

Quantum computing promises unprecedented computational power, but **quantum bits (qubits)** are fragile and easily disturbed by noise and decoherence. **Quantum Error Correction (QEC)** encodes logical qubits into multiple physical qubits to detect and correct errors without disturbing quantum information.

In 2023, **Google's Willow chip** demonstrated:
- A 105-qubit superconducting processor with distance-7 surface code
- Logical qubit lifetime exceeding physical ones by 2.4��
- Hardware-accelerated real-time decoding using **Fusion Blossom**

This project aims to both understand and simulate QEC workflows, and evaluate Willow��s engineering innovations.

---

## �9�3 Objectives

1. **Theoretical Understanding**  
   Learn how QEC works using **repetition and phase-flip codes**, exploring stabilizers, logical qubits, and surface codes.

2. **Simulation Practice**  
   Implement and test QEC pipelines using Python with:
   - `QuTiP` for quantum state simulation
   - `PyMatching` for MWPM decoding
   - `Fusion Blossom` for real-time, hardware-friendly decoding

3. **Case Study Analysis**  
   Investigate the Willow chip��s design, error suppression results, and decoding architecture.

---

## �9�1�1�5 Project Timeline (6 Weeks)

| Week | Topic                                    | Tools & Goals |
|------|------------------------------------------|---------------|
| 1    | Repetition Code & QEC Basics             | Simulate bit-flip error correction with QuTiP |
| 2    | Phase-Flip Code & CSS Structure          | Explore Z-errors, Hadamard tricks, and phase repetition |
| 3    | Stabilizer Formalism & Surface Code      | Study stabilizer layout, logical ops, and distance |
| 4    | Surface Code Simulation                  | Decode syndromes via MWPM using PyMatching |
| 5    | Scaling & Threshold Behavior             | Vary code distances to observe logical error trends |
| 6    | Google Willow Chip Case Study            | Analyze experimental results, decoding strategy, and limitations |

### ��һ������ �ظ������������Ӿ����������

**����Ŀ����ѧϰ�ص㣺**��⾭�������Ӵ�������𣬳������վ���Ļ���˼�롣ѧ����ѧϰ�򵥵��ظ���(repetition code)ԭ���˽����ͨ��������������͸������ط�ת�����ص�������⾭���������ظ�����μ�ⵥ���ش����Լ���������²�������������ս�ͽ������������������żУ���������ֱ�Ӳ�������λ
״̬����

**�漰�����Ӽ�����**���ط�ת����X���󣩵ĸ��������������Ӿ������ͬ������������̬���Ŷ�����żУ�飨parity������˼�롣�������߼����أ������ڶ����������ϵ���Ϣ����������ص�����

**�Ƽ��Ĺ���**��QuTiP����ģ�������̬�ݻ��Ͳ�����ѧ����ʹ��QuTiP����3���ӱ��ص�̬��Ӧ���Ų����������ֳ����ӵ�·ģ�飬���ֶ�ʵ��CNOT���š�Ҳ�ɽ���Python�����⴦����ط�ת���߼���������0/1��ʾ̬��ģ��������;�
������ʵ�ֵı������/Сʵ�飺ʵ��3�����ظ���������̵�ģ�⡣�������������

a. ���룺��һ���߼����أ�|0�7�1 �� |1�7�1�����뵽3��������أ�����ͨ������CNOT�Ž���һ�����ظ��Ƶ��ڶ��������������ϣ��õ� |000�7�1 �� |111�7�1״̬��
b. ����������ѡ��һ���������ʩ��һ�� X ���������ط�ת����ģ�ⵥ���ش���
c. �����⣺ģ�������żУ�飬���������1��2�Ƿ���ͬ���Լ�����2��3�Ƿ���ͬ�����൱�ڲ��������ȶ��ӣ�stabilizer�� �͵Ľ������ȡ�ۺ�����Ϣ(syndrome)��ע�⣬������żУ�����������ֱ
�ӻ�ȡÿ�����ص�ֵ���Ӷ������������Ϣ���ƻ�thepaper.cn��
d. ��������������ۺ����ж���һ�����ط����˷�ת��������ʩ��X������������
e. ��֤������3��������أ���֤�����õ����߼�����״̬�Ƿ����ʼһ�¡�

### ����ѧϰ

- [Qiskit �̿��� & IBM ѧϰ�γ�](https://learning.quantum.ibm.com/course/foundations-of-quantum-error-correction/correcting-quantum-errors):  
  IBM �ṩ�������ѧ�ߵ����߽̲��½ڣ��� *��Correcting Quantum Errors��*��ϵͳ���������Ӵ���У���Ļ���ԭ��͵�һ�����ֵ������롪��9���� Shor �롣�γ̴Ӿ�����������ظ������루˵�����ͨ������������������ش��󣩣��𲽹��ɵ� Shor ����ν����ط�ת�����λ��ת�뼶��ʵ��ͬʱ���� X/Z ���󡣽̲Ļ�ǿ���� **���Ӵ�����ɢ��** ��һ���ĸ��������΢С�Ŷ��ɵ�ЧΪ���޼��ϵ� Pauli ���󣬴Ӷ�ʹ�����Ϊ���ܡ���Щ�ٷ��̳����н���ʾ������ϰ�⣬�����ڹ��̸��

- [Quantum Error Correction for Beginners (��ѧ��ָ��)](https://ar5iv.org/html/0905.2794):  
  Devitt ������ 2009 ��׫д��Ȩ�����������Ӿ�������ۻ�������ͨ�׽��ܣ��ǳ��ʺ�����һ�����ӱ����Ķ��߼�����⡣����ͨ����ϸʵ�������˾�����ش�������Ӵ�������������� **3������** Ϊ�����ͻ���ԭ��Ȼ������˵�һ�����������Ӿ����롪��**9���� Shor ��**������ϵͳ�������ȶ��� Formalism���ȶ��ӹ淶�������Ӿ����е�Ӧ�ã����������ݴ����Ӽ������ֵ����Ƚ������⣬��ѧϰ�ȶ��������۵ľ���ο�֮һ��

- [Stabilizer Codes and Quantum Error Correction (Chapter 1-3)](./Week1/Reference/Stabilizer%20Codes%20and%20Quantum%20Error%20Correction%28Chapter%201-3%29.pdf):  
  �� Week1/Reference �ļ��С�


### ����ʵ��

- [Qiskit ʵ�� 3 ���ر��ط�ת���·ʾ��](https://quantumcomputinguk.org/tutorials/quantum-error-correction-bit-flip-code-in-qiskit):  
  ��ϸ�̳�չʾ�����ʹ�� Qiskit ���� 3 ���ر��ط�ת���·��

- [IBM Quantum Learning �ظ���̳�](https://learning.quantum.ibm.com/tutorial/build-repetition-codes):  
  IBM �ṩ�Ľ̳̣��������ʵ���ظ���ı���;���

### �̳���Ƶ

- [James Wootton �����Ӿ�������](https://www.youtube.com/watch?v=ZY8PddknCos):  
  James Wootton ����Ƶ�̳̣��������Ӿ���Ļ������

- [12 Days of Qiskit ϵ��֮���Ӿ���](https://www.youtube.com/watch?v=e-EaIs-Qr78):  
  Qiskit �ٷ�ϵ����Ƶ���������Ӿ���Ļ���֪ʶ��

- [Steve Girvin �ݴ���㽲��](https://www.youtube.com/watch?v=PI8PqARCwWo):  
  Yale ��ѧ Steve Girvin ���ڵĽ���������̽���ݴ����Ӽ��㡣
---

## �0�0 Simulation Tools

| Tool | Purpose |
|------|---------|
| [QuTiP](http://qutip.org/) | Simulate small quantum states, encode repetition codes |
| [PyMatching](https://github.com/oscarhiggott/PyMatching) | Perform minimum-weight perfect matching (MWPM) for surface codes |
| [Fusion Blossom](https://github.com/yazhe-li/fusion-blossom) | Fast real-time decoder used in Willow with sliding-window support |

---

## �9�4 Core Concepts

- **Quantum Errors**: Bit-flip ($X$), phase-flip ($Z$), and combinations.
- **Stabilizers**: Commuting sets of Pauli operators to detect errors.
- **Logical vs Physical Qubits**: Encoded information vs actual hardware bits.
- **Surface Code**: A 2D QEC code that supports high error thresholds and is experimentally scalable.

---

## �9�8�6�9�9�1 Team Structure

- **Research Lead**: Theory exploration, literature review, writing
- **Simulation Lead**: Code development with QuTiP / PyMatching / Fusion Blossom
- **Presentation Lead**: Timeline, slides, visualization, demo coordination

---

## �9�4 Deliverables

- �7�3 A 5-minute presentation explaining QEC and Willow chip
- �7�3 Python-based simulation report with figures and results
- �7�3 Final written report with findings, architecture analysis, and references

---

## �9�3 References

- [Google Quantum AI](https://quantumai.google/)
- [Nature paper on Willow Chip (2023)](https://www.nature.com/articles/s41586-024-08449-y)
- [PyMatching on GitHub](https://github.com/oscarhiggott/PyMatching)
- [Fusion Blossom on GitHub](https://github.com/yazhe-li/fusion-blossom)
- [Surface Code Overview (Fowler et al. PRA 86, 032324)](https://journals.aps.org/pra/abstract/10.1103/PhysRevA.86.032324)

---

## �9�7 Repository Structure

