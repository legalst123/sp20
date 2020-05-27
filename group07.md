---
layout: page
title: Group 07
nav_order: 12
description:
---


## What factors determine performance within the Scholastic Assessment Test (SAT) in New York City?

![alt text](Images/SAT.jpg)

# I. Introduction

[Kaggle Dataset](https://www.kaggle.com/nycopendata/high-schools)

Standardized testing is one of the biggest, if not the biggest, metrics of educational merit that this country relies upon. The SAT, which is taken by at least 2 million students nationwide every year, has become the gate that must be passed before high schoolers can advance to college. In 2019, the SAT was the focus of the national spotlight after various cheating scandals regarding the testing infrastructure came to light, bringing skepticism over the legitimacy and credibility of the tests themselves. Given the importance of the test, we decided to take a look into the data behind standardized testing and find key factors that played a pivotal role in determining the performance of students. For this particular task, we focused our efforts on the NYC 2014-2015 SAT Scores data set provided by Kaggle, which was categorized by individual schools spanning the NYC area.

# II. The Data

Our first steps in analyzing the data was to select a few of the features from the data set that we wanted to focus our analysis on. Since each individual entry was a unique high school in NYC, we ran different group by functions on the features given by the dataset. The first one of these features was the distribution of scores amongst the individual boroughs within NYC. We grouped the data by the boroughs and aggregated by the average cumulative SAT score in each entry.

![alt text](Images/BarGraph.jpg)

As we can see from the resulting graph, it seems that the distribution amongst the boroughs remains even throughout. Since the average SAT Score for each borough is so similar to each other, we eliminated this feature as a key indicator for predicting SAT scores. Our next focus was the enrollment numbers within each individual school, we looked to see whether the number of students in each school differentiated the scores.

![alt text](Images/Scatter1.png)

Our scatter plot revealed that there was an association that existed between the number of students enrolled and the average SAT score. While it wasn’t a strong predictor, it helped us direct our focus to the amount of students as a key feature. We decided to look deeper into this particular facet and compared the percentage of students tested within a school to the Average SAT score.


![alt text](Images/Scatter2.png)

The visualization above provides us a valuable link between the SAT Scores and the percent tested feature. A possible explanation for the relationship we see is that the schools with a higher percentage of students taking the test have tailored their curriculum to address the SAT. It’s clear that schools that boast a higher turnout to the tests result in a higher average SAT score. However, we also wanted to examine the possible geographical factors within the data.

![alt text](Images/MapSS.png)

The following is a choropleth map of NYC where each area is separated by a NYC neighborhood json file. The purpose of this map is to help visualize any clusters that may be present within the SAT score distribution across NYC. The map does reveal that there are clusters present within the data. Many neighboring areas hold similar SAT score averages and there are clear lines of boundary between different tiers of scores.

# III. The Model

Analyzing the data showed us that there were correlations and relationships between the features of the dataset and the average SAT score. Based on this result, we decided to train a model on the data to assess and predict SAT scores based on the features within the data set. We employed the use of three different regression models: a Linear Regression Model, a Ridge Regression Model, and a LASSO Regression Model.


![alt text](Images/LinearModel.png)

The linear regression model (or OLS) provides a baseline look at the performance of the model since it gives all the features provided the same weight. When assessing the results of our linear model, we can see a definite correlation between the actual and predicted values, signalling the credibility and reliability of the model.

![alt text](Images/RidgeModel.png)

While the Ridge Regression model is very similar to the OLS model, it is slightly different in that it adds a constraint, forcing the coefficients to be lower, but not to zero. By aiming to minimize the impact of less important variables, the Ridge Regression model achieves a higher bias and lower variance. In regards to our dataset, it will help us see whether there are features that may be inhibiting the model’s accuracy.

![alt text](Images/LASSOmodel.png)

Alongside the Ridge model, the LASSO model also decreases the impact of less important variables. However, the LASSO model can throw out variables if the parameter is driven to zero. By implementing the LASSO model on the dataset, we can achieve a result that will have a low variance but a high bias. While this may not sound ideal, it gives us a good picture of which features are important to the model. After training all three models on our training-validation split, we ended up with the following RMSE values:

![alt text](Images/ValRMSE.png)

As we can see from the metrics above, our Linear Model model is performing the best. Before testing the model on the test set, we decided to implement feature selection to help tune the model. To do this, we ran a correlation matrix on the dataset to reveal which features correlated the highest with predicting the SAT score.

![alt text](Images/CorrMatrix.png)

The features that were most significant within the correlation matrix were the Percent Tested, Percent White, and Percent Asian. Based on these findings, we trained an OLS model on these features only so the constraints of the LASSO and Ridge would not apply to them.

![alt text](Images/FeaturesRMSE.png)

However, the feature selection did not achieve the result we were hoping for. Instead of lowering the rmse, it increased it instead. Ultimately, we decided to use the original Linear model with all the features included as our final model since it had the lowest RMSE of all the models we tried.

![alt text](Images/TestSet.png)

The rmse is relatively low within the final model predictions, so we can say the LASSO model performed well.

# IV. Conclusion

The ultimate purpose of this study was to analyze what factors determine performance on the SAT in New York City. In our approach we gathered test scores from highschools during the 2014-2015 school year. By cleaning the data, we were able to create visualizations that would help us pinpoint key factors to explain the distribution of SAT scores across NYC.
In examining the different visualizations it became very clear that the percent of students tested and majority of racial makeup at individual schools were the strongest factors in determining SAT performance. The scatter plot “Average SAT Score of a NYC High School vs. How Many Students Took it”, shows a notable trend where the percent of students who took the SAT in a school has a positive correlation with average SAT score. This means that if a higher percentage of students register for the SAT at a particular school, the students at that school should receive higher scores on average. One explanation for this could be the amount of resources devoted to preparing students for the SAT. Schools where almost all of the students register will probably devote more time and resources to preparing their students for the test, as opposed to schools with a small percentage of students registered they can't spend as much time if any at all because a majority of the class is not taking the test. In further research it would be interesting to analyze why some schools have much lower SAT participation than others, maybe looking at average income and parents level of education. The SAT costs money to sign up for and many students may feel that it is not worth it.

The scatter plot, “Majority Racial Makeup of Schools and SAT Score”, shows, on average, that schools with a majority of White and Asian students score higher than schools with majority of Black or Hispanic students. In regards to race, there are a lot of things that could be at play. Through policy, our country is still seeing the effects of redlining in our communities. Redlining is especially seen in schools, since public schools are partially funded by property taxes. Since Redlining confined Black and Hispanic people to only live in poorer areas, meaning their public schools are often not up to par with schools with majority White students. There also could be a difference in accessibility to private schools for students based on race. In further research, it would be interesting to examine the possible difference in scores between private schools and public schools.

It is very interesting to examine these different factors at play that drastically affect the scores and futures of so many students. We believe that an area that could be explored even further would be income, not only of each student but possibly of each borough or area code. Also, many students attend schools outside of their neighborhood or borough; this made it difficult for the chloropleth maps to find many patterns. After looking at the different models that affect SAT scores, it is apparent that race and a school's focus on the test are huge factors. We suspect that those factors stem from different policies and income inequality between students. For future research, it would be very helpful to examine the average income for each school. Since a major factor for SAT scores was how many students participated and how much a school focused on it, it would be interesting to gather statistics of students who sign up for SAT prep courses offered outside of their school. Our data concluded that major determining factors in an SAT score comes down to racial makeup of a school, ability to pay, and resources dedicated to preparation. With this conclusion, it can be inferred that a major underlying factor in determining a students test score is their income. In future tests, it would be very beneficial to examine this relationship.



```python

```
