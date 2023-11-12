# python-api-challenge

WeatherPy

Dependencies are imported

Generate the Cities List by Using the citipy Library
    Empty lists are made to hold the latitude and longitude combinations as well as city names. Range of latitude and longitude value limits are set to cover full ranges of both latitude, -90 to 90, and longitude, -180 to 180. “np.random.uniform(lat_range[0], lat_range[1], size=1500)”, is used to select 1500 values each, within the latitude and longitude limits from the previous lists. The values selected all have an equal, “uniform”, chance of being selected. Next, the, “Citify”, library is used to generate city names closest to the coordinates given, and only one unique city will be selected and added to the list. Finally the number of unique cities is counted and displayed.

Requirement 1: Create Plots to Showcase the Relationship Between Weather Variables and Latitude

    The base URL variable is created per the OpenWeatherMap API documentation to direct it to their site. This base URL will later be appended with additional search criteria later. An empty list called, “City Data”, is initialized, this will hold the weather data for each city. Next a loop is created to gather information for each city and grouped into quantities of 50 to make it easier to track and analyze. Next the, “city_url”, is constructed to handle each city for each iteration of the loop. “city_url” , is constructed using the, “app_id”, unique to the user and site, “weather_api_key”, “units”,  to use, and, “q”, which is the city to be queried. All of those combined create an endpoint that is used to query each unique city per iteration. The, “city_response = requests.get(city_url + city).json()“, is created next. What this does is it creates a parsed json request equal to the request parameters. The .json response is then parsed based upon criteria that is user defined according to the open weather API documentation that specifies the specific location to grab the data from. It is then appeneded to a dictionary file. An error message exception is returned if the city is not found, this keeps the loop going without aborting the loop as a whole. 

A data frame is created from the list of cities, and the values are counted. The last instance the was ran, it counted 585 cities, meaning it couldn’t find 20 of the cities. Sample data from the data frame is displayed, exported to a CSV, reimported as a CSV and converted back into a data frame with the city ID as the index.

Create the Scatter Plots Requested

A series of scatter plots are created using ALL of the data parsed  from the open weather API json response showing latitude versus other json responses. 

Compute Linear Regression for Each Relationship

A function is then created that creates a scatterplot with a linear regression line and formula. This function accepts the following parameters, “dataframe”, which is the name of a dataframe to be used.“xCol” and “yCol”, which are the specific names, in string form, of columns in the data frame previously declared, the, “x” and “y”, denote which axis the values will be displayed on. The final parameters, “xLabel” and “yLabel”, are strings which define the plot labels. 

# Create a DataFrame with the Northern Hemisphere data (Latitude >= 0)

Data is gathered and split into two groups, northern and southern, hemisphere, based upon the latitude. Northern hemisphere being 0-90 and southern being 0—90. Following this, a series of scatterplots are created that show the differences, and similarities of northern and southern hemisphere.

VacationPy

This script first imports the required dependencies and the CSV created from the, “WeatherPy”, script previously created and displays the cities on a map. note: I used, “ESRI”, for the map tiles, because it looks neat.

Narrow down the city_data_df DataFrame to find your ideal weather condition

A series of parameters are then defined based upon my search criteria, and rows that contain null values are dropped.

Create a new DataFrame called hotel_df

A new dataframe is created by copying the filtered dataframe from the previous step and a column named, “Hotel Name”, is added to the end.

For each city, use the Geoapify API to find the first hotel located within 10,000 metres of your coordinates.

Hotel search criteria for the ”Geoapify”, API are defined to search within a 10km radius of the coordinates. A dictionary of parameters is created that will be used in a later step. The dataframe is looped through based upon the index and row in the dataframe, and the latitude and longitude values are defined using .loc. Next the longitude and latitude values are used to help specify the are that will be used to identify the search area, these are defined using the Geoapify documentation. A JSON request using the parameters is combined with the base url is generated, then the response is read and moved into the name_address variable. The script then tries to find first hotel found within 10kms, adds the name and address to a list, and If nothing is found an exception occurs to keep the script from erroring out. During the search and find loop, the results are printed line by line. Once completed the dataframe is displayed.

Add the hotel name and the country as additional information in the hover message for each city in the map.

Finally another map is created based upon the results of the preferred location and the “within 10kms”, criteria defined earlier. The color of the dots indicate the countries, the size of the dots correspond to the humidity levels, and hovering over the points will display, the latitude, longitude, hotel name, and country.


“Examples#.” Examples - Matplotlib 3.8.1 Documentation, matplotlib.org/stable/gallery/index.html. Accessed 4 Nov. 2023. 
Feulner, Georg, et al. “Why Is the Northern Hemisphere Warmer than the Southern Hemisphere?” NASA/ADS, Apr. 2013, ui.adsabs.harvard.edu/abs/2013EGUGA..15.8172F/abstract#:~:text=Volkwardt,%20Silvia-,Abstract,over%20its%20origin%20for%20centuries. 
Guide, User. “User Guide.” User Guide - HoloViews v1.18.1, 8 Nov. 2023, holoviews.org/user_guide/index.html. 
“Linear Regression in Python.” Real Python, Real Python, 26 June 2023, realpython.com/linear-regression-in-python/. 
Manual, The User. “User Guide#.” User Guide - HoloViews v1.18.1, 8 Nov. 2023, holoviews.org/user_guide/index.html. 
Petrou, Theodore. Panda’s Cookbook: Recipes for Scientific Computing, Time Series Analysis and Data Visualization Using Python. first ed., Packt Publishing, 2017. 
