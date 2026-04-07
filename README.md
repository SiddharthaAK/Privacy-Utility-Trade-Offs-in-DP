# Privacy-Utility Trade-Offs in Differential Privacy

An empirical study of how repeated differentially private (DP) data releases impact analytical utility and downstream decision-making in real-world settings.

---

## Overview

Differential Privacy (DP) is often studied in one-shot query settings, where a statistic is released once with a formal privacy guarantee. In practice, however, many systems release aggregates repeatedly over time. Each release consumes privacy budget, and the accumulated noise can significantly degrade the utility of analytical insights.

This project studies the **privacy–utility trade-off under repeated DP releases**, with a focus on understanding how privacy noise affects both numerical accuracy and practical decision-making.

The main goal is to connect **theoretical privacy guarantees** with **real analytical usefulness** in repeated-release environments.

---

## Key Contributions

- Empirical comparison of **repeated DP release strategies**
- Analysis of **privacy–utility trade-offs** under temporal reporting
- Evaluation of **utility beyond traditional error metrics**
- Study of **decision integrity**, including trends, alerts, and ranking stability
- Multi-domain experimentation across:
  - E-commerce
  - Retail analytics
  - Cybersecurity
- Modular notebook-based workflow for experimentation and evaluation

---

## Repository Structure

```
Privacy-Utility-Trade-Offs-in-DP/
├── CICIDS2017/
│   ├── _cleaned/
│   ├── FINDINGS_CYBERSEC.md
│   ├── cleaning_cicids.ipynb
│   ├── cyber_cumulative.ipynb
│   ├── cyber_disjoint.ipynb
│   ├── cyber_sliding.ipynb
│   ├── eval_cyber.ipynb
│   ├── quantitative_comp_cyber.ipynb
│   └── sensitivity_calibration_cyber.ipynb
│
├── PLECD/
│   ├── cleaning.ipynb
│   ├── processing.ipynb
│   ├── ecom_cumulative.ipynb
│   ├── ecom_disjoint.ipynb
│   ├── ecom_sliding.ipynb
│   └── eval.ipynb
│
├── openretail_cleaned/
│   ├── openretail_cumulative.ipynb
│   ├── openretail_disjoint.ipynb
│   ├── openretail_sliding.ipynb
│   └── openretail_eval.ipynb
│
├── README.md
├── LICENSE
└── .gitignore
```

---

## Core Concepts

### 1. Repeated Differentially Private Releases

Traditional DP analysis often assumes a single release. In realistic analytics systems, however, data is published repeatedly over time. Repeated releases accumulate privacy loss and can significantly degrade utility.

This project focuses on understanding how repeated releases behave in practice, especially when the released data is used for operational monitoring or decision-making.

### 2. Temporal Slicing Strategies

The repository studies multiple ways of structuring repeated releases over time:

- **Cumulative releases**: Each release aggregates information from the start of the observation period up to the current time.
- **Disjoint releases**: Each release covers a non-overlapping interval, making the reports independent across time windows.
- **Sliding-window releases**: Each release covers a rolling window, so adjacent releases overlap in the data they summarize.

These strategies differ in both privacy cost and utility behavior, making them important to compare empirically.

### 3. Utility Beyond Pointwise Error

Most DP evaluations stop at numerical error metrics such as MAE or RMSE. This project extends the evaluation to include practical decision-oriented aspects, such as:

- Trend preservation
- Alert stability
- Ranking consistency
- Usefulness for downstream monitoring

This makes the analysis more realistic for real-world analytics pipelines.

---

## Workflow

The repository follows a notebook-based research workflow.

### Step 1: Data Cleaning

Raw datasets are cleaned and standardized into analysis-ready forms.

**Examples:**
- `PLECD/cleaning.ipynb`
- `CICIDS2017/cleaning_cicids.ipynb`

**Typical tasks in this stage:**
- Removing invalid or inconsistent records
- Formatting timestamps
- Standardizing schema
- Preparing clean inputs for repeated-release experiments

### Step 2: Data Processing

After cleaning, the data is processed into a structure suitable for repeated DP releases.

