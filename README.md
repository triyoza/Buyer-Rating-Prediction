## Using CRISP-DM Methodology Classification Model to predict Buyer Rating in E-Commerce 
- A Final project in Sharing Vision Data Science Bootcamp by Triyoza Aprianda
## Introduction
CRISP-DM (The CRoss Industry Standard Process for Data Mining):
- Business Understanding
- Data Understanding
- Data Preparation
- Feature Engineering
- Modeling
- Evaluation
- Deployment (In this project only until the evaluation stage)
## Business Understanding
Divided into three that have been determined by the instructor:
- Business Objectives: A marketplace company wants to create a guideline containing tips for sellers on how to get a 5 rating from buyers.
- Model Objectives: Create a classification engine to determine whether a buyer gives a 5 rating to the purchased item (label 1) or a rating below 5 (label 0).
- Model Success Criteria (Recall > 0.6; Precision > 0.6; FPR < 0.45), The model created reaches or even exceeds the model success criteria. If not successful, select the model with the best performance.

## Data Understanding
### Data Description
Data used:
- 'model_development_set.csv', used for model development.
- 'back_testing_set.csv', used to test the model created and predict the 'label' column (buyer rating) because in this back_testing_set the 'label' column is hidden by the instructor
- The data 'model_development_set.csv' consists of 13645 rows and 40 columns or features with numeric, categorical, and datetime data types
#### Numeric Features

![numerik](https://user-images.githubusercontent.com/113491625/195153492-871d6ef0-326c-4fcb-96f8-1cbcb74b550d.PNG)
#### Categorical Features

![newww](https://user-images.githubusercontent.com/113491625/195238075-a17ac0b1-5a93-45e0-ab81-f3824dc27b1b.PNG)

#### Datetime Feature

![dtime beru](https://user-images.githubusercontent.com/113491625/195235458-85223345-b70c-48e9-bb94-72f487c1d8db.PNG)

## Exploratory Data Analysis (EDA)
### Numerical Features
#### Multivariate Numerical
One of the regplot with a high correlation

![regplot](https://user-images.githubusercontent.com/113491625/195235492-94246ed8-5985-4cc2-a4cd-446b645a7fb0.PNG)

#### Numeric-Label

![kkkk](https://user-images.githubusercontent.com/113491625/195237690-813f5d64-9ad9-494a-9c61-8d253bd01d35.PNG)

- From the resulting plots, in general, each numeric feature has a higher average value at label 0 (rating below 5).
- However, for the features 'price' and 'description length' the opposite is shown, having a higher average value at label 1 (buyer rating 5).

### Categorical features
Countplot and stacked barplot 

![count and stacked](https://user-images.githubusercontent.com/113491625/195235503-e58eb066-b03c-404f-b1be-24d8c72cbd4c.PNG)

From the bar plots and stacked bar plots shown, it can be seen that for each categorical feature, label 1 or rating 5 is superior for each category in the feature.

### Datetime Feature
From the datetime feature, the length of time for order processing can be identified by identifying the difference between datetime features, so that a column can be created in the form of the length of time required, as follows:

![dtmiee](https://user-images.githubusercontent.com/113491625/195238570-25838d02-5db7-4052-ba26-e6fee0be7659.PNG)

- Some plot results in the form of joint plot

![jointploat](https://user-images.githubusercontent.com/113491625/195235477-56bee122-c5c7-4fe0-b276-e2d935fa2244.PNG)

- The blue dots in the plot are more distant to zero, indicating a rating below 5 (label 0). This shows that the longer it takes the dominant rating given by the buyer is below 5.
- The orange-colored dots on the plot are more clustered near axis 0 which indicates a rating above 5 (label 1). Indicating that the faster the time taken the rating given by the buyer is generally below 5.

### Insights from EDA
- The numeric features for 'price' and 'description length' are unique in that the average value for these features is higher at a rating of 5 than below 5, unlike the other numeric features where the opposite is true.
- In categorical features, in each of the inner categories contained in the feature, there are more ratings of 5 than below 5, but the relationship is less clear.
- Of the three data types, the most influential on the rating is the datetime feature, which is the length of time taken to process the order. Where the longer the processing stage time, the more dominant the rating given by the buyer is below 5.

## Data Preparation and Engineering features
### Train Test Split
- Drop unnecessary features
- Perform a train test split:

![tts](https://user-images.githubusercontent.com/113491625/195228237-275526fa-4b0d-41d4-afda-7cb2700f8fdf.PNG)

### Missing Value Handling
Percentage of missing values for each feature

![mv](https://user-images.githubusercontent.com/113491625/195228246-6b00a3b1-cfc1-47cf-bdcc-ae95a04569f7.PNG)

Handling:
- Simple imputer (strategy = median) for numeric features
- Simple imputer (strategy = most_frequent) for categorical features

### Transformation
- Scaling for numeric features
- One hot encoder for categorical features

### Feature Selection
- Multicollinearity Reduction
- Mutual Information

### Testing Set
Perform all steps: Missing value handling, transformation, and feature selection to the testing set as done to the train set without re-fitting.

## Modeling
- Determining the model
- Hyperparameter tuning using GridSearchCV
- Getting the best parameters
- Fitting to a training set
- Check performance (train and test)
- Performed until finding a model that meets the criteria or the best performance

### Final classification model
- The classification models made are Logistic Regression, Decision Tree, Random Forest, Ada boost, and XGBoost.
- XGboost was chosen because it has the best performance.
- Hyperparameter

![hyp](https://user-images.githubusercontent.com/113491625/195229327-a7bebee6-87d5-493c-916a-e345ee107c26.PNG)

- Final XGBoost performance

![performance](https://user-images.githubusercontent.com/113491625/195229397-73b55262-32ce-4b4e-988d-7ddb958ade80.PNG)

Because it has exceeded the model success criteria specified at the beginning, the final XGboost model is used to predict the label column in 'backtesting_set'

## Evaluation
- Using the data 'back_testing_set.csv which has been transformed and selected following what was done to the training set
- Obtained a predicted label column containing 0 and 1 (0: buyer rated below 5, 1: buyer rated 5), then made it into its column and extracted it to a CSV file

![eval](https://user-images.githubusercontent.com/113491625/195231539-c4a1a7ad-c223-441d-97e4-8daeb584f2cf.PNG)

### Closing
- After submission, the instructor compares the obtained label column with the original hidden label column.
- The performance obtained for the backtesting set of the model I made is: 
Recall 0.68,
Precision 0.68,
FPR 0.45

# ![WhatsApp Image 2022-10-12 at 08 56 53](https://user-images.githubusercontent.com/113491625/195231126-4d58b3a0-c050-4bf4-bbd2-bb0620962ad9.jpeg)

Thank you