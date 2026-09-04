# Adaptive Multimodal Biometric Fusion
Code accompanying the paper:
### *“A Conceptual Framework for Adaptive Multimodal Biometric Fusion”*
#### Overview
This repository contains the simulation code used for the case study presented in the paper. The case study illustrates the proposed adaptive multimodal biometric fusion framework under varying modality availability and reliability conditions.

The implementation is intended to operationalize and illustrate the framework's design dimensions rather than to provide a benchmark or a complete biometric recognition system.
#### Case Study
The simulation compares five fusion conditions:
| Condition | Modality Set | Reliability Weighting | Reliability-Based Selection
| --- | --- | --- | --- |
| I | Fixed | No | No | 
| II | Fixed | Yes | No |
| III | Variable | No | No |
| III-W | Variable | Yes | No |
| IV | Variable | Yes | Yes |

Condition III-W is included to isolate the contribution of reliability-based weighting from the effect of modality selection.

The simulation also evaluates the sensitivity of the adaptive regime to the reliability-selection threshold (tau) and the reliability-estimation noise parameter (sigma).

#### Repository Contents
* case_study.py — Python implementation of the case-study simulation.
* case_study.ipynb — Jupyter/Google Colab notebook containing the simulation and its outputs.
* requirements.txt — Python dependencies required to run the simulation.
* .gitignore — Files and directories excluded from version control.

#### Requirements
* Python 3.x
* NumPy

#### Instalation
install the required dependency with:
```
pip install -r requirements.txt
```
#### Running the Simulation
Run the Python script with:
```
python case_study.py
```
The script reports the results for the five fusion conditions and performs the threshold (tau) and noise (sigma) sensitivity analyses. The notebook can alternatively be opened and executed in Google Colab or another Jupyter-compatible environment.

#### Reproducibility
The simulation uses fixed random seeds for the defined experimental regimes.

For the sensitivity analyses, the same simulated trials are reused across different values of tau and sigma. This ensures that changes in the reported results are attributable to the parameter being varied rather than to newly sampled trials.

The implementation also includes an explicit equal-weight tie-break when available modalities have zero estimated reliability.

#### Scope and Interpretation
The numerical values produced by this code are simulation results for the paper's conceptual case study. They should not be interpreted as empirical performance measurements on a biometric benchmark dataset.

The purpose of the case study is to demonstrate the behavior of the proposed framework across different combinations of modality availability and reliability awareness.

### Citation
This repository accompanies a manuscript currently under peer review.
Citation details will be added once available.

