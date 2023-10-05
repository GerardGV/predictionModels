# PREDICTION MODEL
Machine learning models implemented to predict Packs and Value attributes from a dataset. This solution it is propposed to solve a assignment proposed by Randstad company using lineal regression and random forest.

## 1.DATASET TREATMENT

To solve the problem raised, it is necessary 2 models, one for each objective attribute.
Two types of models are tested: Linear Regression model from sklearn library of python is a good option in case of data with linear relations between characteristics and Random Forest for not lineal case.
Dataset is separated on data to train, test and predict. Besides, character “.” is understood as thousands.
Five values of NaN have been found apart from those that are going to be predicted.

<img src="readmeImages/nan.png?raw=true"/>

Data do not need to be standardized looking the ranges. Dataset.describe() is used to analyse ranges and probably outliers in each numeric attribute.

<img src="readmeImages/describe.png?raw=true"/>

## 2.DATA ANALYSIS
Firstly, sns.pairplot is used to analyse the relation between attributes. With scatter plots is visible that only Packs and Value have a lineal relation. Also, analysing the distributions at the diagonal of the plot matrix,  it seems to not be any outlier.

<img src="readmeImages/pairPlot.png?raw=true"/>

The objective attributes are Packs and Values. To predict them it is necessary to analyse the correlation between objective attributes and the rest. 

Relevant correlations:

- Packs:
  - Value: 0.67
  - ProductName: 0.16
    
- Value:
  - Packs: 0.67
  - MoleculeName: 0.11
  - TradeName: 0.15
  - ProductName: 0.17
    
This is useful to select attributes to train a Linear Regression model. Moreover, adding the attribute Year must be tested because it has more than 0,01 correlation. In other hand, attribute Month is going to give noise to the models. It will be dropped.

<img src="readmeImages/correlations.png?raw=true"/>

## 3.MODEL SELECTION AND RESULTS: LINEAR REGRESSION

One Linear Regression model is created for each objective attribute.  The R^2 metric is used to evaluate model performance instead of the accuracy metric since continuous numerical attributes are predicted.

R^2 predicting Packs with Year attribute:

- Predicting Packs:
<img src="readmeImages/result1.png?raw=true"/>

- Predicting Value:
<img src="readmeImages/result2.png?raw=true"/>

Accuracy predicting Packs without Year attribute:

- Predicting Packs:
<img src="readmeImages/result3.png?raw=true"/>

- Predicting Value:
<img src="readmeImages/result4.png?raw=true"/>


How we saw before looking the plot matrix, a linear model is not good predicting with a dataset which does not have linear relations between their attributes. Additionally, training with attribute year seems to improve accuracy.

As the Linear Models before, we use R^2 metric to evaluate the model’s performance since continuous numerous are predicted as attribute Value. How Random Forest can find not linear patterns, to know which attributes use, a Forward Selection metodologie is used consist in obtain R^2 adding attributes in order to the dataset.

When the Month attribute is added, performance drops for both tests.

Results:

<img src="readmeImages/resultsAccuracy.png?raw=true"/>

After this analysis, attribute Month is not going to be used.

Results predicting each objective attribute:

- Packs prediction:
<img src="readmeImages/accuracy1.png?raw=true"/>

- Value prediction:
<img src="readmeImages/accuracy2.png?raw=true"/>

## CONCLUSION
With this dataset the best option is using a complex model as Random forest and for each objective attribute the best attributes to use are year, MoleculeName_coded, TradeName_coded and ProductName_coded attributes.





