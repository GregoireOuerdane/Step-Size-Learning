# Online Scaled Gradient Methods (OSGM) for Step-size Learning

This repository contains the implementation of **Online Scaled Gradient Methods (OSGM)**, a framework for adaptive step-size learning in gradient-based optimization. The methods achieve **superlinear convergence** on strongly convex quadratic problems using first-order information.

## 📖 Overview

Gradient-based optimization methods often suffer from convergence speed limitations due to fixed step sizes. This project implements novel adaptive methods that learn optimal preconditioning matrices online, accelerating gradient descent beyond classical rates.

### Key Features

- **Three OSGM variants**: Ratio (OSGM-R), Gradient Norm (OSGM-G), and Hypergradient (OSGM-H) surrogate losses
- **Accelerated version**: OSGM-R combined with Nesterov's momentum
- **Theoretical guarantees**: Superlinear convergence on strongly convex quadratics
- **Empirical validation**: Up to 30% faster convergence compared to standard accelerated gradient descent

## Implemented Algorithms

| Algorithm | Description | Requires f(x*) |
|-----------|-------------|----------------|
| **OSGM-R** | Ratio surrogate loss | Yes |
| **OSGM-G** | Gradient norm surrogate loss | No |
| **OSGM-H** | Hypergradient surrogate loss | No |
| **OSGM-R-Accelerated** | OSGM-R with Nesterov momentum | Yes |
| **GD** | Standard Gradient Descent | - |
| **AGD** | Accelerated Gradient Descent | - |
| **SAGD** | Strongly Convex AGD | - |
| **AdaGrad** | Adaptive Gradient Algorithm | - |

## Experiments

### Synthetic Data
- **Least Squares**: $f(x) = \frac{1}{2}\|Ax - b\|^2$
- **Matrix Generation**: $A = CDC^\top + \sigma I$ with varying condition numbers
- **Parameters**: $n=100$, $\sigma \in \{10^{-4}, 10^{-3}, 10^{-2}, 10^{-1}\}$

### Real Data
- **LIBSVM "a1a" dataset**: 1,605 training samples, 30,956 test samples, 123 features
- **SVM Problem**: $f(x) = \frac{1}{n}\sum_{i=1}^n f_i(x) + \frac{\lambda}{2}\|x\|^2$

## Results

Our methods demonstrate:
- **Superlinear convergence** on strongly convex quadratic problems
- **Faster convergence** compared to standard GD and AGD
- **Robust performance** across different condition numbers
- **Competitive results** on real-world SVM problems

![Convergence Plot](results/figures/convergence_comparison.png)

## Project Structure

```
OSGM-step-size-learning/
├── algorithms/           # Optimization algorithm implementations
│   ├── osgm_r.py        # OSGM with ratio surrogate
│   ├── osgm_g.py        # OSGM with gradient norm surrogate
│   ├── osgm_h.py        # OSGM with hypergradient surrogate
│   └── classical.py     # GD, AGD, SAGD implementations
├── problems/            # Problem definitions
│   ├── quadratic.py     # Quadratic optimization problems
│   └── svm.py          # SVM problem with squared hinge loss
├── experiments/         # Experiment scripts and notebooks
├── data/               # Dataset handling utilities
├── results/            # Generated figures and results
└── tests/              # Unit tests
```

## Requirements

- Python 3.8+
- NumPy
- SciPy
- Matplotlib
- scikit-learn
- Pandas

## Contributors

- **Alina Nurysheva** - OSGM-R, OSGM-R-Accelerated, SAGD, AGD, GD
- **Gregoire Ouerdane** - OSGM-H, real data experiments
- **Hussain Bukhari** - OSGM-G, AdaGrad, quadratic case implementations
- Easy navigation for researchers and developers
