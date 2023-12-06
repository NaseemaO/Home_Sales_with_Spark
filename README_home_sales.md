# Home Sales.  Quering Big Data with PySpark and SparkSQL 

# Overview
Apache Spark's PySpark and SparkSQL queries used to determine key metrics about home sales data from an AWS S3 bucket dataset.

Temporary Tables (Temporary Views) created to compare query run times in three different Pyspark big data quering methods: 
DataFrame, Cache of DataFrame, and Partitioned data in Parquet format. 

# Summary 
* The shortest run time was in the Cache DataFrame Model. 

* Interestingly, the Parquet model revealed to have the longest run time. 
My expectation is that RDD (Resilient Distributed Dataset) with the partitioned data that allows for parallel processing in the Parquet Model would be more efficient and would have the shortest query run times in comparison to the DataFrame and Cache Models.

* Data was partitioned by the "date_built" field on the formatted Parquet home sales data
Perhaps the Parquet model had to go to the another partitioned Parquet data to read the "View" rating and that may have resulted in the increase in the run times. 

# Analysis 
Queries for Analysis #1, #2 and #3 were run in PySpark DataFrame Temporary Table. 

Query for Analysis #4 was run in each of the 3 different Temporary Tables for run time comparisons.

    1. The average price for a four-bedroom house sold for each year is displayed in the image below. 
<img src="\Images\4bedrooms.PNG" alt="Avg_Price_Four_Bedroom_House" width="250" height="200">

    2. The average price of a home for each year it was built that has three bedrooms and three bathrooms is displayed in the image below.  
<img src="\Images\3BB.PNG" alt="Avg_Price_3Bedrooms_3Bathrooms" width="250" height="300">

    3. The average price of a home for each year that has three bedrooms, three bathrooms, two floors, and is greater than or equal 
    to 2,000 square feet is displayed in image below. 
<img src="\Images\3BB2F.PNG" alt="Avg_Price_3Bedrooms_3Bathrooms_2Floors" width="250" height="300">

    4. Query: the "view" rating for homes costing more than or equal to $350,000

    Same Query was run in 3 different big data quering methods for run time comparisons. 

    The result and Run Times for Query run on each of the 3 different Temporary Tables DataFrame, Cache of DataFrame, and Partitioned data in Parquet format are displayed in the images below. 

Temporary Table: DataFrame

<img src="\Images\Df_query_run_time.PNG" alt="Temp_Table_DataFrame_Query_Run_Time" width="1000" height="600">



Temporary Table: Cache DataFrame

<img src="Images\cache_query_run_time.PNG" alt="Temp_Table_Cache_DataFrame_Query_Run_Time" width="1000" height="600">



Temporary Table: Parquet 

<img src="Images\parquet_query_run_time.PNG" alt="Temp_Table_Partitioned_Parquet_Query_Run_Time" width="1000" height="600">

Run Times in the 3 different Temporary Table big data query methods:

DataFrame: 0.6911733150482178 seconds

Cache DataFrame: 0.4713459014892578

Parquet: 0.715890645980835 seconds

The shortest run time was in the Cache DataFrame Model 
The longest run time was in the Parquet Model 

# Technical Details
## Programs
    Spark Version 3.5.0
    Java 

    Packages / Modules:
    Pyspark (Python API for Spark)
    SparkSQL 

    Imported dependencies for example: os, environments, PySpark SQL functions

    PySpark run in Jupyter Notebook

    Google Colaboratory used work and run Jupyter Notebook

## Dataset
"https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-classroom/v1.2/22-big-data/home_sales_revised.csv"

## Process
Read in dataset 'home_sales_revised.csv' from an external source, the AWS S3 bucket, into a Spark DataFrame.

<img src="Images\data_in_dataframe.PNG" alt="Data_in_DataFrame" width="900" height="250">

Temporary Tables (Temporary Views) created for three PySpark big data quering methods to prepare data for SparkSQL. 

SparkSql queries include filtering, grouping and aggregating data. 

1. Temporary View of PySpark DataFrame called 'home_sales'

SparkSQL queries ran to answer all 4 analysis questions. Query run time computed for analysis question # 4. 

2. Temporary View of Cached DataFrame 'home_sales'.  Cached the table, verified it is cashed. After use, uncached and verified it is uncashed. 

Ran the query to answer analysis question 4 and query run time computed.  

3. Temporay View of partitioned data in Parquet format. 
Partitioned by 'date_built' field on the formatted parquet home sales data. 

Ran the query to answer analysis question 4 and query run time computed. 

# Acknowledgements: 
Instructor: Hunter Hollis, and TAs: Sam Espe and Randy Sendek for their guidance on this project.
