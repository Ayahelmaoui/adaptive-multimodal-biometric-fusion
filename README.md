# Adaptive Multimodal Biometric Fusion

Code accompanying the paper:

### *"A Conceptual Framework for Adaptive Multimodal Biometric Fusion: Reliability-Awareness and Modality-Set Flexibility as Complementary Axes"*

---

## Overview

This repository contains the Python implementations and notebooks accompanying the conceptual framework for adaptive multimodal biometric fusion.

The repository includes two complementary analyses:

1. **Case-study simulation:** examines the behavior of five fusion conditions under different modality-availability and reliability conditions.
2. **Literature positioning analysis:** positions selected studies according to two dimensions of the proposed framework: Modality-Set Flexibility (MSF) and Reliability-Awareness (RA).

The implementations are intended to operationalize and illustrate the framework's design dimensions. They do not constitute a complete biometric recognition system or an empirical benchmark evaluation.

---

## 1. Case-Study Simulation

The case-study simulation evaluates five fusion conditions, labelled C1–C5.

| Condition | Modality availability | Weighting strategy | Reliability-based selection |
|---|---|---|---|
| C1 | Both modalities required | Equal weighting | No |
| C2 | Both modalities required | Reliability weighting | No |
| C3 | Available modalities can be used independently | Equal weighting | No |
| C4 | Available modalities can be used independently | Reliability weighting | No |
| C5 | Available modalities can be used independently | Reliability weighting | Yes |

C1 and C2 provide fixed-set comparison conditions. C3 and C4 examine fusion when modality availability can vary. C5 additionally applies a reliability-selection threshold to determine whether an available modality contributes to the fusion result.

### Scenarios

Four experimental scenarios are considered:

| Scenario | Face availability | Periocular availability | Quality distribution |
|---|---:|---:|---|
| S1 | 0.95 | 0.90 | High-quality regime |
| S2 | 0.95 | 0.90 | Low-quality regime |
| S3 | 0.60 | 0.90 | High-quality regime |
| S4 | 0.60 | 0.90 | Low-quality regime |

S4 is the primary scenario. The quality distributions are represented using Beta distributions. The simulation uses fixed random seeds for reproducibility.

### Evaluation Metrics

The simulation reports the following outcomes separately:

- **Correctness:** expected correctness across all trials. Abstentions contribute zero.
- **Coverage:** proportion of trials in which a decision is produced.
- **Abstention rate:** proportion of trials in which no decision is produced.
- **Accuracy on answered trials:** correctness conditional on producing a decision.
- **95% confidence-interval half-width:** uncertainty estimate for mean correctness across all trials.

Separating these metrics makes it possible to distinguish decision quality from the system's willingness to produce a decision.

### Primary Comparison

The primary analysis compares C4 and C5 under S4 using the same simulated trials. The difference is calculated on a trial-by-trial basis, and its confidence interval is based on the paired differences.

### Sensitivity Analysis

The simulation examines the effect of two parameters under S4:

- **Selection threshold (tau):** evaluates how changing the reliability threshold affects correctness and decision coverage.
- **Estimator noise (sigma):** evaluates how uncertainty in the reliability estimates affects the fusion conditions.

The same simulated S4 trials are reused throughout each sweep. This controls variation from resampling when comparing parameter values.

### Robustness Check

An optional robustness experiment introduces correlated face and periocular quality values using a Gaussian copula. The transformation preserves the specified Beta marginal distributions while inducing correlation between the modalities.

The robustness experiment uses `rho = 0.6` and reports correctness, coverage, and accuracy on answered trials.

---

## 2. Literature Positioning Analysis

The literature-positioning analysis maps selected studies along two complementary dimensions.

### Modality-Set Flexibility (MSF)

MSF represents the extent to which a fusion approach can accommodate changes in the available modality set.

The score is calculated as:
MSF = 0.6S + 0.4G

Where:

- **S:** indicates whether the modality set is variable (1) or fixed (0).
- **G:** represents the breadth of supported modality configurations, ranging from 0 to 1.
- **G** is set to 0 whenever **S** is 0.

### Reliability-Awareness (RA)

RA represents the extent to which fusion accounts for sample quality, operating context, and modality reliability.

The score is calculated as:
RA = 0.4Q + 0.2C + 0.4R

Where:

- **Q:** represents the use of sample-quality information in fusion.
- **C:** represents the use of operating-context information.
- **R:** represents the use of modality reliability or confidence estimates.

Each component is scored using 0, 0.5, or 1 to distinguish absent, partial or implicit, and explicit evidence, respectively.

### Positioning Plot

The resulting MSF and RA scores are plotted on a two-dimensional map divided into four conceptual regions:

- **Region I:** Fixed-set, unconditioned approaches.
- **Region II:** Fixed-set, reliability-aware approaches.
- **Region III:** Variable-set, unconditioned approaches.
- **Region IV:** Adaptive, flexible fusion approaches.

The plot provides a structured comparison of the selected literature according to the proposed framework. The scores represent the operationalized classification criteria used in this analysis; they should not be interpreted as empirical performance measurements.

---

## Repository Contents

| File | Description |
|---|---|
| `case_study_v2.py` | Python implementation of the case-study simulation. |
| `case_study_v2.ipynb` | Jupyter/Google Colab notebook containing the case-study simulation and outputs. |
| `lit_Positioning.py` | Python implementation of the literature-positioning analysis. |
| `lit_Positioning.ipynb` | Jupyter/Google Colab notebook containing the literature-positioning analysis and plot. |
| `requirements.txt` | Python dependencies required to run the analyses. |
| `.gitignore` | Files and directories excluded from version control. |

---

## Requirements

- Python 3.x
- NumPy
- Pandas
- Matplotlib
- SciPy
- IPython

Install the dependencies using:

```bash
pip install -r requirements.txt
```
## Running the Analyses

### Case-study simulation

Run the Python script:

```bash
python case_study_v2.py
```

Alternatively, open case_study_v2.ipynb in Google Colab or another Jupyter-compatible environment and execute the cells.

### Literature positioning

Run the Python script:

```bash
python lit_Positioning.py
```

Alternatively, open lit_Positioning.ipynb in Google Colab or another Jupyter-compatible environment.

The notebooks display the generated tables and plots as part of their execution. A graphical plotting environment is required for interactive plot display when running the scripts locally.

## Reproducibility
The case-study simulation uses fixed random seeds for the defined experimental scenarios.

For the sensitivity analyses, the same simulated trials are reused while varying the parameter under investigation. This helps ensure that differences in the reported results are attributable to the parameter being varied rather than to newly generated random trials.

The simulation also includes an explicit equal-weight tie-break when available modalities have zero estimated reliability.

The literature-positioning analysis uses predefined classification scores and scoring rules. Its results can be reproduced by executing the corresponding script or notebook with the same input classifications.

## Scope and Interpretation
The case-study results are simulation-based illustrations of the proposed framework. They should not be interpreted as empirical performance measurements obtained from a biometric benchmark dataset.

The literature-positioning analysis is a conceptual comparison of selected studies based on the defined MSF and RA criteria. Its scores depend on the operational definitions and evidence classifications used in the analysis.

Together, these analyses illustrate the framework's two complementary aspects: its positioning relative to existing approaches and the behavior of different fusion conditions under controlled simulation settings.

## Citation
This repository accompanies a manuscript currently under review.

Full citation details will be added following publication.
