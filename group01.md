---
layout: page
title: Group 01
nav_order: 6
description:
---
# Question: Can we build a model to predict someone's stance on gun control?**

By: Jacqueline Wood, Andrew Choi, Omar Gastelum


This question is important because the issue of gun control is so polarizing. If we can identify and understand where these strong differences in opinions come from we can start to understand how to combat this problem and reach more consensus.

Data:
The dataset we will use to answer this question comes from the General Social Survey, which attempts to provide policymakers with an unbiased view on what Americans think about various social issues, including gun control. The surveys are run every other year and we will be using the surveys from 2000 on, so 2000, 2002, 2004, ... 2018.

This dataset includes features such as sex, race, religion, highest level of education, and income which may be helpful for predicting someone's stance on gun control.

The dataset contains categorical responses to the survey questions coded as numbers, so for example the sex feature is coded as: Male: 1, Female: 2.

The response variable (titled gunlaw) are response to the survey question: Would you favor or oppose a law which would require a person to obtain a police permit before he or she could buy a gun?

* Favor: 1
* Oppose: 2

## Import Data and Clean Data

We have separate datasets for the surveys from 2000, 2002, 2004, ... 2018 which we will combine to create our dataset.

To clean the data we will combine all ten of the separate dataframes by restricting each to only contain the columns that all ten dataframes share.

We also will drop rows in which the gunlaw response is nan, as well as dropping any columns that are all nans.

The cleaned dataset looks like this:


