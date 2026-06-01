# Sales-Data-Statistical-Analysis
A beginner-to-intermediate statistics project using Python that demonstrates core statistical concepts descriptive statistics, confidence intervals, hypothesis testing, and data visualization applied to a synthetically generated retail sales dataset.
📦 Dataset
The dataset is synthetically generated inside the notebook using numpy with a fixed random seed (seed=42) for reproducibility. It simulates 20 products sold over 20 consecutive days starting January 1, 2023.
ColumnTypeDescriptionproduct_idintUnique product identifier (1–20)product_namestrProduct label (e.g., "Product 1")categorystrOne of: Electronics, Clothing, Home, Sportsunits_soldintUnits sold — drawn from a Poisson distribution (λ=20)sale_datedateDaily dates from 2023-01-01

Why Poisson? Sales counts are non-negative integers — the Poisson distribution is a natural and realistic model for count data like daily units sold.


🔬 Analysis Pipeline
1. Descriptive Statistics
Computes the core summary statistics for units_sold:
MetricDescriptionMeanAverage units sold across all productsMedianMiddle value — robust to outliersModeMost frequently occurring valueVarianceSpread of values around the meanStd DeviationAverage distance from the mean
Also groups data by category to compute total sales, average sales, and standard deviation per category.

2. Confidence Intervals
Estimates a range where the true population mean is likely to fall, using a t-distribution (appropriate for small samples, n=20).
Two confidence levels are computed:

95% CI — "We are 95% confident the true mean lies within this range"
99% CI — Wider interval; more certainty, less precision

Formula used:
CI = x̄ ± t*(s / √n)
Where:

x̄ = sample mean
t* = t-score for the chosen confidence level
s = sample standard deviation
n = sample size


3. Hypothesis Testing (One-Sample t-test)
Tests whether the observed mean units sold is statistically significantly different from 20.
Null Hypothesis (H₀)Mean units sold = 20Alternative Hypothesis (H₁)Mean units sold ≠ 20Significance Levelα = 0.05Test Usedscipy.stats.ttest_1samp
The result is interpreted as:

If p-value < 0.05 → Reject H₀ (mean is significantly different from 20)
If p-value ≥ 0.05 → Fail to reject H₀ (not enough evidence to conclude a difference)


Note: Since the data is generated with λ=20 (Poisson), we expect to fail to reject H₀ — this is an intentional design choice showing the test working correctly.


4. Visualizations
ChartWhat It ShowsHistogram + KDEDistribution of units sold with mean/median/mode lines overlaidBoxplot by CategorySpread and outliers of units sold for each product categoryBar Plot by CategoryTotal units sold per category — easy for comparing performance

🛠️ Installation & Usage
Prerequisites

Python 3.8+
Jupyter Notebook or JupyterLab

Install Dependencies
bashpip install pandas numpy matplotlib seaborn scipy
Run the Notebook
bashjupyter notebook STATPROJECT.ipynb
Run all cells top to bottom. The sales_data.csv file will be automatically created in your working directory.

📚 Libraries Used
LibraryPurposepandasData manipulation and DataFramesnumpyNumerical operations and random data generationmatplotlibBase plotting libraryseabornHigh-level statistical visualizationsscipy.statsStatistical tests and distributions

💡 Key Concepts Demonstrated

Poisson distribution for realistic count data simulation
Measures of central tendency (mean, median, mode)
Measures of spread (variance, standard deviation)
Confidence interval construction using the t-distribution
One-sample t-test for hypothesis testing
Category-level aggregation with groupby
Statistical visualization with histograms, boxplots, and bar charts


🔁 Reproducibility
The notebook uses np.random.seed(42) — running it multiple times will always produce the same dataset and results.
