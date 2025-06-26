# JHU_COVID-19_ETL_PIPELINE
Pulling live COVID-19 case data from the Johns Hopkins GitHub repo, transforming it, and loading it into SQLite (or any other target).

Explanation of each step:

1. Extract:
We pull the JHU “confirmed cases” time-series CSV right from GitHub via pandas.read_csv(url).

2. Transform:

Melting turns the wide table (dates as columns) into a long table with one row per (country, date).

We parse the date strings into datetime objects.

We aggregate across provinces/states to get a single total per country per day.

Finally, we filter to a few example countries—swap or expand as you like.

3. Load:
We write the cleaned DataFrame into a local SQLite database named covid_etl_demo.db under the table covid_confirmed. You can swap in BigQuery, Redshift, or Snowflake by changing the write method.
