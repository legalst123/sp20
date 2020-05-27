---
layout: page
title: Group 12
nav_order: 17
description:
---

# **Analysis of Crime in Sanctuary vs Non-Sanctuary Cities**

UC Berkeley, LEGALST 123 - Data, Prediction and Law (Spring 2020)

Claire Black, Hunter Bjazevich, Anna Gueorguieva, Alyssa Lau


**Introduction to Research Question and Dataset:**

Donald Trump has been on record saying that we must "end the sanctuary cities that have resulted in so many needless deaths. Cities that refuse to cooperate with federal authorities will not receive taxpayer dollars, and we will work with Congress to pass legislation to protect those jurisdictions that do assist federal authorities"  [(Trump Immigration speech, Pheonix AZ, August 2016)](https://www.washingtonpost.com/news/the-fix/wp/2016/08/31/heres-what-donald-trump-said-in-his-big-immigration-speech-annotated/).

Our goal is to test the claim that sanctuary cities cause "so many needless deaths" and whether President Trump's proposal to freeze federal funding to these cities holds any merit by investigating whether sanctuary cities tend to have higher violent crime rates than non-sanctuary cities.

Our preliminary analysis serves the purpose to help us form a hypothesis and begins with looking at a single city and investigating violent crime rates both before and after that city received their sanctuary status.  For this, we chose to analyze violent crime rates in Los Angeles, California, which became a sanctuary city after the passing of California Senate Bill 54 declared the state of California as a sanctuary state in 2017.  

**The importance of understanding and sorting different types of crime:**

An analysis of crime rate changes using all types of crime may become convoluted and fail to provide a useable conclusion. In order to create conclusions with the most impact, we must first understand which types of crime are most relevant to our analysis.

By creating data frames that sort the top crimes pre-sanctuary city policy vs post-sanctuary city policy, we better understand the dataset and the human contexts from which it arose. These human contexts must be remembered throughout the analysis of data, as our social structure will impact that data we see. Some crimes are historically more reported than others due to social factors. For example, our data includes intimate partner rape. This is more likely to go unreported than forcible rape from a non-intimate partner due to different contexts in which the crime occurs, and is something we should take into account when forming a conclusion.

Below is the first five rows of a table representing crime in LA from 2010-2019. It includes many features such as: the date the crime was reported, the data occurred, which neighborhood, what type of crime, information about the victim, and exact coordinate locations of the crime.





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
      <th>DR_NO</th>
      <th>Date Rptd</th>
      <th>DATE OCC</th>
      <th>TIME OCC</th>
      <th>AREA</th>
      <th>AREA NAME</th>
      <th>Rpt Dist No</th>
      <th>Part 1-2</th>
      <th>Crm Cd</th>
      <th>Crm Cd Desc</th>
      <th>Mocodes</th>
      <th>Vict Age</th>
      <th>Vict Sex</th>
      <th>Vict Descent</th>
      <th>Premis Cd</th>
      <th>Premis Desc</th>
      <th>Weapon Used Cd</th>
      <th>Weapon Desc</th>
      <th>Status</th>
      <th>Status Desc</th>
      <th>Crm Cd 1</th>
      <th>Crm Cd 2</th>
      <th>Crm Cd 3</th>
      <th>Crm Cd 4</th>
      <th>LOCATION</th>
      <th>Cross Street</th>
      <th>LAT</th>
      <th>LON</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1307355</td>
      <td>02/20/2010 12:00:00 AM</td>
      <td>02/20/2010 12:00:00 AM</td>
      <td>1350</td>
      <td>13</td>
      <td>Newton</td>
      <td>1385</td>
      <td>2</td>
      <td>900</td>
      <td>VIOLATION OF COURT ORDER</td>
      <td>0913 1814 2000</td>
      <td>48</td>
      <td>M</td>
      <td>H</td>
      <td>501.0</td>
      <td>SINGLE FAMILY DWELLING</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>AA</td>
      <td>Adult Arrest</td>
      <td>900.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>300 E  GAGE                         AV</td>
      <td>NaN</td>
      <td>33.9825</td>
      <td>-118.2695</td>
    </tr>
    <tr>
      <th>1</th>
      <td>11401303</td>
      <td>09/13/2010 12:00:00 AM</td>
      <td>09/12/2010 12:00:00 AM</td>
      <td>45</td>
      <td>14</td>
      <td>Pacific</td>
      <td>1485</td>
      <td>2</td>
      <td>740</td>
      <td>VANDALISM - FELONY ($400 &amp; OVER, ALL CHURCH VA...</td>
      <td>0329</td>
      <td>0</td>
      <td>M</td>
      <td>W</td>
      <td>101.0</td>
      <td>STREET</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>740.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SEPULVEDA                    BL</td>
      <td>MANCHESTER                   AV</td>
      <td>33.9599</td>
      <td>-118.3962</td>
    </tr>
    <tr>
      <th>2</th>
      <td>70309629</td>
      <td>08/09/2010 12:00:00 AM</td>
      <td>08/09/2010 12:00:00 AM</td>
      <td>1515</td>
      <td>13</td>
      <td>Newton</td>
      <td>1324</td>
      <td>2</td>
      <td>946</td>
      <td>OTHER MISCELLANEOUS CRIME</td>
      <td>0344</td>
      <td>0</td>
      <td>M</td>
      <td>H</td>
      <td>103.0</td>
      <td>ALLEY</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>946.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1300 E  21ST                         ST</td>
      <td>NaN</td>
      <td>34.0224</td>
      <td>-118.2524</td>
    </tr>
    <tr>
      <th>3</th>
      <td>90631215</td>
      <td>01/05/2010 12:00:00 AM</td>
      <td>01/05/2010 12:00:00 AM</td>
      <td>150</td>
      <td>6</td>
      <td>Hollywood</td>
      <td>646</td>
      <td>2</td>
      <td>900</td>
      <td>VIOLATION OF COURT ORDER</td>
      <td>1100 0400 1402</td>
      <td>47</td>
      <td>F</td>
      <td>W</td>
      <td>101.0</td>
      <td>STREET</td>
      <td>102.0</td>
      <td>HAND GUN</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>900.0</td>
      <td>998.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>CAHUENGA                     BL</td>
      <td>HOLLYWOOD                    BL</td>
      <td>34.1016</td>
      <td>-118.3295</td>
    </tr>
    <tr>
      <th>4</th>
      <td>100100501</td>
      <td>01/03/2010 12:00:00 AM</td>
      <td>01/02/2010 12:00:00 AM</td>
      <td>2100</td>
      <td>1</td>
      <td>Central</td>
      <td>176</td>
      <td>1</td>
      <td>122</td>
      <td>RAPE, ATTEMPTED</td>
      <td>0400</td>
      <td>47</td>
      <td>F</td>
      <td>H</td>
      <td>103.0</td>
      <td>ALLEY</td>
      <td>400.0</td>
      <td>STRONG-ARM (HANDS, FIST, FEET OR BODILY FORCE)</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>122.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8TH                          ST</td>
      <td>SAN PEDRO                    ST</td>
      <td>34.0387</td>
      <td>-118.2488</td>
    </tr>
  </tbody>
</table>
</div>







Some of the data needs to be cleaned. Since we are investigating crime rates before and after the passing of California SB 54, there are a number of features we do not need to include (like victim sex), especially if some columns may pose problems if left as is. Also, we have to appropriately replace NaNs and 0s.




Some columns have NaNs or 0s, and depending on the column, we will imputate them with either a 0 or the column average.  For example, victim ages listed as 0 will be replaced with the column average, and columns like 'Weapon Used Cd' will be replaced by a 0, which we will interpret as a weapon not being used.

Below is a cleaned version of crime in LA which allows for easier data manipulation and analysis.


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
      <th>Date Rptd</th>
      <th>DATE OCC</th>
      <th>Year</th>
      <th>TIME OCC</th>
      <th>AREA</th>
      <th>AREA NAME</th>
      <th>Crm Cd</th>
      <th>Crm Cd Desc</th>
      <th>Vict Age</th>
      <th>Vict Descent</th>
      <th>Premis Cd</th>
      <th>Weapon Used Cd</th>
      <th>Weapon Desc</th>
      <th>Status</th>
      <th>Status Desc</th>
      <th>Crm Cd 1</th>
      <th>LAT</th>
      <th>LON</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2010-02-20</td>
      <td>2010-02-20</td>
      <td>2010</td>
      <td>1350</td>
      <td>13</td>
      <td>Newton</td>
      <td>900</td>
      <td>VIOLATION OF COURT ORDER</td>
      <td>48.000000</td>
      <td>H</td>
      <td>501.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>AA</td>
      <td>Adult Arrest</td>
      <td>900.0</td>
      <td>33.9825</td>
      <td>-118.2695</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2010-09-13</td>
      <td>2010-09-12</td>
      <td>2010</td>
      <td>45</td>
      <td>14</td>
      <td>Pacific</td>
      <td>740</td>
      <td>VANDALISM - FELONY ($400 &amp; OVER, ALL CHURCH VA...</td>
      <td>31.765902</td>
      <td>W</td>
      <td>101.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>740.0</td>
      <td>33.9599</td>
      <td>-118.3962</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2010-08-09</td>
      <td>2010-08-09</td>
      <td>2010</td>
      <td>1515</td>
      <td>13</td>
      <td>Newton</td>
      <td>946</td>
      <td>OTHER MISCELLANEOUS CRIME</td>
      <td>31.765902</td>
      <td>H</td>
      <td>103.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>946.0</td>
      <td>34.0224</td>
      <td>-118.2524</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2010-01-05</td>
      <td>2010-01-05</td>
      <td>2010</td>
      <td>150</td>
      <td>6</td>
      <td>Hollywood</td>
      <td>900</td>
      <td>VIOLATION OF COURT ORDER</td>
      <td>47.000000</td>
      <td>W</td>
      <td>101.0</td>
      <td>102.0</td>
      <td>HAND GUN</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>900.0</td>
      <td>34.1016</td>
      <td>-118.3295</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2010-01-03</td>
      <td>2010-01-02</td>
      <td>2010</td>
      <td>2100</td>
      <td>1</td>
      <td>Central</td>
      <td>122</td>
      <td>RAPE, ATTEMPTED</td>
      <td>47.000000</td>
      <td>H</td>
      <td>103.0</td>
      <td>400.0</td>
      <td>STRONG-ARM (HANDS, FIST, FEET OR BODILY FORCE)</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>122.0</td>
      <td>34.0387</td>
      <td>-118.2488</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2114086</th>
      <td>2019-03-28</td>
      <td>2019-03-28</td>
      <td>2019</td>
      <td>400</td>
      <td>6</td>
      <td>Hollywood</td>
      <td>648</td>
      <td>ARSON</td>
      <td>31.765902</td>
      <td>X</td>
      <td>706.0</td>
      <td>506.0</td>
      <td>FIRE</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>648.0</td>
      <td>34.0962</td>
      <td>-118.3490</td>
    </tr>
    <tr>
      <th>2114087</th>
      <td>2019-08-15</td>
      <td>2019-08-14</td>
      <td>2019</td>
      <td>1810</td>
      <td>7</td>
      <td>Wilshire</td>
      <td>331</td>
      <td>THEFT FROM MOTOR VEHICLE - GRAND ($400 AND OVER)</td>
      <td>40.000000</td>
      <td>W</td>
      <td>101.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>331.0</td>
      <td>34.0871</td>
      <td>-118.3732</td>
    </tr>
    <tr>
      <th>2114088</th>
      <td>2019-01-06</td>
      <td>2019-01-06</td>
      <td>2019</td>
      <td>2100</td>
      <td>20</td>
      <td>Olympic</td>
      <td>930</td>
      <td>CRIMINAL THREATS - NO WEAPON DISPLAYED</td>
      <td>46.000000</td>
      <td>B</td>
      <td>102.0</td>
      <td>400.0</td>
      <td>STRONG-ARM (HANDS, FIST, FEET OR BODILY FORCE)</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>930.0</td>
      <td>34.0637</td>
      <td>-118.2870</td>
    </tr>
    <tr>
      <th>2114089</th>
      <td>2019-10-17</td>
      <td>2019-10-16</td>
      <td>2019</td>
      <td>1800</td>
      <td>17</td>
      <td>Devonshire</td>
      <td>420</td>
      <td>THEFT FROM MOTOR VEHICLE - PETTY ($950 &amp; UNDER)</td>
      <td>31.765902</td>
      <td>0</td>
      <td>101.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>420.0</td>
      <td>34.2266</td>
      <td>-118.5085</td>
    </tr>
    <tr>
      <th>2114090</th>
      <td>2019-02-01</td>
      <td>2019-02-01</td>
      <td>2019</td>
      <td>1615</td>
      <td>8</td>
      <td>West LA</td>
      <td>330</td>
      <td>BURGLARY FROM VEHICLE</td>
      <td>33.000000</td>
      <td>W</td>
      <td>707.0</td>
      <td>0.0</td>
      <td>0</td>
      <td>IC</td>
      <td>Invest Cont</td>
      <td>330.0</td>
      <td>34.0420</td>
      <td>-118.4531</td>
    </tr>
  </tbody>
</table>
<p>2114091 rows × 18 columns</p>
</div>



**1. Trends in violent crime in LA from 2010 to 2019:**

President Trump posits that violent crime rates are inflated under systems of sanctuary cities.  Because of this, we will focus on violent crime rates, and not all instances of crime because for this analysis certain crimes, such as embezzlement, are irrelevant.

LA times lists "violent crime" as homicide, rape, assault, robbery. According to the FBI, nationally, the top violent crimes are aggravated assaults (62.5% of crime), robbery (29.5%), forcible rape (6.8%), and murder (1.2%). So, I will isolate these four categories to form a data frame for violent crime.

Source: https://ucr.fbi.gov/crime-in-the-u.s/2010/crime-in-the-u.s.-2010/violent-crime




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
      <th>AREA</th>
    </tr>
    <tr>
      <th>Year</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2010</th>
      <td>12270</td>
    </tr>
    <tr>
      <th>2011</th>
      <td>11285</td>
    </tr>
    <tr>
      <th>2012</th>
      <td>10293</td>
    </tr>
    <tr>
      <th>2013</th>
      <td>9073</td>
    </tr>
    <tr>
      <th>2014</th>
      <td>9356</td>
    </tr>
    <tr>
      <th>2015</th>
      <td>10605</td>
    </tr>
    <tr>
      <th>2016</th>
      <td>11955</td>
    </tr>
    <tr>
      <th>2017</th>
      <td>12455</td>
    </tr>
    <tr>
      <th>2018</th>
      <td>11825</td>
    </tr>
    <tr>
      <th>2019</th>
      <td>10851</td>
    </tr>
  </tbody>
</table>
</div>



The 'violent_df' dataframe above gives the counts of violent crimes per year from 2010 to 2019.  Looking at the violent crime counts in a vacuum, there does not seem to be any discernible difference in the number of violent crimes as the counts look relatively uniform.

Below we have plotted several crime trends. The first plot gives a sense of crime trends from 2010 to 2019, while the second plot hones in on the crime rates from 2016 to 2019, two years before and two years after the passage of California SB 54 declared California as a sanctuary state.






![png](output_19_1.png)



![png](output_20_0.png)


It does appear that if we group the number of crimes per year that the total number of violent crimes decreased substantially between 2017 and 2019, which was immediately after California became a sanctuary state. This could be for a variety of reasons, but if we were to look at this in a vacuum, we see that crime rates actually decreased with the passing of this bill in Los Angeles.  This does not disprove President Trump's proposition, but does serve to prove that sanctuary cities do not have a statistically significant effect on violent crime rates.



**2. Finding Top 5 Crimes of Pre and Post Senate Bill**

The first table below represent the top 5 crimes occuring in LA in 2016 & 2017 (pre-sanctuary bill) and the second table represents the top 5 crimes occuring in LA in 2018 & 2019 (post-sanctuary bill). Counts in the post-sanctuary bill table do seem to decrease in comparison to the first table, however there are many other factors that could have impacted this change and thus we cannot make any direct conclusions yet.




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
      <th>Count Pre-Sanct</th>
    </tr>
    <tr>
      <th>Crime Type</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>ROBBERY</th>
      <td>18576</td>
    </tr>
    <tr>
      <th>ATTEMPTED ROBBERY</th>
      <td>2558</td>
    </tr>
    <tr>
      <th>RAPE, FORCIBLE</th>
      <td>2466</td>
    </tr>
    <tr>
      <th>CRIMINAL HOMICIDE</th>
      <td>576</td>
    </tr>
    <tr>
      <th>RAPE, ATTEMPTED</th>
      <td>234</td>
    </tr>
  </tbody>
</table>
</div>




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
      <th>Count Post-Sanct</th>
    </tr>
    <tr>
      <th>Crime Type</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>ROBBERY</th>
      <td>17397</td>
    </tr>
    <tr>
      <th>ATTEMPTED ROBBERY</th>
      <td>2555</td>
    </tr>
    <tr>
      <th>RAPE, FORCIBLE</th>
      <td>2040</td>
    </tr>
    <tr>
      <th>CRIMINAL HOMICIDE</th>
      <td>513</td>
    </tr>
    <tr>
      <th>RAPE, ATTEMPTED</th>
      <td>171</td>
    </tr>
  </tbody>
</table>
</div>



# Hypothesis:

Our data frame illustrates that the top 5 crimes have not changed, nor has the relative frequency for which the top 5 crimes occur. Based on the preliminary comparisons between the 'Count' column of pre-sanctuary policy crimes and post-santuary policy crimes, there was a decrease in violent crime following the implementation of sanctuary policies in Los Angeles.  This is not to say that sanctuary declaration was responsible for decrease in violent crime rates since there are numerous things that can contribute to this, but is indicative of the lack of evidence for sanctuary cities increasing crime rates.  Using our above analysis of Los Angeles, we hypothesize that santuary city policies do **not** have any significant effect on violent crime rates, and thus believe President Trump's proposition to withhold federal funding from sanctuary cities and states is misguided. Further in-depth analysis of this data, along with additional data can provide evidence for this hypothesis.



# Machine Learning Experiment

If sanctuary cities are actually an indicator of increased crime rates in a given city, theoretically one would be able to predict with accuracy whether or not a given city is a sanctuary city based on their violent crime rates. To investigate this, we are going to create several classification models to predict whether a city is either a sanctuary city (1) or a non-sanctuary city (0).

We have compiled a long list of cities and their rates of violent crime spanning from 2010-2015. This data was consolidated by the Marshall Project using the Uniform Crime Reporting Statistics, an organization under the umbrella of the United States Department of Justice.

We classified cities as sanctuary cities according to their sanctuary status listed by the [Center For Immigration Studies](https://https//cis.org/Map-Sanctuary-Cities-Counties-and-States). If a city was listed in a sanctuary state or sanctuary county, that city would also be listed as a sanctuary city. If a city was first declared a sanctuary city sometime in between 2010-2015, the sanctuary status feature is coded as 0 for the years before the declaration and as 1 for the years after. The violent crime statstics we are using as features include total violent crime rate, homicide rate, rape rate, and aggravated assault rate. We chose to use violent crime rates, rather than total violent crime instances, to account for the variance in population size for cities.

The data in the csv file below has already been cleaned.





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
      <th>department_name</th>
      <th>year</th>
      <th>Sanctuary Status</th>
      <th>total_pop</th>
      <th>violent_per_100k</th>
      <th>homs_per_100k</th>
      <th>rape_per_100k</th>
      <th>rob_per_100k</th>
      <th>agg_ass_per_100k</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Albuquerque</td>
      <td>2010</td>
      <td>0</td>
      <td>545852</td>
      <td>786.110521</td>
      <td>7.694393</td>
      <td>61.921546</td>
      <td>172.207851</td>
      <td>544.286730</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albuquerque</td>
      <td>2011</td>
      <td>0</td>
      <td>551961</td>
      <td>762.735048</td>
      <td>6.884544</td>
      <td>47.829466</td>
      <td>180.809876</td>
      <td>527.211162</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Albuquerque</td>
      <td>2012</td>
      <td>0</td>
      <td>553684</td>
      <td>749.705608</td>
      <td>7.404946</td>
      <td>50.209145</td>
      <td>197.224410</td>
      <td>494.867108</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Albuquerque</td>
      <td>2013</td>
      <td>0</td>
      <td>558165</td>
      <td>774.860480</td>
      <td>6.628864</td>
      <td>78.650578</td>
      <td>187.399783</td>
      <td>502.181255</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Albuquerque</td>
      <td>2014</td>
      <td>1</td>
      <td>558874</td>
      <td>882.846581</td>
      <td>5.367936</td>
      <td>71.930346</td>
      <td>247.103998</td>
      <td>558.444300</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>398</th>
      <td>Wichita</td>
      <td>2011</td>
      <td>0</td>
      <td>384796</td>
      <td>770.018399</td>
      <td>6.496949</td>
      <td>63.670101</td>
      <td>127.340201</td>
      <td>572.511149</td>
    </tr>
    <tr>
      <th>399</th>
      <td>Wichita</td>
      <td>2012</td>
      <td>0</td>
      <td>386409</td>
      <td>749.464945</td>
      <td>5.952242</td>
      <td>62.627941</td>
      <td>128.361399</td>
      <td>552.523363</td>
    </tr>
    <tr>
      <th>400</th>
      <td>Wichita</td>
      <td>2013</td>
      <td>0</td>
      <td>386486</td>
      <td>794.077923</td>
      <td>3.881124</td>
      <td>64.685396</td>
      <td>120.832320</td>
      <td>604.679083</td>
    </tr>
    <tr>
      <th>401</th>
      <td>Wichita</td>
      <td>2014</td>
      <td>0</td>
      <td>387493</td>
      <td>758.465314</td>
      <td>5.419453</td>
      <td>62.710810</td>
      <td>128.002312</td>
      <td>562.332739</td>
    </tr>
    <tr>
      <th>402</th>
      <td>Wichita</td>
      <td>2015</td>
      <td>0</td>
      <td>389824</td>
      <td>984.803398</td>
      <td>6.926203</td>
      <td>89.527582</td>
      <td>188.033574</td>
      <td>700.316040</td>
    </tr>
  </tbody>
</table>
<p>403 rows × 9 columns</p>
</div>



For our classification models, we will need to split the data into training, validation, and test sets. 80% of the data will go into training and 20% into testing. From there, 25% of the training data will be used as a validation set to test our models before applying them to the final test set.




**Discussion of Classification models - Linear SVM Classifier**

The first classification model we will be using is a Linear SVM classifier like the one we saw in a guest lecture to reverse engineer the COMPAS algorithm, as well as in lab. If violent crime rates are truly predictive of whether or not a city is a sanctuary city, then our model, trained with features related to violent crime rates, should be able to accurately classify cities into "Sanctuary" and "Non-Sanctuary."

There are certain advantages and disadvantages of using Linear SVM to classify our cities as either a sanctuary city or non-sanctuary city.  The first advantage, and also the reason we chose to start with Linear SVM, is that the method is fairly simple for two-group classification problems like the one we are investigating.  This essentially creates a linear decision boundary when working in two-dimensional space.  Anything falling on one side of the line will serve as one classification, and the other side will serve as another classification.  With SVM, if there is not a clear linear decision boundary, one could add additional dimensions until there is a clear boundary.  However, in our case we will only be working with *Linear* SVM.

The obvious disadvantage is that this method may oversimplify classification problems.  There may not always be separable data where one set of actual data is separated from the opposite classification.  Because of this, the model may not accurately classify correctly or perform well when applied to new data.  Another disadvantage stems from potentially long training time when first training the model.  We did not experience a problem from this, but if we begin working with larger datasets, especially those where SVM requires more than two dimensions, problems could arise because of computing time.

However, we find that Linear SVM is a good model to begin with for this specific problem. Below is the confusion matrix created by Linear SVM. This confusion matrix shows that 86% of the data was correctly predicted to be non-sanctuary (true-negatives) and 14% of the data was predicted to be non-sanctuary but was actually sanctuary (false-negatives).


![png](output_43_0.png)


**Naive Bayes Classifier**

The second model we will use is the Naive Bayes classifier, which assumes that all of the features are independent of each other and that each feature contributes equally to the outcome. This classifier uses Bayes Theorem to predict membership probabilities of piece of data.


Like Linear SVM, there are a number of advantages and disadvantages to using Naive Bayes classifiers.  One advantage of using the Naive Bayes classifer is that, unlike SVM, this technique works quite well with larger datasets and generally is much faster than SVM.  Additionally, if working with multi-group classification problems, this classifier also performs well.

A disadvantage of using Naive Bayes is that, as I have said above, the classifier assumes that all features are independent of one another.  This is not the case most of the time and in datasets where features overlap or are dependent on one another, the model may perform poorly.

Naive Bayes requires less training data, yet it is stilly a highly scalable algorithm. With the size of our current dataset, we applied this Naive Bayes classifier to investigate how it relates to the simpler method of Linear SVM.

The Naive Bayes confusion matrix shows 54 true-negatives, 3 true-positives, 8 false-negatives and 16 false-positives (where a sanctuary city is represented to be a positive and a non-sanctuary city is a negative).



![png](output_48_0.png)


**Multinomial Logistic Regression**

The final model we will use is multinomial logistic regression.  We will follow the same steps as the two previous classifiers. Logistic regression investigates the relationship between dependent and independent variables.

The advantages of using a logistic regression classifier is that the model is very simple and time effective when working with larger datasets. In the case of having linearly separable data, such as our training data, the logistic regression classifier can potentially be highly effective. Like Linear SVM, this leads to the disadvantage of oversimplifying the classifier and leaving it to work poorly when working with non-linear relationships and when working in more than two dimensions.

We are using this technique largely to see how it compares to SVM and Naive Bayes.

Our final model, a multinomial linear regression gives us 43 true-negatives, 5 false-negatives, 6 true-positives, and 27 false-positives.


![png](output_52_0.png)


Overall, the SVM classifier resulted in the highest mean accuracy on the validation sets, but we figured that this is because of a class imbalance due to sanctuary cities being much less common than non-sanctuary cities in our data.  To remedy this, we put 4x weight on the sanctuary city data in our since non sanctuary cities were roughly 4x more common than sanctuary cities, but the results largely stayed the same. Linear SVM was still the most accurate, so decided to run the test set on that model. The confusion matrix below shows the result of running Linear SVM on our test set.





![png](output_55_0.png)


**ROC Curve and AUC**

Creating a ROC curve of our results and finding the area under the curve can allow us to measure how well our classifier has performed. A ROC curve (Receiver Operating Characteristic curve) is useful in determining thresholds in binary classifiers, as well as providing a measurement of performace of predictive power by finding the Area Under the Curve (AUC). The ROC plots the true positive rate (True Positives / (True Positives + False Negatives)) on the y-axis and the false positive rate (False Positives / (False Positives + True Negatives))on x-axis. The ideal graph would be a line which creates a 90 degree angle by closely traveling up the y-axis and then making a sharp turn to the right to follow the x-axis at the top of the graph. The closer the line goes to a 45 degree angle, the worse your model may be performing. A straight diagonal line of x = y would show no performance skill.

Since our thresholds have already been determined and all tests ran, we will be using AUC to measure predictive power. The higher the AUC, the more likely our classifier is performing well and classifying correctly. By applying scikit-learn functions we can create a ROC plot and find the AUC.


Below is the ROC curve for our linear SVM model. The AUC is 0.5.





![png](output_57_1.png)



The second ROC curve is for multinomial logistic regression. It has an AUC of 0.64.



![png](output_58_1.png)


The final ROC curve is for our naive bayes model. It has an AUC of 0.65.



![png](output_59_1.png)


This ROC/AUC analysis shows that the Linear SVM model, despite being the best performing classifier in terms of accuracy, could not effectively predict whether a city is a sanctuary city based on their crime rates, providing more evidence of our hypothesis that sanctuary status plays no significant role in determining violent crime rates.

Naive Bayes and Logistic Regression classifiers performed more effectively in this analysis, but it is also worth nothing that overall these models didn't predict status very accurately.

Nonetheless, all of the above analyses illustrate the lack of sufficient evidence that sanctuary cities are more dangerous than non-sanctuary cities.

# Conclusion / Summary & Write Up

**Research Question we sought out to answer:**

*Are sanctuary cities generally more dangerous than non-sanctuary cities?  Can we predict whether a city is a sanctuary city or a non-sanctuary city based on an investigation of their violent crime rates?*

Many of our nation's leaders place unfounded blame on various members of our society, especially immigrants.  Various cities around the country have declared themselves as sanctuary cities, meaning that they limit their cooperation with the Federal government's immigration policies.  Many people argue that giving "sanctuary" to undocumented immigrants will increase violent crime in their neighborhoods and cities.  Government leaders, most notably President Trump, have used this argument to end sanctuary cities by threatening to withhold federal funding, citing that they necessitate violent crimes and cause many needless deaths.  Our purpose was to investigate President Trump's claim that sanctuary cities are generally more dangerous than non-sanctuary cities and whether his threat to withhold federal aid was justified or misguided.

**The data we used:**

The [data](https://data.lacity.org/A-Safe-City/Crime-Data-from-2010-to-2019/63jg-8b9z) we used to form our hypothesis was gathered from the Los Angeles Police Department and consists of the years 2010 to 2019.  [According to the LA Times](https://www.latimes.com/california/story/2020-02-15/new-ice-crackdown-sanctuary-cities-sparks-backlash-la) in 2018 when the bill came into effect, local police departments stopped engaging in joint operations with the U.S Immigration and Customs Enforcement (ICE) and no longer transfers immigrants with minor offenses to ice custody.

In order to test our hypothesize we used [data](https://github.com/themarshallproject/city-crime/blob/master/data/ucr_crime_1975_2015.csv) that was gathered by the Marshall Project from the Uniform Crime Reporting Statistics.  This is a database under the U.S. Department of Justice.  The data consists of a long list of cities, many of which are sanctuary cities and many of which are not, as well as their violent crime rates.  We added a column of binary values where the number 1 represented a sanctuary city and 0 represented a non sanctuary city.

**Our hypothesis and how we formed it:**

In order to form a hypothesis, we found it necessary to first investigate a city and its crime rates before and after it declared itself as a sanctuary city.  We chose Los Angeles to be this city because it became a sanctuary city in 2017 with the passing of California Senate Bill 54, giving us available crime data prior to 2017, as well as after 2017 when police departments began to not cooperate with ICE.  Through filtering the crime statistics to only display instances of violent crime, we found that instances of violent crime in Los Angeles did not increase, but actually decreased between 2017 and 2019.  Because this was only one city's data, we did not find it justified to hypothesize that sanctuary cities decrease violent crime rates, but we felt like this analysis was enough to help us hypothesize that sanctuary city status does **not** have any significant effect on rates of violent crime.

**Testing our Hypothesis:**

To test the hypothesis that sanctuary city status has no discernible effect on violent crime rates in a given city, we decided to use the machine learning techniques from class to make a classification model that predicts whether a city is a sanctuary city (1) or a non-sanctuary city (0).  If we were able to predict whether a city was a sanctuary city solely based on their violent crime rates with higher than expected accuracy as well as with reasonable False Positive Rates, we would reject our hypothesis.  If we found that we could not effectively predict a city's sanctuary status based on their violent crime rates we would approve our hypothesis.

We made three separate classification models: Linear SVM, Naive Bayes, and Logistic Regression.  Because of the class imbalance due to more cities being non-sanctuary cities, we changed the 'class_weight' attribute within the sklearn functions to place more weight on sanctuary cities.


**Explanation of our findings**

On the test set using our best performing model, the Linear SVM classifier, we were able to predict with about 84% accuracy whether a city will be a sanctuary city or a non-sanctuary city using Linear SVM.

Regardless of this fairly high success rate in predicting whether a city is classified as a sanctuary city or a non-sanctuary city, there are some caveats to the results from our Linear SVM model.  This model predicted 100% of the time that a city would be a non-sanctuary city, despite us putting a larger class weight on sanctuary cities.  This likely means that we were able to predict with this accuracy based on a city being much more likely to be a non-sanctuary city than they are to be a sanctuary city.  Looking at the entire dataset, there are 330 instances of a non-sanctuary city and 73 instances of a sanctuary city, implying that about 82% of the cities are listed as non-sanctuary.  Given the minimal disparity between this percentage and our predictions, we are concluding from these models that there is no statistically significant difference between crime rates in sanctuary cities vs non-sanctuary cities.

Additionally, the AUC and ROC show that our Linear SVM model does not have much predictive power. This is to be expected, as our data itself leans heavily towards the (0) classification regardless of the class_weights parameter, making it hard to classify correctly when the majority of the data will be trained to classify as (0).  This lack in predictive power may help to further prove that there is no significant difference between crime rates in sanctuary cities vs non-sanctuary cities, as the amount of violent crimes does not seem to be a good indicator when classifying cities.

Because of the poor predictive power found from the ROC/AUC analysis on our Linear SVM model, we found it necessary to also apply this analysis to our other classifiers.  We determined that Naive Bayes and Logistic Regression have more predictive power than the SVM model, but this should be taken with a grain of salt because these models were generally also much less accurate.


**Conclusion:**

No, it does not appear that President Trump's claim that sanctuary cities are generally more dangerous than non-sanctuary cities holds merit, and his threat to withhold federal funding to these cities looks to be misguided.

If we perform our preliminary analysis on other large cities other than Los Angeles, we expect crime rates largely to remain uniform.  If for some reason violent crime rates within a city have increased after declaring a sanctuary status, we believe this to be the result of confounding variables and not a direct effect of becoming a sanctuary city.

Sanctuary cities, as we have concluded, as a class are not more dangerous than non-sanctuary cities.  This is not to say that a city classified as a sanctuary city cannot have higher violent crime rates, but these higher crime rates are most likely a result of an outside factor, and not a result of the sanctuary status.


# Acknowledgment of Ethical, Social and Legal Complexities



**Data as a tool to understand society:**

Data does not exist in a vaccuum independent of varying legal, economic and social factors. Our analysis project is not a showcase of python functions, matrices and graphs -- it is an evaluation and contribution to current discussions being held in our society through the perspective of data. Our society relies on data and our data relies on society. We make claims to be verified through data, just as we may create a claim after discovering interesting patterns in data.

Trump's claim that sanctuary cities have increased violent crime could have serious legal and social implications. Public policies would most likely shift if Trump promoted a removal of sanctuary cities and social tensions might rise. Thus, does Trump's claim have enough evidence to support all these changes? That is what our group attempts to answer. We have shown that violent crime rates are not a good indicator of whether or not a city is a sanctuary city. This brings into question: are the legal actions Trump wishes to take in order to weaken sanctuary policies worth it, if there actually seems to be no difference in crime? This question illustrates the interconnection between law and data. Without data, we cannot understand the impacts of certain laws on society. And while we must take data seriously, we cannot put blind faith into what it tells us. Data could have many pitfalls: it holds implicit bias, it could have been collected poorly, it could have a skewed representation for certain groups, etc. For example, one city may have a better system for detection and prevention of violent crime than another city - independent of whether or not it is sanctuary. There are endless possibilities for where data may not provide an accurate representation of what we aim to describe. Thus, we put our faith into the data we are using, but should not close off discussion of potential changes or pitfalls. Due to all these variabilities, we cannot with certainty say that Trump is wrong because of one data analysis project; this would discredit necessary social debate and policy discussion. Rather, we can provide our perspective into the pool of knowledge and hope that it provides evidence for the legal choice that creates the most positive change. Data and law should support one another in discussions of social change, without overpowering each other. Trump should use data in order to validate his claim, but data should also continue to consider outside social factors that may not be represented within the dataset.


**Potential risks of using ML in the legal realm:**

Our project creates a model which uses features of violent crime to predict whether a city is santuary or not. All cities in the data set have a clear answer at the end - they are *legally* sanctuary or they are not. This allows for a clear cut comparison of how our classifier performs - it either predicted correctly or it did not. However, if we were to attempt to classify on some other arbitrary value such as 'dangerous city' or 'not dangerous city' we may run into more issues. The definition of a 'dangerous city' is arbitrary and problematic. It brings up ethical issues of representation and power. Who has the power to claim a city to be dangerous? Politicians? Data scientists? Citizens of that city? If a data scientist labels a city 'dangerous' in an analysis, this creates a representation of that city that the citizens might not want nor agree with. As data analysts, we must be careful of how we choose to manipulate the data and be aware of the consequences it may have on the groups that the data comes from. Our analysis attempts to remove arbitrary definitions that may be potentially harmful by using a cities own choice of representation (sanctuary or not). But, we are aware that this project could easily shift into an ethically sticky situation where data analysists hold power over how a city will be represented by creating our own classification bins.

Data is a two-edged sword. It can open up discussions of fairness and social good through the exposure of unfair practices / biases that arise explicity in data. However, it can also create conclusions that harm individuals or groups when all necessary social factors are not properly accounted for. Our legal institutions rely heavily on statistics and data in order to create laws and policies. We must be aware that our analysis does not exist independently from laws that have direct social implications. We must approach data analysis with empathy and awareness of the power it holds while using it to the best of our abilities in order create positive social/legal changes.
