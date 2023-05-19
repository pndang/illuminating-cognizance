# Illuminating Cognizance
DSC 80 Project - A Comprehensive Look Into Major Power Outages in the U.S.

## Introduction 

### About the Data:

The subject dataset contains information on major power outages in the continental U.S.

- Number of observations: 1534 rows/outages
- Relevant columns/attributes:
    - **U.S._STATE**: Represents all the states in the continental U.S.
    - **POSTAL.CODE**: Represents the postal code of the U.S. states
    - **ANOMALY.LEVEL**: This represents the oceanic El Niño/La Niña (ONI) index referring to the cold and warm episodes by season. It is estimated as a 3-month running mean of ERSST.v4 SST anomalies in the Niño 3.4 region (5°N to 5°S, 120–170°W)
    - **OUTAGE.START.DATE**: This variable indicates the day of the year when the outage event started (as reported by the corresponding Utility in the region)
    - **OUTAGE.START.TIME**: This variable indicates the time of the day when the outage event started (as reported by the corresponding Utility in the region)
    - **OUTAGE.RESTORATION.DATE**: This variable indicates the day of the year when power was restored to all the customers (as reported by the corresponding Utility in the region)
    - **OUTAGE.RESTORATION.TIME**: This variable indicates the time of the day when power was restored to all the customers (as reported by the corresponding Utility in the region)
    - **CAUSE.CATEGORY**: Categories of all the events causing the major power outages
    - **CAUSE.CATEGORY.DETAIL**: Detailed description of the event categories causing the major power outages
    - **OUTAGE.DURATION**: Duration of outage events (in minutes)
    - **DEMAND.LOSS.MW**: Amount of peak demand lost during an outage event (in Megawatt) [but in many cases, total demand is reported]
    - **RES.PRICE**: Monthly electricity price in the residential sector (cents/kilowatt-hour)
    - **PC.REALGSP.STATE**: Per capita real gross state product (GSP) in the U.S. state (measured in 2009 chained U.S. dollars)
    - **PCT_WATER_INLAND**: Percentage of inland water area in the U.S. state as compared to the overall inland water area in the continental U.S. (in %)

### Analysis Question and Significance

<b>Main Question</b>:  Do outage attributes, specifically start time, consumption information, and anomaly level, seem to influence the nature of the outages, as measured by duration and cause category?
- If there are trends, are they statistically significant?

<b>Significance</b>:  Analyzing the relationships between metrics of major power outages can provide data-driven insights that may lead to a better understanding of the factors that contribute to, and the outcomes, of outages. In the context of urban planning, understanding power outages can significantly assist planners and city officials in coordinating preventive/response mechanisms to improve the lives of city inhabitants.

## Cleaning and EDA

### Data Cleaning

1. Combined OUTAGE.START.DATE and OUTAGE.START.TIME into one column OUTAGE.START, and combined OUTAGE.RESTORATION.DATE and OUTAGE.RESTORATION.TIME into one column OUTAGE.END
- For both outage start and end times, combining the date and time columns helps convert the times to type datetime and simplify the data by having two less, yet more meaningful columns in regards to reflecting the data generating process, which is to record the date and time an outage occurred. Having date and time together in the datetime data type also permits a wider range of operations and plotting capabilities to utilize.
<br>
<br>
2. Converted outage duration from minutes to hours (DURATION.HR)
- Perhaps a personal preference, converting numerical time data to a higher-order unit can simplify the EDA process by dealing with smaller numbers, which are oftentimes more intuitive and easier to process for the human eye. The connection to the data generating process is the same, which is to record the length (duration) of an outage.
<br>
<br>
3. The columns OUTAGE.START.DATE, OUTAGE.RESTORATION.DATE, OUTAGE.RESTORATION.TIME are dropped, which helps simplify the analysis and reduce memory use by keeping a smaller dataset. OUTAGE.START.TIME was not dropped as it is used in later steps.

Data snippet:

