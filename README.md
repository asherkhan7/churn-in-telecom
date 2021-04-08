# Churn in Telecom
 
Modeling on churn telecom data set
 
## Business Case
 
I will use different models to predict which telecom clients are most likely to discontinue their service. I will then compare the models and examine the most useful model for this case. My clients are cable, telegraph, telephone, or broadcasting companies. 
 
## Data Analysis
 
After turning all the data into numerical data types, I looked for NAN values but there were none. After that I looked for correlations and found 99% correlations between redundant columns. I dropped the total day charge, total eve charge, total intl charge, total night charge, and the number vmail messages columns which didn't alter the data. 
 
With the data cleaned, I start to analyze it. The following scatter plots show the binary nature of the data.
![scatterplots](/figures/scatter-plots.png)
 
The following histograms show us which of our variables are normally distributed. Almost all of them seem to be normally distributed. 
![histograms](/figures/histogram-plots.png)
 
## Modeling
 
For the modeling I first defined the function 'evaluate' which took in the model, test and training columns, and the test and training 'churn' column. The first model I fitted was the K-Nearest Neighbors in which I first got dummies (which didn't really make much of a difference). I then conducted the train test split and then normalized the data by transforming the train and test sets after train test split to avoid information leaking. I then fit the model and evaluated it using the function.
 
I then repeated the process with the following models:
- Decision Tree Regression
- Decision Tree Classification
- Bagged Tree
- Random Forest
- Ada Boost
- Gradient Boosting
- XGB Classifier 
 
After I ran the models above, I chose a few which I wanted to tune even further. Firstly for KNN I attempted to find the optimal number of neighbors to use for the classifier, and I managed to improve F1 from 0.48 to 0.5, which has its optimal value at k=1. Still less than I would like F1 to be, but it is an improvement.
- I then did GridSearch tuning for Decision Tree. I was able to increase precision, recall, f1-score, and accuracy.
- I also did GridSearch tuning for Random Forest Classifier. The precision dropped from 100% to 96%. However, it significantly increased recall, f1-score and accuracy from 42%,59%,92% to 69%,80%,95% respectively. 
- I also did Gridsearch for XGB Classifer. Once again, precision dropped from 95% to 94%. However recall, f1-score and accuracy from 71%,81%,95% to 75%,84%,96% respectively.
 
## Conclusions
 
KNN-
Precision: 40%
F1-Score: 70%
Recall: 51%
Accuracy: 80%
 
Regression Tree-
Precision: 65%
F1-Score: 73%
Recall: 69%
Accuracy: 90%
 
Decision Tree-
Precision: 74%
F1-Score: 80%
Recall: 77%
Accuracy: 93%
 
Bagged Tree-
Precision: 76%
F1-Score: 80%
Recall: 78%
Accuracy: 93%
 
Random Forest-
Precision: 60%
F1-Score: 82%
Recall: 69%
Accuracy: 89%
 
Random Forest (After Tuning)-
Precision: 82%
F1-Score: 79%
Recall: 80%
Accuracy: 94%
 
AdaBoost-
Precision: 60%
F1-Score: 61%
Recall: 61%
Accuracy: 88%
 
Gradient Boosting-
Precision: 85%
F1-Score: 77%
Recall: 81%
Accuracy: 94%
 
XG Boost-
Precision: 85%
F1-Score: 77%
Recall: 81%
Accuracy: 94%
 
XG Boost (After Tuning)-
Precision: 93%
F1-Score: 78%
Recall: 85%
Accuracy: 96%
 
Considering the above results, XG Boost after tuning and Random forest after tuning seem to be the most reliable models to run predictions. 
 
From the following chart, it can be seen that the top columns of importance to churn are: international Plan, customer service calls, total day mins.
![feature-imp-tree_clf](/figures/feature-imp-tree_clf.png)
 
Based on the data it seems that customers with international plans and the ones making the most customer service calls are those who are most likely to discontinue service the most. 
