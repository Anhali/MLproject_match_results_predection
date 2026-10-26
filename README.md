## 1. Project Overview
The goal of this project is to predict the outcomes of English Premier League matches (Home Win, Away Win, or Draw) using historical data from 1992 to 2023. We trained and evaluated two machine learning models: **Logistic Regression** and **Random Forest**.
## 2. The Problem: The Challenge of Predicting Draws
In our initial modeling phase, we faced a significant challenge common in sports forecasting: **undetections or extremely poor prediction of 'Draw' matches** (Class 1).

- **The Cause:** Class imbalance. Home wins are historically the most frequent outcome in football (around 46%), whereas draws are less frequent (around 26%) and harder to define because they represent a lack of dominance from either side rather than distinct winning patterns.
- **The Consequence:** Standard models tended to ignore the 'Draw' class to maximize overall accuracy, resulting in exceptionally low recall for draws.

## 3. The Solution: Cross-Validation & Balanced Class Weights
To fix this issue and make our models robust, we implemented two key strategies:

1. **Class Weight Balancing:** We used `class_weight='balanced'` in our parameter grids. This penalizes the model more when it misclassifies the minority classes (Draws and Away Wins), forcing the estimators to learn patterns for all three outcomes instead of defaulting to the majority class.
2. **Stratified Nested Cross-Validation:** We utilized `StratifiedKFold` and `GridSearchCV` to ensure that every fold preserved the percentage of samples for each class. This robust validation approach verified that our performance improvements were consistent and not due to overfitting.

## 4. Final Results & Comparison

### Logistic Regression
- **Best Hyperparameters:** `{'C': 100, 'class_weight': 'balanced'}`
- **Accuracy:** 44%
- **F1-Scores:**
  - Away Win: 0.43
  - Draw: 0.16
  - Home Win: 0.57

### Random Forest (Optimized)
- **Best Hyperparameters:** `{'bootstrap': True, 'class_weight': 'balanced', 'max_depth': 6, 'min_samples_leaf': 2, 'min_samples_split': 8, 'n_estimators': 108}`
- **Accuracy:** 44%
- **F1-Scores:**
  - Away Win: 0.45
  - Draw: **0.27** (Significant improvement from 0.16)
  - Home Win: 0.54

## 5. Conclusion
While predicting football outcomes is notoriously difficult due to inherent randomness, addressing class imbalance through **balanced class weights** and verifying generalization via **nested stratified cross-validation** successfully allowed our Random Forest model to start recognizing and predicting 'Draw' outcomes effectively, raising the F1-score of the Draw class significantly.
```

4. Scroll down to the **Commit changes...** box at the bottom (or top-right).
5. Write a short commit message (e.g., `Update README with project report`).
6. Select "Commit directly to the `main` (or `master`) branch" and click the green **Commit changes** button.

Once completed, this report will immediately become the official homepage of your repository# Premier League Match Prediction Project Report

## 1. Project Overview
The goal of this project is to predict the outcomes of English Premier League matches (Home Win, Away Win, or Draw) using historical data from 1992 to 2023. We trained and evaluated two machine learning models: **Logistic Regression** and **Random Forest**.
!
