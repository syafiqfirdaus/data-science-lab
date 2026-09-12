# Data Science Lab

A collection of hands-on data science projects from the **Applied Data Science Lab** by **[WorldQuant University (WQU)](https://www.wqu.edu/)**.

---

## Project: Mexican Real Estate Market Analysis

> **Research Question:** *Are property prices in Mexico more influenced by property size or by location?*

### Module Summaries

#### 📘 [1.1 Getting to Know the Data](./Hands-on%20Data%20Science%20in%20the%20Mexican%20Real%20Estate%20Market/1.1%20Getting%20to%20Know%20the%20Data.ipynb)
- **Tidy Data Principles**: Enforced tidy data rules (variables in columns, observations in rows, single values per cell).
- **Inspection Ritual**: Audited schemas and types with `.head()`, `.shape`, `.info()`, `.dtypes`, and `.isnull().sum()`.
- **Cleaning Pipelines**: Cleaned three CSVs via `pandas` method chaining—handled missing data, parsed currency strings, converted MXN to USD, and split combined `lat-lon` coordinates.
- **Dataset Assembly**: Concatenated datasets with `pd.concat(..., ignore_index=True)` and analyzed right-skewed price distributions with `.describe()`.

#### 📊 [1.2 Visualizing Housing Data](./Hands-on%20Data%20Science%20in%20the%20Mexican%20Real%20Estate%20Market/1.2%20Visualizing%20Housing%20Data.ipynb)
- **Object-Oriented Plotting**: Utilized Matplotlib's explicit interface (`fig, ax = plt.subplots()`) integrated with Seaborn.
- **Univariate Analysis**: Plotted histograms of price and area, illustrating right-skewness and why median is more reliable than mean in real estate.
- **Bivariate Analysis**: Used boxplots to compare property types and states, revealing market premiums in Distrito Federal vs. stability in Yucatán.
- **Outlier Trimming & Scatterplots**: Applied quantile filtering to remove extreme outliers before plotting size-vs-price regression trends (`sns.regplot`).
- **Small Multiples**: Faceted scatterplots by state to uncover regional market heterogeneity.

---

## Environment Setup

```bash
# 1. Create and activate virtual environment
python -m venv .venv
.\.venv\Scripts\Activate.ps1    # Windows PowerShell

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch JupyterLab
jupyter lab
```