**Examples:**
- `PLECD/processing.ipynb`

**Typical processing tasks:**
- Temporal aggregation
- Constructing slices or windows
- Preparing per-period statistics
- Organizing inputs for different release strategies

### Step 3: DP Experimentation

The project evaluates repeated releases under different temporal strategies:
- Cumulative
- Disjoint
- Sliding

**Example notebooks:**
- `PLECD/ecom_cumulative.ipynb`
- `PLECD/ecom_disjoint.ipynb`
- `PLECD/ecom_sliding.ipynb`
- `openretail_cleaned/openretail_cumulative.ipynb`
- `openretail_cleaned/openretail_disjoint.ipynb`
- `openretail_cleaned/openretail_sliding.ipynb`
- `CICIDS2017/cyber_cumulative.ipynb`
- `CICIDS2017/cyber_disjoint.ipynb`
- `CICIDS2017/cyber_sliding.ipynb`

At this stage, different private release settings are generated and compared.

### Step 4: Evaluation

The final stage evaluates how DP noise affects utility and analytical reliability.

**Evaluation notebooks:**
- `PLECD/eval.ipynb`
- `openretail_cleaned/openretail_eval.ipynb`
- `CICIDS2017/eval_cyber.ipynb`

**This stage studies:**
- Numerical accuracy
- Trend stability
- Comparative performance across strategies
- Effect of privacy noise on practical interpretation

---

## Datasets / Experiment Tracks

### 1. PLECD

This folder contains the main e-commerce experiment pipeline, including:
- Cleaning
- Processing
- Cumulative experiments
- Disjoint experiments
- Sliding-window experiments
- Evaluation

It represents an end-to-end experimental track for repeated DP analysis in an e-commerce setting.

### 2. OpenRetail

This folder contains repeated-release experiments for a retail analytics setting.

**Included notebooks focus on:**
- Cumulative releases
- Disjoint releases
- Sliding releases
- Evaluation

This track allows comparison of repeated DP behavior in another commerce-oriented dataset.

### 3. CICIDS2017

This folder contains the cybersecurity experiment track based on the CICIDS2017 dataset.

**It includes:**
- Data cleaning
- Repeated-release experiments
- Evaluation
- Sensitivity calibration
- Quantitative comparison
- Findings documentation

**Additional files:**
- `quantitative_comp_cyber.ipynb`
- `sensitivity_calibration_cyber.ipynb`
- `FINDINGS_CYBERSEC.md`

This track extends the repeated-release analysis to a cybersecurity domain, where privacy-preserving monitoring can be especially relevant.

---

## How to Run

This repository is notebook-driven, so experiments are typically run inside Jupyter Notebook or JupyterLab.

### 1. Clone the Repository

```bash
git clone https://github.com/SiddharthaAK/Privacy-Utility-Trade-Offs-in-DP.git
cd Privacy-Utility-Trade-Offs-in-DP
```

### 2. Install Dependencies

A base Python data science environment is required. You can start with:

```bash
pip install notebook jupyterlab pandas numpy matplotlib scipy scikit-learn
```

Depending on the notebooks, additional packages may be needed. Check the imports in the relevant notebooks if an error appears.

### 3. Launch Jupyter

```bash
jupyter notebook
```

or

```bash
jupyter lab
```

### 4. Run the Notebooks in Order

A typical workflow is: cleaning → processing → experiment notebook → evaluation

**For example, in PLECD:**
1. `PLECD/cleaning.ipynb`
2. `PLECD/processing.ipynb`
3. `PLECD/ecom_cumulative.ipynb`
4. `PLECD/eval.ipynb`

**For CICIDS2017:**
1. `CICIDS2017/cleaning_cicids.ipynb`
2. `CICIDS2017/cyber_cumulative.ipynb`
3. `CICIDS2017/eval_cyber.ipynb`

---

## Technologies Used

- **Python**
- **Jupyter Notebooks**
- **pandas**
- **numpy**
- **matplotlib**
- **scipy**
- **scikit-learn**

The codebase is designed primarily for experimental research rather than as a packaged software library.

---

## License

See the LICENSE file for details.
