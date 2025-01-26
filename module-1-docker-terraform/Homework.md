# Module 1 Homework - Tyler Heist 
## Docker & SQL

### Question 1:
```
docker run -it python:3.12.8 bash
pip --version
```
This yields **24.3.1**

### Question 2:
pgadmin should use the service name (db) and the port used in the docker network (i.e., not what port is forwarded to on the host end).

So the answer would be `db:5432`

### Question 3:
```
select
	count(*),
	sum(case when trip_distance <= 1 then 1 else 0 end) as up_to_one_mile,
	sum(case when trip_distance > 1 and trip_distance <= 3 then 1 else 0 end) as one_to_three,
	sum(case when trip_distance > 3 and trip_distance <= 7 then 1 else 0 end) as three_to_seven,
	sum(case when trip_distance > 7 and trip_distance <= 10 then 1 else 0 end) as seven_to_ten,
	sum(case when trip_distance > 10 then 1 else 0 end) as over_ten
from public.green_taxi_data
where lpep_pickup_datetime >= '2019-10-01' and lpep_dropoff_datetime < '2019-11-01'
```

Gave `104,802; 198,924; 109,603; 27,678; 35,189`

### Question 4:
```
with 

longest_distance as (
	select
		max(trip_distance) as dist
	from public.green_taxi_data
)

select *
from public.green_taxi_data
cross join longest_distance
where trip_distance = dist
```

Gave `2019-10-31`

### Question 5:
```
select 
	z."Zone",
	sum(gta.total_amount) as zone_amount
from public.green_taxi_data as gta
inner join zones as z
	on z."LocationID" = gta."PULocationID"
where 
	cast(lpep_pickup_datetime as date) = '2019-10-18'
group by 1
having sum(gta.total_amount) > 13000
order by 2 desc
```
Gave `East Harlem North, East Harlem South, Morningside Heights`

### Question 6:
```
select 
	z_do."Zone",
	tip_amount
from public.green_taxi_data as gta
inner join zones as z_pu
	on z_pu."LocationID" = gta."PULocationID"
	and z_pu."Zone" = 'East Harlem North'
inner join zones as z_do
	on z_do."LocationID" = gta."DOLocationID"
where gta.lpep_pickup_datetime >= '2019-10-01' and gta.lpep_pickup_datetime < '2019-11-01'
order by 2 desc
limit 1
```

Gave `JFK Airport`

### Question 7:
Answer: `terraform init, terraform apply -auto-approve, terraform destroy`