| U.S._STATE   | POSTAL.CODE   |   ANOMALY.LEVEL | OUTAGE.START.TIME   | CAUSE.CATEGORY     | CAUSE.CATEGORY.DETAIL   |   DEMAND.LOSS.MW |   RES.PRICE |   PC.REALGSP.STATE |   PCT_WATER_INLAND |   DURATION.HR |
|:-------------|:--------------|----------------:|:--------------------|:-------------------|:------------------------|-----------------:|------------:|-------------------:|-------------------:|--------------:|
| Minnesota    | MN            |            -0.3 | 5:00:00 PM          | severe weather     | nan                     |              nan |       11.6  |              51268 |            5.47874 |    51         |
| Minnesota    | MN            |            -0.1 | 6:38:00 PM          | intentional attack | vandalism               |              nan |       12.12 |              53499 |            5.47874 |     0.0166667 |
| Minnesota    | MN            |            -1.5 | 8:00:00 PM          | severe weather     | heavy wind              |              nan |       10.87 |              50447 |            5.47874 |    50         |
| Minnesota    | MN            |            -0.1 | 4:30:00 AM          | severe weather     | thunderstorm            |              nan |       11.79 |              51598 |            5.47874 |    42.5       |
| Minnesota    | MN            |             1.2 | 2:00:00 AM          | severe weather     | nan                     |              250 |       13.07 |              54431 |            5.47874 |    29         |

### Univariate Analysis

Figure 1 
<iframe src='assets/uni_1.html' width=900 height=500 frameBorder=0></iframe>

Figure 1 shows the distribution of outage duration in hours. Outages that lasted under 5 hours are the most common at 38.8%, followed by outages that lasted between 5 to 15 hours at 14.1%. The histogram then gradually flatten out with decreasing proportions as duration increases.

Figure 2 
<iframe src='assets/uni_2.html' width=900 height=500 frameBorder=0></iframe>

Figure 2 shows the distribution of outage cause categories. Outages caused by severe weather are the most common at 49.7%, followed by outages caused by intentional attacks and system operability disruptions, at 27.2% and 8.3%, respectively. The least common cause of outages is islanding at 2.9%.

### Bivariate Analysis

Figure 3 
<iframe src='assets/bi_1.html' width=900 height=500 frameBorder=0></iframe>

Figure 3 shows a scatterplot between outage duration in hours and monthly residential electricity price. Not considering outliers, there is no apparent trend shown. The majority of outages are less than 200 hours in duration, with a range of monthly residential electricity price between 6 to 20 cents per kilowatt-hour. 

Figure 4
<iframe src='assets/bi_2.html' width=900 height=500 frameBorder=0></iframe>

Figure 4 shows a scatterplot between outage duration in hours and per capita real gross state product. Not considering outliers, there is no apparent trend shown. Similar to previous plot, the majority of outages are less than 200 hours in duration, with a range of per capita gross state product between 31K to 65K U.S. dollars.

### Interesting Aggregates

Pivot table snippet

| U.S._STATE   |   equipment failure |   fuel supply emergency |   intentional attack |   islanding |   public appeal |   severe weather |   system operability disruption |
|:-------------|--------------------:|------------------------:|---------------------:|------------:|----------------:|-----------------:|--------------------------------:|
| Florida      |           9.24167   |                 nan     |             0.833333 |   nan       |         72      |         107.003  |                         3.42833 |
| California   |           8.74683   |                 102.577 |            15.7743   |     3.58095 |         33.8019 |          48.8062 |                         6.06111 |
| Kentucky     |          10.8667    |                 209.5   |             1.8      |   nan       |        nan      |          74.6685 |                       nan       |
| Texas        |           6.76      |                 232     |             4.97949  |   nan       |         19.0069 |          64.2482 |                        13.5133  |
| Indiana      |           0.0166667 |                 204     |             7.03125  |     2.08889 |        nan      |          75.3882 |                        77.86    |

The pivot table above shows the average outage duration aggregated by state and cause category. When visualized, the data facilitates a comparison of the cause category composition of outages among states, particularly information on which outage categories are prevalent in which states, or not, knowing this can help planners channel investments and effort toward the most appropriate solutions.

#### Interesting multivariate plots

Figure 5
<iframe src='assets/multi_1.html' width=1500 height=1000 frameBorder=0></iframe>

Figure 5 shows average outage duration aggregated by state and cause categories. Looking at Michigan for example, equipment failure has the greatest average outage duration at approximately 440.6 hours, followed by severe weather at 80.5 hours. Notably, severe weather seems to be a common cause in virtually every state.

Figure 6
<iframe src='assets/multi_2.html' width=900 height=900 frameBorder=0></iframe>

Figure 6 shows average anomaly level by cause category, subsetted by cause detail. As mentioned, severe weather as a cause category triumphs over other categories in terms of commonality, with "public appeal" having an usually high average ONI Index at 2.3. 

## Assessment of Missingness


## Hypothesis Testing


