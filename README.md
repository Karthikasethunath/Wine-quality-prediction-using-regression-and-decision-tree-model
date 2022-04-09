# Wine-quality-prediction-using-regression-and-decision-tree-model  
## Introduction
Modelling complex human taste is a difficult step in wine company. This dataset was created, using red wine variants of the Portuguese “Vinho Verde” wine. The inputs include objective tests (e.g. PH values) and the output is based on sensory data (median of at least 3 evaluations made by wine experts). Each expert graded the wine quality between 0 (very bad) and 10 (very excellent).
## Problem Formulation
I have chosen the dataset from Kaggle website[1]. The dataset consists of 1600 data points. Each data point is features that determine wine’s quality. There are 11 independent variables, all are numeric:  
1.	fixed acidity- most acids involved with wine or fixed or non-volatile (do not evaporate readily).  
2.	volatile acidity- the amount of acetic acid in wine, which at too high of levels can lead to an unpleasant, vinegar taste.  
3.	citric acid-found in small quantities, citric acid can add 'freshness' and flavour to wines.  
4.	residual sugar - the amount of sugar remaining after fermentation stops, it's rare to find wines with less than 1 gram/litre and wines with greater than 45 grams/litre are considered sweet.  
5.	chlorides-the amount of salt in the wine.  
6.	free sulphur dioxide-the free form of SO2 exists in equilibrium between molecular SO2 (as a dissolved gas); it prevents microbial growth and the oxidation of wine. 
7.	total sulphur dioxide-amount of free and bound forms of S02; in low concentrations, SO2 is mostly undetectable in wine, but at free SO2 concentrations over 50 ppm, SO2 becomes evident in the nose and taste of wine.  
8.	density- the density of water is close to that of water depending on the percent alcohol and sugar content.  
9.	pH- describes how acidic or basic a wine is on a scale from 0 (very acidic) to 14 (very basic); most wines are between 3-4 on the pH scale.  
10.	sulphates- a wine additive which can contribute to sulphur dioxide gas (S02) levels, which acts as an antimicrobial and antioxidant.  
11.	alcohol  
Output variable (based on sensory data):  
12.  quality (score between 0 and 10)  
I will define 2 new categories for the "quality" column. If quality > 5 then category will be "good" or 1, otherwise "average" or 0. 
It’s clear from the below image that we have more good quality wine in our dataset.
![sec(1)](https://user-images.githubusercontent.com/71560738/162576304-96cc63fa-e0e6-47f9-bcfb-b9bee28e2499.png)
![sec(2)](https://user-images.githubusercontent.com/71560738/162576311-2baee1e2-4940-4429-81a3-8425c5b4250b.png)
![sec(3)](https://user-images.githubusercontent.com/71560738/162576312-c7fa41c2-6c3f-4fab-97f9-70629295fc3d.png)
## Methods
Initially, exploratory data analysis was carried out. There weren’t any missing values in the dataset. For selecting the important features, I made use of the correlation chart with the help of seaborn package. None of the features were correlated to the label, quality. Therefore, I chose the features focusing on all factors that could affect the quality of wine.
### Linear Regression
![sec(4)](https://user-images.githubusercontent.com/71560738/162576391-33e3011d-e25d-4695-a7cc-8a46a5ac5481.png)
Our objective is to create a model using the above-mentioned features to predict the wine quality. Since our label is binary (0 or 1), it is ideal to use logistic regression instead of linear regression so as to get a probabilistic value. Here we are interested in knowing the probability if the wine is good or bad, which is a value between 0 and 1. If we use Linear regression the model will be trained to get absolute values which might fall outside the range 0 and 1. So I fit the model using Sklearn package.
Here I use Logistic loss instead of Mean squared error, to measure the performance of the model. The reason being, Y is a non-linear function (sigmoid function) and if we put this in MSE equation it will give us a non-convex graph. Hence gradient descent approach to find global minima in this graph will create complications. Therefore, I stick with log loss.
![sec(5)](https://user-images.githubusercontent.com/71560738/162576404-50619e99-359f-474c-a9ff-7e72b4a4406b.png)  
Before fitting the model, I split the dataset into training and testing sets, 80% and 20% respectively initially. For training we need more data hence the split is more for train set. And for easy computation we go for a single split. Training sets will be used to create the model and the testing set is used to evaluate the model. Any dataset which had had influenced the creation of the model cannot give a fair evaluation of the performance of that model.
### Decision Tree
The reason behind choosing this model is that decision trees can be visualized as a chart and is easy to interpret. In addition, it allows representing highly non-linear functions and can separate data points according to their labels more accurately. We use Gini entropy as the loss function, as it allows to measure the variance across the different classes. Here again we use the same split as the previous model for the same reason. In addition to that I have used GridSearchCV to tune the hyperparameters. So that it gives a combination of hyperparameters for which the model performs the best.
## Results and Conclusion
Both models perform quite well when we take a look at the accuracies and errors. The training accuracies differ by 0.18, the validation accuracies of logistic regression is 0.55 and decision tree is 0.72.
![sec(6)](https://user-images.githubusercontent.com/71560738/162576495-fafd6884-0825-45f2-b72a-f5dd9722fd97.png)
The training and validation accuracies for Decision tree classifier are 0.93 and 0.72 respectively. The loss or impurity is seen in each node which ends with 0.
Based on the result, it seems that the Decision tree classifier is a correct fit, this happened since we used GridSearchCV. Overfitting is one of the major disadvantages of GridSearch as it tunes the hyperparameters based on the training data. Logistic regression seems to perform quite well. But one thing I noticed while going through the data is that it has a highly uneven class distribution (see histogram last plot). This results in false positive paradox. I would consider collecting data with an even class distribution and then apply both the models and interpret the results. The test set construction is explained above and is 20% of the dataset. The test error for Logistic regression is 0.25 and for Decision Tree classifier is 0.07. Even though the test error for logistic regression is much lower than the decision tree classifier, I would choose the later as they are capable of representing highly non-linear functions and can perfectly separate data points according to their labels. For logistic regression the only possible decision boundary is a straight line as it consists of linear functions. This report can be extended by using a good dataset with even class distribution. For the most part Decision tree classifier seems like a good model in terms of interpretability, calculation and results. GridSearchCV is quite useful for tuning the hyperparameters and it is better to apply it on a validation set.
