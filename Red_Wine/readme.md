# Wine Quality — Exploratory Data Analysis

Exploratory Data Analysis (EDA) on the **Red Wine Quality** dataset, covering data cleaning, statistical summaries, correlation analysis, and univariate/bivariate/multivariate visualizations to understand what drives wine quality ratings.

## 📊 Dataset

- **File:** `winequality-red.csv`
- **Format:** semicolon-separated (`;`)
- **Target variable:** `quality` (integer score, typically 3–8)
- **Features:** physicochemical properties of red wine (e.g. `alcohol`, `pH`, `volatile acidity`, `citric acid`, `sulphates`, etc.)

## 🛠️ Requirements

```bash
pip install pandas seaborn matplotlib
```

## 📓 Notebook Structure

### 1. Data Loading & Inspection
- Load the CSV with `pandas`
- Preview with `df.head()`, `df.info()`, `df.shape`, `df.columns`
- Check unique values in `quality`

### 2. Statistical Summary
- `df.describe()` for count, mean, std, min/max, and quartiles of every numeric feature

### 3. Data Cleaning
- Check for missing values (`df.isnull().sum()`)
- Detect duplicate rows (`df.duplicated()`)
- Drop duplicates (`df.drop_duplicates()`)

### 4. Correlation Analysis
- Compute the pairwise correlation matrix (`df.corr()`)
- Visualize it as a heatmap (`seaborn.heatmap`) to spot multicollinearity and features related to `quality`

### 5. Distribution Analysis
- Bar chart of `quality` value counts
- Histograms (with KDE) for every numeric column to check skewness, normality, and outliers — useful for deciding between parametric tests (e.g. paired t-test) and non-parametric ones (e.g. Wilcoxon signed-rank test)

### 6. Univariate / Bivariate / Multivariate Analysis
- `sns.pairplot(df)` for a full grid of pairwise scatter plots and distributions
- `sns.catplot(x='quality', y='alcohol', kind='box')` — box plots of alcohol content across quality levels
- `sns.scatterplot(x='alcohol', y='pH', hue='quality')` — scatter plot colored by quality to spot clustering patterns

## 📈 Key Techniques Demonstrated

| Technique | Purpose |
|---|---|
| Correlation heatmap | Identify redundant/multicollinear features |
| Histograms (KDE) | Check distribution shape, skewness, outliers |
| Pairplot | Visualize all pairwise relationships at once |
| Box plot by category | Compare a numeric feature across quality groups |
| Scatter plot with hue | Explore how two features jointly relate to quality |

## 🚀 Usage

1. Place `winequality-red.csv` in the same directory as the notebook.
2. Open `exploratory_analysis.ipynb` in Jupyter.
3. Run all cells sequentially.

## 📌 Next Steps

- Handle skewed features (e.g. log-transform) before modeling
- Use correlation + pairplot insights for feature selection
- Move to statistical hypothesis testing or predictive modeling (classification/regression on `quality`)

---
*Part of an ongoing ML/statistics learning workflow — EDA techniques here connect directly to hypothesis testing concepts (t-test vs. Wilcoxon) used elsewhere in model evaluation work.*
