# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The project aims to find any relations between the parameters of bike stations and POIs in Vancouver (it can be easily modified for any other city, available on used sources), applying knowledge about APIs, EDA, and regression modeling. 

## Process
### Step 1: CityBikes (1_city_bikes.ipynb)
#### Explored CityBikes API -> Collected data from it -> Explored data -> Saved results

1. Explored API documentation of CityBikes.
2. Wrote function _get_city_data(city)_, which returns all the networks for a specified city.
3. Checked 3-5 cities to choose the one that has data to parse -> chose Odessa, Ukraine.
4. Wrote function _bike_stations_of_city(city)_ which takes all hrefs of city networks from 2. and returns all the stations in the city.
5. Got data for Odessa and noticed that empty_bikes and free_slots are all zeroes, checked a couple of other cities and ended up with Vancouver.
6. Wrote function _get_stations_details(city)_ to parse details for all stations from 5. and put it in DataFrame _vancouver_stations_df_.
7. Saved DataFrame to pkl, for the next steps.

### Step 2: Foursquare and Yelp (2_yelp_foursquare_EDA.ipynb)
#### Explored 4sqr API -> Collected data from it -> Explored Yelp API -> Collected data from it -> Compared 4sqr and Yelp data -> Saved results

1. Imported _vancouver_stations_df_ DataFrame from previous step.
2. Explored Foursquare API, and chose categories of places to parse.
3. Wrote function _get_nearby_places_, which gives the latitude and longitude of bike stations from the previous step and returns all chosen types of POIs in a radius of 1000m and a maximum of 50 POIs per station/location.
4. Explored data and found out that it's incomplete.
5. Explored Yelp API, and chose categories of places to parse.
6. Wrote function _get_yelp_places_ which is similar to 3. and returns all chosen types of POIs in a radius of 1000m and a maximum of 50 POIs per station/location.
7. Compared Foursquare and Yelp data.
8. Since Yelp data is much more precise, saved it to pkl for the next steps.


### Step 3: Joining data + EDA + SQL (3_joining_data.ipynb)
#### Data joining -> EDA -> SQL

1. Imported _vancouver_stations_df_ and _yelp_places_df_ DataFrames from previous steps.
2. Joined them in one DataFrame and saved to pickle.
3. Clenaed data:
     3.1. _Address_ missing values replaced with 'Unknown'
     3.2. _Price Range_ replaced with 5 categories: 1 to 5
     3.3. Checked for duplicates (no duplicates)
5. Created 10 different plots to visualize and explore data.
6. Created SQLite database using this data.

Define Bike Availability Classes:

Low Availability: 0-3 bikes
Medium Availability: 4-8 bikes
High Availability: 9+ bikes
Use a Classification Model:

Logistic Regression (simple)
Random Forest or Decision Tree (handles non-linear relationships)
Neural Networks (if enough data)
Feature Selection:

Keep Ratings, Review Count, and high-impact POI types.
Add time-based features (rush hour vs. non-rush hour)



## Results
(fill in what you found about the comparative quality of API coverage in your chosen area and the results of your model.)

## Challenges 
(discuss challenges you faced in the project)

## Future Goals
(what would you do if you had more time?)
