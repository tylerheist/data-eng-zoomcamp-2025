# Module 3 Homework - Tyler Heist 
## Data Warehouse

### Question 1:

Answer: `20,332,093`


### Question 2:

```sql
select count(distinct PULocationID)
from `dataeng-zoomcamp-449017.ny_taxi.external_yellow_tripdata`;

select count(distinct PULocationID)
from `dataeng-zoomcamp-449017.ny_taxi.yellow_taxi_nonpartitioned`;
```

Answer: `0 MB for the External Table and 155.12 MB for the Materialized Table`


### Question 3:

```sql
select PULocationID
from `dataeng-zoomcamp-449017.ny_taxi.yellow_taxi_nonpartitioned`;

select PULocationID, DOLocationID
from `dataeng-zoomcamp-449017.ny_taxi.yellow_taxi_nonpartitioned`;
```

Answer: `BigQuery is a columnar database, and it only scans the specific columns requested in the query. Querying two columns (PULocationID, DOLocationID) requires reading more data than querying one column (PULocationID), leading to a higher estimated number of bytes processed.`


### Question 4:
```sql
select count(*)
from `dataeng-zoomcamp-449017.ny_taxi.yellow_taxi_nonpartitioned`
where fare_amount = 0;
```

Answer: `8,333`


### Question 5:

Answer: `Partition by tpep_dropoff_datetime and Cluster on VendorID`


### Question 6:
```sql
select distinct VendorID
from `dataeng-zoomcamp-449017.ny_taxi.yellow_taxi_nonpartitioned`
where tpep_dropoff_datetime between '2024-03-01' and '2024-03-15';

select distinct VendorID
from `dataeng-zoomcamp-449017.ny_taxi.yellow_taxi`
where tpep_dropoff_datetime between '2024-03-01' and '2024-03-15';
```
Answer: `310.24 MB for non-partitioned table and 26.84 MB for the partitioned table`

### Question 7:

Answer: `GCP Bucket`

### Question 8

Answer: `False`

### Question 9:

Answer: 0 bytes - I assume total row count is stored as metadata (perhaps in information schema) and that allows for no bytes needing to be processed


