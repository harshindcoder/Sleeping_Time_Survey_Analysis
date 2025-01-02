# Sleeping_time_analysis

## Overview
The goal of the project is to explores how lifestyle factors influence sleep patterns using a dataset that includes variables such as age, meals/day, physical illness, screen time, blue light filter usage, smoking/drinking habits, gender, exercise routines, beverages consumed, sleep direction, and sleep time.

Research shows that adults need at least seven hours of sleep for optimal health. Insufficient sleep is linked to cognitive decline, heart disease, and diabetes. Factors like screen time, alcohol consumption, and exercise routines directly impact sleep quality. Exposure to blue light disrupts the circadian rhythm, and exercise can improve sleep quality, while alcohol consumption delays sleep onset. Additionally, sleep direction, based on Vaastu Shastra, suggests that lying with the head pointed southward can positively affect sleep patterns.

By analyzing this data, we aim to identify key lifestyle patterns that affect sleep duration and quality, providing actionable insights to improve health and well-being.

## Project Understanding
This research aims to identify lifestyle factors—such as screen time, exercise, alcohol consumption, beverages, and sleep direction—that affect sleep quality and duration. By analyzing these factors, we seek to predict sleep patterns and provide actionable insights to improve sleep health and overall well-being.

## Data Collection
The data for this project was gathered from two sources. The first dataset was collected through a survey conducted via a Google Form, where participants self-reported information about their age, gender, daily habits, physical health, screen time, exercise routines, beverage consumption, and sleep patterns.

The second dataset was obtained from a third-party source, providing additional records to complement and expand the analysis. Both datasets were combined to create a comprehensive dataset, enabling a deeper exploration of the factors influencing sleep quality and duration.

## Data Understanding
This project uses a dataset called `sleep_analysis_data.csv` and `sleep_analysis_2_data.csv`, which have been combined to create a comprehensive dataset of 92 entries representing various self-reported lifestyle factors affecting sleep. The dataset contains 11 columns of data related to sleep patterns and associated behaviors:

| Column Name            | Type     | Description                                                |
|------------------------|----------|------------------------------------------------------------|
| Age                    | int64    | The age of the individual                                  |
| Gender                 | object   | The gender of the individual (male, female, other)         |
| meals/day              | object   | The number of meals consumed per day                       |
| physical illness       | object   | Whether the individual has any physical illness            |
| screen time            | object   | The daily amount of time spent on screens (e.g., phone, computer) |
| bluelight filter       | object   | Whether the individual uses a blue light filter on their devices |
| sleep direction        | object   | The direction the individual sleeps in (based on Vaastu Shastra) |
| exercise               | object   | The individual's frequency of physical exercise |
| smoke/drink            | object   | Whether the individual smokes or drinks alcohol            |
| beverage               | object   | The type of beverage consumed (coffee, tea, or none)       |
| sleep time             | float64  | The number of hours the individual sleeps per night        |

Each row represents data from a different individual, providing insights into how various lifestyle factors affect sleep quality and duration. This dataset will be analyzed to uncover patterns and correlations that can help improve sleep health and well-being.

## Data Cleaning
The **data cleaning** process involved multiple steps to prepare the dataset for analysis. Initially, libraries like `pandas` and `numpy` were imported to handle data operations.  

#### Key Cleaning Steps:
1. **Checking Data Types and Null Values**:  
   - Verified data types and identified missing values.  
   - Ensured all columns had consistent formats.  

2. **Feature Engineering**:  
   - Merged 'Tea' and 'Tea and Coffee both' columns for combined beverage preferences.  
   - Converted categorical variables into numerical values using encoding techniques.  

3. **Column Standardization**:  
   - Renamed columns for consistency and readability.  
   - Rearranged columns to improve data organization.  

4. **Unnecessary Columns Dropped**:  
   - Removed irrelevant columns such as 'Gender', 'sleep direction', and 'exercise' based on project requirements.  

5. **Saving Cleaned Data**:  
   - Saved the cleaned dataset as 'clean_data.csv' for further analysis.  

The final dataset contains 92 entries with 11 columns, each representing attributes related to demographics, lifestyle habits, and sleep patterns.

