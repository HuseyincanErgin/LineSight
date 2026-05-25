[README (4).md](https://github.com/user-attachments/files/28236090/README.4.md)
<p align="center">
  <img src="https://raw.githubusercontent.com/HuseyincanErgin/LineSight/main/linesight_banner.svg" alt="LineSight" width="100%">
</p>

<p align="center">
  <b>Production Quality Intelligence & Maintenance Decision Support</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-0f172a?style=for-the-badge&logo=python&logoColor=38bdf8">
  <img src="https://img.shields.io/badge/CustomTkinter-111827?style=for-the-badge&logo=windowsterminal&logoColor=a78bfa">
  <img src="https://img.shields.io/badge/Pandas-1e1b4b?style=for-the-badge&logo=pandas&logoColor=ffffff">
  <img src="https://img.shields.io/badge/NumPy-164e63?style=for-the-badge&logo=numpy&logoColor=ffffff">
  <img src="https://img.shields.io/badge/Matplotlib-0f766e?style=for-the-badge&logo=plotly&logoColor=ffffff">
  <img src="https://img.shields.io/badge/Gemini%20AI-6d28d9?style=for-the-badge&logo=google&logoColor=ffffff">
</p>

---

## About

**LineSight** is a Python desktop application for production quality analysis and maintenance decision support.

It reads inspection data, calculates quality and operational KPIs, scores risky machines, evaluates process capability with **Cp/Cpk**, compares operator/shift performance, and turns it all into AI-supported maintenance recommendations.

> Not just *seeing* the production line — knowing **which machine, shift, or process needs attention first, and why.**

```mermaid
flowchart LR
    A[Inspection Data] --> B[KPI Engine]
    B --> C[Machine Risk]
    B --> D[Operator / Shift]
    B --> E[Cp / Cpk]
    C --> F[Criticality Score]
    D --> F
    E --> F
    F --> G[AI / Rule-Based Insight] --> H[Maintenance Action]
```

---

## Features

| Module | What it does |
|:---|:---|
| **Dashboard** | Pass rate, failure rate, cost, downtime overview |
| **Machine Analysis** | Failure rate, cost, downtime, Cp/Cpk → criticality score |
| **Operator / Shift** | Performance comparison, worst shift/operator detection |
| **Process Capability** | Cp, Cpk and a capability verdict |
| **AI Analysis** | Decision-focused maintenance recommendations |
| **Report Export** | Self-contained HTML executive report |

---

## Machine Criticality Score

LineSight ranks machines by more than just failure count:

```
Criticality = Failure Rate + Failure Cost + Downtime + Cp/Cpk Penalty
```

The top priority isn't always the machine that fails most — sometimes it's the one that costs the most, stops the longest, or has the weakest process capability.

---

## Process Capability (Cp / Cpk)

```
Cp  = (USL - LSL) / (6σ)
Cpk = min[ (USL - μ) / (3σ), (μ - LSL) / (3σ) ]
```

| Cpk | Verdict |
|:---:|:---|
| ≥ 1.33 | Capable — stable and within spec |
| 1.00 – 1.33 | Marginal — acceptable but risky |
| < 1.00 | Not capable — needs re-centering |

---

## Dataset

Minimum required: `Machine_ID`, `Measurement`. Full analysis uses:

```
Machine_ID · Operator_ID · Shift · Product_Type · Measurement
LSL · USL · Status · Failure_Type · Failure_Cost · Downtime_Minutes
```

Missing optional columns are filled with safe defaults where possible.

---

## Installation

```bash
git clone https://github.com/HuseyincanErgin/LineSight.git
cd LineSight
pip install customtkinter pandas numpy matplotlib requests openpyxl
python LineSight_app.py
```

**Demo login:** `admin` / `admin`

**Gemini (optional):** set a key before running, otherwise the built-in rule-based engine is used.

```bash
set GEMINI_API_KEY=your_api_key_here
```

---

## Tech Stack

Python · CustomTkinter · pandas · NumPy · Matplotlib · Requests · OpenPyXL · Google Gemini API (optional)

---

## Developer

**Hüseyincan Ergin** — Industrial Engineering Student @ Marmara University

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/hüseyincan-ergin)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/HuseyincanErgin)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:huseyincanergin@gmail.com)
