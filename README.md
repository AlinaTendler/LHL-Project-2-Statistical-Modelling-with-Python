# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The project aims to find any relations between the parameters of bike stations and POIs in Vancouver (it can be easily modified for any other city, available on used sources), applying knowledge about APIs, EDA, and regression modeling. 

## Process
### Step 1: CityBikes
#### Exploring CityBikes API -> Collecting data from it ->Exploring data

1. Explored API documentation of CityBikes.
2. Wrote function _get_city_data(city)_, which returns all the networks for a specified city.
3. Checked 3-5 cities to choose the one that has data to parse -> chose Odessa, Ukraine.
4. Wrote function _bike_stations_of_city(city)_ which takes all hrefs of city networks from 2. and returns all the stations in the city.
5. Got data for Odessa and noticed that empty_bikes and free_slots are all zeroes, checked a couple of other cities and ended up with Vancouver.
6. Wrote function _get_stations_details(city)_ to parse details for all stations from 5. and put it in DataFrame _vancouver_stations_df_.
7. Saved DataFrame to pkl, to use it on next steps.

### Step 2: Foursquare and Yelp



### Step 2: Foursquare and Yelp

## Results
(fill in what you found about the comparative quality of API coverage in your chosen area and the results of your model.)

## Challenges 
(discuss challenges you faced in the project)

## Future Goals
(what would you do if you had more time?)
