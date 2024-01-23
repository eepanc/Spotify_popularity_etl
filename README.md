# spotify-music-popularity-etl

### Introduction

This ETL project leverages the Spotify API to retrieve the daily top 50 global songs, employing AWS cloud tools for extraction, transformation, and loading. The process starts with a Jupyter notebook using Python to extract data, which is then deposited into an S3 bucket. Subsequently, the data is segregated into different S3 buckets based on categories such as artist, album, and songs. The final step involves loading the processed data into AWS Athena for comprehensive analysis, facilitated by AWS Glue.

### About Datase/API

Utilizing Spotipy, a lightweight Python library for the Spotify Web API, the project extracts essential data elements such as "artist," "album," and "song." 
You can check the [Spotipy API](https://spotipy.readthedocs.io/) for more information and documentation regarding the API.

### AWS Services Used

- **S3 (Simple Storage Service):** AA highly scalable object storage service that enables the storage and retrieval of vast amounts of data from any location on the web.
- **AWS Lambda:** A serverless computing service designed for running code without the need for server management, particularly useful for responding to events like S3 changes.
- **CloudWatch:** Amazon CloudWatch collects and presents real-time logs, metrics, and event data through automated dashboards for efficient infrastructure and application maintenance.
- **Glue Crawler:** A managed service that automatically crawls data sources, identifies formats, and infers schemas to create an AWS Glue Data Catalog.
- **Data Catalog:** AWS Glue Data Catalog serves as a fully managed metadata repository for simplified data discovery and management in AWS.
- **Athena:** An interactive query service facilitating the analysis of data in Amazon S3 using standard SQL, seamlessly integrating with the Glue Data Catalog

### Architecture

<img width="1163" alt="AWS architecture" src="https://github.com/eepanc/Spotify_popularity_etl/blob/main/spotify.png">

### Workflow

- Utilize Spotipy API in a Jupyter Notebook for local ETL processing.
- Deploy a CloudWatch trigger to activate the Python code daily.
- Implement AWS Lambda to extract data into an S3 bucket.
- Set up triggers for automatic transformation and loading into another S3 bucket.
- Employ CloudWatch for writing the transformation and loading functions.
- Load the transformed file into separate S3 buckets for "artist," "album," and "songs."
- Construct Analytics Tables using Glue and Athena for in-depth analysis.
