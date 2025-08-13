Predictive Insights into Hotel Reservations
📌 Overview
This project explores a hotel reservations dataset to analyze booking patterns, identify cancellation trends, and build predictive models.
The goal is to create statistical and machine learning models that can help hotels predict whether a booking will be canceled or not canceled.

📂 Dataset
Source: Hotel Reservations.csv

Key Features:

Guest demographics (e.g., number of adults, children)

Stay details (e.g., number of weekend/weekday nights, arrival month)

Booking preferences (e.g., meal plan, room type, special requests)

Market segment and pricing

Historical booking/cancellation behavior

Target Variable: booking_status

Canceled

Not_Canceled

🔍 Workflow
Data Loading & Inspection

Imported CSV file into R

Checked dimensions, missing values, structure, and summary statistics

Data Cleaning & Preparation

Removed irrelevant columns (IDs and redundant attributes)

Converted arrival_month to factor with month names

Exploratory Data Analysis (EDA)

Univariate Analysis: Histograms, frequency tables, and bar plots for individual features

Bivariate Analysis: Relationship between features and booking status

Boxplots: Visualized numeric variables across cancellation status

Data Splitting

29,000 rows for training

Remaining rows for testing

Modeling

Logistic Regression (baseline classification model)

Linear Discriminant Analysis (LDA) with different decision thresholds (0.3, 0.4)

Naive Bayes classifier

K-Nearest Neighbors (KNN) with k=7

Model Evaluation

Confusion matrices

Accuracy and testing error rate calculation

Comparison of models and threshold adjustments for LDA

📊 Libraries Used & Purpose
Data Manipulation
base R: Reading CSV, indexing, subsetting, basic data operations

Visualization
ggplot2:

Created bar charts with counts and grouped booking status

Custom legends, labels, and aesthetics

gridExtra:

Arranged multiple ggplot2 plots in grid layouts

base plotting functions:

Histograms, barplots, boxplots with labeled counts and color customization

Statistical & Machine Learning
MASS:

lda() function for Linear Discriminant Analysis

e1071:

naiveBayes() for Naive Bayes classification

class:

knn() for K-Nearest Neighbors classification

stats:

glm() for logistic regression

Utilities
attach(): Simplifies direct reference to dataset variables (used in KNN section)

⚙️ How to Run
1.Open the .Rmd file in RStudio

2.Install required packages (if not installed):

```{r}
install.packages(c("ggplot2", "gridExtra", "MASS", "e1071", "class"))
```

3.Set your working directory to the location of Hotel Reservations.csv:

```{r}
setwd("path/to/your/folder")
```
4.Knit the file to HTML or PDF to view the report

📈 Results Summary
Model	Accuracy	Testing Error Rate
Logistic Regression (0.5)	~79.8%	~20.2%
LDA (default)	Varied	Varied
LDA (threshold = 0.3)	Varied	Varied
LDA (threshold = 0.4)	Varied	Varied
Naive Bayes	Varied	Varied
KNN (k=7)	Varied	Varied

(Replace “Varied” with actual computed values when finalizing report.)

📌 Notes
Threshold tuning in LDA can shift the balance between false positives and false negatives.

KNN performance depends on scaling, selected features, and choice of k.

Logistic regression provides interpretable coefficients, useful for feature importance.