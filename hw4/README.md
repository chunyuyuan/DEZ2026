# dez-homework-3
Homework 3: Data Warehousing & BigQuery for Data Engineering Zoomcamp 2026


## Q1
What is count of records for the 2024 Yellow Taxi Data?

SELECT count(*) FROM `hw3.tripdata`;

20,332,093


## Q2
Question 2. Data read estimation
Write a query to count the distinct number of PULocationIDs for the entire dataset on both the tables.

What is the estimated amount of data that will be read when this query is executed on the External Table and the Table?

SELECT count(DISTINCT(PULocationID)) FROM `hw3.tripdata`;

0 MB for the External Table and 155.12 MB for the Materialized Table

green_tripdata_2020-04.csv

## Q3
Write a query to retrieve the PULocationID from the table (not the external table) in BigQuery. Now write a query to retrieve the PULocationID and DOLocationID on the same table.

Why are the estimated number of Bytes different?

BigQuery is a columnar database, and it only scans the specific columns requested in the query. Querying two columns (PULocationID, DOLocationID) requires reading more data than


## Q4
How many records have a fare_amount of 0?

SELECT COUNT(fare_amount)
FROM `hw3.nonpartition_tripdata`
WHERE fare_amount = 0;

8333



## Q5
What is the best strategy to make an optimized table in Big Query if your query will always filter based on tpep_dropoff_datetime and order the results by VendorID (Create a new table with this strategy)

CREATE OR REPLACE TABLE `hw3.partition_tripdata`
PARTITION BY DATE(tpep_dropoff_datetime)
CLUSTER BY VendorID AS (
  SELECT * FROM `hw3.nonpartition_tripdata`
);

Partition by tpep_dropoff_datetime and Cluster on VendorID




## Q6
Use the materialized table you created earlier in your from clause and note the estimated bytes. Now change the table in the from clause to the partitioned table you created for question 5 and note the estimated bytes processed. What are these values?

Choose the answer which most closely matches.

    
310.24 MB for non-partitioned table and 26.84 MB for the partitioned table



## Q7
Where is the data stored in the External Table you created?


GCP Bucket

## Q8
It is best practice in Big Query to always cluster your data:


False

