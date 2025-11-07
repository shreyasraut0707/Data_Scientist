# Data Science Assignment: Trader Behavior & Market Sentiment Analysis

**Candidate Name:** Shreyas  
**Position:** Junior Data Scientist - Trader Behavior Insights  
**Date:** November 2025

---

## 📋 Project Overview

This project analyzes the relationship between cryptocurrency trader performance and Bitcoin market sentiment (Fear vs Greed). The analysis uses two primary datasets:

1. **Bitcoin Fear & Greed Index** - Daily sentiment classifications from 2018-2024
2. **Historical Trader Data from Hyperliquid** - Over 200,000+ trade records including execution details, PnL, and position data

**Objective:** Identify patterns in trader performance during different market sentiment periods to derive actionable trading insights.

---

## 📊 Datasets

### 1. Fear & Greed Index Dataset

- **Columns:** `timestamp`, `value`, `classification`, `date`
- **Classifications:** Extreme Fear, Fear, Neutral, Greed, Extreme Greed
- **Date Range:** 2018-02-01 to 2024-12-02
- **Records:** ~2,646 daily sentiment readings

### 2. Historical Trader Data

- **Columns:** `Account`, `Coin`, `Execution Price`, `Size Tokens`, `Size USD`, `Side`, `Timestamp IST`, `Start Position`, `Direction`, `Closed PnL`, `Transaction Hash`, `Order ID`, `Crossed`, `Fee`, `Trade ID`, `Timestamp`
- **Key Metrics:** Execution price, trade size, PnL, leverage, trading side (Buy/Sell)
- **Records:** 211,226+ trades

---

## 📁 Project Structure

```
ds_Shreyas/
├── notebook_1.ipynb               # Data Loading, Cleaning & EDA
├── notebook_2.ipynb               # Sentiment Analysis & Insights
├── csv_files/                     # Processed data files
│   ├── merged_trader_sentiment.csv
│   ├── cleaned_fear_greed.csv
│   ├── cleaned_trader_data.csv
│   └── analysis_summary.csv
├── outputs/                       # Visualization outputs
│   ├── sentiment_distribution.png
│   ├── buy_sell_distribution.png
│   ├── pnl_distribution.png
│   ├── pnl_by_sentiment.png
│   ├── win_rate_analysis.png
│   ├── volume_analysis.png
│   ├── pnl_distribution_by_sentiment.png
│   ├── buy_sell_sentiment_analysis.png
│   └── cumulative_pnl_over_time.png
├── ds_report.pdf                  # Final analysis report
└── README.md                      # This file
```

---

## 📓 Notebooks Description

### Notebook 1: Data Loading, Cleaning & EDA (`notebook_1.ipynb`)

**Purpose:** Load raw datasets, perform data cleaning, merge on date, and conduct exploratory analysis.

**Key Steps:**

1. Import libraries (pandas, numpy, matplotlib, seaborn)
2. Load Fear/Greed Index and Historical Trader datasets
3. Data inspection and quality checks
4. Date/timestamp conversion and standardization
5. Handle missing values and duplicates
6. Merge datasets on date field
7. Generate basic visualizations:
   - Sentiment distribution across trades
   - Buy vs Sell trade breakdown
   - PnL distribution analysis
8. Save cleaned datasets to `csv_files/`

**Output:**

- Cleaned and merged dataset ready for analysis
- Initial EDA charts saved to `outputs/`
- Summary statistics of the data

---

### Notebook 2: Trader Behavior Analysis (`notebook_2.ipynb`)

**Purpose:** Analyze trader performance differences between Fear and Greed market sentiment periods.

**Key Steps:**

1. Load cleaned merged dataset
2. Create binary sentiment categories (Fear vs Greed)
3. Performance comparison:
   - Average PnL by sentiment
   - Total PnL by sentiment
   - Win rate calculations
4. Statistical significance testing (t-test)
5. Trading volume analysis
6. Risk analysis (volatility, PnL distribution)
7. Trading side analysis (Buy vs Sell performance)
8. Time-series analysis (cumulative PnL over time)
9. Generate comprehensive insights
10. Export summary metrics

**Key Findings:**

- Comparative performance metrics for Fear vs Greed periods
- Win rate differences across sentiment states
- Risk/volatility patterns
- Strategic trading recommendations

**Output:**

- 6+ comprehensive charts saved to `outputs/`
- Analysis summary exported to `csv_files/analysis_summary.csv`
- Key insights and recommendations

---

## 🔗 Google Colab Links

### Notebook 1 - Data Cleaning & EDA

