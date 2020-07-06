# Tracks over Time 

Exploring the Development of transportation tracks from around the world over time.
By: Clifford Cheng, Nora Huntington & Samantha Jamwal

## Describing the Data

The Transit systems of the world Dataset contained multiple datasets with a common Key of ‘city id’, we used this to merge the sets together. Each dataset had many different columns that gave the ability to create maps of the stations and tracks over a geographical map similar to google maps. 

The city dataset contained 334 cities with their corresponding country and geo coordinates. 
![city dataset](https://user-images.githubusercontent.com/62854851/86546716-0b09b900-beeb-11ea-9781-2b0c4ec64ce9.png)


The station dataset contained 15,794 stations around the world with their corresponding geo coordinates and the year building started, the year it opened, and the year it closed, if applicable. 
![station dataset](https://user-images.githubusercontent.com/62854851/86546733-1ceb5c00-beeb-11ea-88b7-f81ad64ceb71.png)

The track dataset contained 9,271 tracks around the world with a list of geo coordinates mapping their section and the year building started, the year it opened, and the year it closed, if applicable. 
![track dataset](https://user-images.githubusercontent.com/62854851/86546750-32608600-beeb-11ea-9796-781619d8f77e.png)


There was also a systems dataset with 488 transit systems and a lines dataset with 1,343 lines. A dataset called station_lines allowed us to map these systems and lines to our station table and a track_lines dataset allowed us to map the systems and lines to our tracks table.

We were interested in the data containing the information of cities, stations and tracks. These included the geolocations, start date, close date and opening date of the tracks and stations along with the names of the cities and their corresponding countries. 

The column ‘coords’ gave a string value instead of a list with the coordinates. To fix this all unnecessary information had to be removed, the string had to be converted to a list and each string had to be converted to a float. The coordinates were also in order of longitude, latitude and had to be reversed. 

#### Was a lot of data missing? If so, what did you do to handle it?


## Data Visualization

First we created a video showing the change in train tracks overtime, using……. 

Figure 1.
(gif/video of tracks across time)

Here you can see…..



Now if we compare the total of track from 1860 to 2019. 1860 was chosen because it had a better dataset to compare to then anytime before that. 

Figure 2.
![1860-bar](https://user-images.githubusercontent.com/62854851/86546776-4b693700-beeb-11ea-9842-8443e0c79622.png)



Figure 3.
![2019- bar](https://user-images.githubusercontent.com/62854851/86546788-54f29f00-beeb-11ea-9e9f-69c29db849dc.png)



As you can see since 1860 a lot more tracks have been put up and the countries that had the most tracks put up in 1860 still rank rather high up in the number of tracks compared to others with the exception of Japan. 

Figure 4.

(timeline showing major events )




##Discrepancies noted

Looking at the data we noted that a lot of track/station data is missing from Asia(excluding Japan), particularly with China. The data shows a discrepancy towards western countries, and may be due to where the data was pulled from. We suspect that there may have been more data from Japan due to the influence of the western countries after WWII. You can see the discrepancies more clearly below. 

Figure 5.


##References





















