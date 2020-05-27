---
layout: page
title: Group 04
nav_order: 9
description:
---

# Predicting Voting Patterns

**Research Question:** With the 2020 election coming up, our group thought it would be interesting to examine a question about voting trends in the United States. Especially given our backgrounds as college students who come from different urban areas (New York, Orange County, and Bay Area) we thought it would be interesting to see how different areas had different voting trends. Thus, that led us to search for datasets that were sorted by county. Given different counties, we wanted to know what are factors that we can examine to help us understand 2016 voting trends? This led us to search for different factors that are sorted by county, and we found datasets that included education, unemployment, median income, poverty, and population levels mapped to each county.  Ultimately, our research question is: **Given factors such as education, unemployment, median income, poverty levels, and population, what is the best predictor of a county’s voting habits by party for the election?**


**Finding and Assembling Data**

To find our datasets we searched for public data offered by reliable and respected sources such as the government that would have both a large amount and accurate data to work with. We were able to find our datasets from Opendatasoft and the USDA which we were able to clean Nan values and combine on the county level using each county's unique FIPS number. Using this combination of datasets were were able to separate our data into training, test, and validation groups and complete our models.

**Description of the Two Datasets**



---


**Opendatasoft Dataset** This dataset is from Opendatasoft (Opendatasoft (2016), *USA 2016 Presidential Election by County*. https://public.opendatasoft.com/explore/dataset/usa-2016-presidential-election-by-county/table/?disjunctive).state. It breaks down the results of the 2016 presidential election by each county in the US. It includes the percentages of people within each county that voted for each party in 2016, as well as the percentages of people in each county who voted for the Republican and Democratic Parties in 2008 and 2012. Additionally, it has data regarding a broad range of variables that differentiate each county, such as education level and median income, as well as the percentage of those below the federal poverty line. Overall, this dataset offeres us a preliminary view of several potential variables that we will analyze in order to determine which factor would best be able to predict a county's voting trends. However, one caution would be that the exact number of votes for each party in 2016 are not included.

**USDA Unemployment Dataset:** This dataset is from the United States Department of Agriculture (USDA) (https://www.ers.usda.gov/data-products/county-level-data-sets/download-data/). This describes county-level unemployment levels and election party data for the years 2007-2018. We will be using this set to understand if unemployment levels affect how the general population votes in presidential elections.

We merged the datasets above on the Fips of each county, which is unique to each county and found in each dataset. Then, we dropped all repeating column names, such as the name of the state or county, and then also used the below function which we wrote to check for columns that were completely full of NaN values and also dropped them. The resulting DataFrame contains important information such as the state, fips, county, total number of votes, etc. that we used for our models.

## Visualizations
We did a few different kinds of visualizations, such as plots of certain features compared to certain counties, as well as geopandas graphs of certain features. Below are some of the geopandas graphs we generated. We had some trouble with some states not properly rendering, thus we had to set those states to be 0, which is why some states are entirely green.

This below graph is the percentage of each county that voted Republican, with the key in the top right corner to demonstrate what each color corresponds to.




![alt ](images/geopandas.png)

This graph below is the percentage of each county that voted Democrat.




![alt ](images/geopandas2.png)

The below graph is the percentage of each county that is white.




![alt ](images/geopandas4.png)

The below graph is the percentage of each county that has at least a high school diploma




![alt ](images/geopandas3.png)

Overall, it was interesting to see how certain things, such as education and race, were inverse of each other in some cases, as well as how certain features closely mirrored voting patterns.

# Modeling

We decided to use Ordinary Least Squares (OLS), Ridge Regression, and Least Absolute Shrinkage and Selection Operator (LASSO) to train our models and answer which features are the best predictors of a county's voting habits. OLS is a powerful method to train our models and we used this as the basis for our understanding of how our features affected voting patterns.


---


We chose to also run a ridge regression because we found that from our OLS model our data may suffer from multicollinearity as many of our independent variables may be highly correlated (i.e. Income and Education Level). In multicollinearity, even though the least squares estimates (OLS) are unbiased, their variances are large which deviates the observed value far from the true value. By adding a degree of bias to the regression estimates, ridge regression reduces the standard errors. Ridge regression solves the multicollinearity problem through shrinkage parameter λ (lambda). This is a regularization method using l2 regularization and shrinks the value of coefficients but doesn’t reach zero, which suggests no feature selection feature.


---


We also decided to also run a LASSO regression because in addition to also penalizing the absolute size of the regression coefficients, LASSO is capable of reducing the variability and improving the accuracy of linear regression models. It uses absolute values in the penalty function instead of squares which penalizes values which cause some of the parameter estimates to turn out exactly zero. The greater the penalty applied, the further the estimates are shrunk towards absolute zero which helped in our feature selection. If group of predictors are highly correlated, lasso picks only one of them and shrinks the others to zero. This is also a regularization method, but using l1 regularization.

**Initial Steps in Model Development**

We are using a training, validation, and test split of 60/20/20 since our sample size, the number of counties in our datasets, is best suited to this split. For our initial selection of X features, we are removing all the features that are directly related to numbers of votes for political parties from the counties, as well as geographic location information of each county, because incorporating these features could cause our models to be extremely biased and could also cause overfitting. For our Y, we are choosing to use the true values of votes for the Republican Party in the year 2016 for each county, since this was one of the more salient and controversial aspects of both that election, and this will most likely also be the case in the upcoming 2020 presidential election.

We then trained models using OLS, Ridge regression, and LASSO on this initially cleaned data, before any further feature selection methods were used.



Below is the plot for the OLS residuals




![alt ](images/olsresiduals.png)

**Dimensionality Reduction**

---


*Used RFE to select 54 most useful features*

We wanted to be able to answer our research question of which features specifically were useful in understanding voting patterns. Thus, after getting a True/False array from RFE, we multipled that array with the feature names to get the most useful features. The reason why we selected 54 features is because we kept increasing the number of features until the RMSE stopped signficantly decreasing. We wanted to be able to improve the RMSE while not having to retain all of the features to be able to draw a more useful conclusion.

Here are the features that were selected using RFE



---


["At Least Bachelors's Degree" 'Graduate Degree', 'White (Not Latino) Population' 'African American Population'
 'Native American Population' 'Asian American Population'
 'Other Race or Races' 'Latino Population' 'Gini.Coefficient'
 'Management.professional.and.related.occupations' 'Service.occupations'
 'Sales.and.office.occupations' 'Farming.fishing.and.forestry.occupations'
 'Construction.extraction.maintenance.and.repair.occupations'
 'Production.transportation.and.material.moving.occupations' 'White'
 'Black' 'Hispanic' 'Asian' 'Amerindian' 'Other' 'White  Asian'
 'Sire Homogeneity' 'lat' 'Poor.physical.health.days' 'Low.birthweight'
 'Children.in.single.parent.households' 'Adult.smoking' 'Adult.obesity'
 'Diabetes' 'Uninsured' 'Unemployment' 'Annual Prcp' 'Winter Prcp'
 'Summer Prcp' 'Spring Prcp' 'Autumn Prcp' 'Annual Tavg' 'Annual Tmin'
 'Winter Tavg' 'Winter Tmax' 'Summer Tmin' 'Spring Tmax' 'Spring Tmin'
 'Autumn Tavg' 'Autumn Tmax' 'temp' 'Unemployment_rate_2010'
 'Unemployment_rate_2013' 'Unemployment_rate_2014'
 'Unemployment_rate_2015' 'Unemployment_rate_2016'
 'Unemployment_rate_2017' 'Unemployment_rate_2018']

Below is the plot for the linear model test set
![alt ](images/linear.png)



Below is the plot for the ridge model
![alt ](images/ridge.png)



Below is the plot for the LASSO model
![alt ](images/lasso.png)



**Explanation of and Reasoning for Using Models**

Using recursive feature elimination to select 50 features out of the 100+ remaining after initial training/validation/test partitioning. We applied this to each of our initial 3 models to refine them and improve them.

Although the RMSE increases and the r2 values decrease, which would suggest that the model is not as accurate after recursive feature selection as before, we believe the RFE process was still essential to answering our research question because we believe this will aid in our model's generalizability to a new dataset with more recent data about these features, that we can use to predict 2020 results. This is because the models before and after feature selection are nearly as accurate as each other, and our feature selection process is likely to minimize overfitting caused by the 100+ features from the intial model that are likely to create noise that the initial models learned from.

Our refined model both retains key features that we are interested in analyzing and minimizes the noise that could be case overfitting and bias.

**Model Results**

The model performed relatively well in all three of the training, validation, and test datsets. Our RMSE values ranged from 6.77 to 7.24 which are very similar and shows that the RFE chose relevant features without overfitting. In addition our r2 values ranged from 0.79 to 0.81, which is a very tight range and shows our model also has a good balance of bias and variance.

**Model Validation**

We will be using in-sample validation, meaning we are concerned with how well our models fit the data they have been trained on, also known as their “goodness of fit”. To validate our models we look to our Root Mean Squared Error (RMSE) and r2 test values. The RMSE provides an indication regarding the dispersion or the variability of the prediction accuracy. The r2 value is the fraction is the ratio of the residual sum of squares to the total data sum of squares. The residuals represent the difference between the prediction and reality. The closer R2 is to 1, the better the prediction.

Given our resulting r2 and RMSE values we concluded that our models performed well.





# Conclusion

**Our Conclusions**

Based on our models and feature selection processes, we can make several conclusions about the best predictors of any given county’s voting habits by party.

First, our recursive feature elimination algorithm allows us to determine the most important and predictive features in each county. There were several features that we expected to be important when formulating our research question, such as population racial demographics, population education levels, unemployment rate, and socioeconomic factors such as the Gini coefficient and children in single parent households. However, we can also conclude that there are other significant factors that we would have been less likely to expect. In particular, it was not necessarily the numerical poverty rate that was most useful in predicting voting patterns, but rather the distribution of job categories within the county, such as the proportion of the population involved in numerous professions and industries, such as service, agriculture, transportation, construction, and fishing. In addition, population health was another group of very important but often overlooked features. This included information about obesity, diabetes, smoking, and low birthweight, to name a few. Finally, a county’s average precipitation and temperature throughout the 4 seasons were also incredibly important.

We believe that these less expected features can serve to provide a stronger and more socio-cultural look at a county’s economy, since the types of jobs available and the climate play a large role on the economy that can often be overlooked in other models and studies.

Given that our models all performed fairly well regardless of the regression methods they were built on, we conclude that our model, if applied to a more recent dataset with similar information about each US county, would be able to predict with relatively high accuracy the voting patterns of each county in this upcoming 2020 presidential election. This conclusion is based on our model performance, our measures to minimize overfitting, and our incorporation of often overlooked features. With all this in mind, we believe that our methods served our goal of answering our research question very well.

**Potential Gaps**

Notably, our feature selection using recursive feature elimination, while incredibly informative and critical to our conclusions, was somewhat of an arbitrary choice, especially since the way we arrived at 54 features was not particularly rigorous. Future work by either us or another investigator may choose to incorporate other feature selection methods instead or alongside ours.

Also, with the emergence and chaos of the COVID-19 pandemic, several of the features that we concluded to be important are likely to undergo drastic changes from 2019 to 2020, such as unemployment rates and population health, which have already dramatically increased and decreased, respectively. This could pose a gap in our work in this project since the accuracy of our models when applied to a potential 2020 dataset could quite possibly be adversely affected. While 2019 data could be used as a substitute, another investigator could possibly consider training a model that takes 2020 into account as well, in order to predict the 2024 presidential election, since 2020 data may contain outliers.

Finally, presidential elections themselves only occur once every 4 years, which is a long time for things to change, and means that any model built to predict future elections would only really be able to be tested once every 4 years in the real world as well. One thing we could do differently, or another investigator may consider, is to try to apply these datasets to predict and find the best features to predict congressional elections in addition to presidential elections.

**Legal, Policy, and Ethical Implications**

If presidential candidates are aware of features that best predict that a county will vote for their party, it could lead to pandering and grand promises that may not necessarily be met, which would mean that models such as ours can lead to the legal and ethical concern of dishonesty in campaigning, for the purpose of getting into office. These kinds of issues could also apply if a candidate is up for reelection, since they can look at voting patterns and distributions in each county, and specifically tailor policies to be favorable to states or counties they or their party previously only lost by a small margin, in order to somewhat buy votes, which creates policy and ethical concerns as well.


```python

```
