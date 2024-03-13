# SQL-Queries-Using-BigQuery-Public-Data

## Top 5 Reasons for Arrest in Chicago, Including Description and Location of the Crime
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

## Top 5 Reasons Crime Types in Chicago, Including Description and Location of the Crime
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
