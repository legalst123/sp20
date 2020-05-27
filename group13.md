---
layout: page
title: Group 13
nav_order: 18
description:
---

<h1>Gun Laws in the United States</h1>
<h2>LEGALST 123</h2>
<h3>Andrew Zhang, Sydney Chang, Simarjeet Kaur</h3>

May 8, 2020

<br>
<h2>Introduction</h2><br>

<h3>Background</h3>

In the United States, the issue of gun legislation is a highly controversial one sparking heated debates echoed throughout multitudes of political and constitutional values. When it comes to regluating firearms, there appears to be two distinct philosophies that ceaselessly clash against each other: gun rights versus gun control. The current President of the United States has repeatedly urged the importance of the Constitution's Second Amendment and admonishes Americans of the imminent threat that states impose on such protections. However, gun laws nonethless play a vital role in ensuring the safety of the poeple.<br>

In this study, we will explore the effectiveness of state gun legislation in curbing gun violence by extracting and applying data from machine learning models. The aim is to identify strengths and weaknesses in modern firearm jurisprudence to assist legislators in tackling a haunting issue that jeopordizes security of all Americans today.<br>
<br>

<h3>Question</h3>
Can predictive modelling be used to extract information on the importance of specific gun legislations in curbing gun violence?
<br>
<br>



<h3>Motivation</h3>
Gun violence is becoming an increasingly prevalent issue affecting all of our lives. When we turn on the news or surf through Facebook, Twitter, and Instagram, the headline "Mass Shooting in..." is a heart-dropping title that seems to frequent our media more and more often. We ask ourselves, "how did Stephen Paddock, a man with a history of mental illness, get his hands on twenty-three high-caliber rifles and kill so many people off the top of a casino building", instead of asking ourselves, "how is it possible that there aren't any laws preventing him from doing that in the first place?" To answer the latter, we realized that there are laws in place, just not in certain states. As a result we decided to gather publicly available datasets to validate our concerns.<br>

<br>


<h2>Data Collection</h2>

1. The <b>'incidents'</b> dataset is our primary tool for this research project. It accounts for all gun incidents within the United States from 2013-2018 with features describing the attributes of each incident. The dataset was gathered through the <a href="https://www.gunviolencearchive.org/reports">Gun Violence Archive</a> website. The organization's description is as follows:

    <p style="margin-left:5%; margin-right:5%;">Gun Violence Archive (GVA) is a not for profit corporation formed in 2013 to provide free online public access to accurate information about gun-related violence in the United States. GVA will collect and check for accuracy, comprehensive information about gun-related violence in the U.S. and then post and disseminate it online.</p><br>


2. We will also be working with the <b>'laws'</b> dataset as well as it accounts for all gun legislation that have been enacted since the beginning of our incidents dataset. We will be combining both of these datasets so that every particular incident is also matched with the specific laws that were enacted in a specific state at the time of the incident. The dataset is from the <a href="https://www.rand.org/pubs/tools/TL283-1.html">RAND Database</a>. The RAND corporation's description is as follows:

      <p style="margin-left:5%; margin-right:5%;">RAND launched the Gun Policy in America initiative in January 2016 with the goal of creating objective, factual resources for policymakers and the public on the effects of gun laws. As part of this initiative, RAND developed a longitudinal data set of state firearm laws that is free to the public, including other researchers, to support improved analysis and understanding of the effects of various laws.</p><br>


3. We will incorporate the <b>'elections'</b> dataset which contains constituency (district) returns for elections to the U.S. House of Representatives from 1976 to 2018. The dataset is from the <a href="https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/IG0UN2">Harvard Dataverse</a>.<br>
<br>
<be>
4. Finally, we will combine the <b>'population'</b> dataset into our <b>'incidents'</b> dataset to help us standardize the number of gun incidents with respect to the overall population of the state. The dataset is from the <a href="https://www.census.gov/data/datasets/time-series/demo/popest/2010s-state-total.html">United States Census Bureau</a>.
<br>
<br>

