# Sales_Repository

## Introduction 
Sales forecasting is a crucial part of the financial planning of any retail operation. Forecasting is a selfassessment tool that uses past sales statistics to intelligently predict future performance (Sun, et al., 2008). This is essential for meeting the demands of consumers whilst controlling pricing and optimizing the use of inventory space, as holding excess inventory adds to overhead costs for a business.
   
### 1. Business Understanding
 A key challenge of modeling retail data is the need to make decisions based on limited history. Holidays and select major events that come once a year, and so does the chance to see how strategic decisions impacted the bottom line. In addition, the relationship of how markdowns (a reduction in the originally marked retail price of merchandise) affect sales not fully known. The goal is to use historical weekly sales data to develop a model that better understands consumer purchasing patterns so we can predict which departments will be affected by these occasional events and to what extent. By doing so, we hope to provide retailers with the knowledge to more efficiently optimize their shelving and inventory space. We would do so by using machine learning models that estimates future sales when provided with current data about relevant features.
   
### 2. Data Understanding
   The dataset (from Kaggle) consists of historical sales data for 45 stores located in different regions of the US between 2010 and 2012. The company runs several promotional markdown events throughout the year. These markdowns precede prominent holidays, the four largest of which are the Super Bowl, Labor Day, Thanksgiving, and Christmas. The training data consist of 421,570 records: 
   
   ● Sales_data-set.csv: sales data (2010-02-05 to 2012-11-01) from departments of all stores 
   
   ● Store_data-set.csv: type and size of the stores 
   
   ● Features_dataset.csv: additional data related to the stores and regions.
   
   It was necessary to combine the 3 datasets into a single dataframe prior to analysis. Below is a snapshot after merging the 3 datasets: 
   
![Merged_Dataframes](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/Merged_Data_Frames.png)

### 3. Data Preparation

We noticed that 1285 rows (out of 400000) have values less than 0 in weekly sales. One option was to replace these with the mean weekly sales. However, we have discarded these rows completely in our analysis assuming they are data entry errors. 

![Clean_Weekly_Sales](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/Weekly_sales_clean.png)

We converted the temperature from Farenheit to Celcius.

![Change_temperature](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/temperature_clean.png)

Values for all features were converted from ‘N/A’ to 0 using .fillna(0).
We converted the “Type” variable into categorical by :

![Change_Category](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/Category_Clean.png)

### 5. Visualization

## Total Sales vs Time
   The figure shows a scatter plot of the total sales vs time. We observe that sales generally follow the same pattern except for 2 spikes in the period, possibly due to seasonal variations or stores enhancing their sales channels.

![Scatter plot](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/Weekly_sales_scatter_plot.png)

More of the Visualization could be seen [here](https://github.com/Hasan557/Sales_Repository/blob/master/Data%20Analytics.pdf)

### 6. Modeling

### Linear Regression
   Linear Regression (LR) is one of the simplest models for machine learning. A multiple LR assumes linear relationships between the features and the target, then fits a line to the data that would result in the lowest residual sum of squared errors (Yan, 2009)x

The resulting accuracy is quite low:

![Linear_Regression](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/LR_Predictions.png)

![Linear_Regression](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/LR_Results.png)

This is due to LR’s inherent shortcomings. LR performs rather okay while dealing with features such as Size, where a single line could fit the data to some extent. However, when adding features that are categorical in nature, such as Dept, LR can’t perform well. The reason is that an increase in a categorical feature's value which is encoded by numerics (Store, Dept) doesn’t have any real meaning in the sense of that feature increasing, unlike continuous variables like Size. Knowing that a number of features are categorical (Dept, Store, Type, IsHoliday, week) and a single line cannot fit them well, we would expect the accuracy of the model to be low using Linear Regression.

### Time-Series Analysis
   A time-series is a series of data points indexed in time order. Time-series forecasting is the use of a model to predict future values based on previously observed values. Since linear regression provided us with poor results, we decided to use time-series modelling to improve our analysis (Hamilton, 1994).
   
![TS_Results](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/TS_results.png)

The predictive model has an R^2 score of 0.59. The residual distribution is centered around 0 with an STD of 0.07. (Further see in the code and report how building time series for individual stores could increase accuracy using external variables).

### Random Forests
   We have used “Random Forests” to predict the weekly sales for all stores. Random forests (RFs) are primarily used for classification and also regression (Breiman, 2001).
RFs are ensembles of decision trees (DTs), whose inputs are bootstraps of the training samples. The final RF prediction is the average of all of these DTs’ predictions for a given test sample (bootstrap aggregation). Since each DT has a different bootstrap set, the variance is reduced without affecting the bias. By using this form of aggregation, RFs generally have high accuracy (less overfitting, more robust to noise), but are less interpretable than single DTs.

![RF_Results](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/RF_Results.png)

The accuracy (94.94%) is high, but can be improved via backward feature elimination. The OOB score (0.97) is quite good as well. These results demonstrate that our model performs well enough.


### 5. Evaluation

![Results_Comparision](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/Results.png)

### Conclusion & Discussion

   In this project, we first explored the data, gaining some insight into possible connections between the features and weekly sales. We then analyzed these features from a statistical point of view to test the hypotheses we made about these connections. Later we used 3 different machine learning methods to predict the weekly sales, arriving at the conclusions below:

●	There is a strong positive correlation between holiday weekends and markdowns, which was expected as Markdowns are strategically planned before holidays.

●	There is also a strong positive correlation between weekly sales and the size of the store, which is consistent with our assumptions.

●	To our surprise, Temperature had little correlation with weekly sales. This may be explained by cultural factors that we did not anticipate due to the data being of US origin. Unlike in the UK, American customers predominantly drive to retail stores, so extreme cold/hot weather has little impact on sales.

●	RFs yield the highest accuracy.

●	Time series analysis is more effective if conducted on individual stores rather than an aggregation.


### Bayesian Model using score-based approach

The features were made categorical in order to use into Apache NatBeans (here)

![Results_Comparision](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/Bayesian_.png)

The Phase-3 graph is the result of score-based learning that modifies the graph from Phase-2 towards the path that maximizes the BIC score. SaiyanH uses a hill-climb method that explores neighbouring graphs in which an edge is reversed, removed, or added, and moves in the direction that increases the BIC score. Once the BIC score cannot be increased attempts are made to escape possible local maximum by performing TABU search. These steps are repeated until the TABU search cannot discover a graph with a higher BIC score. The product is a graph that enables full propagation of evidence by design.

![Results_Final](https://github.com/Hasan557/Sales_Repository/blob/master/Screenshots/Bayesian_Results.png)



## Further Research

Further work could be done on each 45 stores individually.Both time series and Random Forest could be used on each store. This could give better and more accurate results.

