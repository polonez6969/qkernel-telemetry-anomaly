# Quantum Kernel Telemetry Anomaly Detection

*A reproducible framework for studying quantum-kernel geometry and anomaly separability in manifold-structured telemetry.*

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## Overview

This repository implements and evaluates quantum kernel methods for anomaly detection in telemetry regimes where nominal system behavior lies on a low-dimensional, curved manifold embedded in a high-dimensional observation space. Such regimes are characteristic of spacecraft, aerospace, and other tightly coupled dynamical systems, where anomalies correspond to structured departures rather than uncorrelated noise.

The core objective is not to assert generic quantum advantage, but to provide a **controlled, falsifiable testbed** for examining when entanglement-based feature maps yield measurable gains over classical kernels under realistic constraints: limited labeled data, non-Euclidean geometry, and structured anomaly types.

All experiments are reproducible, all baselines are explicit, and all results are accompanied by saved artifacts and diagnostic analyses.

---

## Scientific Contribution

This work contributes:

1. A geometry-aware anomaly detection benchmark targeting manifold-structured telemetry rather than iid feature clouds.
2. A comparative evaluation of entanglement-based quantum kernels against strong classical baselines under matched conditions.
3. Kernel diagnostics (eigenspectra, effective dimension, conditioning) that link performance to representational properties rather than black-box metrics.
4. A modular research platform designed to support falsification, extension, and hardware-oriented follow-on studies.

The emphasis throughout is methodological discipline and interpretability rather than performance maximization alone.

---

## Problem Setting

Many operational telemetry streams exhibit strong coupling, phase relationships, and low intrinsic dimensionality despite high-dimensional observation vectors. Classical kernel methods typically rely on isotropic Euclidean similarity measures, which can be poorly aligned with such curved manifolds.

Anomalies in these systems often manifest as coherent drifts, impulsive deviations, partial sensor dropouts, or structured spoofing signals rather than independent noise. This work examines whether quantum kernels—constructed via entangling feature maps and fidelity-based similarity—offer a more faithful geometry for separating such events.

---

## Method Summary

**Data Generation**  
Synthetic telemetry windows are generated from a low-dimensional, phase-coupled dynamical model with controlled injection of structured anomalies.

**Feature Representation**  
Per-channel summary statistics are encoded into quantum feature maps producing pure quantum states.

**Kernel Construction**  
Similarity is defined via state fidelity, yielding a positive semi-definite kernel suitable for kernel SVMs.

**Feature Maps**  
Implemented encodings include data reuploading with ZZ entanglement, Pauli rotation circuits with entangling topology, and IQP-style circuits with known classical hardness properties.

**Baselines**  
Classical comparators include RBF-SVM, One-Class SVM, and Isolation Forest, evaluated under identical train/test splits.

---

## Reproducibility and Artifacts

Each experiment produces saved configurations, kernel matrices, evaluation metrics, and diagnostic visualizations (ROC curves, kernel PCA, eigenspectra). Random seeds are fixed by default, and all figures are regenerated from stored artifacts rather than transient state.

---

## Selected Results

On representative synthetic telemetry workloads, quantum kernels typically achieve modest but consistent improvements in ROC-AUC over classical RBF kernels, with the largest gaps appearing in structured anomaly regimes and low-data settings.

Performance differences are interpreted in conjunction with kernel geometry diagnostics rather than treated as standalone claims.

---

## Scope and Limitations

This framework is designed for small-to-medium sample regimes where kernel methods are appropriate. Quadratic kernel scaling limits applicability at large dataset sizes, and current results are based on synthetic telemetry rather than operational data. These constraints are explicit design choices intended to isolate representational effects before addressing deployment-scale concerns.

---

## Repository Contents

```
qkernel-telemetry-anomaly/
├── src/                  Core implementation
├── tests/                Unit and integration tests
├── notebooks/            Walkthrough and analysis notebooks
├── pyproject.toml        Packaging and dependencies
└── requirements.txt
```

---

## Getting Started

```bash
git clone https://github.com/christopher-altman/qkernel-telemetry-anomaly
cd qkernel-telemetry-anomaly
pip install -e .
python -m src.main
```

See `--help` for configuration options.

---

## Research Roadmap

A structured research agenda, including hypotheses and experimental designs, is provided in `HYPOTHESES.md`.

---

## Citation

```bibtex
@software{altman2025qkernel,
  title={Quantum Kernel Telemetry Anomaly Detection},
  author={Altman, Christopher},
  year={2025},
  url={https://github.com/christopher-altman/qkernel-telemetry-anomaly}
}
```

---

## License

MIT License. See `LICENSE` for details.
