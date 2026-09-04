# Résolution-EDP-PINN

Comparative study of **Physics-Informed Neural Networks (PINNs)** and the **Finite Difference Method (FDM)** for solving partial differential equations — developed as part of an end-of-studies project (PFA) at École Mohammadia d'Ingénieurs (EMI).

## Overview

The notebook explores the 1D heat equation as a model problem, then extends the study to an inverse problem and a nonlinear PDE:

1. **Analytical reference solution** — closed-form solution for the heat equation with sinusoidal initial condition, used to validate both numerical methods
2. **CFL stability analysis** of the explicit finite-difference scheme (r = αΔt/Δx²)
3. **Quantitative comparison** (L² error) between FDM, PINN, and the exact solution
4. **Inverse problem** — recovering the unknown diffusion coefficient α from noisy data using a PINN
5. **Extension to Burgers' equation** — a canonical nonlinear PDE benchmark for PINNs, including shock formation

## Method comparison

| Method | Direct (heat equation) | Inverse (unknown α) | Nonlinear (Burgers) |
|--------|:---:|:---:|:---:|
| FDM    | ✅ fast, accurate | ❌ requires external optimization | ⚠️ struggles with shocks |
| PINN   | ✅ mesh-free | ✅ natural fit | ✅ canonical benchmark |

## Tech stack

- Python 3.10
- [DeepXDE](https://deepxde.readthedocs.io/) (PyTorch backend) for the PINN implementations
- NumPy, Matplotlib for numerical methods and visualization

## Running the notebook

```bash
pip install deepxde torch numpy matplotlib
```

Set the DeepXDE backend to PyTorch before running (already handled at the top of the notebook):

```python
import os
os.environ["DDE_BACKEND"] = "pytorch"
```

Then open `pinn_edp_complete.ipynb` in Jupyter or Google Colab and run all cells. Generated figures are saved to the `results/` directory.

## References

- Raissi, Perdikaris, Karniadakis (2019). *Physics-informed neural networks.* Journal of Computational Physics.
- Lu, Meng, Mao, Karniadakis (2021). *DeepXDE: A deep learning library for solving differential equations.* SIAM Review.
- Karniadakis et al. (2021). *Physics-informed machine learning.* Nature Reviews Physics.
