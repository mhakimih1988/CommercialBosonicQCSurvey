# Continuous-Variable Quantum Circuit Comparison: Strawberry Fields vs. Bosonic Qiskit

This repository explores and compares two photonic quantum computing frameworks:

- [**Strawberry Fields**](https://strawberryfields.ai) by Xanadu — a platform for continuous-variable (CV) quantum computing.
- [**Bosonic Qiskit (C2QA)**]([https://github.com/Qiskit/bosonic-qiskit](https://github.com/C2QA/bosonic-qiskit) — an extension of Qiskit for simulating CV and hybrid CV-DV (continuous-variable/discrete-variable) systems.

## Overview

We began by reproducing and studying an existing Xanadu-based CV-QAOA implementation from:

> 📎 [qaoaOnGaussianSimulon.ipynb](https://github.com/mhakimih1988/CommercialBosonicQCSurvey/blob/main/XanaduSF/qaoaOnGaussianSimulon.ipynb)

Then, we attempted to recreate similar behavior using **Bosonic Qiskit** (C2QA). The goal was to gain a sense of how both platforms handle continuous-variable quantum circuits, and where their strengths and limitations lie.

## Key Points

- **Strawberry Fields** only supports **purely continuous-variable (CV)** gates. It does not natively support hybrid CV-DV operations such as *conditional displacement*.
- **Bosonic Qiskit (BQ)** supports **both CV and hybrid CV-DV** circuits. To our knowledge, it is currently the only accessible framework that includes hybrid gates (e.g., conditional CV operations conditioned on Fock states).
- While **PennyLane** also integrates with Strawberry Fields and supports CV/DV devices separately, it does **not** (yet) provide native **hybrid CV-DV gates** or circuit constructs.

## Folder Structure

