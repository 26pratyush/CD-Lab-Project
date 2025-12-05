# ⚛️ Qiskit Quantum Compiler Demo

A hands-on prototype demonstrating **quantum compiler stages** using Qiskit's transpiler pipeline on a 5-qubit variational circuit targeting IBM's `FakeSherbrooke` backend.

## 💡 Overview

This project showcases a **quantum compiler workflow** by building a test circuit (Hadamard superposition $\rightarrow$ CNOT entanglement $\rightarrow$ Rx/Ry rotations $\rightarrow$ measurement), then applying Qiskit's preset **pass managers** at optimization levels **0-3**.

It quantifies improvements in circuit **depth**, **gate count**, and **two-qubit operations** while verifying functional equivalence via simulator runs. Based on quantum circuit optimization research for NISQ devices, the demo highlights **layout, routing, gate fusion, and rewriting passes.**

## ✨ Features

* **Realistic 5-qubit test circuit** mimicking VQE/QAOA ansätze.
* Targets `FakeSherbrooke` (127-qubit IBM superconducting model with **connectivity constraints**). 
* Compares optimization levels **0-3** (baseline $\rightarrow$ aggressive rewriting).
* Generates metrics tables, circuit diagrams, and output histograms.
* Verifies semantics preservation (original vs. optimized distributions match).

## 🛠️ Prerequisites

* Python 3.10+
* Qiskit 1.2+ (includes Aer, IBM Runtime, Visualization)

---

**Run all cells to see:**

  * Original circuit visualization
  * Level-by-level transpilation metrics
  * Bar charts comparing depth/gate counts
  * Simulator verification of output distributions

-----

## 📊 Results

Higher optimization levels reduce **depth by \~70%** and **two-qubit gates** significantly, with **level-2** producing hardware-native circuits (ECR gates, routed layout) that match original behavior.

| Level | Depth | Size (Total Gates) | Two-Qubit (CX/ECR) Gates |
| :---: | :---: | :---: | :---: |
| **Original** | 10 | 28 | 8 |
| **0** (Layout) | 61 | 118 | 20 |
| **2** (Optimized) | \~20 | \~80 | \~6 |

## 📚 Research Basis

Inspired by **"A Comprehensive Review of Quantum Circuit Optimization"** (Karuppasamy et al.), focusing on **NISQ challenges**: noise, connectivity, and depth minimization via local/global rewriting and hardware mapping.


## 🔜 Future Work

  * Custom pass pipelines
  * ML-assisted routing
  * Error mitigation integration
  * Larger benchmarks (20+ qubits)
  * Real IBM Quantum hardware execution
