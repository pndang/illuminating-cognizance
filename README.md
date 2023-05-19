# Illuminating-Cognizance
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

<b>Main Question</b>: Do outage attributes, specifically start time, consumption information, and anomaly level, seem to influence the nature of the outages, as measured by duration and cause category?
- If there are trends, are they statistically significant?

<b>Significance</b>: Analyzing the relationships between metrics of major power outages can provide data-driven insights that may lead to a better understanding of the factors that contribute to, and the outcomes, of outages. In the context of urban planning, understanding power outages can significantly assist planners and city officials in coordinating preventive/response mechanisms to improve the lives of city inhabitants

## Cleaning and EDA

### Data Cleaning


## Assessment of Missingness


## Hypothesis Testing


