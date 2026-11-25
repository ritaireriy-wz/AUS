# AUS
Learn and implement Autonomous Systems theory with me: vectorized NumPy weather data analysis, LTI systems, low-pass filters, and signal sampling exercises from the MSc program at ELTE.

<div align="center">

# AUS with Ireri
### Computer Science for Autonomous Systems — NumPy, Weather & Signal Processing

*Vectorized Python implementations, mathematical models, and theoretical notes from the MSc in Computer Science for Autonomous Systems curriculum at Eötvös Loránd University (ELTE).*

[![University](https://img.shields.io/badge/ELTE-Faculty%20of%20Informatics-003366?style=for-the-badge)](https://www.inf.elte.hu/en/)
[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![NumPy](https://img.shields.io/badge/NumPy-Vectorized-013243?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)

</div>

---

## Overview

**AUS with Ireri** bridges core mathematical theory in autonomous systems with high-performance numerical computing in Python. Rather than relying on slow iterative loops, every module emphasizes **vectorized array operations**, **memory-safe slicing**, and **signal-level mathematical modeling**—foundational skills for real-time sensor processing and autonomous control pipelines.

The repository is organized around two core analytical tracks:

1. **Climatological & Environmental Data Analysis (Almaty Dataset)** — Applying vectorized array transformations, seasonal indexing, and ecological indices to multi-variable climate records.
2. **Signals, Systems & Sampling Foundations** — Modeling continuous and discrete Linear Time-Invariant (LTI) systems, analog/digital low-pass filters, and frequency-domain sampling constraints.

---

## 🧭 Core Modules & Theoretical Scope

| Module | Domain Focus | Key Mathematical & Computational Concepts |
| :--- | :--- | :--- |
| **01 · Climate Analytics** | **Almaty 12-Month Weather Dataset** | • Unit conversions & element-wise array arithmetic ($\text{°C} \rightarrow \text{°F}$)<br>• **De Martonne Aridity Index:** $I = \frac{P}{T + 10}$ for annual & seasonal climate classification<br>• Seasonal slicing (`[2:5]` Spring), fancy indexing (`[[11, 0, 1]]` Winter), and boolean masking |
| **02 · LTI Systems & Filtering** | **Signals & Control Foundations** | • Continuous-time vs. discrete-time **Linear Time-Invariant (LTI)** system response<br>• Transfer functions $H(s)$ and frequency response analysis<br>• First-order **RC circuit** & **Butterworth** low-pass filter characteristics |
| **03 · Sampling & Aliasing** | **Digital Signal Acquisition** | • Uniform time-domain sampling ($f_s = 1/T_s$)<br>• **Nyquist–Shannon Sampling Theorem** ($f_s > 2f_{\max}$)<br>• Spectral folding and **aliasing** artifacts in undersampled signals |

---

## Key NumPy Engineering Patterns

This repository enforces strict numerical computing best practices for both production performance and automated grading compatibility:

* **Zero-Loop Vectorization:** Replacing explicit Python `for` loops with broadcasted NumPy ufuncs and bitwise boolean masks (`&`, `|`, `~`) for fast array evaluation.
* **1-Based Calendar Alignment:** Reconciling 0-indexed Python arrays with 1-indexed calendar months when extracting extrema via `np.argmax` / `np.argmin`:
  $$\text{Calendar Month} = \text{Array Index} + 1$$
* **Non-Destructive Extrema Extraction:** Combining `.copy()` with out-of-bounds suppression (`-np.inf` / `np.inf`) to isolate seasonal peaks and troughs without mutating source arrays.
* **Strict Primitive Type Casting:** Explicitly casting NumPy scalar types (`np.float32`, `np.int64`, `np.bool_`) to native Python primitives (`float`, `int`, `bool`) to guarantee clean JSON serialization and autograder type assertions.

---

## 📂 Repository Structure

```text
AUS_with_Ireri/
├── notebooks/
│   ├── 01_almaty_weather_numpy.ipynb       # Vectorized climate analysis & De Martonne index
│   └── 02_signals_lti_sampling.ipynb       # LTI transfer functions, RC/Butterworth filters & Nyquist
├── src/
│   ├── weather_metrics.py                  # Modular functions for seasonal & aridity calculations
│   └── signal_utils.py                     # Sampling, filtering, and frequency analysis helpers
├── tests/
│   └── test_implementations.py             # Unit tests & primitive type verification
├── requirements.txt
└── README.md