```python
gss.head()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>abany</th>
      <th>abdefect</th>
      <th>abhlth</th>
      <th>abnomore</th>
      <th>abpoor</th>
      <th>abrape</th>
      <th>absingle</th>
      <th>acqntsex</th>
      <th>adults</th>
      <th>affrmact</th>
      <th>...</th>
      <th>wrkstat</th>
      <th>wrkwayup</th>
      <th>wtss</th>
      <th>wtssall</th>
      <th>wtssnr</th>
      <th>xmarsex</th>
      <th>xmovie</th>
      <th>xnorcsiz</th>
      <th>year</th>
      <th>zodiac</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>4.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0985</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>3</td>
      <td>2000</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>0.5493</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>3</td>
      <td>2000</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>1.0985</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>3</td>
      <td>2000</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>3.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>0.5493</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>3</td>
      <td>2000</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>0.5493</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>3</td>
      <td>2000</td>
      <td>12.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 404 columns</p>
</div>

    The shape of the cleaned dataset is (14545, 404)

So we have 404 features, all of the responses to the many survey questions, and about 14545 survey responses total.

## Exploratory Data Analysis

To get a better sense of our data let's look at some EDA visualizations.

First, let's look at the opinions of gun control (gunlaw) over the years.

![png](images/output_17_0.png)

As shown above, the majority of people responded that they would favor a law which would require a person to obtain a police permit before he or she could buy a gun.

However, over the years the number of people that answer favor oscillates, but the number of people that answer oppose seems to be slightly increasing.

Let's compare the relative sizes of those that favor gunlaw and oppose gunlaw.

![png](images/output_19_0.png)

As shown above a large majority of those surveyed favor a law that would require people to obtain a police permit before buying a gun. Having such imbalanced classes will make it critical to not just rely on the accuracy score to assess the model. This is because if you have a very imbalanced dataset and you just classify everything as the larger class you may have a relatively high accuracy, but that does not mean the model will generalize well.

Now let's look at the relationship between gunlaw and owngun (if you own a gun or not). I hypothesize that if you own a gun you are more likely to oppose gun control.

![png](images/output_21_0.png)


![png](images/output_21_1.png)

Based on the plots above it is obvious that the majority of people favor a gun law regardless of whether or not they own a gun. However, more people oppose a gun law if they own a gun.

Now, I want to investigate correlation. However, almost all of my response variables are categorical so instead of using the typical Pearson's correlation coefficient I am going to use the Cramer's V statistic, which measures association between categorical variables using a chi-squared test.

Because there are so many features instead of calculating Cramer's V for every pair of variables, I am going to calculate Cramer's V for every feature with gunlaw (our response variable).


![png](images/output_25_0.png)


The resulting top Cramer's V statistic features make a lot of sense.

* gunlaw has an association of 1 with itself
* Some other interesting top features include:
  * rifle (if they own a rifle)
  * hunt (if they hunt)
  * partyid
  * owngun (if they own a gun)
  * helpnot (Should federal govt do more or less?)
  * numwomen (Number of female sex partners since 18)
  * natrace (Improving the conditions of blacks)
  * natenvir (Improving & protecting environment)
  * sexsex (Sex of sex partners in last year)
  * polviews (Think of self as liberal or conservative)
  * helppoor (Should govt improve standard of living?)
  * sex

Many of these features I assumed would be associated with opinions on gun control, such as hunt and partyid. The more suprising high associations are helpnot and numwomen.

## Encode Categorical Variables

All of the GSS features are categorical responses coded as numbers. Although the variables are already encoded as numbers, these numbers cannot be passed into the models because it will consider 6 to be higher than 5, when it simply means a different category and there is no order.

As a result, I will use one-hot encoding to make dummy variables of each possible response and use those instead as my features. Dummy variables make a column for each possible response and place a 1 in the row if the respondent responded that and 0 otherwise.


The resulting dummified dataset looks like this:

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>abany_1.0</th>
      <th>abany_2.0</th>
      <th>abdefect_1.0</th>
      <th>abdefect_2.0</th>
      <th>abhlth_1.0</th>
      <th>abhlth_2.0</th>
      <th>abnomore_1.0</th>
      <th>abnomore_2.0</th>
      <th>abpoor_1.0</th>
      <th>abpoor_2.0</th>
      <th>...</th>
      <th>zodiac_11.0</th>
      <th>zodiac_12.0</th>
      <th>zodiac_2.0</th>
      <th>zodiac_3.0</th>
      <th>zodiac_4.0</th>
      <th>zodiac_5.0</th>
      <th>zodiac_6.0</th>
      <th>zodiac_7.0</th>
      <th>zodiac_8.0</th>
      <th>zodiac_9.0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>...</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 16935 columns</p>
</div>

    The shape of the dummified dataset is (14545, 16935)

So the dummified dataset has many features, 16935 to be exact because each original feature gets broken up into multiple depending on the responses.

The dataset still has the same number of overall responses - 14545 total responses.

## Split Data

Now that we have our data cleaned and concatenated we will split the data into the training, validation, and test sets.

The breakdown will be 60% for training, 20% for validation, and 20% for testing.

![png](images/output_38_0.png)


## Fit Logistic Regression Model

First, I am going to try out a logistic regression model for this use case.

I chose to use logistic regression because the response variable is either 0 (favor gun control) or 1 (oppose gun control). Logistic regression is the appropriate regression analysis to conduct when the dependent variable is dichotomous (binary) because it outputs the probability of either 0 and 1 and using a cutoff you can classify the predictions into either group.

    The score of the logistic regression model on the training set is  0.987166265612467

    The score of the logistic regression model on the validation set is  0.7222413200412513

                            precision    recall  f1-score   support

     class 0: favor gunlaw       0.81      0.83      0.82      2217
    class 1: oppose gunlaw       0.41      0.38      0.39       692

                  accuracy                           0.72      2909
                 macro avg       0.61      0.60      0.61      2909
              weighted avg       0.71      0.72      0.72      2909

Above is the classification report of the logistic regression model on the validation set.

Precision is the ability of a classifier not to label an instance positive that is actually negative.

  * The precision rate is pretty high for class 0: favor gunlaw (0.81) and about half for class 1: oppose gunlaw (0.83).
  * So the precision rate 0.81 for class 0: favor gunlaw means when a response is actually in class 1: oppose gunlaw, we classify it as class 0 only 0.19 of the time.

Recall is the ability of a classifier to find all positive instances.

  * The recall value for class 0: favor gunlaw is 0.83, meaning that 83% of the time a response is in that class, we label it as such.
  * As you can see, the recall value for class 1: oppose gunlaw is lower at 0.38, meaning the fraction of those that are truly within this class that we got right and classified as class 1 is only 38%.

Obviously, the classifier is better at classifiying class 0: favor gunlaw - likely because the majority of the data falls within this category so its able to learn it better. Because the classes are imbalanced it is important to look at precision and recall scores, not just accuracy because a very imbalanced model can have a high accuracy without generalizing well.

Our model with high precision but lower recall for class 1: oppose gunlaw returns very few results, but most of its predicted labels are correct when compared to the test labels.

![png](images/output_45_0.png)


The plot of the confusion matrix above shows that for the original logistic regression model:

* the number of True Positives is: 1841
* the number of False Positives is: 376
* the number of False Negatives is: 432
* the number of True Negatives is: 260

This plot shows similar information to the classification report and shows this model is better at predicting class 0: favor gunlaw. I think this is because the majority of people favor gunlaw so the original data is imbalanced.

![png](images/output_47_0.png)

The ROC curve above shows the tradeoff between the True Positive Rate (y-axis) and the False Positive Rate (x-axis). The closer this curve comes to the 45 degree diagonal, which indicates no predictive power, the worse its performance.

The Area Under the Curve (AUC) value is also shown on the plot as 0.68. The higher the AUC the better because it indicates more distance from the 45 degree diagonal and more predictive power.

Let's see how the model does with cross validation. Cross validation allows us to test out how our model may generalize to unseen data without using the test set. It does this by breaking the training data into k-folds and using one of the folds as a pseudo-test set.

	The cross validation score of the logistic regression is  0.72945978856297

The cross validation score is comparable to how the model performed on the validation set.

## Fit Random Forest Classifier

A random forest classifier combines many decision trees into a single model that decides on an output - either 0 or 1.

Decision trees learn from data to approximate a sine curve with a set of if-then-else decision rules. The deeper the tree, the more complex the decision rules and the fitter the model. By using many decision trees in a random forest classifier you can achieve increased accuracy.

    The score of the random forest model on the train set is  1.0

    The score of the random forest model on the validation set is  0.7641801306290822


Although this model has a higher accuracy score we need to consider other metrics, such as precision and recall, to determine if this is just a result of the imbalanced classes.

                            precision    recall  f1-score   support

     class 0: favor gunlaw       0.76      1.00      0.87      2217
    class 1: oppose gunlaw       0.71      0.01      0.03       692

                  accuracy                           0.76      2909
                 macro avg       0.74      0.51      0.45      2909
              weighted avg       0.75      0.76      0.67      2909


The classification report for the random forest classifier is shown above.

Precision:

  * The precision rates for each class is fairly high, meaning that when a response does not fall within a class, we missclassify it as that class rarely.
  * So the precision rate 0.76 for class 0: favor gunlaw means when a response is actually in class 1: oppose gunlaw, we classify it as class 0 only 0.34 of the time

Recall:

  * The recall value for class 0: favor gunlaw is 1, meaning that every time a response is in that class, we label it as such.
  * As you can see, the recall value for class 1: oppose gunlaw is very low, meaning the fraction of those that are truly within this class that we got right and classified as class 1 is only 1% - pretty low.
      * This classifier pretty much classifies everything as class 0: favor gunlaw and although this results in relatively high accuracy (because the dataset is imbalanced) this is a problem for when you want to apply this model to never before seen data.

Obviously, the classifier is better at classifiying class 0: favor gunlaw because the majority of the data falls within this category. However, this classification report shows that this model is heavily influenced by the imbalanced classes and classifies almost every data point as class 0: favor gunlaw. Although yes this is what it learned from the data, that makes this model less generalizable than the previous logistic regression model.

This model definitely trades precision for recall, however it is important to have a good balance. This high precision is likely just because of the imbalanced data.

![png](images/output_58_0.png)

The plot of the confusion matrix above shows that for the original random forest classifier:

* the number of True Positives is: 2213
* the number of False Positives is: 4
* the number of False Negatives is: 682
* the number of True Negatives is: 10

The model has very low FP and TN values. The low FP count means that the model rarely classifies someone as favoring gun control when they do not, but the low TN count indicates that we correctly identify those that oppose gun control rarely.

The high number of mistakes for class 1: oppose gunlaw is concerning. It appears that this model may have overfit and instead of capturing the true underlying differences in the data, is almost always classifying every person as class 0: favor gunlaw.

This plot once again shows that the model is far better at predicting class 0: favor gunlaw because that is the true value for the majority of the points. However, this model has an even larger imbalance between the performance on the classes than the logistic regression model.

![png](images/output_60_0.png)


Like I explained earlier, the closer the ROC curve (shown above) comes to the 45 degree diagonal, which indicates no predictive power, the worse its performance.

The Area Under the Curve (AUC) value for this original random forest classifier is 0.73, which is slightly higher than the AUC value for logistic regression (0.67). The higher the AUC the better because it indicates more distance from the 45 degree diagonal and more predictive power.

The cross validation score for this model is shown below. Although the value is slightly higher than the cross validation score for the logistic regression model, I am still concerned about the low recall score for this model.

	The cross validation score of the random forest model is  0.7647532961135891

Although the cross validation score for this model is higher than the logistic regression model this model has a huge imbalance between precision and recall, which is not desired.

## Perform Grid Search

Grid search tests multiple combinations of parameters and determines the resulting model with the highest accuracy. Therefore, we can use that model with the tuned parameters.

### Grid Search for Logistic Regression

Let's see if grid search improves the perfomance of the logistic regression model. The grid search results are shown below.

	Best Penalty: l1
	Best C: 1.0

	The score of the best logistic regression model on the validation set is  0.7315228600893778

                            precision    recall  f1-score   support

     class 0: favor gunlaw       0.81      0.85      0.83      2217
    class 1: oppose gunlaw       0.42      0.36      0.39       692

                  accuracy                           0.73      2909
                 macro avg       0.62      0.61      0.61      2909
              weighted avg       0.72      0.73      0.72      2909


After performing grid search, the logistic regression model improved very slightly, but still much less imbalanced than the random forest model. Therefore, I will likely move forward with this model.

![png](images/output_72_0.png)

The tuned model seems to perform very similarly to the previous logistic regression model with an AUC of 0.68.

### Grid Search for Random Forest

Let's see if we can decrease the imbalance of errors by tuning the random forest using grid search, meaning testing multiple hyperparameter combinations. The grid search results are shown below.

    Best max depth: 3
    Best max features: 3
    Best min samples split: 3
    Best number of estimators: 100

    The score of the best random forest model on the validation set is  0.7621175661739429

                            precision    recall  f1-score   support

     class 0: favor gunlaw       0.76      1.00      0.87      2217
    class 1: oppose gunlaw       0.00      0.00      0.00       692

                  accuracy                           0.76      2909
                 macro avg       0.38      0.50      0.43      2909
              weighted avg       0.58      0.76      0.66      2909

Grid search did not improve the imbalance of errors. In fact, now both precision and recall for class 1: oppose gunlaw are 0. This means the model is likely classifying everything as class 0: favor gunlaw.

![png](images/output_81_0.png)

The tuned mode actually performs worse than the original with an AUC value of 0.60.

## Look at Feature Importances from Random Forest Model

A great feature of random forest models is that you can access the importance of each of the features. Using the relative importances we can see which features contribute the most to someone's stance on gun control.

![png](images/output_85_0.png)

The top 50 most important features make a lot of sense.

Some of the common themes are:

  * owngun (whether or not you own any gun)
  * rifle (whether or not you own a rifle)
  * shotgun (whether or not you own a shotgun)
  * hunt (whether or not you hunt)
  * pistol (whether or not you own a pistol)
  * sex
  * partyid
  * polviews (Think of self as liberal or conservative)

Some more interesting top features include:

  * nateduc_3: govt spending too much on national education
  * numwomen_0: 0 female sex partners since age 18
  * srcbelt_6: Other rural (where interview took place)
  * natchld_1: govt spending too little on assistance for childcare
  * natrace_3: govt spending too much on imporoving the conditions of black people
  * cappun_1: favor death penalty
  * granborn_4: 4 grandparents born outside of US
  * natmass_1: govt spending too little on mass transportation
  * fear_2: not afraid to walk at night in neighborhood
  * conpress_3: hardly any confidence in the press
  * courts_2: the courts are not harsh enough when dealing with criminals
  * helpblk_5: govt should not give special treatment to black people
  * xnorcsiz_10: interview took place in open country
  * natarms_1: govt spending too little on the military, armaments and defense

Now that we have the most important features, we can see the key differences between those that favor gun control and those that oppose.

## Tuned Logistic Regression Performance on Test Set

Our tuned logistic regression model seems to be the best overall model so let's evaluate how it performs on the test set.

    The score of the best logistic regression model on the test set is  0.732897903059470

                            precision    recall  f1-score   support

     class 0: favor gunlaw       0.80      0.86      0.83      2211
    class 1: oppose gunlaw       0.43      0.34      0.38       698

                  accuracy                           0.73      2909
                 macro avg       0.62      0.60      0.60      2909
              weighted avg       0.71      0.73      0.72      2909


The classification report shows that the final logistic regression model is less sensitive to the class imbalance than the random forest classifier.

For class 0: favor gunlaw:

* the precision rate is 0.8 (high)
* the recall rate is 0.86 (also high)

For class 1: oppose gunlaw:

* the precision rate is 0.43
* the recall rate is 0.34
    * although both of these values are lower than for class 0: favor gunlaw these numbers indicate that the model is performing better on class 1 than with the random forest classifier

The final model performs fairly well on the test set, by having a high overall accuracy of 0.73, but also having reasonable precision and recall numbers for each class.

![png](images/output_91_0.png)


The plot of the confusion matrix above shows that for the original random forest classifier:
* the number of True Positives is: 1894
* the number of False Positives is: 317
* the number of False Negatives is: 460
* the number of True Negatives is: 238

These numbers are very similar to how the model performed on the validation set which is a good sign that this is the performance we can expect when the model is applied to future unseen data.

This model has a relatively good balance between the different errors, which is promising. The high number of True Positives indicates that the model is very good at classifying those as class 0: favor gunlaw, when they do. But this model has a reasonably high value of True Negatives meaning we classify more people as class 1: oppose gunlaw, when they actually do then we did with the random forest classifier.

This plot once again shows that the model is far better at predicting class 0: favor gunlaw because that is the true value for the majority of the points. However, this model performs better on class 1: oppose gunlaw, which is the balance we are trying to strike.

![png](images/output_93_0.png)


The AUC is 0.67 for this model applied to the test set, which is comparable to its performance on the validation set, a good sign for generalizability.

Although this AUC is lower than the AUC for the random forest classifier this model has higher recall scores, which is important.

## Conclusion

The question we aimed to answer is: **Can we build a model to predict someone's stance on gun control?**

Using General Social Survey data, we built two accurate models, a logistic regression and a random forest classifer, to predict gunlaw: Would you favor or oppose a law which would require a person to obtain a police permit before he or she could buy a gun?

  * Favor: 0
  * Oppose: 1

Both logistic regression and random forest classifiers can make binary predictions of someone's stance on gun laws so these models were appropriate to use. Perhaps to further avoid overfitting more feature selection could have been conducted.

Although both models had similar accuracies, the logistic regression had a better precision-recall tradeoff, which seemed to be less skewed by the class imbalance in the data. Used on the test set the final logistic regression model had an accuracy of about 0.73.

We used the random forest classifier to determine feature importances and were able to identify some of the features that were most indicative of someone's opinion on gun control. Some of the most important features included whether someone owned a gun, whether they hunted, and their party identification. However, there were some more unexpected important features such as 0 female sex partners since age 18, hardly any confidence in the press, and the courts are not harsh enough when dealing with criminals.

Determining the strongest predictors of someone's stance on gun control is important because once we understand where these strong differences in opinions come from we can begin to understand how to combat this problem and reach more consensus.

Knowledge like this can help inform future policy as more and more people begin to favor some form of gun control. This important information about the American electorate identifies important issues to people and where opinions may diverge, valuable information for any election.

Going further this logistic regression model can be further tuned and trained with more data in order to become a more accurate predictor on unseen data. More data could help rectify the issues of class imbalance. This research, specifically the most important features, could inform future feature selection for a more refined model.
