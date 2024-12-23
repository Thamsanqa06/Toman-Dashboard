# Toman Bike Sales Report
## Table Of Content
- Project Overview
- Data Sources And Tools
- Project Structure
- Analysis & Results
- Recommendations
- Referances
### Brief Overview
By Using SQL and POWER-BI to show sales from the Toman Bikes where you will be able to see Sales trends in order to navigate the Revenue and Profit between 2021 and 2022. You will see the Incoporation os SQL abd Power BI
### Data Sources And Tools
- To have access to the full dataset [Click here](https://github.com/Gaelim/YT_bike_share).
- Tools Used: SQL, POWER-BI Desktop There are open source tools and they can be downloaded for free.
### Project Structure
##### 1. Build a Database on SQL
   - After Downloading Dataset, I had to build the database, store and extract my data on my SQL.
##### 2. Develop SQL queries 
- Before Developing a SQL Querie I had to first do data-preprocessing where I Joined both dataSets (2021 and 2022) using union and use it as a sub-query to extract the cost.
- Secondly create a complete querie plus the subquery to extract only the important variables that would help us in achiving our goals based on the st metrics in Addiction, create two more variables (Profit and Revenue)
- See the full querie below.
``` sql
WITH CTE AS (
    SELECT * FROM Bike_2021
    UNION
    SELECT * FROM Bike_2022
)
SELECT 
    dteday As Date,
    season as Season,
    a.yr as Year,
    weekday,
    hr,
    rider_type,
    CAST(riders AS FLOAT) AS riders,
    CAST(price AS FLOAT) AS price,
    COGS,
    CAST(riders AS FLOAT) * CAST(price AS FLOAT) AS Revenue,
    CAST(riders AS FLOAT) * CAST(price AS FLOAT) -  CAST(COGS AS float ) * CAST(riders AS FLOAT)  AS Profit
FROM CTE a
LEFT JOIN Cost b
ON a.yr = b.yr;
```

##### 4. Connect Power BI to your database
Make sure you Change the the data type of the following variables
 - Date into Date
 - Hr, Price, Rider, Profit & Renenue into numbers
##### 5. Build a Dashboard
- A Table was used to display the Hourly sales a Week between 8am till 5pm.
- A line graph + bar graph was used to display Revenue and Profit overtime
- A Donut graph used to display types of rider.

###  Analysis & Results
##### 1. Rider Growth
  - 2021: 1.2 million riders.
  - 2022: 2.1 million riders.
  - Total (2021–2022): 3.3 million riders.
##### 2. Customer Segmentation
  - Registered Riders:
    - Total: 2.7 million riders.
    - Revenue: $12 million.
    - Profit: $8 million.
  - Casual Riders:
    - Total: 620,000 riders.
    - Revenue: $3 million.
    - Profit: $2 million.
##### 3. Financial Summary (2021–2022)
  - Total Revenue: $15 million.
  - Total Profit: $10 million.
  - Profit Margin: 45% (Increase)
##### 4. Seasonal Trends
  - High Demand: Observed during the third season (summer months).
  - Low Demand: Observed during the first season (winter months).

### Recommendations
1. To Increase the Numbers during winter season create winter special to increase the revenue.
### References
- Absent Data YouTube Channel [Click Here](https://www.youtube.com/@absentdata)


