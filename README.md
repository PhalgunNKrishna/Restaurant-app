# Restaurant-app

By Phalgun Krishna and Ryan Bui

A web application side project that ranks the restaurants in a group's vicinity based on how well each restaurant matches all the group members' cuisine preferences. The application includes a map of restaurants and provides directions to restaurants if prompted.

## Instructions to Run Project
In order to run the project, simply load the google_places_api.html and follow the prompts.

## Overview of the Project
The backbone of our restaurant deciding algorithm is a map data sctructure with restaurant names as its keys and whose corresponding values equal the number of times a google API query outputs the name ofthat restaurant. The following pseudo-code provides the basic understanding of this algorithm:

Imagine there have been 3 queries to the google API as follows:
1. Vegan
2. Burger
3. Indian

m = new map(string, int)

for each restaurant name outputted by the query:  
	if this restaurant is not one of the map's keys:  
		 make it an entry with key = restaurant and value = 1  
	else:  
		find the entry in the map and increment it's value by 1  

The following snippet from our code does exactly this:

```c
if (status == google.maps.places.PlacesServiceStatus.OK) {
		for (var j = 0; j < results.length; j++) {
			var name = results[j].name;
			if (restaurs.has(name) == false) {
				restaurs.set(name, 1);
			} else {
				var temp_val = restaurs.get(name);
				temp_val++;
				restaurs.set(name, temp_val);
			}
		}
}
```
The algorithm would then sort the keys based on their values in descending order and rank restaurants by this sorted list of restaurants. 

### Challenges
Our biggest challenge was simply starting the project. While obtaining the google API key was fairly easy, our lack of experience with HTML and javascript proved difficult to overcome. Thankfully, a YouTube video for locating cofee shops provided us with a strong basis for our code. The link to the first of three videos is here: https://www.youtube.com/watch?v=eLGtNm4dSxc. Another challenge we found was creating a function to get directions to the markers displayed in our application. While this link, http://www.geocodezip.com/v3_MW_example_map4c.html , provided us with an idea of how to attempt this, we still found great difficult in calling our javascript getDirections function from the HTML embedded within the marker. 

### Improvements
We eventually plan to provide directions to the restaurants listed in the "Top 5 Choices" sidebar as well as including all the restaurants outputted by the queries created by the application's user.

