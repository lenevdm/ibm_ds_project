# ibm_ds_project
IBM applied data science capstone project

## Project scenario
SpaceX is an American aerospace manufacturer known for its ambitious goal of reducing space transportation costs and enabling the colonization of Mars. One of the key innovations introduced by SpaceX is the development and implementation of reusable rocket technology. The first stage of SpaceX's Falcon 9 and Falcon Heavy rockets, which is the part that provides the initial thrust during liftoff, is designed to be recovered and reused for multiple launches. This is in contrast to traditional rocket designs where the first stage is typically discarded after a single use.

A new rocket company, Space Y, wants to compete with SpaceX. In this project we will determine the price of each launch. Data will be collected from various sources, processed and compiled into dashboards. We will also determine if the first stage of the rocket will be reused or not by training a machine learning model to predict if the first stage will be reused.

## Collecting the data
### SpaceX API
We will be using launch data from the SpaceX REST API.
The endpoint we are using: https://api.spacexdata.com/v4/launches/past 

Responses are given as a list of json objects. Each json object represents a launch. 
We will normalise the json into a flat table. 
### Webscraping wiki pages
BeautifulSoup will be used to scrape html tables that contain useful launch data for Falcon 9 rockets. 
Data will be parsed and converted to a Pandas dataframe

## Data wrangling
Tasks:
- Get additional data from the SpaceX API
- Sampling data to remove unwanted data (for example, remove Falcon 1 data)
- Dealing with nulls (especially in the payload mass data)

## Exploratory analysis using SQL

## Exploratory analysis using Pandas and Matplotlib

## Interactive visual analytics and dashboard

## Predictive analysis (classification)

## Final presentation
