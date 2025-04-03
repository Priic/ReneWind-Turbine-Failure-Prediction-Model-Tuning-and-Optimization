# ReneWind-Turbine-Failure-Prediction-Model-Tuning-and-Optimization

![windturbine](https://github.com/user-attachments/assets/7cf4fbec-abc3-43d5-847a-f4d6ead38367)

### Business Context

Renewable energy sources play a crucial role in the global energy mix, with `wind energy` being one of the most developed and widely adopted technologies worldwide. The U.S. Department of Energy promotes `predictive maintenance` to enhance operational efficiency.<br>
Predictive maintenance uses sensor information and analysis methods to measure and predict degradation and future component capability. The idea behind predictive maintenance is that failure patterns are predictable and if component failure can be predicted accurately and the component is replaced before it fails, the costs of operation and maintenance will be much lower.

`ReneWind `is a renewable energy company providing `machine learning solutions through predictive modeling` and analysis. Using sensor data from wind turbines, the company aims to identify failure patterns and predict component degradation before breakdowns occur, reducing operational costs.
The dataset consists of **`40 predictors and 1 target`** variable, with **`20,000 training observations`** used for model development and **`5,000 test observations`** for performance evaluation of the final model. All the variables present are **`ciphered versions of sensor data`** related to various environmental factors (temperature, humidity, wind speed, etc.) or and wind turbine components (gearbox, tower, blades, brakes). 

**`Model building Approach:`**

I have performed **`Exploratory Data Analysis (EDA)`** and **`Data Preprocessing (handling missing values and feature scaling)`**, before building multiple classification models:<br>

1. Applied **`Cross validation(CV StratifiedKFold)`** and built 7 classification model with **`original data`**.
2. To addressed data imbalance alongside cross-validation (CV), built another 7 classification model **`with oversampled data(SMOTE method)`** and,
3. Another7 classification model using **`Random Undersampler method `**.
4. Selected the best-performing model and **`hyper-tuned`** them (**`using grid-serachCV and randomSearch`**).
5. Deployed the final model in a **`standardized pipeline (ImbPipeline)`**, automating preprocessing, feature transformation, and training to ensure consistency, prevent data leakage.
   
***`Classification model used are:`** (`logistic regression, decision trees, random forest, bagging classifier and boosting methods(Adaboost,Xgboost and GBM)`* 

## Objective

Our `goal` was to create a model which can `identify failures early`, so that the generators could be repaired before failing/breaking to reduce the overall maintenance cost. As we know the cost of repairing a generator is much lower than the `cost of replacing(FN) `it, and the cost of inspection is even lower, so the `main focus `on building the model was to `maximized the Recall `to `minimizing` the chances of `false negatives` and avoid unexpected failures.

The nature of predictions made by the classification model will translate as follows:

- **`True positives (TP)`** are failures correctly predicted by the model. These will result in repairing costs.
- **`False negatives (FN)`** are real failures where there is no detection by the model. These will result in replacement costs.
- **`False positives (FP)`** are detections where there is no failure. These will result in inspection costs.

It is given that the cost of repairing a generator is much less than the cost of replacing it, and the cost of inspection is less than the cost of repair.
“1” in the target variables should be considered as **`failure`** and “0” represents **`No failure`**.

## Data Description
- The data provided is a **`transformed version of original data`** which was collected using sensors.
- `Train.csv` - To be used for training and tuning of models.
- `Test.csv `- To be used only for testing the performance of the final best model.
-  Both the datasets consist of `40 predictor variables and 1 target` variable
