# ibm_ds_project
IBM applied data science capstone project

## Project scenario
SpaceX is an American aerospace manufacturer known for its ambitious goal of reducing space transportation costs and enabling the colonization of Mars. One of the key innovations introduced by SpaceX is the development and implementation of reusable rocket technology. The first stage of SpaceX's Falcon 9 and Falcon Heavy rockets, which is the part that provides the initial thrust during liftoff, is designed to be recovered and reused for multiple launches. This is in contrast to traditional rocket designs where the first stage is typically discarded after a single use.

A new rocket company, Space Y, wants to compete with SpaceX. In this project we will determine the price of each launch. Data will be collected from various sources, processed and compiled into dashboards. We will also determine if the first stage of the rocket will be reused or not by training a machine learning model to predict if the first stage will be reused.

SpaceX advertises Falcon 9 rocket launches on its website with a cost of 62 million dollars; other providers cost upward of 165 million dollars each, much of the savings is because SpaceX can reuse the first stage. Therefore if we can determine if the first stage will land, we can determine the cost of a launch. This information can be used if an alternate company wants to bid against SpaceX for a rocket launch.

## Collecting the data
### SpaceX API
We will be using launch data from the SpaceX REST API.
The endpoint we are using: https://api.spacexdata.com/v4/launches/past 

Responses are given as a list of json objects. Each json object represents a launch. 
We will normalise the json into a flat table. 

Tasks:
1. Request and parse the SpaceX launch data using the GET request
2. Filter the dataframe to only include Falcon 9 launches
3. Dealing with Missing Values

The data_falcon9 Pandas dataframe now contains the following columns:
- FlightNumber
- Date
- BoosterVersion
- PayloadMass
- Orbit
- LaunchSite
- Outcome
- Flights
- GridFins
- Reused
- Legs
- LandingPad
- Block
- ReusedCount
- Serial
- Longitude
- Latitude

Looking at the data_falcon9 dataframe, the following columns have null values:
- PayloadMass
We calculate the mean of the PayloadMass column, and replace all null values with the mean.

The API data is exported as a csv file: dataset_part_1.csv

### Webscraping wiki pages
Use web scraping to collect Falcon 9 historical launch records from a Wikipedia page titled `List of Falcon 9 and Falcon Heavy launches`
https://en.wikipedia.org/wiki/List_of_Falcon_9_and_Falcon_Heavy_launches

For consistency, we will scrape the data from a snapshot of the List of Falcon 9 and Falcon Heavy launches Wikipage updated on 9th June 2021
`static_url = "https://en.wikipedia.org/w/index.php?title=List_of_Falcon_9_and_Falcon_Heavy_launches&oldid=1027686922"`

Tasks:
1.  Request the Falcon9 Launch Wiki page from its URL
2.  Extract all column/variable names from the HTML table header
3.  Create a data frame by parsing the launch HTML tables

The output of this stage is the CSV file: spacex_web_scraped.csv

## Data wrangling
In this section, we will perform an exploratory data analysis and also determine training labels

Tasks:
1. Calculate the number of launches on each site
2. Calculate the number and occurrence of each orbit
3. Calculate the number and occurence of mission outcome of the orbits
4. Create a landing outcome label from Outcome column

Data from this process is exported to CSV as dataset_part_2.csv

## Exploratory analysis using SQL
In this section we will understand the Spacex DataSet, load it  into the corresponding table in a Db2 database, and execute SQL queries to answer assignment questions.

Tasks:
1. Display the names of the unique launch sites in the space mission
2. Display 5 records where launch sites begin with the string 'CCA'
3. Display the total payload mass carried by boosters launched by NASA (CRS)
4. Display average payload mass carried by booster version F9 v1.1¶
5. List the date when the first succesful landing outcome in ground pad was acheived.
6. List the names of the boosters which have success in drone ship and have payload mass greater than 4000 but less than 6000
7. List the total number of successful and failure mission outcomes
8. List the names of the booster_versions which have carried the maximum payload mass. Use a subquery
9. List the records which will display the month names, failure landing_outcomes in drone ship ,booster versions, launch_site for the months in year 2015.
10. Rank the count of landing outcomes (such as Failure (drone ship) or Success (ground pad)) between the date 2010-06-04 and 2017-03-20, in descending order.

## Exploratory analysis using Pandas and Matplotlib
Tasks:
1. Visualize the relationship between Payload and Orbit type
2. Visualize the relationship between Payload and Launch Site
3. Visualize the relationship between success rate of each orbit type
4. Visualize the relationship between FlightNumber and Orbit type
5. Visualize the relationship between Payload and Orbit type
6. Visualize the launch success yearly trend
7. Create dummy variables to categorical columns
8. Cast all numeric columns to `float64`

## Interactive visual analytics and dashboard

## Predictive analysis (classification)

## Final presentation
