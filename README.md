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

#### 📈 [1.3 Correlation and Variable Relationships](./Hands-on%20Data%20Science%20in%20the%20Mexican%20Real%20Estate%20Market/1.3%20Correlation%20and%20Variable%20Relationships.ipynb)
- **Pearson Correlation ($r$)**: Quantified linear relationships between numeric features, establishing a national baseline ($r \approx 0.59$) between property area and price.
- **Correlation Matrix & Heatmaps**: Used `pandas.select_dtypes("number").corr()` and `seaborn.heatmap()` to visualize pairwise associations and identified non-actionable geographic artifacts (`lat` vs `lon`).
- **Segmented Correlations**: Leveraged split-apply-combine (`groupby`, `corr`, `.iloc`, `.xs`) across states and property types (houses vs. apartments) to expose market heterogeneity.
- **Simpson's Paradox**: Analyzed how aggregate national trends mask divergent local market dynamics (e.g., strong size-price relationships in rural states vs. weak relationships in dense urban centers like CDMX).
- **Feature Engineering**: Engineered `price_per_m2` using `.assign()` and `lambda` functions to uncover non-linear diminishing returns of property size.

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


