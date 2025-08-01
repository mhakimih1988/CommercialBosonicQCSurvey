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

To explore the capabilities of different bosonic quantum frameworks, we implemented a CV-QAOA-inspired algorithm using both:

- **Strawberry Fields** (Xanadu)
- **Bosonic Qiskit** (C2QA)

This comparison is limited to **continuous-variable (CV)** components only, because **Strawberry Fields does not support hybrid CV-DV gates**. In contrast, **Bosonic Qiskit does support hybrid gates**, such as **conditional displacements**, which opens up more flexibility in circuit design.

📄 **Read the detailed comparison report:**  
[comparisonBQ_SF.pdf](CVQaoaCompSFvsBQ/comparisonBQ_SF.pdf)

---


```text
.
├── CVQaoaCompSFvsBQ/           # CV-QAOA comparison: Strawberry Fields vs. Bosonic Qiskit
│   ├── cvqaoaSFLike.ipynb        # CV-QAOA using Bosonic Qiskit in SF-like form
│   ├── comparisonBQ_SF.pdf       # Summary of CV-only comparison findings
│   └── README.md                 # Section-specific notes

├── XanaduSF/                   # Work with Xanadu’s Strawberry Fields
│   ├── qaoaOnGaussianSimulon.ipynb
│   ├── cvqaoaOnSimulonSuccessful.ipynb
│   └── README.md

├── quandelaPerceval/           # Work with Quandela’s Perceval platform
|   ├── VQE_onTheBackend.ipynb      # Attempted VQE implementation on supported backend
│   └── README.md


├── survey_report.pdf           # High-level PDF report outlining project goals
└── README.md                   # This file
```