**Colab Link:** https://colab.research.google.com/drive/1NbW7jylby6gk7XzwlqnwJlNdnkzQN5KW?usp=sharing

### Notebook 2 - Analysis & Insights

**Colab Link:** https://colab.research.google.com/drive/1oG_yWR3XiMWY1qUG4M-dFO2YY4Ty-XId?usp=sharing

> **Note:** Sharing permissions are set to "Anyone with the link can view"

---

## 🐙 GitHub Repository

**Repository Link:** https://github.com/shreyasraut0707/Data_Scientist

**Repository contains:**

- Complete `ds_shreyasraut/` folder structure
- All notebooks (.ipynb files)
- All data files in `csv_files/`
- All visualizations in `outputs/`
- This README.md
- ds_report.md

---

## 🔧 Setup Instructions

### Prerequisites

- **Python 3.8 or higher** (Tested on Python 3.11.9)
- **Required Libraries:**
  - pandas (2.3.3+)
  - numpy (2.3.4+)
  - matplotlib (3.10+)
  - seaborn (0.13+)
  - scipy (1.15+)

### Installation Steps

#### Step 1: Verify Python Installation

```cmd
# Check Python version (should be 3.8 or higher)
python --version
```

#### Step 2: Install Required Packages

```cmd
# Install all required packages
pip install pandas numpy matplotlib seaborn scipy

# Or install with specific versions (recommended)
pip install pandas==2.3.3 numpy==2.3.4 matplotlib==3.10.7 seaborn==0.13.2 scipy==1.15.2
```

#### Step 3: Verify Installation

```cmd
# Verify packages are installed correctly
python -c "import pandas, numpy, matplotlib, seaborn, scipy; print('All packages installed successfully!')"
```

---

## 🚀 How to Execute the Project

### **Option 1: Using Python Script (Fastest & Recommended for Windows)**

This is the **easiest method** that combines both notebooks into a single executable script.

#### Step 1: Navigate to Project Directory

```cmd
cd C:\Users\Shreyas\OneDrive\Desktop\Data_Scientist\ds_Shreyas
```

#### Step 2: Verify Data Files Are Present

```cmd
# Check if CSV files exist in the parent directory
dir ..\fear_greed_index.csv
dir ..\historical_data.csv
```

