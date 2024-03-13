# SQL-Queries-Using-BigQuery-Public-Data

## Top 5 Reasons for Arrest in Chicago with Description and Location of the Crime
```SQL
SELECT
COUNT(unique_key) AS number_of_crime, 
primary_type,
description,
location_description
FROM bigquery-public-data.chicago_crime.crime
WHERE arrest=True
GROUP BY primary_type, description, location_description
ORDER BY number_of_crime DESC
LIMIT 5
```
## Results
![ch-crime](https://github.com/KhatunaKurdovanidze/SQL-Queries-Using-BigQuery-Public-Data/blob/main/ch-crime.png)

## Top 5 Crime Types in Chicago with Description and Location of the Crime
```SQL
SELECT
COUNT(unique_key) AS number_of_crime, 
primary_type,
description,
location_description
FROM bigquery-public-data.chicago_crime.crime
GROUP BY primary_type, description, location_description
ORDER BY number_of_crime DESC
LIMIT 5
```
## Results
![ch-crime1](https://github.com/KhatunaKurdovanidze/SQL-Queries-Using-BigQuery-Public-Data/blob/main/ch-crime1.png)

## London Bike Hire Top 5 Stations by Duration

```SQL
WITH cte AS (
SELECT 
start_station_id,
start_station_name, 
SUM(duration) AS total_duration
FROM bigquery-public-data.london_bicycles.cycle_hire
WHERE start_date BETWEEN "2022-01-15 00:00:00 UTC" AND "2023-01-15 23:59:00 UTC"
GROUP BY start_station_name, start_station_id
)

SELECT 
cte.start_station_id,
cte.total_duration,
cy.name,
ROUND(cy.latitude,6) AS latitude,
ROUND(cy.longitude,6) AS longitude
FROM CTE cte
RIGHT JOIN bigquery-public-data.london_bicycles.cycle_stations cy
ON cte.start_station_id=cy.id
ORDER BY total_duration DESC
LIMIT 5;
```
## Results
![London1](https://github.com/KhatunaKurdovanidze/SQL-Queries-Using-BigQuery-Public-Data/blob/main/London1.png)

## Tableau Map
![London](https://github.com/KhatunaKurdovanidze/SQL-Queries-Using-BigQuery-Public-Data/blob/main/London.png)
