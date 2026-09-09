# 📊 Retail Sales Exploratory Data Analysis (EDA)

An end-to-end Exploratory Data Analysis (EDA) project in Python analyzing retail sales performance, customer demographic patterns, and purchasing behaviors to extract actionable business insights.

---

## 📌 Project Overview

This project uncovers revenue drivers, seasonal purchase cycles, and customer segment profiles from historical retail transaction records. Through structured data inspection, statistical profiling, and visualizations, the analysis identifies sales trends across time, top-grossing inventory segments, and opportunities for conversion optimization.

---

## 🚀 Key Features

* **Data Cleaning & Inspection:** Dimension profiling (`shape`), datatype auditing (`dtypes`), and null/duplicate handling.
* **Descriptive Statistical Summary:** Measures of central tendency (mean, median, mode) and dispersion (standard deviation, IQR) across numeric fields.
* **Time Series Sales Analysis:** Line charts capturing month-over-month (MoM) and quarter-over-quarter (QoQ) revenue trajectories and seasonal spikes.
* **Demographic Segmentation:** Age cohort distributions and gender breakdown of transactional volume.
* **Product Performance:** Top 10 revenue-generating SKUs and categorical sales distributions.
* **Correlation Heatmap:** Multi-variable correlation matrix evaluating pricing, order volume, discounts, and net revenue.
* **Deep-Dive Visualizations:** Highlighting non-obvious insights such as discount sensitivity vs. profit margins.
* **Actionable Business Strategy:** Strategic roadmap based directly on empirical data trends.

---

## 🛠️ Tech Stack

* **Language:** Python 3.9+
* **Environment:** Jupyter Notebook / Google Colab / VS Code
* **Core Libraries:**
  * `pandas` – Data manipulation, cleaning, and aggregation
  * `numpy` – Numerical computation and array operations
  * `matplotlib` – Baseline visualization engine
  * `seaborn` – Statistical data visualization

---

## 📁 Repository Structure

```text
├── data/
│   └── retail_sales.csv          # Sourced dataset (Kaggle)
├── notebooks/
│   └── retail_sales_eda.ipynb    # Main Jupyter Notebook with code & observations
├── visuals/                      # Exported charts and correlation plots
├── requirements.txt              # Project dependencies
└── README.md                     # Project documentation
```

---

## ⚙️ Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/<your-username>/retail-sales-eda.git
   cd retail-sales-eda
   ```

2. **Create and activate a virtual environment:**
   ```bash
   # Windows
   python -m venv venv
   venv\Scripts\activate

   # macOS/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook notebooks/retail_sales_eda.ipynb
   ```

---

## 📦 Sourcing the Dataset

This project can be paired with transactional retail datasets from [Kaggle](https://www.kaggle.com):
* **Recommended Search Terms:** `retail sales dataset`, `superstore sales`, `e-commerce sales dataset`
* **Placement:** Download the CSV and place it inside the `data/` directory as `retail_sales.csv`.

---

## 💡 Key Insights & Actionable Recommendations

* **Inventory Optimization for Seasonal Peaks:** Align restocking schedules 4–6 weeks ahead of identified peak quarterly surges (e.g., Q4 holiday spikes) to prevent out-of-stock events on top-tier SKUs.
* **Targeted Cohort Marketing:** Concentrate promotional spend on the primary purchasing demographic while tailoring product bundling to underperforming segments to lift basket size.
* **Discount Rationalization:** Protect margins by capping promotions on high-demand, low-elasticity categories, shifting markdown budgets toward clearance or cross-selling slower-moving inventory.

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.