**Note:** The script expects these files in the parent directory (`Data_Scientist\`). If they're elsewhere, you'll need to update file paths in the notebooks.

#### Step 3: Run the Analysis Script

```cmd
python run_analysis.py
```

#### Expected Output:

- **Console Output:** Progress messages and analysis summary
- **Execution Time:** Approximately 5 minutes
- **Generated Files:**
  - 9 charts in `outputs/` folder (PNG format, 300 DPI)
  - 6 CSV files in `csv_files/` folder
  - Analysis summary in `csv_files/analysis_summary.csv`

#### Step 4: Verify Results

```cmd
# Check generated charts
dir outputs

# Check generated CSV files
dir csv_files

# View analysis summary
type csv_files\analysis_summary.csv
```

---

### **Option 2: Using Jupyter Notebooks (Local)**

If you want to run notebooks interactively and see step-by-step results.

#### Step 1: Install Jupyter (if not already installed)

```cmd
pip install jupyter notebook ipykernel
```

#### Step 2: Navigate to Project Directory

```cmd
cd C:\Users\Shreyas\OneDrive\Desktop\Data_Scientist\ds_Shreyas
```

#### Step 3: Launch Jupyter Notebook

```cmd
jupyter notebook
```

This will open Jupyter in your default web browser.

#### Step 4: Execute Notebooks in Order

1. **First, open and run `notebook_1.ipynb`:**

   - Click "Cell" → "Run All" or press `Shift + Enter` on each cell
   - This will:
     - Load and clean the data
     - Merge trader data with sentiment data
     - Generate 3 initial charts
     - Save cleaned data to `csv_files/`
   - **Execution time:** ~2 minutes

2. **Then, open and run `notebook_2.ipynb`:**
   - Click "Cell" → "Run All" or press `Shift + Enter` on each cell
   - This will:
     - Load the merged dataset from notebook_1
     - Perform sentiment-based analysis
     - Generate 6 additional charts
     - Create statistical summaries
   - **Execution time:** ~3 minutes

#### Step 5: Review Outputs

- Charts will be saved in `outputs/` folder
- Processed data will be in `csv_files/` folder
- Review `analysis_summary.csv` for key metrics

---

### **Option 3: Google Colab (Cloud Execution)**

Perfect for running without local Python installation.

#### Step 1: Upload Notebooks to Google Colab

1. Go to [Google Colab](https://colab.research.google.com/)
2. Click "File" → "Upload notebook"
3. Upload `notebook_1.ipynb` and `notebook_2.ipynb`

#### Step 2: Upload Data Files to Colab

For each notebook, add this cell at the top:

```python
from google.colab import files
uploaded = files.upload()
# Upload fear_greed_index.csv and historical_data.csv when prompted
```

Or mount Google Drive:

```python
from google.colab import drive
drive.mount('/content/drive')
# Place CSV files in your Google Drive and update paths
```

#### Step 3: Update File Paths in Notebooks

Change file paths from `../fear_greed_index.csv` to:

- `fear_greed_index.csv` (if uploaded directly)
- `/content/drive/MyDrive/fear_greed_index.csv` (if using Google Drive)

#### Step 4: Run Notebooks

1. **Run `notebook_1.ipynb` first** (Runtime → Run all)
2. **Then run `notebook_2.ipynb`** (Runtime → Run all)

#### Step 5: Download Results

```python
# Add this at the end of notebook_2 to download results
from google.colab import files
import os

# Download all charts
for filename in os.listdir('outputs'):
    files.download(f'outputs/{filename}')

# Download analysis summary
files.download('csv_files/analysis_summary.csv')
```

#### Step 6: Share Notebooks

1. Click "Share" button in top-right
2. Set to "Anyone with the link can view"
3. Copy link and update README.md

---

## 🔍 Troubleshooting

### Common Issues and Solutions

#### Issue 1: "ModuleNotFoundError: No module named 'pandas'"

**Solution:**

```cmd
pip install pandas numpy matplotlib seaborn scipy
```

#### Issue 2: "FileNotFoundError: fear_greed_index.csv not found"

**Solution:**

- Ensure CSV files are in the correct location
- For notebooks: Files should be in parent directory (`../fear_greed_index.csv`)
- For script: Files should be in parent directory relative to `ds_Shreyas/`

#### Issue 3: "numpy.dtype size changed" error

**Solution:**

```cmd
pip uninstall numpy pandas -y
pip install pandas==2.3.3 numpy==2.3.4
```

#### Issue 4: Jupyter kernel dies or crashes

**Solution:**

- Use `run_analysis.py` script instead (Option 1)
- Or restart kernel: Kernel → Restart & Run All

#### Issue 5: Charts not displaying in Jupyter

**Solution:**
Add this at the top of notebooks:

```python
%matplotlib inline
```

---

## 📦 Project Files Explained

### Input Files (Required)

- `../fear_greed_index.csv` - Bitcoin Fear & Greed sentiment data (2,644 records)
- `../historical_data.csv` - Trader transaction history (211,224 trades)

### Output Files (Generated Automatically)

**CSV Files in `csv_files/` folder:**

1. `cleaned_fear_greed.csv` - Cleaned sentiment data
2. `cleaned_trader_data.csv` - Cleaned trader data
3. `merged_trader_sentiment.csv` - Combined dataset (211,218 records)
4. `fear_performance.csv` - Performance metrics during Fear periods
5. `greed_performance.csv` - Performance metrics during Greed periods
6. `analysis_summary.csv` - Final analysis summary with key metrics

**Charts in `outputs/` folder:**

1. `sentiment_distribution.png` - Count of trades by sentiment
2. `buy_sell_distribution.png` - Buy vs Sell trade proportions
3. `pnl_distribution.png` - Distribution and boxplot of PnL
4. `pnl_by_sentiment.png` - Average and Total PnL by sentiment
5. `win_rate_analysis.png` - Win rates comparison (Fear vs Greed)
6. `volume_analysis.png` - Trading volume by sentiment
7. `pnl_distribution_by_sentiment.png` - Risk profiles (Boxplot & Violin)
8. `buy_sell_sentiment_analysis.png` - Buy/Sell performance analysis
9. `cumulative_pnl_over_time.png` - Cumulative PnL over time

---

## ⏱️ Execution Time Estimates

- **Python Script (`run_analysis.py`):** ~5 minutes total
- **Notebook 1 (`notebook_1.ipynb`):** ~2 minutes
- **Notebook 2 (`notebook_2.ipynb`):** ~3 minutes
- **Total Project Completion:** ~5-7 minutes (including setup)

---

## ✅ Verification Steps

After execution, verify everything worked correctly:

```cmd
# Check number of output charts (should be 9)
dir outputs\*.png

# Check number of CSV files (should be 6)
dir csv_files\*.csv

# View key results
type csv_files\analysis_summary.csv
```

**Expected Results:**

- 9 PNG files in `outputs/` folder
- 6 CSV files in `csv_files/` folder
- No error messages in console
- `analysis_summary.csv` contains Fear vs Greed metrics

---

## 📈 Key Analysis Questions Answered

1. **Do traders perform better during Fear or Greed periods?**

   - Comparative PnL analysis
   - Win rate comparison
   - Statistical significance testing

2. **How does trading volume differ across sentiment states?**

   - Trade count by sentiment
   - Average trade size analysis

3. **What are the risk profiles during different sentiments?**

   - Volatility (standard deviation) comparison
   - PnL distribution analysis

4. **Are there exploitable patterns for trading strategies?**
   - Buy vs Sell performance by sentiment
   - Cumulative PnL trends over time
   - Strategic recommendations based on data

---

## 📊 Key Visualizations

All charts are saved in the `outputs/` folder:

1. **sentiment_distribution.png** - Distribution of sentiment classifications in trading data
2. **buy_sell_distribution.png** - Proportion of Buy vs Sell trades
3. **pnl_distribution.png** - Overall PnL distribution and boxplot
4. **pnl_by_sentiment.png** - Average and Total PnL comparison (Fear vs Greed)
5. **win_rate_analysis.png** - Win rate comparison and Win/Loss breakdown
6. **volume_analysis.png** - Trading volume and trade count by sentiment
7. **pnl_distribution_by_sentiment.png** - Risk profile comparison (Boxplot & Violin)
8. **buy_sell_sentiment_analysis.png** - Buy/Sell performance across sentiments
9. **cumulative_pnl_over_time.png** - Time-series cumulative PnL trends

---

## 🎯 Main Insights Summary

### Performance Metrics

- **Fear Periods:**
  - Average PnL: $X.XX
  - Win Rate: XX.XX%
  - Trade Volume: XXX,XXX trades
- **Greed Periods:**
  - Average PnL: $X.XX
  - Win Rate: XX.XX%
  - Trade Volume: XXX,XXX trades

### Statistical Significance

- T-test results indicate [significant/not significant] difference in performance
- P-value: X.XXXXX

### Strategic Recommendation

[Based on analysis, provide 2-3 sentence recommendation on optimal trading approach during different sentiment periods]

> **Note:** Detailed findings and interpretations are available in `ds_report.pdf`

---

## 📝 Methodology

### Data Processing

1. **Date Alignment:** Converted all timestamps to standardized datetime format
2. **Merging Strategy:** Inner join on date field to match trades with sentiment
3. **Missing Data:** Removed trades with missing PnL or date information
4. **Sentiment Categorization:** Grouped "Extreme Fear" + "Fear" → Fear; "Extreme Greed" + "Greed" → Greed

### Analysis Approach

1. **Descriptive Statistics:** Mean, median, standard deviation, count
2. **Comparative Analysis:** Group-by sentiment and compare metrics
3. **Statistical Testing:** Independent t-test for significance
4. **Visualization:** Multiple chart types for comprehensive understanding
5. **Time-series:** Cumulative performance tracking over time

---

## 🚀 Future Work & Enhancements

Potential areas for deeper analysis:

- Machine learning model to predict profitable trades based on sentiment
- Account-level performance clustering
- Symbol-specific sentiment analysis
- Leverage impact on PnL across sentiments
- Intraday timing patterns within sentiment periods
- Multi-factor analysis combining sentiment with other market indicators

---

## 📧 Contact & Submission

**Submission Email:**

- **To:** saami@bajarangs.com, nagasai@bajarangs.com, chetan@bajarangs.com
- **CC:** sonika@primetrade.ai
- **Subject:** "Junior Data Scientist – Trader Behavior Insights"

**Attachments:**

- Resume
- GitHub repository link
- Google Colab links (in this README)

---

## ✅ Submission Checklist

- [x] ✅ Created `ds_Shreyas/` folder structure
- [x] ✅ Completed `notebook_1.ipynb` - Data Cleaning & EDA
- [x] ✅ Completed `notebook_2.ipynb` - Analysis & Insights
- [x] ✅ Generated all visualizations in `outputs/`
- [x] ✅ Saved processed data in `csv_files/`
- [ ] ⏳ Created `ds_report.pdf` with key findings
- [ ] ⏳ Uploaded notebooks to Google Colab with view access
- [ ] ⏳ Uploaded project to GitHub repository
- [ ] ⏳ Updated README.md with Colab and GitHub links
- [ ] ⏳ Sent application email with all materials

---

## 📄 License

This project is submitted as part of the Junior Data Scientist hiring process for the Web3 Trading Team.

---

**Last Updated:** November 6, 2025  
**Version:** 1.0
