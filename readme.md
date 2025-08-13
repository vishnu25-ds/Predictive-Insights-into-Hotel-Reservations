# Predictive Insights into Hotel Reservations

## 📌 Overview
This project uses statistical analysis and machine learning techniques to **predict hotel booking cancellations**.  
By understanding customer **behavior**, booking patterns, and cancellation trends, the model can help hotel management:

- Minimize last-minute cancellations  
- Optimize revenue forecasting  
- Improve resource allocation and staffing  
- Enhance guest satisfaction  

The analysis covers **Exploratory Data Analysis (EDA)**, **data preprocessing**, **model building**, **evaluation**, and **interpretation**.

________________________________________
# 🎯 Problem Statement
Hotels face significant operational and financial challenges from reservation cancellations.
The key questions addressed in this project are:
1.	Which factors influence booking cancellations the most?
2.	Can we accurately predict if a booking will be canceled?
3.	Which model balances accuracy and business priorities (precision vs. recall) best?
________________________________________
# Workflow
## 1.	Data Loading & Inspection
	-Imported CSV file into R
	-Checked dimensions, missing values, structure, and summary statistics
## 2.	Data Cleaning & Preparation
	-Removed irrelevant columns (IDs and redundant attributes)
	-Converted arrival_month to factor with month names
## 3.	Exploratory Data Analysis (EDA)
	-Univariate Analysis: Histograms, frequency tables, and bar plots for individual features
	-Bivariate Analysis: Relationship between features and booking status
	-Boxplots: Visualized numeric variables across cancellation status
## 4.	Data Splitting
	-29,000 rows for training
	-Remaining rows for testing
## 5.	Modeling
	-Logistic Regression (baseline classification model)
	-Linear Discriminant Analysis (LDA) with different decision thresholds (0.3, 0.4)
	-Naive Bayes classifier
	-K-Nearest Neighbors (KNN) with k=7
## 6.	Model Evaluation
	-Confusion matrices
	-Accuracy and testing error rate calculation
	-Comparison of models and threshold adjustments for LDA

# 📊 Libraries Used & Purpose
## Data Manipulation
	base R: Reading CSV, indexing, subsetting, basic data operations
## Visualization
### 	ggplot2:
	-Created bar charts with counts and grouped booking status
	-Custom legends, labels, and aesthetics
### 	gridExtra:
	-Arranged multiple ggplot2 plots in grid layouts
### 	base plotting functions:
	-Histograms, barplots, boxplots with labeled counts and color customization
## Statistical & Machine Learning
### 	MASS:
	-lda() function for Linear Discriminant Analysis
### 	e1071:
	-naiveBayes() for Naive Bayes classification
### 	class:
	-knn() for K-Nearest Neighbors classification
### 	stats:
	-glm() for logistic regression
________________________________________

# 📂 Dataset
•	Source: Kaggle - Hotel Reservations Classification Dataset
•	Observations: 36,275
•	Features: 19 columns (11 used after preprocessing)
•	Response Variable: booking_status
	-"Canceled"
	-"Not_Canceled"
Predictors Used
•	no_of_adults
•	no_of_children
•	no_of_weekend_nights
•	no_of_week_nights
•	type_of_meal_plan (categorical)
•	room_type_reserved (categorical)
•	lead_time
•	arrival_month (categorical)
•	market_segment_type (categorical)
•	avg_price_per_room
•	no_of_special_requests
Dropped Features & Rationale
•	Booking ID — unique identifier, no predictive power
•	Required car parking space — low variance, weak correlation
•	Arrival year — single/few values
•	Arrival date — redundant with arrival month
•	Repeated guest — imbalance in distribution
•	No of previous cancellations — not representative for most customers
•	No of previous bookings not canceled — similar to above
________________________________________
# 🛠 Data Preprocessing
•	Checked for missing values — none found
•	Converted arrival_month numeric (1–12) → categorical (Jan–Dec)
•	Removed irrelevant columns
•	Split dataset:
	-Training set: 29,000 observations (~80%)
	-Test set: 7,275 observations (~20%)
•	Scaled numeric predictors for KNN to ensure fair distance calculations
________________________________________
# 📊 Exploratory Data Analysis (EDA)
Key Insights
•	Seasonality: Aug–Oct had the highest bookings.
•	Room Preferences: Room Type 1 dominated reservations.
•	Guests: Most bookings had 2 adults, no children.
•	Special Requests: Bookings with at least 1 special request were more often canceled.
•	Lead Time: Longer lead times were associated with higher cancellations.
•	Meal Plans: Meal plan 1 was most common.
•	Market Segments: Online bookings formed the majority.
Example EDA Visualizations
•	Histograms for numeric features (lead time, price, nights)
•	Barplots for categorical variables (room type, market segment)
•	Boxplots comparing numerical predictors across booking status
________________________________________
# 🤖 Modeling Approach
Four models were tested, plus variations in LDA decision thresholds:
Model	                                   Description
Logistic Regression	                       Linear classifier using log-odds transformation
Linear Discriminant Analysis (LDA)	       Projects data to maximize class separation
Naive Bayes	                               Probabilistic model assuming feature independence
K-Nearest Neighbors (KNN)	               Classifies based on nearest neighbors in feature space

________________________________________
# 📈 Model Results
Model	       Accuracy	Precision	Recall	F1-Score
Logistic Reg.	79.81%	73.56%	    60.75%	66.55%
LDA	            79.08%	73.27%	    57.80%	64.62%
LDA (0.3)	    77.88%	63.82%	    76.42%	69.56%
LDA (0.4)	    79.22%	69.22%	    66.86%	68.02%
Naive Bayes	    76.36%	69.19%	    51.35%	58.95%
KNN (k=7)	    84.65%	79.43%	    72.27%	75.68%

# Key Findings
•	KNN performed best overall (Accuracy 84.65%).
•	LDA (0.3) gave the best recall (good for catching potential cancellations).
•	Precision focus → KNN was preferred to reduce false positives.
# Evaluation Criteria
•	Precision priority: Minimize false positives (predicting “Canceled” when it’s actually “Not_Canceled”).
•	Recall consideration: Useful if we want to capture as many true cancellations as possible.
•	Chosen Model: KNN for its superior precision, accuracy, and F1-score.
________________________________________
# 📦 Libraries Used
Data Handling
•	base R — Data loading, transformation, subsetting
Visualization
•	ggplot2 — Advanced bar charts, grouped plots
•	gridExtra — Plot arrangements
•	Base plotting (hist(), barplot(), boxplot())
Modeling
•	stats — Logistic Regression (glm())
•	MASS — Linear Discriminant Analysis (lda())
•	e1071 — Naive Bayes (naiveBayes())
•	class — K-Nearest Neighbors (knn())

________________________________________
# 🚀 Future Work
•	Include external datasets (weather, events, economic indicators)
•	Extend time coverage beyond 2018 for updated patterns
•	Explore tree-based and ensemble methods (Random Forest, Gradient Boosting)
•	Implement cost-sensitive learning to balance FP and FN based on business needs
•	Tune hyperparameters for Naive Bayes and KNN for potential improvements

________________________________________
# ⚙️ How to Run
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


