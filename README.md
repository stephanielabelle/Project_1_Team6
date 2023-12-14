# Project_1_Team6
project 1 team 6

We got the airbnb dataset from kaggle.com. 
We chose the airbnb data because it allowed us to implement a lot of the tools learned in the classroom (cleaning, mapping, plotting, API etc.).
These days all are looking for places to go for vacations, and the first thing we think about is a reasonable place to stay. By analysing this dataset we wanted an understanding of relationships that effect rental price and renter satisfaction in an AirBnB rental.

We have cleaned the raw dataset with the following steps:

- Dropped duplicates in ‘id’ and kept only one entry, since all duplicates had the same information.
- Dropped null values from the following columns - 'host_identity_verified', 'lat','long','neighbourhood group','instant_bookable','cancellation_policy','room type','Construction year','price','last review','review rate number', and 'calculated host listings count'
- Retaining the dataframe with ‘availability 365’ column with values <=365 and >= 0 and ‘minimum nights’ > 0 and dropping all the other invalid values.
- Replaced the neighborhood group of ‘Brooklyn’ by its proper spelling where it wasn’t correct.
- Removed the ‘$’ and ‘,’ in the ‘price’ and ‘service fee’ columns, to make it just numbers so that it is easier for calculations.
- Filling the column ‘service fee’ empty cells with 0 so that it does not give NaN when we do calculations.
- Changed the datatype of the ‘last review’ column to datetime (it was an object).



Divya:

This section is for hvplot and geoapify API.
- First, with the cleaned csv data I have displayed the distribution of properties of all the neighborhoods in the dataset depicted by a different colour for each neighborhood group. Hovering over each point displays the price and rating of each property. This shows us the concentration of properties in different areas.
- Next, I wanted to display the average stats for each 'neighborhood group' as a whole. Hence, I gathered just the required columns and calculated the average values for 'longitude', 'latitude' for each 'neighborhood group' to plot, and average, minimum, and maximum 'price', and average 'rating' to display. Then, I used the geoapify API to get the 'attractions' near each neighborhood group. Since the response did not display 'name' at times, necessary checks had to be made to make sure the correct value is being populated. Also, restricted the attractions to 3 so as not to overcrowd the display. The map plot contains the neighborhood groups showing the avg, min and max price, avg rating and attractions. The size of the points is number of airbnb listings in each 'neighborhood group'. This helps us in identifying which neighborhood might be suitable to choose the airbnb from based on which attractions need to be near, which have better rating or what price range is preferred.
- Then, wanted to display the 10 most expensive places with good rating for people looking for the best places to stay. Dataframe was sorted to get the highest price and best rating. Neighborhood and neighborhood group were combined to get the location. We get the nearest 3 attractions for each listing using geoapify API and plot the map with the size based on the 'price'. The map displays more details of each property like 'Price','Service Fee','Room Type','Location','Rating','Minimum Nights', and 'Attractions'. This helps to decide on the place by considering all the information available as it is not just an overview of a group, but exact information of a listing.
- Also wanted to display 10 of the least expensive places for the budget travelers. Data was populated this time with lowest price and best rating. After getting the combined location and attractions, the map was plotted with the size based on the 'price'. This map also displays all the details such as 'Price','Service Fee','Room Type','Location','Rating','Minimum Nights', and 'Attractions', which helps us make an informed decision to choose a place to stay.
- Finally, thought of having a combined view of most expensive and least expensive places to see if there is any difference in the location for the variation of the price. After plotting the merged graph, I am displaying all the details like before on hovering. But the plot does not give an insight into why certain places are so expensive and others are not. So it does not seem to be based on just location as per the plotted data.
