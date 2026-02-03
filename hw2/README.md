# dez-homework-1
Homework 2: Workflow Orchestration for Data Engineering Zoomcamp 2026


## Q1
Within the execution for Yellow Taxi data for the year 2020 and month 12: what is the uncompressed file size (i.e. the output file yellow_tripdata_2020-12.csv of the extract task)?

134.5 MiB

## Q2
What is the rendered value of the variable file when the inputs taxi is set to green, year is set to 2020, and month is set to 04 during execution? 

green_tripdata_2020-04.csv

## Q3
How many rows are there for the Yellow Taxi data for all CSV files in the year 2020?

SELECT COUNT(*)
FROM zoomcamp.yellow_tripdata
WHERE filename LIKE 'yellow_tripdata_2020%';


24648499


## Q4
How many rows are there for the Green Taxi data for all CSV files in the year 2020? 

SELECT COUNT(*)
FROM `kestra-learning-485617.zoomcamp.green_tripdata`
WHERE filename >= "green_tripdata_2020-01.csv"
  AND filename <  "green_tripdata_2021-01.csv";


1734051



## Q5
How many rows are there for the Yellow Taxi data for the March 2021 CSV file? 

1925152



## Q6
How would you configure the timezone to New York in a Schedule trigger? 

Add a timezone property set to America/New_York in the Schedule trigger configuration






