# Data Engineering YouTube Analysis Project by Minh Duc
------
# Project Goals

1. Data Ingestion — Build a mechanism to ingest data from different sources
2. ETL System — We are getting data in raw format, transforming this data into the proper format
3. Data lake — We will be getting data from multiple sources so we need centralized repo to store them
4. Scalability — As the size of our data increases, we need to make sure our system scales with it
5. Cloud — We can’t process vast amounts of data on our local computer so we need to use the cloud, in this case, we will use AWS
6. Reporting — Build a dashboard to get answers to the question we asked earlier

# Getting Started
## 1.Create IAM role in AWS
* You must create user with Role Admin and S3 FullAcess
* Create access key to connect AWS console by AwsCLI
  ![image](https://github.com/minhduc2672002/youtube-trending-statistic/assets/133132824/900f81d0-9308-44e7-8471-09f3a990353d)
## 2.Create S3 bucket
* Create bucket with name de-on-youtube-raw-ap-southeast-1-dev-youtube
  ![image](https://github.com/minhduc2672002/youtube-trending-statistic/assets/133132824/a49d6a65-013f-46f3-9fa7-ee1c14c6d35e)
## 3. Upload file to s3 bucket
Link dataset: https://www.kaggle.com/datasets/rsrishav/youtube-trending-video-dataset?resource=download&select=US_youtube_trending_data.csv

Here I use the US dataset
```
vào thư mực data
#Copy toàn bộ file json vào
aws s3 cp . s3://de-on-youtube-raw-ap-southeast-1-dev-youtube/youtube/raw_statistics_reference_data/ --recursive --exclude "*" --include "*.json"
aws s3 cp US_youtube_trending_data.csv s3://de-on-youtube-raw-ap-southeast-1-dev-youtube/youtube/raw_statistics/region=us/
```
Result
![image](https://github.com/minhduc2672002/youtube-trending-statistic/assets/133132824/2b888cec-705c-46eb-b052-430be70f0623)

## 4. Create crawler from AWS Glue
Choose from bucket

![image](https://github.com/minhduc2672002/youtube-trending-statistic/assets/133132824/269bddf4-1f73-4365-b4e0-47e655f14a80)

Create role for Glue service

![image](https://github.com/minhduc2672002/youtube-trending-statistic/assets/133132824/a0c98b97-7ae1-4f1d-ac8e-c68786cc0b13)

Create database in glue
![image](https://github.com/minhduc2672002/youtube-trending-statistic/assets/133132824/870b4d7e-f54a-4876-a6ce-e4b3a45685ba)

Result after run crawler 

![image](https://github.com/minhduc2672002/youtube-trending-statistic/assets/133132824/92b0f5f8-106f-4554-8396-d7d9be6db40e)



