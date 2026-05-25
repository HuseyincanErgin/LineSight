<div align="center">

# LineSight

### Production Quality Intelligence & Maintenance Decision Support

**Turn production inspection data into machine risk scores, Cp/Cpk insights, shift performance signals, and AI-supported maintenance actions.**

<br/>

![Python](https://img.shields.io/badge/Python-0B1220?style=for-the-badge&logo=python&logoColor=38BDF8)
![Desktop App](https://img.shields.io/badge/Desktop%20Application-172554?style=for-the-badge&logo=windows&logoColor=white)
![Quality Analytics](https://img.shields.io/badge/Quality%20Analytics-0F766E?style=for-the-badge)
![Cp Cpk](https://img.shields.io/badge/Cp%20%2F%20Cpk-6D28D9?style=for-the-badge)
![Gemini AI](https://img.shields.io/badge/Gemini%20AI-9333EA?style=for-the-badge&logo=google&logoColor=white)

<br/>

```text
┌──────────────────────────────────────────────────────────────┐
│                        LineSight                             │
│      Production Quality • Machine Risk • AI Insights          │
├──────────────────────────────────────────────────────────────┤
│  Input     →  CSV / Excel production inspection data          │
│  Analyze   →  Machines, operators, shifts, Cp/Cpk, failures   │
│  Decide    →  Maintenance priority and quality actions        │
│  Export    →  Executive-style HTML report                     │
└──────────────────────────────────────────────────────────────┘
```

</div>

---

## Overview

**LineSight** is a Python-based desktop decision-support application designed for production quality and maintenance analysis.

The app reads production inspection data, calculates operational and quality-related KPIs, identifies risky machines, evaluates process capability with **Cp/Cpk**, compares operator and shift performance, and generates AI-supported maintenance recommendations.

Instead of only showing raw data, LineSight focuses on one main question:

> **Which machine, shift, or process area needs attention first — and why?**

---

## Core Idea

Manufacturing data often contains many signals: measurements, pass/fail results, machine IDs, operator IDs, shifts, failure costs, downtime values, and specification limits.

LineSight brings these signals together and converts them into a practical decision flow:

```text
Production Data
      ↓
Data Cleaning & Normalization
      ↓
KPI Calculation
      ↓
Machine / Operator / Shift Analysis
      ↓
Cp & Cpk Capability Evaluation
      ↓
Criticality Scoring
      ↓
AI-Supported Maintenance Recommendations
      ↓
HTML Report Export
```

---

## Key Features

| Module | What it does |
|:---|:---|
| **Dashboard** | Shows overall production KPIs such as total inspections, pass rate, failure rate, cost, and downtime |
| **Machine Analysis** | Calculates machine-level failure rate, failure cost, downtime, Cp/Cpk, and criticality score |
| **Operator / Shift Analysis** | Compares operators and shifts based on failure rate, pass rate, cost, and average measurement |
| **Process Capability** | Evaluates process performance using Cp and Cpk based on LSL and USL values |
| **AI Analysis** | Uses Gemini AI or a built-in rule-based engine to generate maintenance and quality recommendations |
| **Raw Data View** | Displays the uploaded or demo-generated production dataset |
| **Report Export** | Exports a clean HTML report containing KPIs, AI insights, and analysis tables |

---

## What LineSight Calculates

LineSight calculates several production quality and maintenance metrics automatically:

```text
Total Inspections
Pass Count
Fail Count
Pass Rate
Failure Rate
Total Failure Cost
Total Downtime
Average Measurement
Cp
Cpk
Cost per 1000 Units
Machine Criticality Score
```

The machine criticality score is built from a weighted combination of:

- Failure rate
- Failure cost
- Downtime
- Process capability penalty based on Cpk

This makes the app useful not only for quality analysis, but also for maintenance prioritization.

---

## Process Capability Logic

LineSight uses standard Cp and Cpk formulas to evaluate process capability.

```text
Cp = (USL - LSL) / (6σ)
```

```text
Cpk = min((USL - μ) / (3σ), (μ - LSL) / (3σ))
```

Interpretation:

| Cpk Value | Meaning |
|:---:|:---|
| **Cpk ≥ 1.33** | Capable process |
| **1.00 ≤ Cpk < 1.33** | Marginal process |
| **Cpk < 1.00** | Not capable process |

This helps reveal whether a machine is simply producing failures, or whether the process itself is unstable, off-center, or too variable.

---

## AI Insight System

LineSight does not depend entirely on AI.

The app first calculates reliable statistics internally. Then, if a Gemini API key is provided, AI is used as a controlled explanation layer.

```text
Calculated Statistics
        +
Machine / Shift / Operator Summaries
        +
Cp / Cpk Results
        ↓
Gemini AI or Rule-Based Engine
        ↓
Actionable Quality & Maintenance Recommendations
```

If no Gemini API key is entered, the application still works using its built-in rule-based analysis system.

This prevents the app from becoming useless when AI access is unavailable.

---

## Tech Stack

| Technology | Purpose |
|:---|:---|
| **Python** | Main programming language |
| **CustomTkinter** | Desktop user interface |
| **pandas** | Data cleaning and analysis |
| **NumPy** | Numerical calculations |
| **Matplotlib** | Charts and visualizations |
| **Requests** | Gemini API communication |
| **OpenPyXL** | Excel file support |
| **Google Gemini API** | Optional AI-supported analysis |

---

## Expected Data Format

LineSight requires at least these columns:

```text
Machine_ID
Measurement
```

For a more complete analysis, the recommended dataset structure is:

```text
Machine_ID
Operator_ID
Shift
Product_Type
Measurement
LSL
USL
Status
Failure_Type
Failure_Cost
Downtime_Minutes
```

| Column | Description |
|:---|:---|
| `Machine_ID` | Machine identifier |
| `Operator_ID` | Operator identifier |
| `Shift` | Production shift |
| `Product_Type` | Product category or type |
| `Measurement` | Quality measurement value |
| `LSL` | Lower Specification Limit |
| `USL` | Upper Specification Limit |
| `Status` | Pass / Fail result |
| `Failure_Type` | Type of failure or defect |
| `Failure_Cost` | Cost caused by failed units |
| `Downtime_Minutes` | Downtime caused by failures |

If some optional columns are missing, LineSight fills safe default values where possible.

---

## How to Run

```bash
# Clone the repository
git clone https://github.com/HuseyincanErgin/LineSight.git

# Go to the project folder
cd LineSight

# Install dependencies
pip install customtkinter pandas numpy matplotlib requests openpyxl

# Run the application
python LineSight_app.py
```

---

## Demo Login

The application includes a simple demo login screen.

```text
Username: admin
Password: admin
```

---

## Gemini API Key

Gemini AI usage is optional.

For safer usage, do not hardcode your real API key inside the Python file before uploading to GitHub.

Recommended method:

```bash
set GEMINI_API_KEY=your_api_key_here
```

Then run:

```bash
python LineSight_app.py
```

If no API key is provided, LineSight continues with its built-in rule-based recommendation engine.

---

## Project Structure

```text
LineSight/
│
├── LineSight_app.py
│   └── Main desktop application
│
├── README.md
│   └── Project documentation
│
└── requirements.txt
    └── Optional dependency list
```

Suggested `requirements.txt`:

```text
customtkinter
pandas
numpy
matplotlib
requests
openpyxl
```

---

## Application Flow

```text
1. Login to the application
2. Use demo data or upload CSV / Excel data
3. Review dashboard KPIs
4. Analyze machine-level risk
5. Compare operators and shifts
6. Evaluate Cp / Cpk process capability
7. Generate AI-supported insights
8. Export the final HTML report
```

---

## Use Case

LineSight can be useful for:

- Production quality monitoring
- Machine failure analysis
- Maintenance prioritization
- Operator and shift comparison
- Cp/Cpk-based process capability evaluation
- Industrial engineering analytics projects
- Quality dashboard demonstrations
- Decision-support system prototypes

---

## Project Tags

<div align="center">

![Industrial Engineering](https://img.shields.io/badge/Industrial%20Engineering-0F766E?style=for-the-badge)
![Production Analytics](https://img.shields.io/badge/Production%20Analytics-0369A1?style=for-the-badge)
![Machine Risk](https://img.shields.io/badge/Machine%20Risk-7C3AED?style=for-the-badge)
![Maintenance Decision Support](https://img.shields.io/badge/Maintenance%20Decision%20Support-4338CA?style=for-the-badge)
![Quality Control](https://img.shields.io/badge/Quality%20Control-0891B2?style=for-the-badge)
![Python App](https://img.shields.io/badge/Python%20App-111827?style=for-the-badge)

</div>

---

## Developer

<div align="center">

**Hüseyincan Ergin**  
Industrial Engineering Student @ Marmara University

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Hüseyincan%20Ergin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/hüseyincan-ergin)
[![GitHub](https://img.shields.io/badge/GitHub-HuseyincanErgin-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/HuseyincanErgin)
[![Email](https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:huseyincanergin@gmail.com)

</div>
