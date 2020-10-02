# Shopper Clustering and Intent to Purchase: Project Overview
- Created a random forest model to predict (accuracy=0.90, precision=0.76) whether a shopper would be a purchaser.
- Performed a separate cluster analysis to designate shoppers as "target", "general", and "uninterested" which could be used as one-hot features in a predictive model on future data.
- Created and solved a business case for this type of e-commerce data
- Engineered two new features from the raw data.
- Performed PCA on the input features to reduce the dimensionality of the data until it explained 95% of the variance.
- Optimized Logistic Regression and Random Forest models using RandomizedSearchCV.

## Code and Resources Used
**Python Version:** 3.7\
**Packages:** pandas, numpy, sklearn, seaborn, matplotlib\

## Data Sources
Kaggle - https://www.kaggle.com/roshansharma/online-shoppers-intention

## Data Meanings
Below are the data meanings derived from the descriptions given by the uploader of the data: 
- Administrative, Informational, Product Related: Number of times this type of page was visited by the shopper in this session.
- Administrative Duration, Informational Duration, Product Related Duration: total time spent on these pages by the shopper in this session.
- Bounce Rate: the percentage of visitors who enter the site from that page and then leave ("bounce") without triggering any other requests the analytics server during that session.
- Exit Rate: Calculated as for all pageviews to the page, the percentage that were the last in the session.
- Page Value: The average value for a web page that a user visited before completing an e-commerce transaction.
- Special Day: Indicates the closeness of the site visiting time to a specific special day (e.g. Valentine's Day) in which the sessions are more likely to be finalized with transaction. The value of this attribute is determined by considering the dynamics of e-commerce such as the duration between the order date and delivery date
  - For example, for Valentine’s day, this value takes a nonzero value between February 2 and February 12, zero before and after this date unless it is close to another special day, and its maximum value of 1 on February 8.
- Operating System, Browser, Region, Traffic Type: Categorical variables (though they are numeric they were likely label encoded)
- Visitor type: A categorical variable stating whether the shopper is a Returning Visitor or New Visitor
- Weekend: A boolean indicating whether the visit was made on the weekend
- Month: A categorical variable for which month of the year the visit was made (e.g. 'Feb' for February)

## Cluster Analysis
I used K-Means coupled with the elbow-method (to determine K) for multiple combinations of features. Below are some images that highlight that analysis.

![alt text](https://github.com/nkrajew/shopper_cluster_proj/blob/master/images/cluster_image_resize.PNG "clustering image")

## Data Prep
Before building models I had to prep the data in multiple ways.
- Turned categorical featuers into dummy varaibles using pandas.get_dummies.
- Truned binary categorical variables into 1 or 0 using Label Encoder.
- Standardized numerical features using StandardScaler.
- Binarized the target variable using Binarizer.
- Split the data into test and train sets with test size = 0.2.
- Created an alternate dimension-reduced dataset using PCA

## Model Building
I built two models for this project: Logistic Regression and Random Forest.
- Before using the data in the models, I standardized the numerical features using StandardScaler.
- For the Logistic Regression model I also derived its inputs using PCA.
- I used RandomizedSearchCV to find the optimal hyperparameters for the Random Forest model.

## Model Performance
I chose to evaluate the models on their F1 score since the target was imbalanced. Additionally, it fit with my business case that I walked through at the end of my analysis. It was important to the business case to reduce False Positives and False Negatives (have high Precision and Recall). 

![alt text](https://github.com/nkrajew/shopper_cluster_proj/blob/master/images/performance.PNG "Performance")

## Summarized Use Case
**Scenario:** Our marketing team has discovered that through targeted advertising efforts they can increase consumer spend (increase revenue from e-commerce shoppers that make a purchase). They want to leverage this information to increase company profits. Executive management asked if we could build a model that could effectively target consumers so that our marketing dollars are being used efficiently. Does our random forest model satisfy this request?

**Strategy:** With our trained random forest model, our new strategy will be to market only to predicted purchasers. Our model has shown to predict about 11% of shoppers as purchasers. Of those 11%, the model correctly classified 76% of them as purchasers (this is the precision of the model).

**Results:** \
Spend = 5 dollars 10,000 shoppers 11% = 5,500 dollars \
Reveune Lift = 11% 10,000 76% * 10 = 8,360 dollars \
Profit = 8,360 - 5,500 = 2,860 dollars (profit)

**Recommendations:** It is recommended that the marketing team pursue targeted ads using the random forest model. The model will lead to an increase in profits of 2,860 dollars.

## Considerations
**Can we do better?** \
If the model performed perfectly (100% True Positive Rate with 0% False Positives), the largest profit that could be realized is 8,000 dollars. Therefore, our model was able to realize about 36% of the potential profits from targeted ads. If the model can be further fine-tuned then even greater profits could be realized.
**Potential Improvement Opportunities** 
- Transform the data to be Gaussian before using a linear model.
- Check the data for collinearity before using in the models.
- Use LASSO, Ridge, or ElasticNet when forming a linear model.
- Try alternative forecasting models (XGB, SVM, etc.).
- Find more features to engineer by researching ecommerce more or talknig to a domain expert
