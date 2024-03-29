# The Zuber Database
## Introduction
As an analyst for Zuber, a newly established ride-sharing company in Chicago, your responsibility is to analyze the available data to uncover patterns and insights. Your primary objective is to gain a better understanding of passenger preferences and determine how external factors influence ride frequency. To achieve this, you will work with a database containing information from competitors to identify trends and test a hypothesis on the impact of weather on ride demand. By leveraging data analytics, you will help Zuber make data-driven decisions to improve their services and outperform their competitors in the ride-sharing industry
## **:file_folder: DATASETS**
The data set contains the following 4 tables which you may refer to the relationship diagram below to understand the connection.
### **1.neighborhoods table**: 
<details><summary>
View Table
 </summary> 
 data on city neighbourhoods
 
 -Show the first 5 values
   
 | neighborhood_id	|  name |
 | --------------- |  --------- |
 | 0	              | Albany Park |
 | 1	              | Andersonville |
 | 2	              | Archer Heights |
 | 3	              | Armour Square |
 | 4	              | Ashburn       |
 | 5	              | Auburn Gresham |

 </details>

### **2.cabs**:
<details><summary>
View Table
 </summary>
 data on rides
 
 -Show the first 5 values
 
 -vehicle_id was cut short 11 characters.
 
  | cab_id	|  vehicle_id | company_name |
  | ------ |  -----------| ------------ |
  | 0      |  0fc17a66d66...| Dispatch Taxi Affiliation |
  | 1      |  38f6145c9a2...| Taxi Affiliation Services |
  | 2      |  11c21d0290e...| Star North Management LLC |
  | 3      |  43c12494b50...| Dispatch Taxi Affiliation |
  | 4      |  a48710b8f31...| Blue Ribbon Taxi Association Inc |
  | 5      |  c591191b4ca...| Blue Ribbon Taxi Association Inc |
 
 </details>
 
### **3.trips**:
<details><summary>
View Table
 </summary>
 data on rides
 
 -Show the first 5 values
 | trip_id	|  cap_id | start_td            | end_ts	            | duration_seconds	| distance_miles | pickup_location_id | dropoff_location_id |
 | ------ |  --------| ------------------- | -----------------  | -----------------| ---------------| -------------------| --------------------|
 | 1       |  1514   |  2017-11-07 21:00:00| 2017-11-07 21:00:00 | 81              |  0.04          | 0                  | 0                   |
 | 2       |  1514   |  2017-11-07 21:00:00| 2017-11-07 21:00:00 | 671             |  0.65          | 0                  | 0                   |
 | 3       |  1768   |  2017-11-03 14:00:00| 2017-11-03 15:00:00 | 318             |  0.9           | 0                  | 0                   |
 | 4       |  4274   |  2017-11-24 04:00:00| 2017-11-24 04:00:00 | 115             |  0.4           | 0                  | 0                   |
 | 5       |  3970   |  2017-11-12 03:00:00| 2017-11-12 03:00:00 | 475             |  1.6           | 0                  | 0                   |

 </details>
 
 ### **4.weather_records**:
 <details><summary>
View Table
 </summary>
 data on rides
 
 -Show the first 5 values
  | record_id	|  ts                | temperature | description|
  | --------- | -------------------| ------------| -------------| 
  | 1         | 2017-11-01 00:00:00| 276.15	     | broken clouds| 
  | 2         | 2017-11-01 01:00:00| 275.7       | scattered clouds|
  | 3         | 2017-11-01 02:00:00| 275.61      | overcast clouds |
  | 4         | 2017-11-01 03:00:00| 275.35      | broken clouds   |
  | 5         | 2017-11-01 04:00:00| 275.24      | broken clouds   |
 
  </details>
  
 ## Table scheme
  
  ![image](https://github.com/kaizermm/The-Zuber-Database/assets/121756502/2edba3f3-131c-40eb-b0d0-273d6213d7db)

## :speech_balloon: Table of contents for SQL
ANALYSIS QUESTIONS for SQL
1. Find the number of taxi rides for each taxi company. Name the resulting field trips_amount and print it along with the company_name field. Sort the results by the trips_amount field in descending order.

2. Could you please generate the SQL query that retrieves the pickup location names and the total number of trips taken to each pickup location, while also joining the 'cabs,' 'trips,' and 'neighbourhoods' tables to associate the data correctly and sorting the results in descending order of trip count?

3. Could you please create an SQL query to retrieve the drop-off locations with the highest number of trips, using the "neighbourhoods" dataset's "name" column, joined with the "cabs" and "trips" tables? The query should calculate the count of trips for each drop-off location and order the results in descending order of trip count.

4. Retrieve from the trips table all the rides that started in the Loop (neighborhood_id: 50) and ended at O'Hare (neighborhood_id: 63) on a Saturday. Get the weather conditions for each ride. Use the method you applied in the previous task. Also, retrieve the duration of each ride. Ignore rides for which data on weather conditions is not available.

## :speech_balloon: Table of contents for Python
While PostgreSQL was instrumental in extracting data, it fell short in providing crucial visualizations and in-depth statistical analyses. Our objectives included pinpointing the most frequented pickup and drop-off locations, determining the leading taxi company, and rigorously testing a hypothesis concerning the average ride duration between the Loop and O'Hare International Airport on rainy Saturdays.

1. After using PostgreSQL, to pull out the 4 data sets:
### Dropoff_location.csv.It contains the following data:
* drop_location: Chicago neighborhoods where rides ended
* n_trip: total number of rides that ended in each neighbourhood

### Rides_per_company.csv.It contains the following data
* company: taxi company name
* trips_amount: the number of rides for each taxi company

### Pickup_location.csv: It contains the following data
* pickup_location: Chicago neighborhoods where rides started
* n_trop: number of rides that ended in each neighbourhood

### Weather_condition.csv: It contains the following data
* start_ts: date and time of the beginning of the ride that started in the Loop and ended at O'Hare
* Weather_conditions: When the description matches 'rain' or contains '%storm%', we categorize it as 'Bad'; otherwise, it's classified as 'Good'.
* duration_second: ride duration in seconds where ride that started in the Loop and ended at O'Hare

Step for data analysis
1. Load the data and Preprocessing
2. Top ten companies with highest number of rides.
3. Number of trips for each dropoff location
4. Number of trips for each each pickup location
5. Prepare data for testing hypotheses
## Conclusion and further improvement
Conclusion: The project identified Loop and River North as the top drop-off locations, with Flash Cab leading in trip numbers. Notably, ride durations between the Loop and O'Hare Airport vary on rainy Saturdays, implying weather's impact on ride durations.

Improvement Area: Further analysis and predictive models could explore and quantify the precise influence of weather conditions on ride durations, allowing for more informed decision-making and service optimization.

## Preview
![image](https://github.com/kaizermm/Zuber-Rideshare-Analysis/assets/121756502/07fdd33d-2c7b-4ee0-95d5-a0d7cb5f71ec){width=300}


![image](https://github.com/kaizermm/Zuber-Rideshare-Analysis/assets/121756502/f7ec6e80-fb33-47f9-b197-9ad20feb824b){width=300}


