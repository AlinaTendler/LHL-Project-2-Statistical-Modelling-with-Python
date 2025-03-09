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
5. Created 7 different plots to visualize and explore data.
6. Created SQLite database using this data.


### Step 4: Building a Model (4_model_building.ipynb)
#### Model bulding -> Analyzing -> Stretch task

1. Built a regression model using Python’s `statsmodels`.
2. Interpreted results.
3. Answered questions from Stretch. (_can you think of a way to turn the above regression problem into a classification one? Without coding, can you sketch out how you would cast the problem specifically, and lay out your approaches?_)


 ##### Define Bike Availability Classes:

     - Low Availability: 0-3 bikes
     - Medium Availability: 4-8 bikes
     - High Availability: 9+ bikes

##### Classification Model:
 
     - Logistic Regression
     - Random Forest or Decision Tree 

## Results

I collected, joined and cleaned data from three different sources. Used EDA to explore it and then built regression model, which showed

## Challenges 

Categories are not standartized. 1 item may have from 0 to 10+ catrgories in random order, i.e. cafe may be 1st or somewhere in the middle of the list. Later I realized that I could use categories from parsing parameters, but I didn't implement it.

I created a couple of heatmaps using folium, but GitHub didn't display it properly, then I found a partial solution with static maps (streamlit_folium), but didn't implement it.

Most of the data on Foursquare was not available. I didn't dig dipper to understand why.

## Future Goals

If I had more time, I would:

- collect data from Yelp for more categories
- collect more data from Fourqquare and join it with Yelp data 
- use API parameters to sort POIs by category
- collect and explore bikes data for different time of the day and week
- would use number of reviews adjustet by the age of POI to check relation between POI popularity and distance from bike station/ number of nearby stations in specific radius
- check how _free_bike_ and _empty_slots_ numbers change after closing hour
- collect some data for rush hours and quiet hours in POIs and check relation with _free_bike_ and _empty_slots numbers_