Below is a sample of our processed incidents dataset.
<br>
<br>

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
      <th>state</th>
      <th>n_killed</th>
      <th>n_injured</th>
      <th>incident_url_fields_missing</th>
      <th>congressional_district</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>n_guns_involved</th>
      <th>state_house_district</th>
      <th>state_senate_district</th>
      <th>...</th>
      <th>Minimum purchase and sale age - long guns</th>
      <th>Minimum age for youth possession - long guns</th>
      <th>Minimum age for youth possession - handguns</th>
      <th>Child access laws - negligent storage (CAP)</th>
      <th>Child access laws - intentional, reckless, or knowing provision</th>
      <th>num_laws</th>
      <th>number_incidents</th>
      <th>dates</th>
      <th>date</th>
      <th>political_val</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alabama</td>
      <td>0</td>
      <td>4</td>
      <td>False</td>
      <td>5.0</td>
      <td>34.7982</td>
      <td>-87.6854</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>6.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>8.0</td>
      <td>1</td>
      <td>[Timestamp('2013-07-06 00:00:00')]</td>
      <td>2013-07-06</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Alabama</td>
      <td>3</td>
      <td>5</td>
      <td>False</td>
      <td>2.0</td>
      <td>32.3719</td>
      <td>-86.2952</td>
      <td>0.0</td>
      <td>77.0</td>
      <td>26.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>8.0</td>
      <td>1</td>
      <td>[Timestamp('2013-12-28 00:00:00')]</td>
      <td>2013-12-28</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Alabama</td>
      <td>38</td>
      <td>50</td>
      <td>False</td>
      <td>587.0</td>
      <td>4412.4395</td>
      <td>-11464.4633</td>
      <td>13.0</td>
      <td>6617.0</td>
      <td>1991.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>8.0</td>
      <td>132</td>
      <td>[Timestamp('2014-01-01 00:00:00'), Timestamp('...</td>
      <td>2014-01-01</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Alabama</td>
      <td>16</td>
      <td>39</td>
      <td>False</td>
      <td>406.0</td>
      <td>3266.5745</td>
      <td>-8597.1413</td>
      <td>9.0</td>
      <td>5708.0</td>
      <td>1904.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>8.0</td>
      <td>99</td>
      <td>[Timestamp('2014-02-01 00:00:00'), Timestamp('...</td>
      <td>2014-02-01</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Alabama</td>
      <td>28</td>
      <td>53</td>
      <td>False</td>
      <td>480.0</td>
      <td>3707.3779</td>
      <td>-9724.1740</td>
      <td>45.0</td>
      <td>6346.0</td>
      <td>2107.0</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>8.0</td>
      <td>112</td>
      <td>[Timestamp('2014-03-01 00:00:00'), Timestamp('...</td>
      <td>2014-03-01</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>

<br>


A distribution plot that respresents the total number of incidents per month we be modelling. We can see right off the bat that many of the monthly gun incidents are between 0-20.


![png](output_39_1.png)


<h1>Machine Learning</h1>

The regression tool we used for our model was the <b>random forest regression</b>.

We chose to employ a random forest model because of its versatility, dimensionality, and effiency. Not only does it handle binary features, categorical features, and numerical features, there is very little pre-processing that needs to be done. Furthermore, since the random forest model works with subsets of data, it enables fast processing of high dimensional data.

Below is a scatter plot of the predicted versus the actual number of crime commited within a certain state of a certain month.
<br>
<br>

<h2>Random Forest Regression</h2>

![png](output_44_0.png)


    RMSE:  42.85826350673882
    R-Squared Value:  0.7534352412088899


<h3>Prediction Error</h3>

The graph below models the difference between the 45 degree line (which is essentially the prediction line had the model achieved an r-squared score of 1.0) and the actual line of best fit which reduced the mean-squared error of all the points from the line. Our initial impression is that the prediction error of our model is not too bad.

![png](output_46_0.png)

<h3>Residual Plot</h3>

This graph depicts our residual plot for both the training set and the test set. Furthermore, the graph helps us better visualize the distribution. On first glance, we can see that the residuals for lower predicted values of gun incidents occur more frequently on the test set whereas the residuals seem to be more prevalent in the training set as the number of gun incidents being predicted increased.




![png](output_48_0.png)

<h3>Feature Importance</h3>

We can see which laws contribute most to our model.

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
      <th>feature</th>
      <th>importance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>12</th>
      <td>Prohibited possessor - Adjudicated by police a...</td>
      <td>0.172396</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Castle Doctrine - Stand Your Ground</td>
      <td>0.116788</td>
    </tr>
    <tr>
      <th>35</th>
      <td>Prohibited possessor - DVRO - Removal</td>
      <td>0.101255</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Carrying a concealed weapon (CCW) - shall issue</td>
      <td>0.065584</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Dealer license - handguns</td>
      <td>0.062249</td>
    </tr>
    <tr>
      <th>31</th>
      <td>Prohibited possessor - DVRO</td>
      <td>0.061401</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Prohibited possessor - Adjudicated as mentally...</td>
      <td>0.046219</td>
    </tr>
    <tr>
      <th>48</th>
      <td>Registration - handguns</td>
      <td>0.046093</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Carrying a concealed weapon (CCW) - shall issu...</td>
      <td>0.038020</td>
    </tr>
    <tr>
      <th>53</th>
      <td>Minimum age for youth possession - handguns</td>
      <td>0.034097</td>
    </tr>
  </tbody>
</table>
</div>
<br>
<br>
 We see that the <i>'Prohibited possessor - Adjudicated by police as mentally incompetent/defective/incapacitated/disabled'</i> law, which prohibits those determined by police as mentally incompetent, defective, incapacitated or disabled from obtaining firearms, contributed to over 17% of our whole model, while <i>'Castle Doctrine - Stand Your Ground'</i>, which is a law stating that people have no duty to retreat in their home and may use reasonable force including deadly force, to defend their property, person, or another, contributing roughly 11% of our model. The list is sorted in descending order. The results aren't suprising, but are very indicative of which laws are really useful in combatting gun violence...pretty cool.

Another (rough) visualization of the feature importance.



![png](output_51_1.png)


The feature importances from random forest are calculated based on the training data given to the model, not on predictions on a test dataset. Thus, these numbers do not indicate the true predictive power of the model, especially if our model overfits onto the training set. In order to see the true feature importance more accurately, we need to employ another assessment.
<br>
<br>

<h2>Permutation Feature Importance</h2>

<b>Permutation feature importance</b> is used to measure the importance of a feature by calculating the increase in the model’s prediction error after permuting the feature. A feature is considered important if shuffling its values <i>increases</i> the model error, showing that the model relied on the feature for the prediction. A feature is considered unimportant if shuffling its values leaves the model error <i>unchanged</i>, showing that the model ignored the feature for that prediction.<br>

We decided to use permutation feature importance because it takes into account both the <b>main feature effect</b> and the <b>interaction effects on model performance.</b> Note that using the error ratio instead of the error difference allows the feature importance measurements to be comparable across different problems.<br>

![png](output_54_0.png)



The benefits of using boxplots is that we can observe the magnitude and spread of distinct features that the model depended on the most when making predictions.<br>

We can see that the law, 'Prohibited possessor - Adjudicated by police as mentally incompetent, defective, incapacitated, or disabled' is nearly just as important in predicting gun violence when we permute the features to account for both the main feature effect and its interaction effects. However, we also see that the most important feature is one that was barely present in the basic feature importance approach - prohibited posessor, ERPO, expanded ex-parte. This is because the feature importance method we employed earlier from our random forest model selects features that have <b>high cardinality</b>. In our dataset, that law had the most unique values, thus causing the model to assume that it was the most important feature when we can see here that it is not.<br>

Although the legislation with the greatest importance in determining gun violence varies each time the features are permuted, the top 5 most important laws seem to always appear:<br>

1. Prohibited Possessor, ERPO, Expanded ex-parte

    - A law that allows law enforcement to petition a court to temporarily remove firearms from a person before the person has appeared in court (we believe that this law, and all other prohibited possessor laws, has a postive effect on gun violence - those who may be arrested, charged, and released on bail may be more likely to commit an act of violence).


2. Prohibited Possessor - Prohibited possessor - Adjudicated by police as mentally incompetent, defective, incapacitated, or disabled.

    - Prohibits the possession of firearms (or handguns) by individuals adjudicated as being mentally incompetent, defective, incapacitated, or disabled.


3. Prohibited possessor - Committed to MH facility - outpatient

    - Prohibits the possession of firearms by individuals who have been court-ordered to attend outpatient mental health institutions.


4. Waiting Period - Hand Guns

    - Establishes the minimum amount of time sellers must wait before delivering a gun to a purchaser (we think this law has a positive effect because someone who may be emotionally charged at the time of purchasing a hand-gun may have time to reflect on their rash decisions before taking action).


5. Prohibited possessor - DVRO - Ex parte - Expanded

    - A law preventing an individual served with a domestic violence restraining order (executed before the respondent appears in court to defend himself or herself) from owning, possessing, or purchasing firearms extended to dating partners. Since domestic violence is a huge contributer to overall crime rates in major cities - like San Francisco (Zhang, 2020), it can be the case that issuing this prohibited possessor law deters much of the gun violence that occurs in homes.
<br>
<br>

<h2>Train-Validate-Test Set Change - By State</h2>

<b>**Note**</b> - The problem with the original train-validate-test split is that the model may pick up some patterns that are particular to each state. For example, a specific state may generally have the same gun laws throughout the years, so when we use a validation set of a particular state that has already been learned, the machine might predict not based on the specific laws that were enacted, but rather the patterns of that specific state. To remove this confounding factor, we will split the training and validation sets into specific states rather than a random 60:20:20 proportion


![png](output_59_0.png)


    RMSE:  41.48164793207804
    R-Squared Value:  0.7986591719394602


Now, we will employ the trained model onto a completely new set of states.


![png](output_60_0.png)

    RMSE:  98.9944915843157
    R-Squared validation:  -0.4118070774376641


We see that our intial skepticism may have been validated. It turns out that our original model may most likely be overfitted to each particular state's legislative pattern. When we attempt to remove the confounding factors of state-like legislative patterns by training on one paticular group of states and validating on another completely different sets of states, we see that the model is much worse at generalizing itself.

Interestingly enough, the prohibited possessor law (adjudicated by police as mentally incompetent, defective, incapacitated, or disabled) seems to be much more important when we use less states to train our model.

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
      <th>feature</th>
      <th>importance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>24</th>
      <td>Prohibited possessor - Adjudicated by police a...</td>
      <td>0.288450</td>
    </tr>
    <tr>
      <th>34</th>
      <td>Prohibited possessor - DVRO - Expanded - Surre...</td>
      <td>0.172905</td>
    </tr>
    <tr>
      <th>42</th>
      <td>Maximum waiting period - handgun permits</td>
      <td>0.084822</td>
    </tr>
    <tr>
      <th>46</th>
      <td>Time for background checks - extra time</td>
      <td>0.080847</td>
    </tr>
    <tr>
      <th>49</th>
      <td>Registration - long guns</td>
      <td>0.073388</td>
    </tr>
    <tr>
      <th>48</th>
      <td>Registration - handguns</td>
      <td>0.047016</td>
    </tr>
  </tbody>
</table>
</div>

<br>
<br>

<h2>Model Exploration</h2>

Before we begin exploring our model, we want explain why we chose to stick with our original model without the state level train-validate-test group split. Our research question is to determine whether we can use predictive modelling techniques to evaluate the impact of gun <b>legislation</b> on gun rates. We are <b>not</b> attempting to train a model to generalize and predict gun violence rates among the different states. Instead, want to observe the impact of legislation. Had our research question been different (can we use historical gun violence incidents data to build a predictive modelling tool to aid police law enforcement?), our model will have been flawed because it overfitted on our training set.<br>

For this project, we wanted to make sure that we as well as our readers know that the model is not intended for general purposes, but rather as an insightful exploration.
<br>
<br>
<br>

<h2> Model Prediction - Based on State Politics </h2>



For conistency, we created a dictionary of both the politial party reference and the state abbreviations so that all Democratic/Republican variables will have -1.0/1.0 and every state e.g. 'CA' will be changed to 'California'.


Again, to maintain consistency with our earlier data combination method, we will be matching the elected representative of each state with the month of the incident group. For example, In California, 05/2017, the majority of representatives in the house of representatives were Democrats; therefore, the incident group will be assigned a 'Democrat' state with a value of -1.

Here's how the incidents were distributed based on state politics.

![png](output_72_1.png)

    Root-Mean-Squared Error:  42.95066690400527
    R-Squared validation:  0.6790008384471147


Clearly, blue states (Democratic) have higher predicted and actual gun incidents. However, this does not convey the whole picture. States like California and New York may have more gun violence, but their population is much greater too. To resolve this issue, we will import, clean, and concatenate a new dataset containing the population of every state within the year 2003-2018. Then we will standardize the 'number_incidents' column as a proportion of the state population so that we can observe a more accurate measure of gun violence <i>rates</i>.


    Predicted Gun Incidents per 1000 People - Democratic State:  0.10318809660645226

    Predicted Gun Incidents per 1000 People - Republican State:  0.069624877454705

    Actual Gun Incidents per 1000 People - Democratic State:  0.10305495689655171

    Actual Gun Incidents per 1000 People - Republican State:  0.06959536784741145

![png](output_78_1.png)

Ratio of gun incidents (per 1000 people) of Democratic states to Republican states.

    Ratio - Actual Values 1.4807732193111005
    Ratio - Predicted Values:  1.4820578560239774


Average number of gun laws in effect:

    Republican States:  num_laws    11.697731
    Democratic States:  num_laws    20.524398







![png](output_82_1.png)


As we can see, our model is more effective in predicting gun violence in republican states compared to democratic states. Perhaps, this can be associated with the homogeneity of republican, conservative populations as opposed to the more progressive left.<br>

An interesting converging point seen in the graph above is in November, 2016 - the months approaching and following the presidential election...something worth exploring further.

<h2> Classification </h2>

In the next section, we will observe the impact of gun legislation on the number of victims injured within a single gun violence incident.<br>

To conduct this exploration, we have decided to use classification to understand how laws affect the number of victims injured in a gun incident.


To implement a classification algorithm, we will first need to define a threshold for which the dependent variable (number of victims injured) will be assigned a binary value of 1 (high number of injured victims) or 0 (low number of injured victims). To balance out the two classes, the threshold will be set to the median value of all values in the 'n_injured' column. The median number of injured victims per state within a certain month is 23.

The confusion matrix for our classification model.

0 - under 23 injured<br>
1 - over 23 injured

![png](output_91_1.png)

    Accuracy: 85.25%





![png](output_94_0.png)


<h2>ROC/Precision-Recall Curves - Feature Importance Thresholds</h2>

Next, we will visualize both the reciever operating characteristics (ROC) curves as well as the precision-recall curves for different threshold of feature importance. The purpose behind this is to determine the optimal number of laws to factor in to determining the number of injuries that arise from gun violence - that is, laws above a certain importance threshold will be incorporated into the classification model.

Essentially, ROC Curves summarize the trade-off between the true positive rate (TPR) and false positive rate (FPR) for a classification model using different probability thresholds, while the precision-recall curves summarizes the trade-off between the positive predictive value and the "sensitivity" of a  classification model using different probability thresholds. There are certain tradeoffs to achieving a high statistic in any one of these indicators; the key here is to find a balance with the feature importance thresholds so that we optimize the value for all.
<br>
<br>
![png](output_96_0.png)

We see that the turqoise curve, right below the blue curve achieves the most optimal value of all four statistics. The threshold we will therefore employ when tuning our model is one that takes only the laws with the feature importance of 0.008 or above into account.

The refined confusion matrix:

![png](output_98_1.png)

    Accuracy: 87.21%

We see clearly that our model accuracy has improved from before (85.25% accuracy to 87.21%). Nearly a 2% jump! This just comes to show that there is a significant difference in the real-world effectiveness of certain gun laws at reducing the number fo injuries that arise from gun violence over others.
<br>
<br>

<h1>Discussion</h1>

To measure the importance of certain gun legislations in preventing (and encouraging) crime, we observed the relative importance of the laws in modelling the behaviour of gun violence within certain states.<br>

A key assumption we made in deriving this relationship is that certain laws have either a negative or positive bias towards the number of gun incidents. For example, we assumed that a law that requires a "cooldown" interval between the time the gun are purchased and the physical delivery of the firearm has a negative bias on the number of gun incidents - that is, it results in <b>less</b> gun incidents. On the other hand, we assumed that the castle doctrine, which makes it legal for property owners to use physical, including deadly, force to prevent criminal trespassers, has a positive effect on gun violence.<br>

Furthermore, the technique in which we grouped and merged the data had its limitations. To create an output variable which the computer was tasked to predict, we combined all incidents within a certain state into one month, summed the number of incidents within that group, and assigned the laws that were in effect in accordance with the date on which the first incident occured. Clearly, there are certain flaws with such a technique. Particularily with respect to the essense of our project, the laws that were not in effect at the beginning of the month, but came into effect at the end, wouldn't have been factored into our model. Beyond such a limitations to our model, we must also acknowledge the limitations of our resources - notably, computer processing power and project timeframe. Had we grouped the dataframe by week or even by day, our model would be much more representative of reality; in our case, the method according to which our datasets were concatenated required huge amounts of processing power (to the extent that even our simple approach took over half an hour to process).

With these key assumptions acknowledged and conceded, our results were nevertheless extremely informative - not just in terms of what types of laws were most effective in combatting gun violence, but also towards indicating the effect of a completely new factor: state effects.<br>

<h2>Legislation Importance</h2>

To identify which laws are most important in predicting crime, we first observe the inbuilt attribute 'feature_importance_' in the random forest regression model. From this method, we are able to see which features the algorithm uses to predict crime and which aren't as important. The assumption behind this method is that laws that contribute most to our model predictions are also the most useful for legislators to consider when deciding which laws they should pass and which ones they could potentially overlook - because every gun law that is enacted is one step further in abridging American citizens' consitutional protection.

The results that came back are interesting. According to our model, prohibited possessor laws that prohibits dealers from selling firearms to individuals who are deemed mentally incompetent or incapacitated appears to have the most effect on predicting gun violence. This, in turn, raises an interesting question:

Had this law been effective at deterring individuals who are deemed mentally incapacitated, how could Stephen Paddok, a man who, according to the police, had "bouts of depression" following his mass loss of wealth through gambling the years prior to the mass shooting, have been able to acquire assault weapons from eight different dealers in California and Nevada - both of which had the specific prohibited possessor law in place at the time of purchase?<br>

Doubting the validity of such a legislation being the most important law at curbing gun violece, we decided to evaluate the legal effectiveness more intricately through permutation of feature importance across the dataset. This would allow us to take into account both the main feature effect and the interaction effects on model performance; the interaction effects being the main concern. From the results, we observed that such prohibited possessor law, along with several others, was indeed an important in our prediction accuracy. As it turns out, laws prohibiting specific individuals who are deemed potentially dangeous to society from owing firearms the law requiring a waiting period before the physical delivery of a handgun were also extremely significant.

<h2>State Effects</h2>

Our initial concern with the randomly distributed regression model was that it may have picked up some patterns that were inherent to each state. As a result, the model would not have been predicting the number of crimes based wholly on particular laws, but rather on the patterns of laws inherent to each state. To test our hypothesis, we split the training and test sets based on state. Our model was trained on 25 randomly selected states, and tested on 27. The training set's results were unsuprising. The model predicted almost exactly the same way the previous models were predicted. Contrarily, the test set confirmed our hypthesis; it was clear that the poor predictive power of our model when the confounding variable of state was removed indicates that our model may be overfitting to individual state patterns. Luckily for us, the purpose of our endeavor was not to create a predictive model, but rather to use the attributes of predictive modelling to understand legislative significance.

<h2>Political Affiliation</h2>

From state effects, we formulated a new theory:

  - Could the rate of gun violence vary between states because of their political values?

To answer our question, we utilized data describing each states' majority political affiliation based on their elected representatives at the time. To level the results, we also factored in state populations so that the predicted crimes would be standardized based on state population. The results took us by surprise.<br>

We had initially predicted that states with a Democratic majority would have less number of gun incidents per capita. Our anticipations were based several factors. Republicans tend to be more supportive of gun rights and Second Amendment protections compared to their Democratic counterparts. This is a fact supported by the number of gun laws in effect. In Republican states, the average number of laws in effect was 11.69, whereas in Democratic states that number spikes to 20.52. However, the results speak blatantly against our predictions. Most notably, in both our predicted and actual number of crimes per 1000 people in the states, Democratic states had nearly 50% <b>more</b> gun incidents than Republican states (48.1% predicted, 48.2% actual).<br>

<b>Similar Studies</b>

Further researching this anomaly we discovered in our findings, we stumbled upon a <a href="https://www.washingtonpost.com/news/wonk/wp/2018/05/31/the-surprising-way-gun-violence-is-dividing-america/">study</a> published by Washington Post that brought up the political divide between states with different rates of gun violence. They found they in more rural, Republican states, suicide rates with firearms tended to be higher, while in more metropolitan, Democratic regions, homicides due to gun violence were higher. Our research mirrored these findings, as we found that in Democratic states, gun violence rates were higher overall.  This, however, does have ethical implications. It is imperative to consider the demographics of major cities in comparison to rural areas (diverse compared to predominantly white) when drawing conclusions from our data and using it as a legislative tool.


<h3>Future Applicability and Ethics</h3>


We believe that our findings would be very useful for political science researchers and legislators interested in exploring the effects of gun laws  - considering that our findings show why the focus shouldn't be on the number of gun laws but rather on the circumstances in which these gun laws are enacted. However, there is no one definitive reason as to why the rate of gun violence is higher in certain states and lower in other states.

In order to procure more in-depth findings, the next step in research would be to hone in on specific neighborhoods within these states and attempt to analyze both the social and economic make-up of these neighborhoods. For instance, is there a correlation between the rate of gun violence and the average salary? Could infrastructure possibly be related to the rate of gun violence? After all, gun violence stems from the person holding the gun. Therefore, what is the environment that these gun holders are in?

In earlier studies, we established that gun violence tends to affect lower income minority communities disproportionately (SF Crime Analysis, 2020). If future researchers successfully establish a more generalizable predictive model, those models could be adversely used for punitive reasons, like policing, in areas where gun vioence predictions have significant bias. For these tools to be implemented in real-world practice, they would have to be scrutinized under strict parity guidelines. Furthermore, more in-depth research bears certain privacy risks, especially when it comes to factoring in income and other sensitive information.

<h2>Conclusion</h2>

The results we have uncovered through this data investigation project provides valuable insights into the way gun violence occurs. The first speaks to the importance of certain laws over others in preventing gun violence. As the proverbial statement goes, sometimes it is not a matter of quantity but rather quality. While all firearm legislations may certainly play a role in minimizing violence, some are undoubtedly more effective than others. For one, prohibited possessor laws targeting those who are mentally ill, and those who have restaining orders, as well as laws requiring certain waiting periods before recieving weapons seem to be the primary influencers of gun violence.

State effect, and perhaps more importantly political value, also plays a pivotal role in predicting gun violence. Although the number of firearm laws enected in Democratic states nearly double that of Republican states, the rate of gun violence seem to adhere less to general expectations. It appears that in states where gun rights are more supported than gun control, gun violence occur much less frequently.
