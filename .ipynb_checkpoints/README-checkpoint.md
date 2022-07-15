# Songs and Songs Played ETL Pipeline
Extract data on songs and Sparkify songs played log, and transform and load into postgresql database for further analytics.
The schema created for loading contains a songs played fact table and dim tables for users, songs, artists and time songs were played.

## Usage
```python
python3 -m create_tables
```
Drops (if exists) and creates the sparkify database. 
Establishes connection with the sparkify database and gets cursor to it.  
Drops all the tables.  
Creates all tables needed for song play analytics.

```python
python3 -m etl
```
Reads datasets from `data` file repository which contains Sparkify logs data and song data. Transforms and loads data into postgresql database.

## Repo Files
There are two directories from which data will be extracted. `logs_data` contains Sparkify logs on songs played by users. `song_data` contains dimensional data about songs on Sparkify

## Schema and ETL Pipeline
The star schema was used in the final datamart. The design allows fast aggregation and simplified queries (less joins than a snowflake schema). 
The ETL pipeline handles conflict for duplicate insertion of primary keys and does not accept null primary keys improving data integrity.