# Nuclear Instrumentation Health Monitoring System
### An On-Line Monitoring Approach to Calibration Drift Detection

---

## Overview

This project implements a sensor health monitoring system modeled after 
On-Line Monitoring (OLM) methodologies used in the nuclear power industry 
for instrumentation calibration drift detection. The analytical approach 
is consistent with NRC guidance and 10CFR50 Appendix B quality assurance 
principles.

The system demonstrates two core analytical techniques:

- **SPRT (Sequential Probability Ratio Test)** — sequential hypothesis 
  testing for early drift detection in individual sensor signals
- **PCA-Based Multivariate Sensor Validation** — principal component 
  analysis for cross-sensor consistency checking and fault isolation

---

## Motivation

Nuclear power plants rely on thousands of sensors to monitor critical 
parameters including temperature, pressure, flow, and neutron flux. 
Sensor calibration drift — the gradual deviation of a sensor's output 
from its true value — poses safety and compliance risks if undetected 
between scheduled calibration intervals.

Traditional calibration approaches require plant shutdowns on fixed 
schedules. On-Line Monitoring allows continuous, data-driven assessment 
of sensor health during normal plant operation, enabling earlier drift 
detection and more efficient maintenance decisions.

---

## Project Structure
```
nuclear-health-monitor/
│
├── data/               # Dataset (see data/README.md for download instructions)
├── notebooks/          # Jupyter notebooks for exploration and analysis
├── src/                # Core Python modules
│   ├── sprt.py         # Sequential Probability Ratio Test implementation
│   ├── pca_validator.py # Multivariate sensor validation
│   └── report.py       # Automated report generation
├── reports/            # Generated analysis outputs
└── docs/               # Methodology and procedure documents
```

---

## Methodology

### SPRT (Sequential Probability Ratio Test)
Based on Wald (1945), adapted for nuclear sensor monitoring per EPRI 
and NRC On-Line Monitoring guidance. Tests sequentially whether incoming 
sensor residuals are consistent with a healthy (zero-mean) or drifting 
(offset-mean) process, accumulating log likelihood ratios until sufficient 
evidence exists to declare a decision.

### PCA-Based Sensor Validation
Models the expected correlation structure across a group of physically 
related sensors. Sensors that deviate from the learned correlation model 
generate large residuals, enabling fault isolation — identifying *which* 
sensor in a correlated group has drifted.

---

## Setup
```bash
git clone https://github.com/YOUR_USERNAME/nuclear-health-monitor.git
cd nuclear-health-monitor
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

Then download the dataset per `data/README.md`.

---

## Status

🔧 In active development

| Module | Status |
|--------|--------|
| Data exploration | 🔧 In progress |
| SPRT implementation | ⏳ Planned |
| PCA validator | ⏳ Planned |
| Report generation | ⏳ Planned |
| Procedure documentation | ⏳ Planned |

---

## References

- Wald, A. (1945). Sequential Tests of Statistical Hypotheses.
- EPRI TR-104965: On-Line Monitoring of Instrument Channel Performance
- NRC Regulatory Guide 1.239: Guidance for On-Line Monitoring
- UCI CCPP Dataset: https://archive.ics.uci.edu/ml/datasets/Combined+Cycle+Power+Plant