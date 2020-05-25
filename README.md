# Sales_Repository

## Introduction 
 
   Sales forecasting is a crucial part of the financial planning of any retail operation. Forecasting is a selfassessment tool that uses past sales statistics to intelligently predict future performance (Sun, et al., 2008). This is essential for meeting the demands of consumers whilst controlling pricing and optimizing the use of inventory space, as holding excess inventory adds to overhead costs for a business (Guerts & Kelly, 1986).
   
## Hypothesis 
   To go forward with our analysis, we hypothesize that there are meaningful underlying dependencies between the features provided in the dataset, and that by training a model on these features, we would be able to reuse that model in production (i.e. given the features, the model estimates the result). Also, we assume that these underlying relations can be learned by the model. We will be using three methods (Linear Regression, Time-Series, Random Forests) and have the following intuitions: 
   
   ● The LR model might not perform as well as the others since it is very simple. 
   
   ● The Time-Series model would probably yield better results, since the problem is inherently timedependent. However ensemble methods (including RFs) are known to be quite powerful.
   
   ● To make a knowledge based graph using score-based approach to evaluate which variables provide cause-effect relationships between variables.
   
 ## Data Overview 
   The dataset (from Kaggle) consists of historical sales data for 45 stores located in different regions of the US between 2010 and 2012. The company runs several promotional markdown events throughout the year. These markdowns precede prominent holidays, the four largest of which are the Super Bowl, Labor Day, Thanksgiving, and Christmas. The training data consist of 421,570 records: ● Sales_data-set.csv: sales data (2010-02-05 to 2012-11-01) from departments of all stores 
   
   ● Store_data-set.csv: type and size of the stores 
   ● Features_dataset.csv: additional data related to the stores and regions 

