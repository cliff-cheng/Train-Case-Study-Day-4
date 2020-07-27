# Galvanize (Day 4) - Case Study
Transit Systems of the World - https://www.kaggle.com/citylines/city-lines

![alt-text](https://media.giphy.com/media/dxxPrxycJYHYhNxWlm/giphy.gif)

> Project Goals:
- Data clean and explore the world's transit systems from 1832 to 2017.
- Obtain insights and present visualizations of data.
---

### Table of Contents
- [Description](#description)
- [Data Understanding](#data-understanding)
- [Data Preparation](#data-preparation)
- [Models](#models)
- [Author-Info](#author-info)


---

## Description

What did the expansion of the London Underground, the world’s first underground railway which opened in 1863, look like? What about the transportation system in your home city? Citylines collects data on transportation lines across the world so you can answer questions like these and more.

This project will explore the dataset from Citylines that contains data on the worlds track systems from 1837 to 2017. The primary objective is to organize and clean the dataset in order to create a data analysis tool to help other users infer their own inights. A secondary objective would be to demonstrate the power of this data analysis tool to obtain insights and visualizations.



[Back To The Top](#Google-Analytics-Ecommerce)

---

## Data Understanding

The data consisted of 7 tables and a total of 43 columns. The tables range from city data, lines coordinates, to station data/coordinates. In total, the dataset contained 50,000 rows of data and the download was roughly 9MB. Each table had unique cities keys that allowed the data to be related to the city the stations and lines connected to. Furthermore, there were additional unique keys that allowed stations to be related to lines. Some lines were connected to multiple cities so when analyizing the data, I had to compensate. 

<p align="center">
<img src="trainimages/backofhand.png" width="350" height="450">
<p/>

[Back To The Top](#Google-Analytics-Ecommerce)

---

## Data Preparation

The first step was to white board this relationship and build functions in order to easily clean the data in steps to be branched off into other useful functions. Once I understood schema and main functions, I built a number of helper functions to automate the data cleaning processes. I wanted the data analysis tool to be able to take in the raw, uncleaned, dataset and immediately begin running analysis. This would allow the tool to contune working with the dataset as Citylines continues to track and update their dataset. In addition, partioning the cleaning and plotting functions allows other users to remove functions they deem nessary in order to build their own insight gather model. 



<p align="center">
<img src="trainimages/ga_bigquery_query.png" width="350" height="350">
</p>

When the data was load, I created 5 functions to automate clean and plotting the data based on column inputs. Since this project focused on ad revenue, the charts below are specific to the "source" of revenue. However, I could have just as easily changed "source" to "device" or "city" to explore differences in metrics among different devices or regions. 

- Barchart (Exploring overall data)
- Piechart (Exploring % of categories)
- Time Series (Exploring data through time)
- Table (Measure ratios of grouped data)
- Table and Barchart (Further Analysis of data)

<p align="center">
<img src="trainimages/PieChart.png" width="400" height="400">
</p>
<p align="center">
<img src="trainimages/medium_ratios.png" width="500" height="600">
 <img src="trainimages/Revenue.png" width="700" height="500">
 </p>
 
[Back To The Top](#Google-Analytics-Ecommerce)

CPM makes up for 7.4% of total revenue while CPC only 1.5%. However, there is a significant difference in revenue per visit between CPM and CPC. We will explore that further in the next section and run a number of hypothesis tests.

---

## Models

CPC vs CPM
Alpha Threshold = 5%

Null Hypothesis:
1. The purchase rate/visit of CPC and CPM come from the same distribution.
2. The revenue/visit of CPC and CPM come from the same distribution.
3. The page views/visit of CPC and CPM come from the same distribution.
4. The time spent/visit of CPC and CPM come from the same distribution.

Alternative:
1. The purchase rate/visit of CPC and CPM come from different distributions.
2. The revenue/visit/visit of CPC and CPM come from different distributions.
3. The page views/visit of CPC and CPM come from different distributions.
4. The time spent/visit of CPC and CPM come from different distributions.

A histogram of purchase amounts per visitor is below.
<p align="center">
<img src="trainimages/Histogram.png" width="700" height="400">
</p>
CPC had 13,079 visits and 242 purchases. CPM had 6,184 visits and 140 purchases. Since the data from the histogram is not normally distributed, I decided to use the Mann-Whitney U-test.
<p align="center">
<img src="trainimages/p_values.png" width="400" height="400">
</p>
The results from our Mann-Whitney U-test returned a p-value of 0.027 and 0.024 for purchase/visit rate and revenue/visit respectively. This is below our p-value threshold of 5% so we can reject the null and accept the alternative hypothesis that CPM is better than CPC advertising.

The p-values for pageviews/visit and time spent/visit were far larger than 5% so we cannot reject the null.

However, the variances of the data are quite large so I ran the Welsh T-Test with equal variance being False:
<p align="center">
<img src="trainimages/Welsh%20T%20Test.png" width="350" height="300">
</p>
The p-value for purchase rate is .064 which is above the alpha threshold so we cannot reject the null. However, for average revenue per visit our p-value was .046 which is below our alpha threshold so we can reject the null and accept the alternative hypothesis that CPM is better than CPC. This does not necessarily indicate that CPM is more accretive than CPC because we do not know the price the Google Merchanise Store paid for their CPM and CPC ad campaigns. We can, however, use the average revenue per visit metric to help bid on CPM and CPC ad traffic in the future.


[Back To The Top](#Google-Analytics-Ecommerce)

---

## Author Info

- LinkedIn - [clifford-cheng](https://www.linkedin.com/in/clifford-cheng/)
- Email - cliffpcheng@gmail.com
- Link to Presentation - Google Slides(https://docs.google.com/presentation/d/1hmPWkk8wQeU-I1R2UWYbF2AE2LGmVv5vj5d2Z5rZG5g/edit?usp=sharing)

[Back To The Top](#Google-Analytics-Ecommerce)