### Exploratory Data Analysis (EDA)

The EDA section examines the collected data to identify patterns, trends, and relationships among variables. Key observations include:  

1. **Demographics**: The dataset contains a balanced distribution of males and females, reducing gender bias. However, the sample size for other genders is limited, which may affect predictions.  
2. **Age Distribution**: Most participants are young adults, potentially influencing generalizability to older age groups.  
3. **Sleep Direction and Exercise**: All sleep directions are adequately represented, enabling meaningful predictions related to orientation. Exercise data highlights varied levels of activity among participants.  
4. **Lifestyle Patterns**: The dataset covers screen time, beverage consumption, and smoking/drinking habits, which are essential for analyzing sleep time impacts.  
5. **Health and Habits**: While most participants report being healthy, this could lead to biased interpretations regarding physical illness.  

Visualizations such as count plots, histograms, and correlation heatmaps are used to highlight trends and dependencies between variables.

## Regression Analysis

### Logistic Regression

We chose to apply Logistic Regression for this analysis because we aimed to predict whether an individual would get adequate sleep (7 hours or more) based on various lifestyle factors. Since the target variable (sleep time) is binary (1 for 7 or more hours, and 0 for less than 7 hours), logistic regression is an appropriate model. Logistic regression is particularly useful for classification tasks like this, where the goal is to estimate the probability of an event occurring, and it works well even with binary outcomes.

#### Model Training and Test Results
The dataset was split into training and testing sets, with 70% of the data used for training and 30% for testing. The logistic regression model was trained on the training set and then evaluated on both the training and test sets. The evaluation metrics for both the training and test datasets are as follows:

**Training Results**:
- Accuracy: 87.5%
- Precision: 88.64%
- Recall: 92.86%
- F1 Score: 90.70%

The training results show that the model performs well in predicting whether an individual gets enough sleep. With high precision and recall, the model effectively identifies both true positives (individuals getting enough sleep) and true negatives (individuals not getting enough sleep).

**Test Results**:
- Accuracy: 85.71%
- Precision: 83.33%
- Recall: 93.75%
- F1 Score: 88.24%

The test results also show strong performance, with a slight drop in accuracy and precision compared to the training set. However, the recall remains high, indicating that the model is particularly good at identifying individuals who do get enough sleep. This suggests the model's ability to generalize well to unseen data.

**ROC Curve and Insights**
The Receiver Operating Characteristic (ROC) Curve is a valuable tool for assessing the performance of a binary classification model. It illustrates the tradeoff between the true positive rate (sensitivity) and the false positive rate (1 - specificity) across different thresholds. The area under the curve (AUC) provides a single metric that summarizes the model's ability to distinguish between the classes.

**ROC Curve for Training Data**:
The ROC curve for the training set has a high AUC value, indicating that the model is good at differentiating between individuals who get enough sleep and those who do not. The curve's steep ascent shows a high true positive rate with a low false positive rate, further validating the model's strong performance on the training data.

**ROC Curve for Test Data**:
The ROC curve for the test set is also strong, with an AUC indicating the model retains its ability to classify accurately. The model's ability to distinguish between the classes remains effective even on the test data, demonstrating its generalizability.

## Insights:
**Key Features**: The coefficients from the logistic regression model reveal which lifestyle factors are most influential in determining sleep patterns. Factors such as "no beverage" consumption, "north" and "south" sleep directions, and "smoke/drink" habits have higher positive coefficients, suggesting they significantly impact whether a person gets adequate sleep. In contrast, "coffee" consumption has a strongly negative coefficient, indicating it might be a barrier to getting enough sleep.

**Model's Predictive Power**: The logistic regression model performed well overall, with high accuracy, precision, recall, and F1 scores, and the ROC curves further validated the model's effectiveness. This suggests that lifestyle factors such as exercise, screen time, and beverage consumption can be strong predictors of sleep quality, providing valuable insights for improving sleep health.

**Generalization**: While the model performs well on both the training and test sets, there is a slight decrease in precision on the test set, suggesting that some predictions are more challenging. This is typical in real-world data, where the model may encounter new patterns not seen during training.
