# Pokemon Go - Vocabulary

## Links
Data sets
* [Data set Pokemon Go](https://www.kaggle.com/semioniy/predictemall/home).
* Pokemon ID to pokemon name [data set](https://www.kaggle.com/abcsds/pokemon#Pokemon.csv).

[Github repo](https://github.com/MaggieTsang/INFO370-Final-Project).



## Definitions

**[Pokemon go gym](https://bulbapedia.bulbagarden.net/wiki/Gym)** is a place where a Pokemon can workout. Each gym tends to specialize for a special type of Pokemon. 

> the question has arisen as to whether players can make their own Gyms. While players can’t do this instantly, as it would lead to a pretty intense influx of Gyms and upset of the PokeCoin economy, they can submit a request for a new Gym location here. Only businesses can be submitted, but it’s worth a shot if your area is low on Gyms.

> Hopefully you don’t live too far away from your local Gym, but in case you can’t spot one from where you live, go for a quick walk or car trip around your neighborhood. Niantic has been pretty good at placing Gyms relatively close to most populated areas, even if you live in a small town. Just remember to stay safe and aware while you’re out adventuring.

[Pokemon ID](https://bulbapedia.bulbagarden.net/wiki/List_of_Pok%C3%A9mon_by_National_Pok%C3%A9dex_number) is a unique ID that references a Pokemon.

INFO 370
Final Resource

Group Members: JT Anderson, Alaina Kwan, Maggie Tsang, Ben Walchenbach

Github: https://github.com/MaggieTsang/INFO370-Final-Project 
Data: Pokemon Go Data

# Predicting Pokemon Go Appearances by Pokemon Types

## Purpose of the Topic/Research Question:

> The main focus of our project was to get a better understanding of the Pokemon Go algorithm and to understand how different features influenced the spawn rates of Pokemon. We were specifically intrigued by the types of Pokemon and how their spawn rates were influenced by geography, time, and a combination of other available features provided in our dataset. Because our target was a categorical variable (type of pokemon), we faced a unique challenge in terms of using models to analyze correlations and using machine learning to predict spawn rates. This shaped the approaches for our project, our feature selection, and our statistical conclusions. 

> Our original research question revolved around whether or not Pokemon spawn rates were at all related to neighborhood incomes. Due to the complex nature of using machine learning with categorical features, plus our lack of experience using these techniques, we were unable to examine this relationship with ML methods. However, we were still able to explore this aspect of the data using map visualizations created in Python using the Folium library, then comparing these with existing maps of cities with neighborhood income demographics.

## Exploratory Data Analysis

> We chose to focus on five different American cities for this part of our exploration. These cities included New York City, Los Angeles, Chicago, Denver, and Seattle. We chose NYC, LA, and Chicago based on population (as they are the 3 cities with the highest populations in the US), but chose Seattle and Denver based off personal preference. Since we all live in Seattle, we thought it would be an interesting city to look into. One of the group members previously lived in Denver and thought it would be interesting to compare since Seattle and Denver have similar population sizes.

## City Comparisons

![alt text](img/ny_comparison.png “New York Comparison”)
Comparison between New York City’s Pokemon appearances (mapped using Folium) vs NYC Median Income by Neighborhood (all maps courtesy of [Statistical Atlas](https://statisticalatlas.com/United-States/Overview)).
![alt text](img/la_comparison.png “Los Angeles Comparison”)
Comparison between LA’s Pokemon appearances vs LA Median Income by Neighborhood
![alt text](img/chicago_comparison.png “Chicago Comparison”)
Comparison between Chicago’s Pokemon appearances vs Chicago Median Income by Neighborhood
![alt text](img/seattle_comparison.png “Seattle Comparison”)
Comparison between Seattle’s Pokemon appearances vs Seattle Median Income by Neighborhood
![alt text](img/denver_comparison.png “Denver Comparison”)
Comparison between Denver’s Pokemon appearances vs Denver Median Income by Neighborhood

> For all maps, orange dots are Pokemon that appeared during the day, while teal dots are Pokemon that appeared at night.

> Looking across all five maps, it is clear that some places have a correlation, while others do not. For example, New York City and Chicago seem to be the most egregious when it comes to Pokemon sightings appearing in wealthier areas as opposed to low-income areas. There are, however, small clusters of outliers. Los Angeles, on the other hand, doesn’t seem to have this problem. The highest-income neighborhoods actually seem to have the least amount of Pokemon sightings middle-to-moderate income areas seem to have more.
Denver doesn’t seem to have any correlation, and Seattle doesn’t seem to have much of one either.

> When researching our problem, we found out that Pokestops (which are common spawn points for Pokemon) and Gyms (gathering places for Pokemon Go players, which then attracts more Pokemon) were determined by Google landmark data, as well as self-reported locations of interest. This makes a lot of sense when looking at Seattle’s map, which has huge clusters around University District, which has many landmarks. The correlation (or lack thereof) in other cities could also be attributed to different neighborhood’s amount of landmarks. This makes it understandable why the richest neighborhoods in Los Angeles don’t have any sightings, since these neighborhoods are secluded, and the residents are often celebrities. New York City, on the other hand, has rich neighborhoods that also have historic landmarks.

> While income may have a broader effect overall, in the case of these five cities, income did not always correlate with Pokemon appearances.

## Quantitative questions are clearly and concisely explained with thoughtful text and compelling visual

> After we chose our data set, realized that our data had no quantitative variables, and instead had categorical variables. Due to the lack of quantitative variables, we do not have any quantitative questions. However, we were curious whether or not we could predict the Pokemon type To address the issue of our categorical target variables, we use the pandas function pd.get_dummies to encode the different Pokemon types. This process 

## A nuanced understanding of the important features of the dataset and topic is demonstrated.

> After encoding our data, we used forward feature selection in order to look for features with high coefficients within our dataset. Through this process, we got four variables back: longitude, sunrise, sunset, and population density. However, the process that we used for feature selection is specifically used for numeric dependent values, and our dependent value--Pokemon Type--is categorical. Since the methods didn’t correlate, we did not use any of the suggested features from our process. Instead, we used it as a data exploration step in order to further look into the data.

> There are also some possible reasons for these high correlations. While investigating the data, we found that the city labels were often quite inaccurate, with many Seattle data points being labeled as Los Angeles. We noticed this was a difference in latitude, which led us to believe that the creator of the data set must have sorted cities by longitude instead. This places greater precedence on the longitude value, rather than latitude.

> Population density may be an effect because of Pokemon Go’s game mechanics. Developers (and avid players) have always maintained that the more Pokemon Go players in one area, the more Pokemon will spawn. This inclusion of population density would make sense if this is true. Lastly, sunrise and sunset may be times during the day in which more people are active on Pokemon Go. However, this is purely conjecture.


## High-level insights (important descriptive information, major trends, notable outliers, etc.) should be prominent in your resource.

Stuff here 


## Methods and results of statistical approaches are clear

Stuff here
