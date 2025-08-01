# Continuous Variable Photonic Simulations with Quandela Perceval

As part of our broader survey of commercially available quantum computing platforms, this repository explores the photonic quantum computing framework developed by **Quandela** — a European leader in discrete-variable (DV) photonics.

Quandela provides open-access tools for photonic quantum simulation through their [Perceval](https://perceval.quandela.net/docs/v0.13/index.html#) Python library, which facilitates photonic circuit construction, simulation, and compilation.

## About This Repository

This repository contains Jupyter notebooks that explore the use of Perceval to implement and simulate photonic quantum circuits, with bosonic quantum computing. In particular, we have adapted and extended examples such as the Variational Quantum Eigensolver (VQE) from the official Quandela documentation ([VQE example](https://perceval.quandela.net/docs/v0.6/notebooks/Variational%20Quantum%20Eigensolver.html)) to run on Quandela’s backend simulator as well as on their available real hardware platforms.

The implementation examples in this repository focus on:

- Adapting Perceval’s example circuits to run on backend simulators and hardware
- Building photonic circuits using Perceval’s intuitive syntax and modular components


## Why Quandela?

Quandela’s photonic stack is one of the most complete among commercial vendors, offering:

- A user-friendly Python API (`perceval`)
- A web-based knowledge center for theory, practical examples, and tutorials
- Simulators that can efficiently handle intermediate-scale quantum photonic circuits
- A growing focus on hardware-software co-design, including access to real quantum photonic chips

## Getting Started

To follow the notebooks in this repository, install Perceval (v0.13 or higher):

```bash
pip install perceval
```


## Usage Limitations and Licensing (Quandela)

Quandela's platform provides access to both backend simulators and real photonic hardware. However, under the free-tier account, there are important limitations:

- **Runtime per job is limited to 5 minutes**
- **Only 200 credits are provided**, which is often insufficient for running more complex or updated algorithms such as VQE.

For academic users, it is possible to apply for an **academic license**, which increases the job runtime to **30 minutes**. This is very helpful for running longer simulations or hybrid quantum-classical algorithms.

That said, even with the academic license, **additional credits must still be purchased** to run jobs beyond the small free allocation.

## Python version: Python 3.13.3





