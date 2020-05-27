---
layout: page
title: Group 09
nav_order: 14
description:
---

# Analyzing Regional Trends in Police Stop Data Across the United States
### Names: Rishabh Parekh, Emmy Yu, Manu Prakasam

## **About the Data: Ethical Data Collection**
Publicly-available Standardized Stop Data from: https://openpolicing.stanford.edu/data/

The Stanford Open Policing Project data are made available under the [Open Data Commons Attribution License](https://opendatacommons.org/licenses/by/summary/), which allows us to:
>To Share: To copy, distribute and use the database.
<br>To Create: To produce works from the database.<br>
To Adapt: To modify, transform and build upon the database.

The Stanford Opening Policing Project data comes from the [working paper](https://5harad.com/papers/100M-stops.pdf):
<br> **E. Pierson, C. Simoiu, J. Overgoor, S. Corbett-Davies, D. Jenson, A. Shoemaker, V. Ramachandran, P. Barghouty, C. Phillips, R. Shroff, and S. Goel. (2019) “A large-scale analysis of racial disparities in police stops across the United States”.**<br>

The accompanying [README](https://github.com/stanford-policylab/opp/blob/master/data_readme.md) file describes how the data was standardized and cleaned for privacy and secruity reasons. Descriptions of the column meanings are also given.  

### **Downloading data from The Stanford Open Policing Project:**
Specifically, we will be looking at the datasets from San Francisco, New Orleans, and Pittsburgh.  

```python
sfcrime = pd.read_csv('ca_san_francisco_2019_12_17.csv')
sfcrime.head()
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
      <th>raw_row_number</th>
      <th>date</th>
      <th>time</th>
      <th>location</th>
      <th>lat</th>
      <th>lng</th>
      <th>district</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>type</th>
      <th>arrest_made</th>
      <th>citation_issued</th>
      <th>warning_issued</th>
      <th>outcome</th>
      <th>contraband_found</th>
      <th>search_conducted</th>
      <th>search_vehicle</th>
      <th>search_basis</th>
      <th>reason_for_stop</th>
      <th>raw_search_vehicle_description</th>
      <th>raw_result_of_contact_description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>869921</td>
      <td>2014-08-01</td>
      <td>00:01:00</td>
      <td>MASONIC AV &amp; FELL ST</td>
      <td>37.773004</td>
      <td>-122.445873</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>asian/pacific islander</td>
      <td>female</td>
      <td>vehicular</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>warning</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>No Search</td>
      <td>Warning</td>
    </tr>
    <tr>
      <th>1</th>
      <td>869922</td>
      <td>2014-08-01</td>
      <td>00:01:00</td>
      <td>GEARY&amp;10TH AV</td>
      <td>37.780898</td>
      <td>-122.468586</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>citation</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>No Search</td>
      <td>Citation</td>
    </tr>
    <tr>
      <th>2</th>
      <td>869923</td>
      <td>2014-08-01</td>
      <td>00:15:00</td>
      <td>SUTTER N OCTAVIA ST</td>
      <td>37.786919</td>
      <td>-122.426718</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>hispanic</td>
      <td>male</td>
      <td>vehicular</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>citation</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>No Search</td>
      <td>Citation</td>
    </tr>
    <tr>
      <th>3</th>
      <td>869924</td>
      <td>2014-08-01</td>
      <td>00:18:00</td>
      <td>3RD ST &amp; DAVIDSON</td>
      <td>37.746380</td>
      <td>-122.392005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>hispanic</td>
      <td>male</td>
      <td>vehicular</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>warning</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>No Search</td>
      <td>Warning</td>
    </tr>
    <tr>
      <th>4</th>
      <td>869925</td>
      <td>2014-08-01</td>
      <td>00:19:00</td>
      <td>DIVISADERO ST. &amp; BUSH ST.</td>
      <td>37.786348</td>
      <td>-122.440003</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
      <td>citation</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>No Search</td>
      <td>Citation</td>
    </tr>
  </tbody>
</table>
</div>




```python
nola_crime = pd.read_csv('la_new_orleans_2019_12_17.csv')
nola_crime.head()
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
      <th>raw_row_number</th>
      <th>date</th>
      <th>time</th>
      <th>location</th>
      <th>lat</th>
      <th>lng</th>
      <th>district</th>
      <th>zone</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>officer_assignment</th>
      <th>type</th>
      <th>arrest_made</th>
      <th>citation_issued</th>
      <th>warning_issued</th>
      <th>outcome</th>
      <th>contraband_found</th>
      <th>contraband_drugs</th>
      <th>contraband_weapons</th>
      <th>frisk_performed</th>
      <th>search_conducted</th>
      <th>search_person</th>
      <th>search_vehicle</th>
      <th>search_basis</th>
      <th>reason_for_stop</th>
      <th>vehicle_color</th>
      <th>vehicle_make</th>
      <th>vehicle_model</th>
      <th>vehicle_year</th>
      <th>raw_actions_taken</th>
      <th>raw_subject_race</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2010-01-01</td>
      <td>01:11:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6</td>
      <td>E</td>
      <td>26.0</td>
      <td>black</td>
      <td>female</td>
      <td>6th  District</td>
      <td>vehicular</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>TRAFFIC VIOLATION</td>
      <td>BLACK</td>
      <td>DODGE</td>
      <td>CARAVAN</td>
      <td>2005.0</td>
      <td>NaN</td>
      <td>BLACK</td>
    </tr>
    <tr>
      <th>1</th>
      <td>9087</td>
      <td>2010-01-01</td>
      <td>01:29:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7</td>
      <td>C</td>
      <td>37.0</td>
      <td>black</td>
      <td>male</td>
      <td>7th  District</td>
      <td>vehicular</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>TRAFFIC VIOLATION</td>
      <td>BLUE</td>
      <td>NISSAN</td>
      <td>MURANO</td>
      <td>2005.0</td>
      <td>NaN</td>
      <td>BLACK</td>
    </tr>
    <tr>
      <th>2</th>
      <td>9086</td>
      <td>2010-01-01</td>
      <td>01:29:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7</td>
      <td>C</td>
      <td>37.0</td>
      <td>black</td>
      <td>male</td>
      <td>7th  District</td>
      <td>vehicular</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>TRAFFIC VIOLATION</td>
      <td>BLUE</td>
      <td>NISSAN</td>
      <td>MURANO</td>
      <td>2005.0</td>
      <td>NaN</td>
      <td>BLACK</td>
    </tr>
    <tr>
      <th>3</th>
      <td>267</td>
      <td>2010-01-01</td>
      <td>14:00:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7</td>
      <td>I</td>
      <td>96.0</td>
      <td>black</td>
      <td>male</td>
      <td>7th  District</td>
      <td>vehicular</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>TRAFFIC VIOLATION</td>
      <td>GRAY</td>
      <td>JEEP</td>
      <td>GRAND CHEROKEE</td>
      <td>2003.0</td>
      <td>NaN</td>
      <td>BLACK</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>2010-01-01</td>
      <td>02:06:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5</td>
      <td>D</td>
      <td>17.0</td>
      <td>black</td>
      <td>male</td>
      <td>5th  District</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>CALL FOR SERVICE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>BLACK</td>
    </tr>
  </tbody>
</table>
</div>




```python
pittcrime = pd.read_csv('pa_pittsburgh_2019_12_17.csv')
pittcrime.head()
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
      <th>raw_row_number</th>
      <th>date</th>
      <th>time</th>
      <th>location</th>
      <th>lat</th>
      <th>lng</th>
      <th>neighborhood</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>officer_id_hash</th>
      <th>officer_age</th>
      <th>officer_race</th>
      <th>officer_sex</th>
      <th>type</th>
      <th>violation</th>
      <th>arrest_made</th>
      <th>citation_issued</th>
      <th>warning_issued</th>
      <th>outcome</th>
      <th>contraband_found</th>
      <th>frisk_performed</th>
      <th>search_conducted</th>
      <th>reason_for_stop</th>
      <th>raw_zone</th>
      <th>raw_object_searched</th>
      <th>raw_race</th>
      <th>raw_ethnicity</th>
      <th>raw_zone_division</th>
      <th>raw_evidence_found</th>
      <th>raw_weapons_found</th>
      <th>raw_nothing_found</th>
      <th>raw_police_zone</th>
      <th>raw_officer_race</th>
      <th>raw_officer_zone</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2008-01-01</td>
      <td>00:14:00</td>
      <td>351 S Negley Ave</td>
      <td>40.459466</td>
      <td>-79.932802</td>
      <td>NaN</td>
      <td>20.0</td>
      <td>white</td>
      <td>male</td>
      <td>3bb3b1bd48</td>
      <td>41.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>pedestrian</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>False</td>
      <td>Other</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>White</td>
      <td>White</td>
      <td>-</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>2008-01-01</td>
      <td>00:14:00</td>
      <td>376  Main St</td>
      <td>40.465868</td>
      <td>-79.955594</td>
      <td>NaN</td>
      <td>19.0</td>
      <td>white</td>
      <td>male</td>
      <td>3bb3b1bd48</td>
      <td>41.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>pedestrian</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>False</td>
      <td>Other</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>White</td>
      <td>White</td>
      <td>-</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>2008-01-01</td>
      <td>00:14:00</td>
      <td>Stamair Way &amp;  Baum Blvd</td>
      <td>40.456812</td>
      <td>-79.939041</td>
      <td>NaN</td>
      <td>16.0</td>
      <td>white</td>
      <td>male</td>
      <td>3bb3b1bd48</td>
      <td>41.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>pedestrian</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>False</td>
      <td>Other</td>
      <td>-</td>
      <td>NaN</td>
      <td>White</td>
      <td>White</td>
      <td>-</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>2008-01-01</td>
      <td>01:59:00</td>
      <td>N Braddock Ave &amp;  Thomas Blvd</td>
      <td>40.448873</td>
      <td>-79.893923</td>
      <td>NaN</td>
      <td>21.0</td>
      <td>NaN</td>
      <td>male</td>
      <td>b62aedb5bb</td>
      <td>29.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>pedestrian</td>
      <td>NaN</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>arrest</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>True</td>
      <td>majorCrimes    Other</td>
      <td>-</td>
      <td>person</td>
      <td>Black</td>
      <td>White</td>
      <td>-</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>2008-01-01</td>
      <td>14:50:00</td>
      <td>2518  West Liberty Ave</td>
      <td>40.398780</td>
      <td>-80.026439</td>
      <td>NaN</td>
      <td>41.0</td>
      <td>white</td>
      <td>male</td>
      <td>1ccb6bd45a</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>pedestrian</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>True</td>
      <td>narcVice</td>
      <td>-</td>
      <td>person vehicle  place</td>
      <td>White</td>
      <td>NaN</td>
      <td>N/V</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



### **Data Applicability:**
Our research question will assess the relationship between race/socioeconomic backgrounds and the amount of interactions with the police. With the given data, we will have access to race of the individual, location, and time of each stop a police officer makes. The information of location can give us a general idea of an individual's socioeconomic background based on the neighborhood they are in.

Furthermore, using the race of the individual, we can find the total number of stops per race. We will also calculate the proportion of total number of stops and the population of that specific race in the area. This can show us if there is a disproportionate rate of interactions with the law enforcment and minorities.

Using the Stanford Open Policing data, we will also compare the three distinctly different cities: San Francisco, Pittsburgh, and New Orleans. This will allow us to see if policing is similar or different across the nation, and will further give us a general idea of the relationship between minorities and law enforcement.


### **Standardizing the Data:**
Certain columns that are common across all cities (and lend themselves to interesting analyses) were selected and merged to create one DataFrame for easier analysis and plotting.

Each row in the cleaned data represents a stop. Coverage varies by location. From the original Open Policing data, fields with an asterisk were removed for public release due to privacy concerns. All columns except ```raw_row_number```, ```violation```, ```disposition```, ```location```, ```officer_assignment```, any city or state subgeography (i.e. county, beat, division, etc), ```unit```, and ```vehicle_{color, make, model, type} ```are also digit sanitized (each digit replaced with "-") for privacy concerns. These columns from the original dataset were removed for the purpose of our analysis.

# **Exploratory Data Analysis**


```python
sf_crime_to_merge = sfcrime[["date", "time", "subject_age", "subject_race", "subject_sex", "type", "outcome", "citation_issued", "reason_for_stop"]]
sf_crime_to_merge = pd.DataFrame(sf_crime_to_merge)
sf_crime_to_merge["city"] = "San Francisco"
```


```python
pitt_crime_to_merge = pittcrime[["date", "time", "subject_age", "subject_race", "subject_sex", "type", "outcome", "citation_issued", "reason_for_stop"]]
pitt_crime_to_merge = pd.DataFrame(pitt_crime_to_merge)
pitt_crime_to_merge["city"] = "Pittsburgh"
```


```python
nola_crime_to_merge = nola_crime[["date", "time", "subject_age", "subject_race", "subject_sex", "type", "outcome", "citation_issued", "reason_for_stop"]]
nola_crime_to_merge = pd.DataFrame(nola_crime_to_merge)
nola_crime_to_merge["city"] = "New Orleans"
```


```python
#Exploratory Data Analysis Dataframe
eda_merged = (sf_crime_to_merge.append(pitt_crime_to_merge)).append(nola_crime_to_merge)
```


```python
eda_merged
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
      <th>date</th>
      <th>time</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>type</th>
      <th>outcome</th>
      <th>citation_issued</th>
      <th>reason_for_stop</th>
      <th>city</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014-08-01</td>
      <td>00:01:00</td>
      <td>NaN</td>
      <td>asian/pacific islander</td>
      <td>female</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>False</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>San Francisco</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2014-08-01</td>
      <td>00:01:00</td>
      <td>NaN</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>True</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>San Francisco</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2014-08-01</td>
      <td>00:15:00</td>
      <td>NaN</td>
      <td>hispanic</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>True</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>San Francisco</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2014-08-01</td>
      <td>00:18:00</td>
      <td>NaN</td>
      <td>hispanic</td>
      <td>male</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>False</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>San Francisco</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2014-08-01</td>
      <td>00:19:00</td>
      <td>NaN</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>True</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>San Francisco</td>
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
    </tr>
    <tr>
      <th>512087</th>
      <td>2017-12-31</td>
      <td>00:48:00</td>
      <td>28.0</td>
      <td>black</td>
      <td>female</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>False</td>
      <td>TRAFFIC VIOLATION</td>
      <td>New Orleans</td>
    </tr>
    <tr>
      <th>512088</th>
      <td>2017-12-31</td>
      <td>00:48:00</td>
      <td>25.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>False</td>
      <td>TRAFFIC VIOLATION</td>
      <td>New Orleans</td>
    </tr>
    <tr>
      <th>512089</th>
      <td>2017-12-31</td>
      <td>00:48:00</td>
      <td>23.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>False</td>
      <td>TRAFFIC VIOLATION</td>
      <td>New Orleans</td>
    </tr>
    <tr>
      <th>512090</th>
      <td>2017-12-31</td>
      <td>00:48:00</td>
      <td>25.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>False</td>
      <td>TRAFFIC VIOLATION</td>
      <td>New Orleans</td>
    </tr>
    <tr>
      <th>512091</th>
      <td>2017-12-31</td>
      <td>12:49:00</td>
      <td>37.0</td>
      <td>black</td>
      <td>female</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>True</td>
      <td>TRAFFIC VIOLATION</td>
      <td>New Orleans</td>
    </tr>
  </tbody>
</table>
<p>1691720 rows × 10 columns</p>
</div>




```python
plt.figure(figsize=(12,6))
ax = sns.countplot(x="city", hue="subject_race", data=eda_merged)
plt.title('Frequency of Stops by Race')
plt.legend(loc = 'upper right')
plt.show()
```


![png](output_17_0.png)


From the figure above, it is clear that the demographic range differs significantly across out three target locations: San Francisco, Pittsburgh, and New Orleans. It is important to note that the frequency of stops by race have some correlation to the racial demographics in these cities. For example, there is a large spike in stops for Blacks in New Orleans compared to both San Francisco and Pittsburgh. However, data from the [Demographic Statistical Atlas](https://statisticalatlas.com/United-States/Overview) shows that New Orleans has 58.9% Black population compared to San Francisco's 5.4% and Pittsburgh's 24.3%.


```python
#The lengths of the datasets differ by location, with San Francisco having the greatest number of citations.
eda_merged.groupby('city').count()[['citation_issued']]
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
      <th>citation_issued</th>
    </tr>
    <tr>
      <th>city</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>New Orleans</th>
      <td>512092</td>
    </tr>
    <tr>
      <th>Pittsburgh</th>
      <td>274555</td>
    </tr>
    <tr>
      <th>San Francisco</th>
      <td>905070</td>
    </tr>
  </tbody>
</table>
</div>




```python
eda_time = eda_merged.copy()
eda_time['date'] = pd.to_datetime(eda_time['date'])
eda_time['year'] = eda_time['date'].dt.year
eda_grouped = eda_time.groupby(['city','year']).count()[['citation_issued']].reset_index()

plt.figure(figsize=(15,8))
sns.countplot(x='city', hue='year', data=eda_time)
plt.title('Frequency of Stops by Year Across Locations')
plt.legend(loc = 'best')
plt.show()
```


![png](output_20_0.png)


From the barchart above, it can be seen that the greater dataset lengths are not entirely due to a higher number of stops made by police. As seen in the DataFrame above, San Francisco has the highest number of citations issued. The SF data also contains data from 2007-2016, where the 2016 end data is  partial data. The Pittsburgh data is from 2008-2018, where the beginning and end years contains partial data as well. The New Orleans data contains the years 2010-2018 (partial 2018, data collection ended before end of year). **Therefore, for fair comparisons and aggregations against locations, data will be limited to the years 2010-2015.**


```python
#taking only the stops from 2010-2015
inclusive_years = [2010, 2011, 2012, 2013, 2014, 2015]
eda_standard = eda_time[eda_time['year'].isin(inclusive_years)]
eda_standard.head()
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
      <th>date</th>
      <th>time</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>type</th>
      <th>outcome</th>
      <th>citation_issued</th>
      <th>reason_for_stop</th>
      <th>city</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014-08-01</td>
      <td>00:01:00</td>
      <td>NaN</td>
      <td>asian/pacific islander</td>
      <td>female</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>False</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>San Francisco</td>
      <td>2014.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2014-08-01</td>
      <td>00:01:00</td>
      <td>NaN</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>True</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>San Francisco</td>
      <td>2014.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2014-08-01</td>
      <td>00:15:00</td>
      <td>NaN</td>
      <td>hispanic</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>True</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>San Francisco</td>
      <td>2014.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2014-08-01</td>
      <td>00:18:00</td>
      <td>NaN</td>
      <td>hispanic</td>
      <td>male</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>False</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>San Francisco</td>
      <td>2014.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2014-08-01</td>
      <td>00:19:00</td>
      <td>NaN</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>True</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>San Francisco</td>
      <td>2014.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.figure(figsize=(12,6))
ax = sns.countplot(x="city", hue="subject_sex", data=eda_standard)
plt.title('Frequency of Stops by Gender')
plt.legend(loc = 'upper right')
plt.show()
```


![png](output_23_0.png)


In this figure showing the frequency of stops by gender across the three cities, it is clear that although the SF dataset contains the most number of stops, the division of stops by gender is fairly consistent across the cities. Stops of males constitutes more than half of the data in each location.


```python
eda_merged['year'] = pd.DatetimeIndex(eda_merged["date"]).year
plt.figure(figsize=(12,6))
ax = sns.countplot(x="subject_race", hue="outcome", data=eda_merged.sort_values(by=['outcome', 'subject_race']))
plt.title('Type of Police Stop by Race: Total')
plt.legend(loc = 'upper left')
plt.show()
```


![png](output_25_0.png)



```python
plt.figure(figsize=(12,6))
sf = eda_merged.loc[eda_merged["city"] == "San Francisco"]
ax = sns.countplot(x="subject_race", hue="outcome", data=sf.sort_values(by=['outcome', 'subject_race']))
plt.title('Type of Police Stop by Race: San Francisco')
plt.legend(loc = 'upper left')
plt.show()
```


![png](output_26_0.png)


**Note:** The San Francisco dataset does not have an "unknown" category option listed for the subject's race.

According to the 2018 US Census Bureau, San Francisco County's population was 40% Non-Hispanic White, 5.4% Hispanic White, 5.2% Black or African American, 34.3% Asian, 8.1% Some Other Race, 0.3% Native American and Alaskan Native, 0.2% Pacific Islander and 6.5% from two or more races. Based on this data, it's interesting to note the relatively low count of AAPI subjects stopped based on their percentage of the population, and the relatively high count of black and Hispanic subjects stopped based on their percentage of the population.


```python
plt.figure(figsize=(12,6))
pitt = eda_merged.loc[eda_merged["city"] == "Pittsburgh"]
ax = sns.countplot(x="subject_race", hue="outcome", data=pitt.sort_values(by=['outcome', 'subject_race']))
plt.title('Type of Police Stop by Race: Pittsburgh')
plt.legend(loc = 'upper left')
plt.show()
```


![png](output_28_0.png)

In Pittsburgh, the two races with the most significant percentages are black and white. We see relatively similar trends for these two races, with one small difference being that more black subjects receive more warnings than citations and more white subjects receive citations than warnings. This could indicate a number of different things, including more black subjects are unecessarily stopped or for smaller infractions. An additional note, given Pittsburgh's population  ~65% white and ~24% black (from the Demographic Statistical Atlas referenced earlier), we see a higher relative count of stops for black subjects than the demographics of the city would predict given an even distribution of stops across race.


```python
plt.figure(figsize=(12,6))
nola = eda_merged.loc[eda_merged["city"] == "New Orleans"]
ax = sns.countplot(x="subject_race", hue="outcome", data=nola.sort_values(by=['outcome', 'subject_race']))
plt.title('Type of Police Stop by Race: New Orleans')
plt.legend(loc = 'upper right')
plt.show()
```


![png](output_29_0.png)

An interesting difference between New Orleans and our other cities is the very high rate of arrests relative to citations and warnings. San Francisco has the lowest relative rate of arrests, followed by Pittsburgh, with New Orleans having a rate of arrest nearly at par with citations and warnings.

We then took a look to see if there were trends year over year.





```python
plt.figure(figsize=(10,6))
sf_years = sf['year'].value_counts()
sns.lineplot(data=sf_years, label='SF')
pitt_years = pitt['year'].value_counts()
sns.lineplot(data=pitt_years, label='Pittsburgh')
nola_years = nola['year'].value_counts()
sns.lineplot(data=nola_years, label='New Orleans')
plt.ylim(ymin=0)
plt.xlabel("Year")
plt.ylabel("Count")
plt.title("Stops Over Time By Cities")
plt.legend()
plt.show()
```


![png](output_32_0.png)


We see some interesting trends in stop count by year that vary by city. NOLA is up and down but decreasing, SF is decreasing over time for the most part and Pitt saw a trend upward followed by a trend downward, resulted in an arc-like graph. We then took a deeper look into New Orleans to see if time trends differed by race, but we did not find any immediately striking results.


```python
plt.figure(figsize=(10,6))
nola_black = nola.loc[nola["subject_race"] == "black"]
nola_black = nola_black['year'].value_counts()
sns.lineplot(data=nola_black, label="black")
plt.ylim(ymin=0)
nola_white = nola.loc[nola["subject_race"] == "white"]
nola_white = nola_white['year'].value_counts()
sns.lineplot(data=nola_white, label="white")
plt.ylim(ymin=0)
plt.xlabel("Year")
plt.ylabel("Count")
plt.title("Stops in New Orleans Over Time by Race")
plt.legend()
plt.show()
```


![png](output_34_0.png)

We then decided to take a look at if an analysis of time of day versus stoppage rates by race produced any interesting results.


```python
plt.figure(figsize=(10,6))
with_time_sf = sfcrime.copy()
with_time_sf['subject_race'] = with_time_sf['subject_race'].replace(['asian/pacific islander', 'hispanic', 'black', 'other'], 'non-white')
with_time_sf['time'] = pd.to_datetime(with_time_sf['time'])
with_time_sf['time'] = with_time_sf['time'].dt.hour
sns.countplot(x='time', hue='subject_race', data=with_time_sf.sort_values(by='subject_race'))
plt.xticks(rotation=70)
plt.title('Count of Stops by Race Throughout Time of Day (SF)');
```


![png](output_37_0_new.png)


For the majority of the day in San Francisco, the ratio between the number of non-white subjects stopped and the number of white subjects stopped stays relatively constant with slightly more non-white subjects stopped. We then see  that this gap widens between the hours of 10pm and midnight.


```python
plt.figure(figsize=(10,6))
with_time_nola = nola_crime.copy()
with_time_nola['subject_race'] = with_time_nola['subject_race'].replace(['asian/pacific islander', 'hispanic', 'black', 'other', 'unknown'], 'non-white')
with_time_nola['time'] = pd.to_datetime(with_time_nola['time'])
with_time_nola['time'] = with_time_nola['time'].dt.hour
sns.countplot(x='time', hue='subject_race', data=with_time_nola.sort_values(by='subject_race'))
plt.xticks(rotation=70)
plt.title('Count of Stops by Race Throughout Time of Day (New Orleans)');
```


![png](output_39_0_new.png)


We see relatively similar ratios throughout the day in New Orleans.


```python
plt.figure(figsize=(10,6))
with_time_pitt = pittcrime.copy()
with_time_pitt['subject_race'] = with_time_pitt['subject_race'].replace(['asian/pacific islander', 'hispanic', 'black', 'other', 'unknown'], 'non-white')
with_time_pitt['time'] = pd.to_datetime(with_time_pitt['time'])
with_time_pitt['time'] = with_time_pitt['time'].dt.hour
sns.countplot(x='time', hue='subject_race', data=with_time_pitt.sort_values(by='subject_race'))
plt.xticks(rotation=70)
plt.title('Count of Stops by Race Throughout Time of Day (Pittsburgh)');
```


![png](output_41_0_new.png)


In Pittsburgh, we see the most interesting results. Throughout the day time hours we see more white subjects stopped. However, as it gets into night time, we see a greater percentage of those stopped being non-white and from midnight to 3am, non-white subjects make up a majority of those stopped. However in contrast to New Orleans and San Francisco, the number of people stopped is far lower at night versus the day.

From these graphs, we find that the relative rates of stoppage for non-white versus white subjects change dependent on the time of day in San Francisco and Pittsburgh. This difference in ratio dependent on time of day could possibly indicate police bias and warrants further study to determine the cause.


## **Modeling**
#### Modeling and analysis will be evaluated based on appropriateness to question, clarity in explanation of model and the reasons for using it, and the exposition of the relationship between the team’s modeling efforts and the conclusions the team draws.

In particular, we seek to see if there is underlying discrimination (eg. racial, gender, etc) based on the frequency of stops in each of these cities. From the Exploratory Data Analysis performed above, it is already clear that each of the select cities: San Francisco, Pittsburgh, and New Orleans has varying demographics and distribution of stops.


Since our goal of identifying possible underlying discrimination in policing is a broad topic, here are some variables that we took into consideration:

- **Severity of the Crime** (ie. if the stop resulted in a warning, citation, or an arrest in order of increasing severity)
- **Time of Day** (ie. when does the crime occur? is there a distinction between crimes occuring during night or day?
- **Type of Stop** (ie. pedestrian, vehicular, etc)
- **Subject Age** (ie. age of the person stopped)


**To promote fair comparisons, the following considerations were taken into account during standardization/cleaning of the data:**

- Based on the availability of data, only data from the years 2010-2015 will be used.
- By the sheer volume of data, and since the total number of citations varied in each of the cities, a random sample of 200,000 stops will be taken from each city.
- "Unknown" or NaN values listed under subject race will be dropped from the datasets.  
- Implementing a the 24-hour time, where the minutes become fractions of the hour.
- Implement One-Hot Encoding on the "outcomes" column for its 3 outcomes: arrest, citation, and warning and on the "type" column for its 2 types: vehicular, pedestrian.


```python
sfcrime = sfcrime[["date", "time", "subject_age", "subject_race", "subject_sex", "type", "outcome", "citation_issued", "warning_issued", 'arrest_made', "reason_for_stop"]]
sf_crime = sfcrime.iloc[sfcrime.dropna().index, :]
random.seed(30)
sf_crime_resampled = sf_crime.sample(200000)
```









```python
sf_crime_resampled[['citation_issued',"warning_issued", "arrest_made"]] = sf_crime_resampled[['citation_issued',"warning_issued", "arrest_made"]].astype(int)
sf_crime_resampled['vehicular'] = (sf_crime_resampled['type']=='vehicular').astype(int)
sf_crime_resampled['pedestrian'] = (sf_crime_resampled['type']=='pedestrian').astype(int)

sf_crime_resampled['time'] = pd.to_datetime(sf_crime_resampled['time'])
sf_crime_resampled['time'] = sf_crime_resampled['time'].dt.hour + sf_crime_resampled['time'].dt.minute/60
sf_crime_resampled.head()
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
      <th>date</th>
      <th>time</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>type</th>
      <th>outcome</th>
      <th>citation_issued</th>
      <th>warning_issued</th>
      <th>arrest_made</th>
      <th>reason_for_stop</th>
      <th>vehicular</th>
      <th>pedestrian</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>496292</th>
      <td>2011-04-23</td>
      <td>1.966667</td>
      <td>30.0</td>
      <td>asian/pacific islander</td>
      <td>male</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>697863</th>
      <td>2013-09-05</td>
      <td>1.500000</td>
      <td>26.0</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>543063</th>
      <td>2011-10-04</td>
      <td>23.833333</td>
      <td>20.0</td>
      <td>asian/pacific islander</td>
      <td>female</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>478772</th>
      <td>2011-02-21</td>
      <td>14.000000</td>
      <td>26.0</td>
      <td>hispanic</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>183677</th>
      <td>2008-05-29</td>
      <td>12.216667</td>
      <td>60.0</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>1</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
nola_crime = nola_crime[["date", "time", "subject_age", "subject_race", "subject_sex", "type", "outcome", "citation_issued", "warning_issued", 'arrest_made', "reason_for_stop"]]
nola_crime = nola_crime.iloc[nola_crime.dropna().index, :]
random.seed(30)
nola_crime_resampled = nola_crime.sample(200000)
```



```python
nola_crime_resampled[['citation_issued',"warning_issued", "arrest_made"]] = nola_crime_resampled[['citation_issued',"warning_issued", "arrest_made"]].astype(int)
nola_crime_resampled['vehicular'] = (nola_crime_resampled['type']=='vehicular').astype(int)
nola_crime_resampled['pedestrian'] = (nola_crime_resampled['type']=='pedestrian').astype(int)

nola_crime_resampled['time'] = pd.to_datetime(nola_crime_resampled['time'])
nola_crime_resampled['time'] = nola_crime_resampled['time'].dt.hour + nola_crime_resampled['time'].dt.minute/60
nola_crime_resampled.head()
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
      <th>date</th>
      <th>time</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>type</th>
      <th>outcome</th>
      <th>citation_issued</th>
      <th>warning_issued</th>
      <th>arrest_made</th>
      <th>reason_for_stop</th>
      <th>vehicular</th>
      <th>pedestrian</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>441600</th>
      <td>2013-11-05</td>
      <td>18.500000</td>
      <td>23.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>308926</th>
      <td>2017-08-01</td>
      <td>16.966667</td>
      <td>22.0</td>
      <td>black</td>
      <td>female</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>327897</th>
      <td>2017-08-14</td>
      <td>1.733333</td>
      <td>49.0</td>
      <td>black</td>
      <td>female</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>476436</th>
      <td>2015-12-02</td>
      <td>17.066667</td>
      <td>27.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>464300</th>
      <td>2017-11-22</td>
      <td>23.900000</td>
      <td>20.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
pitt_crime = pittcrime[["date", "time", "subject_age", "subject_race", "subject_sex", "type", "outcome", "citation_issued", "warning_issued", 'arrest_made', "reason_for_stop"]]
pitt_crime = pitt_crime.iloc[pitt_crime[['subject_race', 'subject_age']].dropna().index, :]
pitt_crime = pitt_crime.sample()
pitt_crime
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
      <th>date</th>
      <th>time</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>type</th>
      <th>outcome</th>
      <th>citation_issued</th>
      <th>warning_issued</th>
      <th>arrest_made</th>
      <th>reason_for_stop</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>47015</th>
      <td>2018-02-20</td>
      <td>20:59:00</td>
      <td>46.0</td>
      <td>white</td>
      <td>NaN</td>
      <td>pedestrian</td>
      <td>NaN</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>narcVice vehicleCodeViolation</td>
    </tr>
  </tbody>
</table>
</div>



Upon further analysis of the Pittsburgh dataset, there were too many null values to use this dataset. Since our chosen features included the the subject age and race, simply dropping the null values meant that a majority of the dataset was also discarded. In the cell above, only one instance included information on both the race and the age. If the outcome null values were also dropped in this instance, none of the stops in the Pittsburgh dataset would be viable for our analysis.

**Therefore, our model and analysis will be limited to San Francisco and New Orleans.**   

## **Logistic Regression Classifier**

### **Why logistic regression?**
We have incorporated logistic regression and naive bases to the analysis regarding the overall accuracy and fairness of police stops as it pertains to race. The inputs that we would receive would be both categorical and quantitative. Furthermore, we chose a no-regularization logistic regression for the baseline of the model. Since this analysis aims to perform classification, the essence of a logistic regression model is designed on a certain event that would exist or not. In our project, the logistic regression model aims to delineate between a binary result (1 for white vs. 0 for non-white individuals). In essence, underlying racial discrimination will be classified based on trends in features that will predict if the police stop was for a white individual or non-white minority individual. A similar analysis may also be done based on gender. Furthermore, logistic regression would be used to find the relationships between dependent variables and other independent or nominal variables.


To implement logistic regression, the subject_race column is transformed into a binary format: 1 for white vs. 0 for non-white individuals.


```python
sf_crime_resampled['race_binary'] = (sf_crime_resampled['subject_race'] == 'white').astype(int)
sf_crime_resampled.head()
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
      <th>date</th>
      <th>time</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>type</th>
      <th>outcome</th>
      <th>citation_issued</th>
      <th>warning_issued</th>
      <th>arrest_made</th>
      <th>reason_for_stop</th>
      <th>vehicular</th>
      <th>pedestrian</th>
      <th>race_binary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>496292</th>
      <td>2011-04-23</td>
      <td>1.966667</td>
      <td>30.0</td>
      <td>asian/pacific islander</td>
      <td>male</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>697863</th>
      <td>2013-09-05</td>
      <td>1.500000</td>
      <td>26.0</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>543063</th>
      <td>2011-10-04</td>
      <td>23.833333</td>
      <td>20.0</td>
      <td>asian/pacific islander</td>
      <td>female</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>478772</th>
      <td>2011-02-21</td>
      <td>14.000000</td>
      <td>26.0</td>
      <td>hispanic</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>183677</th>
      <td>2008-05-29</td>
      <td>12.216667</td>
      <td>60.0</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
nola_crime_resampled['race_binary'] = (nola_crime_resampled['subject_race'] == 'white').astype(int)
nola_crime_resampled.head()
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
      <th>date</th>
      <th>time</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>type</th>
      <th>outcome</th>
      <th>citation_issued</th>
      <th>warning_issued</th>
      <th>arrest_made</th>
      <th>reason_for_stop</th>
      <th>vehicular</th>
      <th>pedestrian</th>
      <th>race_binary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>441600</th>
      <td>2013-11-05</td>
      <td>18.500000</td>
      <td>23.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>308926</th>
      <td>2017-08-01</td>
      <td>16.966667</td>
      <td>22.0</td>
      <td>black</td>
      <td>female</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>327897</th>
      <td>2017-08-14</td>
      <td>1.733333</td>
      <td>49.0</td>
      <td>black</td>
      <td>female</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>476436</th>
      <td>2015-12-02</td>
      <td>17.066667</td>
      <td>27.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>464300</th>
      <td>2017-11-22</td>
      <td>23.900000</td>
      <td>20.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




**To perform modeling and analysis on our dataset, the dataset will be split into a training, validation, and test set:**

- Training set 70%
- Validation set 15%
- Test set 15%

### ***San Francisco***


```python
#SF features matrix
X_sf = sf_crime_resampled[['subject_age', 'time', 'citation_issued', "warning_issued", "arrest_made", 'vehicular', 'pedestrian']]
y_sf = sf_crime_resampled['race_binary']
```


```python
# Train/Test Split
X_sf_train, X_sf_test, y_sf_train, y_sf_test = train_test_split(X_sf, y_sf, train_size = .70, test_size = .30)

# Train/Validation Split
X_sf_test, X_sf_validate, y_sf_test, y_sf_validate = train_test_split(X_sf_test, y_sf_test, train_size = .50, test_size = .50)
```


```python
log_reg = LogisticRegression()
log_model = log_reg.fit(X_sf_train, y_sf_train)
log_pred = log_model.predict(X_sf_train)
log_reg_confusion_matrix = confusion_matrix(y_sf_train, log_pred)
```




![png](output_54_1.png)



![png](output_54_2.png)



```python
log_model.score(X_sf_validate, y_sf_validate)
```




    0.5872



### ***New Orleans***


```python
#New Orleans features matrix
X_nola = nola_crime_resampled[['subject_age', 'time', 'citation_issued', "warning_issued", "arrest_made", 'vehicular', 'pedestrian']]
y_nola = nola_crime_resampled['race_binary']
```


```python
# Train/Test Split
X_nola_train, X_nola_test, y_nola_train, y_nola_test = train_test_split(X_nola, y_nola, train_size = .70, test_size = .30)

# Train/Validation Split
X_nola_test, X_nola_validate, y_nola_test, y_nola_validate = train_test_split(X_nola_test, y_nola_test, train_size = .50, test_size = .50)
```


```python
log_reg = LogisticRegression()
log_model = log_reg.fit(X_nola_train, y_nola_train)
log_pred = log_model.predict(X_nola_train)
```


```python
log_reg_confusion_matrix_nola = confusion_matrix(y_nola_train, log_pred)
# Plot non-normalized confusion matrix
plt.figure()
plot_confusion_matrix(log_reg_confusion_matrix_nola, classes=class_names,
                      title='Confusion Matrix')

# Plot normalized confusion matrix
plt.figure()
plot_confusion_matrix(log_reg_confusion_matrix_nola, classes=class_names, normalize=True,
                      title='Normalized Confusion Matrix')
```



![png](output_60_1.png)



![png](output_60_2.png)



```python
log_model.score(X_nola_validate, y_nola_validate)
```




    0.7420666666666667



## **Ridge Regression Classifier**

### **Why Ridge Regression?**
Ridge regression is a type of squared loss regression used when the number of predictors exceeds the number of observations (eg. p>n) and when the model experiences multicollinearity. Since both p>n and multicollinearity are issues when using linear least squares regression, ridge regression would be used instead. Ridge regression works by using a shrinkage estimator that essentially would produce new estimates that are "shrunk" to the population's true parameters. It is a L2 "squared" regularization that adds a penalty equal to the squared magnitude of the coefficients. A tuning parameter 𝜆  would determine the strength of this penalty. The constraints put on each of the estimators helps to shrink extreme variance and fluctuations; this sacrifices training accuracy for a model that is likely to generalize better. In other words, ridge regression introduces enough bias that shrinks variance to make estimates closer to the true population values.

Here, we try to improve upon the logistic model. RidgeClassifier is a classifier variant of the Ridge regressor (provided by scikit-learn), and can be much faster than logistic regression. It is used below in place of the **sklearn.linear_model.Ridge()** model.

### ***San Francisco***


```python
ridge = RidgeClassifier()
ridge_model = ridge.fit(X_sf_train, y_sf_train)
ridge_pred = ridge_model.predict(X_sf_train)
```


```python
ridge_confusion_matrix_sf = confusion_matrix(y_sf_train, ridge_pred)
# Plot non-normalized confusion matrix
plt.figure()
plot_confusion_matrix(ridge_confusion_matrix_sf, classes=class_names,
                      title='Confusion Matrix')

# Plot normalized confusion matrix
plt.figure()
plot_confusion_matrix(ridge_confusion_matrix_sf, classes=class_names, normalize=True,
                      title='Normalized Confusion Matrix')
```



![png](output_66_1.png)



![png](output_66_2.png)



```python
ridge_model.score(X_sf_validate, y_sf_validate)
```




    0.5870333333333333



### ***New Orleans***

```python
ridge_nola = RidgeClassifier()
ridge_nola_model = ridge_nola.fit(X_nola_train, y_nola_train)
ridge_nola_pred = ridge_nola_model.predict(X_nola_train)
```


```python
ridge_confusion_matrix_nola = confusion_matrix(y_nola_train, ridge_nola_pred)
# Plot non-normalized confusion matrix
plt.figure()
plot_confusion_matrix(ridge_confusion_matrix_nola, classes=class_names,
                      title='Confusion Matrix')

# Plot normalized confusion matrix
plt.figure()
plot_confusion_matrix(ridge_confusion_matrix_nola, classes=class_names, normalize=True,
                      title='Normalized Confusion Matrix')
```



![png](output_70_1.png)



![png](output_70_2.png)



```python
ridge_nola_model.score(X_nola_validate, y_nola_validate)
```




    0.7420666666666667


## **One-Hot Encoding**

What follows are our attempts at one-hot encoding ```reason_for_stop``` and using resultant columns as additional features as a means of improving accuracy.


### ***San Francisco***

```python
sf_crime_resampled_new = pd.concat([sf_crime_resampled,pd.get_dummies(sf_crime_resampled['reason_for_stop'], prefix='stopreason')],axis=1)
sf_crime_resampled_new
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
      <th>date</th>
      <th>time</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>type</th>
      <th>outcome</th>
      <th>citation_issued</th>
      <th>warning_issued</th>
      <th>arrest_made</th>
      <th>reason_for_stop</th>
      <th>vehicular</th>
      <th>pedestrian</th>
      <th>race_binary</th>
      <th>stopreason_Assistance to Motorist</th>
      <th>stopreason_BOLO/APB/Warrant</th>
      <th>stopreason_DUI Check</th>
      <th>stopreason_MPC Violation</th>
      <th>stopreason_MPC Violation|Moving Violation</th>
      <th>stopreason_Mechanical or Non-Moving Violation (V.C.)</th>
      <th>stopreason_Mechanical or Non-Moving Violation (V.C.)|DUI Check</th>
      <th>stopreason_Mechanical or Non-Moving Violation (V.C.)|Moving Violation</th>
      <th>stopreason_Moving Violation</th>
      <th>stopreason_Moving Violation|Assistance to Motorist</th>
      <th>stopreason_Moving Violation|DUI Check</th>
      <th>stopreason_Moving Violation|Mechanical or Non-Moving Violation (V.C.)</th>
      <th>stopreason_Moving Violation|NA</th>
      <th>stopreason_Moving Violation|Traffic Collision</th>
      <th>stopreason_Traffic Collision</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>496292</th>
      <td>2011-04-23</td>
      <td>1.966667</td>
      <td>30.0</td>
      <td>asian/pacific islander</td>
      <td>male</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
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
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>697863</th>
      <td>2013-09-05</td>
      <td>1.500000</td>
      <td>26.0</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
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
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>543063</th>
      <td>2011-10-04</td>
      <td>23.833333</td>
      <td>20.0</td>
      <td>asian/pacific islander</td>
      <td>female</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
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
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>478772</th>
      <td>2011-02-21</td>
      <td>14.000000</td>
      <td>26.0</td>
      <td>hispanic</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
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
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>183677</th>
      <td>2008-05-29</td>
      <td>12.216667</td>
      <td>60.0</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
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
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
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
      <th>452716</th>
      <td>2010-11-18</td>
      <td>21.750000</td>
      <td>44.0</td>
      <td>white</td>
      <td>female</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
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
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>119254</th>
      <td>2007-11-04</td>
      <td>21.866667</td>
      <td>62.0</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>Moving Violation</td>
      <td>1</td>
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
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>356527</th>
      <td>2009-12-21</td>
      <td>11.833333</td>
      <td>21.0</td>
      <td>other</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
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
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>487440</th>
      <td>2011-03-22</td>
      <td>21.750000</td>
      <td>23.0</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>Mechanical or Non-Moving Violation (V.C.)</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
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
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>823151</th>
      <td>2015-09-17</td>
      <td>13.750000</td>
      <td>40.0</td>
      <td>hispanic</td>
      <td>male</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Moving Violation</td>
      <td>1</td>
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
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>200000 rows × 29 columns</p>
</div>




```python
sf_crime_resampled_new.drop(['reason_for_stop'],axis=1, inplace=True)
```



```python
X_sf_new = sf_crime_resampled_new[columns_we_want]
```


```python
y_sf_new = sf_crime_resampled_new['race_binary']
```


```python
# Train/Test Split
X_sf_train, X_sf_test, y_sf_train, y_sf_test = train_test_split(X_sf_new, y_sf_new, train_size = .70, test_size = .30)

# Train/Validation Split
X_sf_test, X_sf_validate, y_sf_test, y_sf_validate = train_test_split(X_sf_test, y_sf_test, train_size = .50, test_size = .50)
```


```python
log_reg = LogisticRegression()
log_model = log_reg.fit(X_sf_train, y_sf_train)
log_pred = log_model.predict(X_sf_train)
```



```python
log_confusion_matrix_sf = confusion_matrix(y_sf_train, log_pred)
# Plot non-normalized confusion matrix
plt.figure()
plot_confusion_matrix(log_confusion_matrix_sf, classes=class_names,
                      title='Confusion Matrix')

# Plot normalized confusion matrix
plt.figure()
plot_confusion_matrix(log_confusion_matrix_sf, classes=class_names, normalize=True,
                      title='Normalized Confusion Matrix')
```




![png](output_81_1.png)



![png](output_81_2.png)



```python
log_model.score(X_sf_validate, y_sf_validate)
```




    0.5855




```python
ridge = RidgeClassifier()
ridge_model = ridge.fit(X_sf_train, y_sf_train)
ridge_pred = ridge_model.predict(X_sf_train)
```


```python
ridge_confusion_matrix_sf = confusion_matrix(y_sf_train, ridge_pred)
# Plot non-normalized confusion matrix
plt.figure()
plot_confusion_matrix(ridge_confusion_matrix_sf, classes=class_names,
                      title='Confusion Matrix')

# Plot normalized confusion matrix
plt.figure()
plot_confusion_matrix(ridge_confusion_matrix_sf, classes=class_names, normalize=True,
                      title='Normalized Confusion Matrix')
```




![png](output_84_1.png)



![png](output_84_2.png)



```python
ridge_model.score(X_sf_validate, y_sf_validate)
```




    0.5855



### ***New Orleans***


```python
nola_crime_resampled_new = pd.concat([nola_crime_resampled,pd.get_dummies(nola_crime_resampled['reason_for_stop'], prefix='stopreason')],axis=1)
nola_crime_resampled_new
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
      <th>date</th>
      <th>time</th>
      <th>subject_age</th>
      <th>subject_race</th>
      <th>subject_sex</th>
      <th>type</th>
      <th>outcome</th>
      <th>citation_issued</th>
      <th>warning_issued</th>
      <th>arrest_made</th>
      <th>reason_for_stop</th>
      <th>vehicular</th>
      <th>pedestrian</th>
      <th>race_binary</th>
      <th>stopreason_SUSPECT PERSON</th>
      <th>stopreason_SUSPECT VEHICLE</th>
      <th>stopreason_TRAFFIC VIOLATION</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>441600</th>
      <td>2013-11-05</td>
      <td>18.500000</td>
      <td>23.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>308926</th>
      <td>2017-08-01</td>
      <td>16.966667</td>
      <td>22.0</td>
      <td>black</td>
      <td>female</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>327897</th>
      <td>2017-08-14</td>
      <td>1.733333</td>
      <td>49.0</td>
      <td>black</td>
      <td>female</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>476436</th>
      <td>2015-12-02</td>
      <td>17.066667</td>
      <td>27.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>464300</th>
      <td>2017-11-22</td>
      <td>23.900000</td>
      <td>20.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
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
    </tr>
    <tr>
      <th>157539</th>
      <td>2012-04-23</td>
      <td>14.916667</td>
      <td>69.0</td>
      <td>black</td>
      <td>female</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>26292</th>
      <td>2018-01-18</td>
      <td>12.633333</td>
      <td>57.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>332641</th>
      <td>2011-08-18</td>
      <td>16.816667</td>
      <td>44.0</td>
      <td>white</td>
      <td>male</td>
      <td>vehicular</td>
      <td>citation</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>311926</th>
      <td>2017-08-03</td>
      <td>19.083333</td>
      <td>61.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>warning</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>329071</th>
      <td>2015-08-15</td>
      <td>18.233333</td>
      <td>25.0</td>
      <td>black</td>
      <td>male</td>
      <td>vehicular</td>
      <td>arrest</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>TRAFFIC VIOLATION</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>200000 rows × 17 columns</p>
</div>




```python
nola_columns = list(nola_crime_resampled_new.columns)
nola_columns_desired = ['time',
 'subject_age',
 'citation_issued',
 'warning_issued',
 'arrest_made',
 'vehicular',
 'pedestrian',
 'stopreason_SUSPECT PERSON',
 'stopreason_SUSPECT VEHICLE',
 'stopreason_TRAFFIC VIOLATION']
```


```python
X_nola_new = nola_crime_resampled_new[nola_columns_desired]
y_nola_new = nola_crime_resampled_new['race_binary']
```


```python
# Train/Test Split
X_nola_train, X_nola_test, y_nola_train, y_nola_test = train_test_split(X_nola_new, y_nola_new, train_size = .70, test_size = .30)

# Train/Validation Split
X_nola_test, X_nola_validate, y_nola_test, y_nola_validate = train_test_split(X_nola_test, y_nola_test, train_size = .50, test_size = .50)
```


```python
log_reg = LogisticRegression()
log_model = log_reg.fit(X_nola_train, y_nola_train)
log_pred = log_model.predict(X_nola_train)
```


```python
log_confusion_matrix_nola = confusion_matrix(y_nola_train, log_pred)
# Plot non-normalized confusion matrix
plt.figure()
plot_confusion_matrix(log_confusion_matrix_nola, classes=class_names,
                      title='Confusion Matrix')

# Plot normalized confusion matrix
plt.figure()
plot_confusion_matrix(log_confusion_matrix_nola, classes=class_names, normalize=True,
                      title='Normalized Confusion Matrix')
```



![png](output_92_1.png)



![png](output_92_2.png)



```python
log_model.score(X_nola_validate, y_nola_validate)
```




    0.7444




```python
ridge_nola = RidgeClassifier()
ridge_nola_model = ridge_nola.fit(X_nola_train, y_nola_train)
ridge_nola_pred = ridge_nola_model.predict(X_nola_train)
confusion_matrix(y_nola_train, ridge_nola_pred)
```




![png](output_92_1.png)



![png](output_92_2.png)

**Note:** The RidgeClassifier did not change the confusion matrix for New Orleans.




```python
ridge_nola_model.score(X_nola_validate, y_nola_validate)
```




    0.7444333333333333



## **Modeling Conclusions**

### **Numerical Results**
In modeling the San Francisco dataset, the logistic regression model and the ridge regression model (after adding additional features like one-hot encoding) both gave an validation accuracy of 58.4%.

In modeling the New Orleans dataset, the logistic model and the ridge regression model scored a validation accuracy of 74.6%.  

### **Evaluation Methods**
Our two methods of evaluating our results are using confusion matrices and using the **model.score()** function. In our confusion matrix, we see our true negatives at (0,0) in the matrix, false negatives at (1,0), false positives at (0,1), and true positives at (1,1). True negatives are non-white subjects predicted to be non-white, false negatives are white subjects predicted to be non-white, false positives are non-white subjects predicted to be white, and true positives are white subjects predicted to be white. **model.score()** returns the mean accuracy on the given test data and labels.

### **Interpretation of Results**
We see higher accuracies for our New Orleans models because our models are predicting all values to be non-white. For the New Orleans dataset, this results in higher accuracy because majority of the dataset population (and city population) is non-white. In San Francisco on the other hand, a plurality of the population is white. Thus, our scores just indicate what the percentage of non-white subjects within the dataset. It is of note however, that the percentage of non-white subjects within the dataset is higher than the overall percentage of people of color in New Orleans, suggesting that people of color are stopped at a higher rate than white people, even when you control for percentage of the population.

### **Reflecting on the Chosen Models**
The accuracy of our predictive models for San Francisco are low, in which the model only predicts correctly a little more than half the time. While this may be consequence of the chosen features or the choice of the classifier itself, considerations should also be taken that the features simple do not correlate well with race. Therefore, even adding additional features to the model did not increase the accuracy by a significant amount. Training on additional noise would work to decrease the accuracy. In other words, rather than there being a problem with the model, there may just be little to no underlying racial discrimination in the features that we chose to train the model on.

### **Potential Improvements**
- **Oversampling:** An imbalance in the dataset can be seen from the proportion of whites to other ethnicities. Especially in the New Orleans data set, there are considerably more non-white individuals than white individuals in the sampled training set, which leads the models to tend to exclusively predict subject_race as non-white. A potential solution is to oversample rows with white subjects in our training data to increase the likelihood that the model will predict a white subject. Since one of the primary goals of model validation estimation of how it will perform on unseen data, oversampling correctly is critical.

- **Bootstrapping** Given the imbalance in the datasets (especially in the case of New Orleans) between the white and non-white populations, a method to create more variability in the data would be to bootstrap (random sampling with replacement). In this way, the model would be able to train on more data without having to collect additional data.

- **Important Null values:** In standardizing the data from both the San Francisco and New Orleans datasets, all the Null/NaN/None values were dropped. However, there may be underlying patterns to these dropped values. More exploratory data analysis could be performed to see why certain values failed to appear in the given datasets.
