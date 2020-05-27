---
layout: page
title: Group 05
nav_order: 10
description:
---

## **Will a reduction in Short Term Rental competition lead to an increase in listing prices in San Francisco?**


## **PROJECT DESCRIPTION**

In 2017 legislation was enacted that required AirBnb hosts to register all of their short term rentals with the city of San Francisco and banned any stays longer than 90 days. Our team hypthothesized that the decrease in supply of Short Term rentals would result in a spike of the average pricing. To analyze the proposed trend we took the data from insideairbnb and SF Airbnb Listings which provided the listing price, amount of listings, and the locations of lisitngs in San Francisco. The data that we took was the pricing for listings, and the amount of listings before the ban in 2017, this data was compared to the numbers that we found after the effective date of the law. Our model first split the data with a test-train-validate split, which was used to construct a cross-validation ridge regression model to identify any correlation between the volume of listings and price of listings. To more closely analyze our findings we crafted a choropleth maps and bar charts to provide visual analysis.



## **FINDINGS**

Based on our model it is evident that the regulation imposed on short-term housing for Airbnb showed that there was no statistically significant effect on the price of future listings for short-term rentals on Airbnb. The visuals we used in our analysis are presented below.



### **Visualizations**

Below, there is a chart showing the mean listing reviews_per_month as the y value and the month that value was reported as the x value. As shown, there is a clear increase in the reviews_per_month post September 2017, which supports our hypothesis that the demand for short term rentals was consistent even while the number of listings decrease. Therefore, as a result there was a spike in the average stays per listing, and following a spike in reviews per listing, as well. It appears that based on the results the STR regulation had substantial positie impacts in San Francisco, the benefits include a more affordable price for customers, and as rate of stays decreased more people have access to long term affordable housing, lastly, the city likely saw an increase in revenue due to the collected fines for houses that did not properly register their AirBnb with the city.

Related to the COVID-19 crisis, review rates decreased from Jan. 2020 - April 2020, likely because the issued shelter in place.


![Picture](https://drive.google.com/uc?id=18SFnQzgH8c5rFMZeyAlyEgy-4Frnd8nP)

Below the mean listing price is shown as the y value and the month that value was reported as the x value. The data shows a -10% decrease in mean price for SF AirBnB listings from Sept. 2017 to Oct. 2017, this trend is a result of AirBnB removing any listed rentals that were not compliant with any of the policies enacted by the city. Based on the prediction model the major decrease in short term rental housing on Airbnb did not result in a rise in market price in 2018 in a statistically significant way. This trend was not consistent with what we expected a reduction in listings to result in a jump in mean price with a constant demand.

![Picture](https://drive.google.com/uc?id=1JWfNdlRRrZCPdWhaIpUXeDEP1T4tp7IP)

Below the drop in listings from 2017-2018 was a consequence of the regulations put into place in the city. We suspect that the proceeding increase was a result of more rentals that were compliant and an increase in short term demand for business travel.



![Picture](https://drive.google.com/uc?id=1sg2BBBGvyJ_CDZI21rxeflJYnKoIiWGa)

Comparing the two maps you can see the stark decrease in listing density resulting from increased STR regulation.


![Picture](https://drive.google.com/uc?id=1JvWQPS7TOjmyKgsaYPZMI9ml0HDdcYaX)



![Picture](https://drive.google.com/uc?id=1Did0AZkFh2t1Up5hk4C2HpiNtnU3Ja-K)

The choropleth map shows a strong clustering of rentals in the financial district in May of 2018, more so than June of 2017. The reason we suspect is that the decrease in price made the short term rentals at AirBnB more attractive, and business stays increased and drew away customers from the hotel industry. It would be interesting to further analyze the impact these regulations had on the hotel industry.

## **Conclusions** (also included in the final project model previously submitted)

The overall methods we used in analysis were very successful in identifying questiosn and theories that we presented at the beginning of the examination. In the tremendous amount of research we conducted we continuously posed new questions and altered the scope of what we were conducting. The utilized model and training features were instrumental in finding our conclusions and digging into underlying trends. The RMSE and accuracy could have been adjusted to prove more accurate results but for the purpose of our analysis, they presented adequate data. Upon further investigation, it would be interesting to see how the regulation impacted AirBnb as a company, especially with San Francisco being such a high volume area of rentals.

"What this implies beyond a Python notebook is that the market does self-regulate to some extent. Airbnb revealed that of the 4,780 listings that were removed as a result of the 2017 legislation, over 70% had not been booked in the previous 6 months. From a legal perspective, this means that the SF short-term rental legislation did not negatively affect property owners or Airbnb significantly - a legislative success. Future policy initiatives that wish to impact Airbnb as little as possible should aim to follow San Francisco's work. We can also conclude that these regulations turned out to pose no ethical dilemmas for the sake of local property owners. Those who were legally renting out properties before the rules were put in place continue to do so with seemingly no change to their income.

What would be interesting for future research is the impact that the legislation had on the long-term housing market in San Francisco. From the research that we have gathered, the motivation behind such regulations all across the world is to decrease long-term housing prices in the area. Profits from Airbnb incentivize large property management companies to buy up properties from individuals in order to use them as permanent Airbnbs, shorting the supply of housing for residents in the area and in turn driving up market prices. It would be significant to analyze whether this kind of regulation has actually succeeded in achieving their goal, that is, if local long-term property prices actually decreased after such regualtion went into place. We attempted to answer this question for a brief period of time until it proved to be ultimately too difficult to gather a comprehensive data set from just Zillow. In the future, if we were able to access information from paid real estate databases for the area, I believe it would be wholly possible to conduct meaningful research on this posed question."


```python

```
