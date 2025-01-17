# Supervised Linear Regression Analysis
Colab notebook to test linear models (Ridge, Lasso, Elastic Net)

## **Dataset Summary**

_Domain:_ Obesity dataset from Kaggle.

_Objective:_ Predict likelihood of Obesity and understand which features impact Obesity.

_Key Features:_ **Obesity (target variable)**, Weight, Height, Age, Family_history, CAEC_Frequently, etc,.

This dataset includes data for the estimation of obesity levels in individuals from the countries of Mexico, Peru and Colombia, based on their eating habits and physical condition. The data contains 17 attributes and 2111 records, the records are labeled with the class variable NObesity (Obesity Level), that allows classification of the data using the values of Insufficient Weight, Normal Weight, Overweight Level I, Overweight Level II, Obesity Type I, Obesity Type II and Obesity Type III.

## **Objectives**

Testing our hypothesis: Age, Height and Weight will contribute most to obese patients.

Steps

1. Interpret and visualize key features/data.

2. Remove/transform features (Age and NCP).

   2a. Performed Log, Cube Root, Yeo-Johnson, Quantile (normal), and Winsorized transformations on skewed features to determine the best approaches.
3. Encode dataset.

4. Test for multicollinearity and drop/combine redundant data.

5. Determine feature correlation strength.

6. Begin modeling and attempt to get the highest possible R2 score using Ridge, Lasso and Elastic Net models + optimization techniques like Bayesian Optimization.

7. Present key findings and recommended next steps.

## Insights and key findings

Model scores suggest moderate accuracy, capturing about 47% of the variance. On average, predictions might misclassify by one or two obesity levels (MAE), with some larger errors present (RMSE). Given the limitations, it is worth exploring other models that are more suitable for handling the ordinal nature of the target variable.

### **Optimization Results Summary**

After running our models through Bayesian Optimization, we have the following results:

<ins>Ridge:</ins>

Best Parameters: {'model__alpha': 23.03, 'selective_poly__degree': 3, 'selective_poly__interaction_threshold': 0.054, 'feature_selection__k': 24}
Test R²: 0.4515

<ins>Lasso:</ins>

Best Parameters: {'model__alpha': 0.0114, 'selective_poly__degree': 3, 'selective_poly__interaction_threshold': 0.050, 'feature_selection__k': 20}
Test R²: 0.4742

<ins>ElasticNet:</ins>

Best Parameters: {'model__alpha': 0.0171, 'selective_poly__degree': 3, 'selective_poly__interaction_threshold': 0.061, 'feature_selection__k': 20}
Test R²: 0.4760

<ins>Pre-skew transformations</ins>

Ridge Test R²: 0.4344 / 
Lasso Test R²: 0.4673 / 
ElasticNet Test R²: 0.4708

<ins>Post-skew transformations</ins>

Ridge Test R²: 0.4324 / 
Lasso Test R²: 0.4710 /
ElasticNet Test R²: 0.4715

<ins>Model Performance without polynomial features</ins>

Ridge Test R²: 0.3753 / 
Lasso Test R²: 0.4250 / 
ElasticNet Test R²: 0.4171

<ins>Full Model Training</ins>

Ridge Test R²: 0.4324 / 
Lasso Test R²: 0.4710 / 
ElasticNet Test R²: 0.4715 

## Next Steps

Despite rigorous testing, data manipulation, and optimization, our models achieved an average R² of approximately 47% on the best-performing runs, occasionally reaching up to 52% for outlier models. The dataset presented unique challenges that limited performance under linear modeling approaches. As seen in our residuals plots, our linear models don't fit the complex categorical features very well.

**Our next steps are to:**

Augment the dataset with synthetic data to improve model training.
Explore flexible modeling approaches, as the dataset's complexity suggests non-linear models (e.g., Ordinal Regression or Classification models) may yield better performance. Linear models were used here to align with course requirements.
Develop a more robust feature tracking system to maintain clear mappings of original feature names during transformation and handling processes.
Our goal is to achieve 90% predictive accuracy by addressing these challenges in future iterations.
