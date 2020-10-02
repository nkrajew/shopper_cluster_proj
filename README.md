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
"The values of these features are derived from the URL information of the pages visited by the user and updated in real time when a user takes an action, e.g. moving from one page to another."

- Administrative, Informational, Product_Related: Number of times this type of page was visited by the shopper in this session.
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

