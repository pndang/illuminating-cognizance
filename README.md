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

2. Converted outage duration from minutes to hours (DURATION.HR)
- Perhaps a personal preference, converting numerical time data to a higher-order unit can simplify the EDA process by dealing with smaller numbers, which are oftentimes more intuitive and easier to process for the human eye. The connection to the data generating process is the same, which is to record the length (duration) of an outage.

3. The columns OUTAGE.START.DATE, OUTAGE.RESTORATION.DATE, OUTAGE.RESTORATION.TIME are dropped, which helps simplify the analysis and reduce memory use by keeping a smaller dataset. OUTAGE.START.TIME was not dropped as it is used in later steps.

Data snippet:

| U.S._STATE   | POSTAL.CODE   |   ANOMALY.LEVEL | OUTAGE.START.TIME   | CAUSE.CATEGORY     | CAUSE.CATEGORY.DETAIL   |   DEMAND.LOSS.MW |   RES.PRICE |   PC.REALGSP.STATE |   PCT_WATER_INLAND |   DURATION.HR |
|:-------------|:--------------|----------------:|:--------------------|:-------------------|:------------------------|-----------------:|------------:|-------------------:|-------------------:|--------------:|
| Minnesota    | MN            |            -0.3 | 5:00:00 PM          | severe weather     | nan                     |              nan |       11.6  |              51268 |            5.47874 |    51         |
| Minnesota    | MN            |            -0.1 | 6:38:00 PM          | intentional attack | vandalism               |              nan |       12.12 |              53499 |            5.47874 |     0.0166667 |
| Minnesota    | MN            |            -1.5 | 8:00:00 PM          | severe weather     | heavy wind              |              nan |       10.87 |              50447 |            5.47874 |    50         |
| Minnesota    | MN            |            -0.1 | 4:30:00 AM          | severe weather     | thunderstorm            |              nan |       11.79 |              51598 |            5.47874 |    42.5       |
| Minnesota    | MN            |             1.2 | 2:00:00 AM          | severe weather     | nan                     |              250 |       13.07 |              54431 |            5.47874 |    29         |

## Assessment of Missingness


## Hypothesis Testing


