# ibm_ds_project
IBM applied data science capstone project

## Project scenario
SpaceX is an American aerospace manufacturer known for its ambitious goal of reducing space transportation costs and enabling the colonization of Mars. One of the key innovations introduced by SpaceX is the development and implementation of reusable rocket technology. The first stage of SpaceX's Falcon 9 and Falcon Heavy rockets, which is the part that provides the initial thrust during liftoff, is designed to be recovered and reused for multiple launches. This is in contrast to traditional rocket designs where the first stage is typically discarded after a single use.

A new rocket company, Space Y, wants to compete with SpaceX. In this project we will determine the price of each launch. Data will be collected from various sources, processed and compiled into dashboards. We will also determine if the first stage of the rocket will be reused or not by training a machine learning model to predict if the first stage will be reused.

SpaceX advertises Falcon 9 rocket launches on its website with a cost of 62 million dollars; other providers cost upward of 165 million dollars each, much of the savings is because SpaceX can reuse the first stage. Therefore if we can determine if the first stage will land, we can determine the cost of a launch. This information can be used if an alternate company wants to bid against SpaceX for a rocket launch.

## Collecting the data
Tasks:
1. Request and parse the SpaceX launch data using the GET request
2. Filter the dataframe to only include Falcon 9 launches
3. Dealing with Missing Values

### SpaceX API
We will be using launch data from the SpaceX REST API.
The endpoint we are using: https://api.spacexdata.com/v4/launches/past 

Responses are given as a list of json objects. Each json object represents a launch. 
We will normalise the json into a flat table. 

**Helper functions**
- getBoosterVersion(data): Takes the dataset and uses the rocket column to call the API and append the data to the list
- getLaunchSite(data): Takes the dataset and uses the launchpad column to call the API and append the data to the list
- getPayloadData(data): Takes the dataset and uses the payloads column to call the API and append the data to the lists
- getCoreData(data): Takes the dataset and uses the cores column to call the API and append the data to the lists

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
Looking at the data_falcon9 dataframe, the following columns have null values:
- PayloadMass
We calculate the mean of the PayloadMass column, and replace all null values with the mean.

The API data is exported as a csv file: dataset_part_1.csv

## Exploratory analysis using SQL

## Exploratory analysis using Pandas and Matplotlib

## Interactive visual analytics and dashboard

## Predictive analysis (classification)

## Final presentation
