# Exploring Bosonic Quantum Computing Platforms

This repository is dedicated to exploring **bosonic quantum systems**, particularly in the context of continuous-variable (CV) and discrete-variable (DV) models. Our focus lies in understanding gate capabilities, simulation tools, hardware constraints, and the compatibility of each platform with algorithms such as the **Quantum Approximate Optimization Algorithm (QAOA)**.

---

## 📌 Goals and Strategy

The main goals of this project are:

- Investigate **gate-level capabilities** across CV and DV models
- Explore **compatibility with QAOA-type circuits**

We focus on three commercially active platforms:

- **Xanadu** (*Strawberry Fields*)
- **Quandela** (*Perceval*)
- **Bosonic Qiskit** (*C2QA extension of Qiskit*)

Due to their superior documentation, device access, and simulator tools, we place special emphasis on **Xanadu** and **Quandela** in this study.

You can find a summary of this strategy in the accompanying short survey report PDF in the repository.

---

## ⚖️ CV Comparison: Strawberry Fields vs. Bosonic Qiskit

To explore the capabilities of different photonic quantum frameworks, we implemented a CV-QAOA-inspired algorithm using both:

- **Strawberry Fields** (Xanadu)
- **Bosonic Qiskit** (C2QA)

This comparison is limited to **continuous-variable (CV)** components only, because **Strawberry Fields does not support hybrid CV-DV gates**. In contrast, **Bosonic Qiskit does support hybrid gates**, such as **conditional displacements**, which opens up more flexibility in circuit design.

The comparison focuses on:

- Gate support and expressivity
- Circuit construction and simulation
- Alignment with CV-QAOA structures

📄 **Read the detailed comparison report:**  
[comparisonBQ_SF.pdf](CVQaoaCompSFvsBQ/comparisonBQ_SF.pdf)

---


## 📁 Repository Structure

```text
.
├── CVQaoaCompSFvsBQ/           # Comparison between Strawberry Fields and Bosonic Qiskit (CV only)
│   └── comparisonBQ_SF.pdf     # Report summarizing findings from CV-level comparison
│
├── XanaduSF/                   # Notebooks and materials for Xanadu's Strawberry Fields platform
│   └── qaoaOnGaussianSimulon.ipynb
│
├── quandelaPerceval/           # Code and analysis for the Quandela (Perceval) platform
│
├── survey_report.pdf           # High-level overview of platform goals and focus
│
└── README.md                   # This file
