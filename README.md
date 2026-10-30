# SML Lab Experiments — Executed Notebooks

All 9 notebooks in this folder were executed end-to-end successfully (9/9 PASS)
with outputs, plots and results saved inside each file — ready to submit or paste.
Kernel used: Python 3.11 (pandas, numpy, matplotlib, seaborn, scipy, scikit-learn, statsmodels).

Datasets included: `Social_Network_Ads.csv` (400 users) and `customer_data.csv`
(81 customers, converted from the original .xlsx). The Palmer Penguins and Iris
datasets are downloaded from GitHub at runtime (internet needed for those two).

---

## 1. EXP1_EDA.ipynb — Exploratory Data Analysis
Performs initial exploration of `customer_data.csv`: checks the shape and first rows,
then plots histograms for all numeric columns and an Age distribution with a KDE curve.
Computes a correlation matrix of numeric features and displays it as an annotated
heatmap, revealing which variables move together before any modelling.

## 2. EXP2.ipynb — Data Cleaning and Preprocessing
Builds a full preprocessing pipeline on `customer_data.csv`: removes duplicate rows
(e.g. repeated C021), converts the invalid "XXXX" placeholder in
Customer_Lifespan_Months to NaN, and parses Date_of_Purchase. Imputes missing values
(median for numeric, mode for City), label-encodes binary columns (Gender,
Purchase_Channel, Churn_Status), one-hot encodes City and Region, detects outliers
with the IQR rule, caps extreme values (winsorizing), and finally applies a
RobustScaler to the numeric features.

## 3. Exp3 SML.ipynb — Sampling Techniques (SRS, Stratified, Cluster)
Compares three sampling methods on the Palmer Penguins dataset: simple random
sampling, stratified sampling by species, and cluster sampling by island.
For each method it measures how close the sample mean body mass is to the true
population mean across repeated draws, showing why stratification reduces variance
while cluster sampling with only three islands stays imprecise.

## 4. Exp4SML.ipynb — Central Limit Theorem Demonstration
Draws 10,000 samples of size 30 from an exponential distribution, which is strongly
non-normal, and plots the histogram of the sample means. The resulting bell-shaped
curve demonstrates that sample means approach normality regardless of the underlying
distribution. Supports varying sample size and distribution to show the effect of n.

## 5. Exp6SMLD.ipynb — Bootstrap and Maximum Likelihood Estimation
Two parts. First, 5,000 bootstrap resamples of iris petal length per species are used
to estimate standard errors and confidence intervals of the mean without any
distributional assumption. Second, Maximum Likelihood Estimation is applied to
synthetic Normal(mu=50, sigma^2=100) data; the MLE estimates (sample mean and
biased variance) come close to the true parameters, confirming MLE consistency.

## 6. Exp 7 (naive_bayes_classification).ipynb — Naive Bayes Classification
Trains a Gaussian Naive Bayes classifier on the Social Network Ads data using Age
and EstimatedSalary to predict Purchased. Reports accuracy, confusion matrix and
classification report, then draws the decision boundary over the two features.
Serves as the probabilistic baseline for comparison with the decision tree.

## 7. Exp 9 KMeans .ipynb — K-Means Clustering
Applies K-Means (k=3) to standardized Age and EstimatedSalary from the Social
Network Ads dataset so both features contribute equally. Visualizes the resulting
clusters in a scatter plot and summarizes each cluster with mean Age, mean salary
and purchase rate, showing natural customer segments independent of the label.

## 8. decision_tree_classification.ipynb — Decision Tree Classification
Fits a Decision Tree on the same Social Network Ads features and target as Exp 7,
evaluates it with accuracy, confusion matrix and classification report, and plots
the learned tree. Reports feature importance, visualizes the (piecewise-rectangular)
decision boundary, and allows direct comparison of tree vs. Naive Bayes behaviour.

## 9. Two_Way_ANOVA_Demo.ipynb — Two-Way ANOVA Without Replication
Walks through a two-way ANOVA by hand: enters a small two-factor table, visualizes
group means, then computes the grand mean, row/column sums of squares and residual
SS step by step. Derives the F-statistics and p-values for both factors to test
whether each factor significantly affects the response.

---

### How to run
1. Install Jupyter: `pip install notebook` (or use any Jupyter installation).
2. Keep the notebooks and the two CSV files in the same folder.
3. Open and run all cells — notebooks 3 and 5 need internet for Penguins/Iris.
