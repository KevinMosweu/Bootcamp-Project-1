# Uber VS Weather: New York City

## Description

Since Uber is one of the most popular modes of transportation nowadays we wanted to look at the effect of different weather conditions on Uber pricing and usage. 

We gathered Uber ride data from kaggle for New York City from 2009-2015. This data consisted of 200,000 records of Uber trips which included pick up and drop off locations by latitude and longitude, start date and time, fare amount and passenger count for each trip.

Due to limitations we short listed the Uber ride data to 2900 records. Next using the pick up latitude and longitude and timestamps created from pick up date and time, we made API calls to OpenWeathermap's One call API 3.0 to collect weather data at the time and location of each trip.

Finally with all the data gathered we performed statstical analysis to see if different temperatures, weather types and times of day had any effect on Uber pricing and usage.

## Phase 1: Cleaning the Uber ride data

Once we gathered the Uber data from kaggle we inspected the various columns to see if there was any inconsistancies or bad data we needed to remove. We found records containing pick up and drop off latitudes and longitudes that were 0 values or did not indicate reasonable distances from New York City and removed them. Next we found fare amounts with negative values and we removed these records as well. We made also made calculations and added a seperate column for distance between pick up and drop off points. Inspecting this column we found 0 distance values and removed the records with these data points.

We grouped the data into different bins by time of day, fare amount, month, year and added new columns with these bins as these would be useful for our analysis. The next step was to create a timestamp column from the pick up date and time column in order to be able to make API calls. Looking at the records for 2015, these only went into 6 months of the year and we wanted to do our analysis on full years so we dropped records for the year 2015.


## Phase 2: Gathering Weather Data

Due to API call limitations we decided to take a sample of 2900 records from the cleaned uber ride data to collect weather data on. We used the pick up latitude and longitude and timestamp columns to make API calls from the OpenWeathermap website to give us the temperature and type of weather at the time and location of pick up for each record. We divided the sample into 3 seperate data sets for years 2009-2010, 2011-2012, 2013-2014 and assigned each set of data among the 3 collaborators to make API calls for weather data due to a limit call of a 1000 per person.

After collecting weather data for each of the 3 seperate data sets, these were now combined into one final data set which contained uber ride and weather data.

## Phase 3: Visualisation and Analysis

With the weather data now collected we created bins for temperature and added an extra column indicating temperature intervals and proceeded to do analysis and visualisation for the effects of temperature, weather type, time interval on fare amount and trip distance.

- Temperature

We did linear regressions for temperature vs fare amount and trip distance and found weak correlations

![1_temp_vs_fare_regression](https://user-images.githubusercontent.com/119974799/218878997-5f5ab985-c96c-4d9c-8157-94b5f3675f31.png)



Since the correlations were weak we decided to do further statistical analysis

Next we grouped the data by temperature interval to find the average fare amount and average trip distance for each interval. We then did Anova tests to see if there was any statistically significant difference between the groups for fare amount and trip distance, both p-values returned were greater than 0.05. We could not reject the null hypothesis that states that there is no statstically significant effect of temperature on average fare amount or trip distance in our data set.

- Weather Types

We did linear regressions models for trip distance vs fare amount for different weather types, namely clear, cloudy, rainy, snowy and misty weather. As expected trip distance was strongly correlated to fare amount for these weather types, however snowy weather correlation was moderately greater than the rest, which suggested that snowy weather resulted in increased pricing per distance.

To dive deeper into this analysis we grouped the data by these weather types to find the average fare amount and average trip distance for each type of weather. We then proceeded to do Anova tests to see if there was any statistically significant difference between the average fare amounts and average trip distances of the weather type groups. In both cases the p-values returned were greater than 0.05 thus we could not reject the null hypothesis that weather type has no effect on average fare amount or average trip distance.

- Time Interval

We grouped the data by time interval and calculated summary statistics for fare amount and trip distance to see if time interval had any effect. There wasn't much variation between the mean and median values between the different time intervals for both fare amount and distance.

For further analysis we ran an Anova test comparing the different time intervals for average fare amount and the p-value returned was greater than 0.05, we could not reject the null hypothesis stating that time interval has no statistically significant effect on average fare amount in our data set.

We also did an Anova test comparing the different time intervals for average trip distance and the p-value returned was less than 0.05. We rejected the null hypothesis stating that there is no statistically significant effect of time intervals on average trip distance.

To explore further we ran one sample T tests for the different time interval groups against the population mean for trip distance. The T tests for the following time intervals returned p-values lower than 0.05, showing a statistically significant difference in average trip distance compared to the population average trip distance: 12 am- 4 am, 10 am - 1 pm, 1 pm - 5 pm, 8 pm - 11 pm, 11pm - 12 am. However the T tests for these following time groups returned p-values less than 0.05 and thus did not show a statistically significant difference in average trip distance from the average trip distance of the population: 4am-7am, 7am-10am and 5pm-8pm.

## Conlusion

Temperature and weather type did not seem to have an effect on fare amount or trip distance. For time intervals, there was no effect on fare amount, however there seemed to be an effect on trip distance for certain time intervals.

## Limitations

For more accuracy it would be beneficial to do analysis on a much larger set of data.

## Collaborators

Fahmida Billa

Karan Anand

Kevin Mosweu
