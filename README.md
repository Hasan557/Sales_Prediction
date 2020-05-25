# Sales_Repository

## Introduction 
Sales forecasting is a crucial part of the financial planning of any retail operation. Forecasting is a selfassessment tool that uses past sales statistics to intelligently predict future performance (Sun, et al., 2008). This is essential for meeting the demands of consumers whilst controlling pricing and optimizing the use of inventory space, as holding excess inventory adds to overhead costs for a business (Guerts & Kelly, 1986).
   
### 1. Business Understanding
 A key challenge of modeling retail data is the need to make decisions based on limited history. Holidays and select major events that come once a year, and so does the chance to see how strategic decisions impacted the bottom line. In addition, the relationship of how markdowns (a reduction in the originally marked retail price of merchandise) affect sales not fully known. The goal is to use historical weekly sales data to develop a model that better understands consumer purchasing patterns so we can predict which departments will be affected by these occasional events and to what extent. By doing so, we hope to provide retailers with the knowledge to more efficiently optimize their shelving and inventory space. We would do so by using machine learning models that estimates future sales when provided with current data about relevant features.
   
### 2. Data Understanding
   The dataset (from Kaggle) consists of historical sales data for 45 stores located in different regions of the US between 2010 and 2012. The company runs several promotional markdown events throughout the year. These markdowns precede prominent holidays, the four largest of which are the Super Bowl, Labor Day, Thanksgiving, and Christmas. The training data consist of 421,570 records: 
   
   ● Sales_data-set.csv: sales data (2010-02-05 to 2012-11-01) from departments of all stores 
   
   ● Store_data-set.csv: type and size of the stores 
   
   ● Features_dataset.csv: additional data related to the stores and regions.
   
![Merged_Dataframes](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/Merged_Data_Frames.png)

### 3. Data Preparation

![Clean_Weekly_Sales](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/Weekly_sales_clean.png)

![Change_temperature](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/temperature_clean.png)

![Change_Category](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/Category_Clean.png)


### 4. Modeling

## Linear Regression
## Description
   Linear Regression (LR) is one of the simplest models for machine learning. A multiple LR assumes linear relationships between the features and the target, then fits a line to the data that would result in the lowest residual sum of squared errors (Yan, 2009)
   

## Time-Series Analysis
## Description
   A time-series is a series of data points indexed in time order. Time-series forecasting is the use of a model to predict future values based on previously observed values. Since linear regression provided us with poor results, we decided to use time-series modelling to improve our analysis (Hamilton, 1994).

## Random Forests
## Description
   We have used “Random Forests” to predict the weekly sales for all stores. Random forests (RFs) are primarily used for classification and also regression (Breiman, 2001).
RFs are ensembles of decision trees (DTs), whose inputs are bootstraps of the training samples. The final RF prediction is the average of all of these DTs’ predictions for a given test sample (bootstrap aggregation). Since each DT has a different bootstrap set, the variance is reduced without affecting the bias. By using this form of aggregation, RFs generally have high accuracy (less overfitting, more robust to noise), but are less interpretable than single DTs (Zhao and Zhang, 2008).




