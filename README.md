# AWS-Data-Engineering-YouTube-Analysis-Project

## Overview

This project aims to securely manage, streamline, and perform analysis on the structured and semi-structured YouTube videos data based on the video categories and the trending metrics.

## Project Goals
1. Data Ingestion — Build a mechanism to ingest data from different sources
2. ETL System — We are getting data in raw format, transforming this data into the proper format
3. Data lake — We will be getting data from multiple sources so we need centralized repo to store them
4. Scalability — As the size of our data increases, we need to make sure our system scales with it
5. Cloud — We can’t process vast amounts of data on our local computer so we need to use the cloud, in this case, we will use AWS
6. Reporting — Build a dashboard to get answers to the question we asked earlier.

## Steps Performed
The process goes as follows:

- Uploaded the data from my local machine into the S3 bucket using AWS CLI commands while trying to maintain a proper file organization. Stored the JSON and CSV files in separate folders.
- Used AWS Glue Catalog to crawl the data from JSON and CSV files from the raw bucket which would be stored in a separate database.
- On facing issues raised due to the data in the JSON format, create a Python function using AWS Lambda to clean them and convert them into parquet format.
- Created a trigger on this Lambda function so as to run every time new data is being added to S3 bucket and the output was stored in a new database in Athena.
- Converted the CSV files into parquet format as well using AWS Glue ETL.
- Created a new Glue Crawler to crawl the clean data into the database.
- Now when all the clean data from the parquet files (converted from CSV and JSON files) is present in the same database, developed an ETL job using - AWS Glue Studio to join both the tables and store it in a separate S3 bucket intended to use for BI purposes.
- The data is now ready to be used for building dashboards out of it. I decided to analyze this data for finding out the popularity, most liked video categories, video reach, engagement and likes to views comparison of channels in UK and Canada.

## Services used:
1. Amazon S3: Amazon S3 is an object storage service that provides manufacturing scalability, data availability, security, and performance.
2. AWS IAM: This is nothing but identity and access management which enables us to manage access to AWS services and resources securely.
3. QuickSight: Amazon QuickSight is a scalable, serverless, embeddable, machine learning-powered business intelligence (BI) service built for the cloud.
4. AWS Glue: A serverless data integration service that makes it easy to discover, prepare, and combine data for analytics, machine learning, and application development.
5. AWS Lambda: Lambda is a computing service that allows programmers to run code without creating or managing servers.
6. AWS Athena: Athena is an interactive query service for S3 in which there is no need to load data it stays in S3.

## Dataset Used
This Kaggle dataset contains statistics (CSV files) on daily popular YouTube videos over the course of many months. There are up to 200 trending videos published every day for many locations. The data for each region is in its own file. The video title, channel title, publication time, tags, views, likes and dislikes, description, and comment count are among the items included in the data. A category_id field, which differs by area, is also included in the JSON file linked to the region.

https://www.kaggle.com/datasets/datasnaek/youtube-new

## Architecture Diagram
<img src="architecture.jpeg">
