# Continuous Variable QAOA on Xanadu Backends

After surveying several commercially available quantum platforms, we chose to work with **Xanadu**, a leader in photonic quantum computing. Xanadu has generously granted us access to both their **X8 hardware** and the **`simulon_gaussian` backend simulator**.

This repository contains two Jupyter notebooks that implement the **Continuous Variable Quantum Approximate Optimization Algorithm (CV-QAOA)**, inspired by the excellent work of **Jack Ceroni**, who has generously shared his research through his GitHub account: [Lucaman99](https://github.com/Lucaman99).

The two original examples that served as the foundation for this project are:

- [**Continuous QAOA**](https://lucaman99.github.io/blog/2019/07/06/Continuous-QAOA.html) — adapted into `qaoaOnGaussianSimulon.ipynb`
- [**CV-QAOA Implementation with Xanadu**](https://github.com/Lucaman99/Quantum-Computing/blob/master/xanadu/cvqaoa.ipynb) — adapted into `cvqaoaOnSimulonSuccessful.ipynb`

We adopted and modified these examples to make them compatible with **Xanadu’s `simulon_gaussian` backend**, introducing only minor changes where needed to fit the constraints of this simulator.

During our research and implementation process, we encountered a number of important constraints and challenges specific to these platforms.

---

## Attempt to Run on Xanadu X8 Hardware

As part of this project, we attempted to implement the CV-QAOA algorithm on **Xanadu’s X8 hardware** — the only available photonic quantum chip on their cloud platform.

However, through discussions with Xanadu’s support team, we learned that the **X8 is a passive device** and **cannot implement displacement operations**, which are essential for the cost unitary:

```math
e^{i p \hat{x} / \hbar}
```

# Limitations of the Xanadu Hardware and Simulator

While the **Xanadu X8 hardware** offers exciting possibilities as a photonic quantum processor, it unfortunately proved unsuitable for implementing the CV-QAOA algorithm. This is primarily because the X8 is a **passive device**, lacking the ability to perform **displacement operations**, which are fundamental to the cost unitary in CV-QAOA:

$$
e^{i p \hat{x} / \hbar}
$$

Without displacement, key components of the algorithm cannot be realized on the hardware, which restricted our ability to run the full protocol outside of simulation.

---

## Challenges with the `simulon_gaussian` Backend Simulator

Given the hardware limitations, we focused our efforts on the **`simulon_gaussian`** backend simulator, which is capable of simulating continuous-variable photonic circuits including displacement and squeezing operations.

However, this simulator presented its own challenge: it **does not support the `Pgate`**, the quadratic phase gate defined as

$$
\hat{P}(s) = \exp\left( i \frac{s}{2\hbar} \hat{x}^2 \right),
$$

which is essential for implementing certain parts of the QAOA cost unitary.

---

## Workaround: Emulating the `Pgate` via Conjugation

To address this, we employed a well-known decomposition of the `Pgate` in terms of rotation and displacement gates, leveraging the identity

$$
\hat{P}(s) = \hat{R}(-\pi/2) \, \hat{Z}(s) \, \hat{R}(\pi/2),
$$

where:

- **`Pgate(s)`** implements a momentum shear, corresponding to a quadratic phase shift in the position basis.
- **`Zgate(z)`** performs a momentum displacement:

  $$
  \hat{Z}(z) = \exp(i z \hat{x}),
  $$

- **`Rgate(θ)`** is a phase-space rotation:

  $$
  \hat{R}(\theta) = \exp(i \theta \hat{n}),
  $$

  acting on annihilation operators as:

  $$
  \hat{a} \to \hat{a} \cos \theta + \hat{a}^\dagger \sin \theta,
  $$

  and on quadratures as:

  $$
  \hat{p} \to \hat{p} \cos \theta - \hat{x} \sin \theta.
  $$

Although neither `Rgate` nor `Zgate` individually can replace the `Pgate`, the conjugation by rotation gates realizes the quadratic phase gate effectively.

---

## Code Snippet for Emulation

```python
Rgate(-np.pi/2) | q[0]
Zgate(-2 * hbar * p) | q[0]
Rgate(np.pi/2) | q[0]

