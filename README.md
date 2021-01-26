# Project: Data Warehouse with AWS
-------------------------
## Introduction 

This project focuses on moving Sparkify, a made up music stereaming company, user base  and song database data onto the cloud AWS (Amazon Web Services). The task consists of creating an ETL pipeline that extracts Sparkify data from S3, stages them in Redshift, and transforms data into a set of dimensional tables for their analytics team to continue finding insights in what songs their users are listening to. 

## Getting Started

There are two datasets available for this project (Log Data and Songs Data) and they are both a collection of JSON files residing in publically available S3 buckets. This project leverages on Python, SQL, PostgreSQL, and AWS services.

## Schema

This project uses a star schema optimized for queries on song play analysis which includes the following tables:

#### Staging Table 

* __staging_songs__ - information about songs and artists (event_id,artist_name,auth,user_first_name,user_gender,item_in_session,user_last_name,song_length,\ 
                      user_level,location,method,page,registration,session_id,song_title,status, ts,user_agent,user_id)

* __staging_events__ - actions completed by users (song_id,num_songs,artist_id,artist_latitude,artist_longitude,artist_location,artist_name,title,duration,year)
    

#### Fact Table

* __songplays__ - records in log data associated with song plays i.e. records with page NextSong (songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent)

#### Dimension Tables
* __users__ - users in the app (user_id, first_name, last_name, gender, level)
* __songs__ - songs in music database (song_id, title, artist_id, year, duration)
* __artists__ - artists in music database (artist_id, name, location, latitude, longitude)
* __time__ - timestamp of records in songplays broken down into specific units (start_time, hour, day, week, month, year, weekday)

## Prerequisites

AWS and Python 3 is the environment utilized with the addition of the following libraries:

* __postgresql__ (+ dependencies) 
* __jupyter__ (+ dependencies) 


## Installing

```
import configparser
import psycopg2
from sql_queries import create_table_queries, drop_table_queries
from sql_queries import copy_table_queries, insert_table_queries

```

## Deployment

* **etl.ipynb**: Jupyter Notebook for creating/testing the core logic implemented in etl.py file.
* **testing_code.ipynb**: Jupyter Notebook for testing the accuracy of SQL queries and ETL.
* **create_tables.py**: This file drops and creates your tables. It is executed to reset tables before each time ETL script is run.
* **etl.py**: This file reads and processes a single file from song_data and log_data and loads the data into the tables. 
* **sql_queries.py**: Contains the data description language (DDL) syntax for creation/dropping of table as well as the data manipulation language (DML) for inserting data.
* **dwh.cfg**: Contains the configuration paramaters for AWS.


### _Acknowledgments_

* Chapeau to StackOverflow, GitHub, and Udacity Knowledge platforms for providing some guidance code.
