# Mexican Real Estate Market Analysis

Part of the **Applied Data Science Lab** by **[WorldQuant University (WQU)](https://www.wqu.edu/)**.

---

## 🎯 Research Question
> **"Are property prices in Mexico more influenced by property size or by location?"**

This project explores the Mexican real estate market using exploratory data analysis (EDA), data cleaning, statistical modeling, and visualization to determine the primary drivers of residential real estate valuation.

---

## 📂 Project Structure

```text
├── 1.1 Getting to Know the Data.ipynb                   # Data auditing, cleaning, and wrangling
├── 1.2 Visualizing Housing Data.ipynb                   # Distribution analysis, boxplots, and scatterplots
├── 1.3 Correlation and Variable Relationships.ipynb     # Pearson correlation, heatmaps, and Simpson's Paradox
├── README.md                                            # Project documentation (this file)
└── data/                                                # Raw and cleaned CSV datasets
    ├── mexico-real-estate-1.csv
    ├── mexico-real-estate-2.csv
    ├── mexico-real-estate-3.csv
    └── mexico-real-estate-combined-clean.csv
```

---

## 📑 Module Breakdown

### 📘 [1.1 Getting to Know the Data](./1.1%20Getting%20to%20Know%20the%20Data.ipynb)
* **Tidy Data Principles**: Enforced tidy data formatting where every variable is a column, observation is a row, and each cell contains a single value.
* **Inspection Ritual**: Audited schemas and types with `.head()`, `.shape`, `.info()`, `.dtypes`, and `.isnull().sum()`.
* **Cleaning Pipelines**: 
  - Applied `pandas` method chaining to clean three disparate CSV files.
  - Handled missing values and dropped corrupted records.
  - Parsed messy currency strings and converted Mexican Pesos (`price_mxn`) to USD (`price_usd`) using fixed historical exchange rates.
  - Split combined `lat-lon` string columns into separate numeric float coordinates (`lat`, `lon`).
* **Dataset Assembly**: Concatenated all cleaned datasets into a unified dataset (`mexico-real-estate-combined-clean.csv`) with `pd.concat(..., ignore_index=True)` and analyzed initial right-skewed price distributions.

---

### 📊 [1.2 Visualizing Housing Data](./1.2%20Visualizing%20Housing%20Data.ipynb)
* **Object-Oriented Plotting**: Built visualizations using Matplotlib's explicit object-oriented API (`fig, ax = plt.subplots()`) coupled with Seaborn styling.
* **Univariate Analysis**: 
  - Plotted histograms and kernel density estimates for `price_usd` and `area_m2`.
  - Highlighted right-skewness and demonstrated why median is a more robust measure of central tendency than mean in real estate.
* **Bivariate Analysis**: 
  - Used boxplots to compare price distributions across property types (apartments vs. houses) and Mexican states.
  - Revealed severe price premiums in Distrito Federal (Mexico City) vs. stable distributions in states like Yucatán.
* **Outlier Trimming & Scatterplots**: 
  - Calculated 1st and 99th percentiles using `.quantile()` to filter extreme outliers that distorted regression lines.
  - Plotted size-vs-price regression trends using `sns.regplot`.
* **Small Multiples**: Created faceted scatterplots by state to visually uncover regional market heterogeneity.

---

### 📈 [1.3 Correlation and Variable Relationships](./1.3%20Correlation%20and%20Variable%20Relationships.ipynb)
* **Pearson Correlation ($r$)**: 
  - Quantified pairwise linear associations on a scale from $-1$ to $+1$.
  - Established a moderate-to-strong national baseline correlation between `area_m2` and `price_usd` ($r \approx 0.59$), meaning area accounts for approximately 35% of price variance ($r^2 \approx 0.35$).
* **Correlation Matrix & Heatmaps**: 
  - Computed full pairwise correlation matrices with `data.select_dtypes("number").corr()`.
  - Visualized relationships using `sns.heatmap(..., annot=True, cmap="coolwarm")`.
  - Identified spurious relationships (e.g., $r_{\text{lat, lon}} \approx -0.48$), diagnosing it as a geographic artifact of Mexico's diagonal shape rather than a market signal.
* **Segmented Correlations**: 
  - Leveraged split-apply-combine pipelines (`groupby`, `corr`, `.iloc`, `.xs`) to compute correlations segmented by state and property type.
  - Showed that size is a stronger predictor for **houses** ($r \approx 0.72$) than for **apartments** ($r \approx 0.52$).
* **Simpson's Paradox**: 
  - Demonstrated that the national $r \approx 0.59$ is a weighted average masking vast local divergence (e.g., rural states show $r > 0.80$ while dense urban centers like Distrito Federal show $r \approx 0.05$).
* **Feature Engineering (`price_per_m2`)**: 
  - Engineered the normalized `price_per_m2` metric using `.assign()` and `lambda` functions.
  - Plotted `area_m2` vs. `price_per_m2` to reveal non-linear **diminishing returns** (larger properties are cheaper per square meter).

---

## 💡 Key Takeaways
1. **Size matters, but unevenly**: While property size correlates positively with price overall, its predictive power depends heavily on property type (stronger for houses than apartments).
2. **Location is the major confounder**: National averages disguise extreme regional variations (Simpson's Paradox). In dense metropolitan areas like Mexico City, location and amenities override raw square footage.
3. **Diminishing returns on area**: Price per square meter decreases as total property area grows, exhibiting a hyperbolic non-linear pattern.
