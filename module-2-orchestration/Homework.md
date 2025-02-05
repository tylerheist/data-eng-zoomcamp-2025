# Module 2 Homework - Tyler Heist 
## Kestra

### Question 1:

Answer: `128.3 MB`


### Question 2:

Answer: `green_tripdata_2020-04.csv`


### Question 3:

```
select count(*)
from public.yellow_tripdata
where filename ilike '%_2020-%'
```
Answer: `24,648,499`


### Question 4:
```
select count(*)
from public.green_tripdata
where filename ilike '%_2020-%'
```
Answer: `1,734,051`


### Question 5:
```
select count(*)
from public.yellow_tripdata
where filename ilike '%_2021-03.csv'
```

Answer: `1,925,152`


### Question 6:


Answer: `Add a timezone property set to America/New_York in the Schedule trigger configuration`


