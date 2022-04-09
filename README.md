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
