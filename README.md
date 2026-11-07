# Fraud Detection Analysis

## Project Overview

This project explores financial transaction patterns associated with fraudulent activity using Python and Power BI. The goal was to investigate transaction behavior, identify potential fraud indicators, and communicate analytical findings through an interactive dashboard.

The analysis uses the **PaySim synthetic financial transaction dataset**, which contains over 6.3 million simulated transactions. The project focuses on exploratory data analysis, data quality assessment, class imbalance, transaction characteristics, and account balance behavior.

## Tools and Technologies

- **Python:** Data exploration and analysis
- **pandas and NumPy:** Data manipulation and feature engineering
- **Matplotlib and Seaborn:** Data visualization
- **Jupyter Notebook / VS Code:** Interactive analysis
- **Power BI:** Dashboard development and reporting
- **uv:** Python environment and dependency management
- **Git and GitHub:** Version control

## Dataset

The PaySim dataset contains **6,362,620 transactions and 11 original variables**, including transaction types, amounts, account balances, and fraud indicators.

The original dataset includes five transaction types: PAYMENT, TRANSFER, CASH_OUT, CASH_IN, and DEBIT.

The target variable, `isFraud`, identifies transactions labeled as fraudulent within the simulation.

**Note:** PaySim is a synthetic dataset. Findings are intended to demonstrate analytical techniques and should not be interpreted as representative of real-world banking fraud.

The raw dataset is not included in this repository because of its size. It must be obtained separately before reproducing the full analysis.

## Analysis Workflow

### 1. Data Exploration and Quality Assessment

- Loaded and inspected the original dataset using pandas.
- Examined data types, dataset dimensions, and descriptive statistics.
- Evaluated missing values and duplicate records.
- Investigated unique values and transaction distributions.

The initial assessment identified no missing values or exact duplicate records.

### 2. Fraud Distribution and Class Imbalance

Analyzed the distribution of fraudulent and legitimate transactions.

| Classification | Transactions | Percentage |
|---|---:|---:|
| Legitimate | 6,354,407 | 99.87% |
| Fraudulent | 8,213 | 0.13% |

The dataset is highly imbalanced, highlighting why classification accuracy alone would be insufficient for evaluating a fraud detection model.

### 3. Fraud Patterns by Transaction Type

Compared transaction volume, fraud counts, and fraud rates across transaction types.

| Transaction Type | Fraud Cases | Fraud Rate |
|---|---:|---:|
| TRANSFER | 4,097 | 0.77% |
| CASH_OUT | 4,116 | 0.18% |
| CASH_IN | 0 | 0.00% |
| DEBIT | 0 | 0.00% |
| PAYMENT | 0 | 0.00% |

TRANSFER transactions had the highest fraud rate, while CASH_OUT transactions accounted for slightly more fraud cases overall.

### 4. Transaction Amount Analysis

Compared transaction amounts between fraudulent and legitimate transactions using summary statistics.

- Median legitimate transaction: approximately $74,685
- Median fraudulent transaction: approximately $441,423
- Fraudulent transactions had substantially higher median amounts overall.

Additional analysis by transaction type showed that the relationship between transaction amount and fraud status varied across categories.

### 5. Account Balance Analysis

Created derived variables to investigate changes in originating and destination account balances.

The analysis identified an unusual relationship between originating account balance consistency and fraud labels.

Because the dataset is synthetic, this finding requires careful interpretation and may reflect characteristics of the simulation rather than real-world fraud behavior.

### 6. Power BI Dashboard

Prepared transaction-level and aggregated datasets for Power BI.

The dashboard presents:

- Total transaction volume
- Total fraudulent transactions
- Overall fraud rate
- Fraud cases by transaction type
- Fraud rates by transaction type

The dashboard uses full-dataset summary statistics to preserve accurate overall metrics.

## Key Findings

1. Fraudulent transactions represented only **0.13%** of the dataset, demonstrating substantial class imbalance.
2. TRANSFER transactions had the highest fraud rate at approximately **0.77%**.
3. CASH_OUT transactions accounted for the greatest number of fraudulent transactions, with **4,116 cases**.
4. Fraudulent transactions generally involved higher amounts, although this relationship differed by transaction type.
5. Account balance patterns revealed potentially useful relationships that require additional investigation and consideration of synthetic data limitations.

These findings demonstrate the importance of evaluating fraud through multiple dimensions rather than relying on a single indicator.

## Project Structure

```text
fraud_detection_analysis/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   └── fraud_analysis.ipynb
├── powerbi/
│   └── fraud_dashboard.pbix
├── src/
│   └── analysis.py
├── pyproject.toml
├── uv.lock
└── README.md
```

The `data/raw/` and `data/processed/` directories are excluded from Git tracking to avoid committing large datasets.

## Reproducing the Project

### Prerequisites

Install the following tools:

- Git
- Python
- uv
- Visual Studio Code with Python and Jupyter extensions
- Power BI Desktop (Windows) to open the dashboard

### 1. Clone the Repository

```powershell
git clone https://github.com/abeaderstadt/fraud_detection_analysis.git
cd fraud_detection_analysis
```

### 2. Set Up the Python Environment

This project uses uv to manage dependencies.

```powershell
uv python install
uv sync
```

### 3. Open the Project

```powershell
code .
```

In VS Code, open `notebooks/fraud_analysis.ipynb` and select the Python kernel from the project's `.venv` environment.

### 4. Obtain the Dataset

Download the PaySim synthetic financial transaction dataset and save the original CSV as:

```text
data/raw/paysim_data.csv
```

The dataset is publicly available through Kaggle:

[PaySim Synthetic Financial Datasets for Fraud Detection](https://www.kaggle.com/datasets/ealaxi/paysim1)

### 5. Run the Analysis

Open:

```text
notebooks/fraud_analysis.ipynb
```

Run the notebook cells in sequence to reproduce the exploratory analysis, derived features, and Power BI data exports.

The processed CSV files are saved in:

```text
data/processed/
```

### 6. Open the Power BI Dashboard

Open the Power BI report:

```text
powerbi/fraud_dashboard.pbix
```

The report uses processed datasets generated from the Python analysis.

If Power BI cannot locate the CSV files, update their paths in **Transform Data → Data source settings**, then refresh the report.

## Project Limitations

- The dataset contains simulated rather than real banking transactions.
- Fraud labels and transaction characteristics may reflect simulation-specific assumptions.
- The analysis is exploratory and does not establish causal relationships.
- A fraud-enriched transaction sample was created for exploration; overall dashboard metrics are calculated from the complete dataset.
- No production fraud detection system was developed or deployed.

## Future Improvements

Potential next steps include evaluating classification models, investigating precision and recall, exploring fraud detection thresholds, and testing additional features for identifying suspicious transactions.

## Author

**Alissa Beaderstadt**

M.S. Data Analytics

[GitHub](https://github.com/abeaderstadt)