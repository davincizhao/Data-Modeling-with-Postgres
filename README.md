# Project: Data Modeling with Postgres

## Introduction
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. 
The analytics team is particularly interested in understanding what songs users are listening to. Currently, 
they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, 
as well as a directory with JSON metadata on the songs in their app.

so as a data engineer , I create a Postgres database with tables designed to optimize queries on song play analysis, 
and bring you on the project. I create a database schema and ETL pipeline for this project.


## Database schema:
1.Fact table: songplays  (songplay_id , start_time , user_id , level, \
song_id , artist_id , session_id , location , user_agent)

2.dimensional tables:

- Table: songs (song_id , title , artist_id , year , duration )

- Table: artists (artist_id , name , location , latitude , longitude ) 

- Table: users (user_id , first_name , last_name , gender , level )

- Table time (start_time , hour , day , week , month , year , weekday ) 
 
## ETL pipeline:

1.create the songs and artists dimensional tables from 'data/song_data' files.
- Use the get_files function provided above to get a list of all song JSON files in data/song_data
- Use pandas read() function read the data in JSON file, so data become a dataframe.
- Select columns for song ID, title, artist ID, year, and duration in dataframe
- Insert above list from dataframe as a Record into Song Table 
- in artists table, repeat the same step,but select different columns from JSON file. 

2.create the time and users dimensional tables, as well as the songplays fact table.
- Use the get_files function provided above to get a list of all song JSON files in data/log_data
- Use pandas read() function read the data in JSON file, so data become a dataframe. 
- Extract the timestamp, hour, day, week of year, month, year, and weekday from the ts column for time table
- Combine column_labels and time_data into a dictionary and converting this into a dataframe
- Insert above Record into time Table
- In user table, repeat the same step,but select different columns from JSON file. 

## How to run python script.
- First, open the terminal , and input command "python create_tables.py" to create the tables, the "create_tables.py" must be in the same directry with "data".

- Second, run "python etl.py" to Extract data from "data/log_data" and "data/song_data" and insert into the tables.

- Third, open jupyter notebook "test.ipynb" to test thedatabase and ETL pipeline.
 
 
 
