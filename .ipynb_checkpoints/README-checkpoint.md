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

> We chose to focus on five different American cities for this part of our exploration. These cities included New York City, Los Angeles, Chicago, Denver, and Seattle. We chose NYC, LA, and Chicago based on population (as they are the 3 cities with the highest populations in the US), but chose Seattle and Denver based off personal preference. Since we all live in Seattle, we thought it would be an interesting city to look into. One of the group members previously lived in Denver and thought it would be interesting to add to the comparisons, since Seattle and Denver have similar population sizes.

## City Comparisons
All income maps courtesy of [Statistical Atlas](https://statisticalatlas.com/United-States/Overview)

![New York Comparison](img/ny_comparison.png)
Comparison between New York City’s Pokemon appearances (mapped using Folium) vs NYC Median Income by Neighborhood.
![Los Angeles Comparison](img/la_comparison.png)
Comparison between LA’s Pokemon appearances vs LA Median Income by Neighborhood
![Chicago Comparison](img/chicago_comparison.png)
Comparison between Chicago’s Pokemon appearances vs Chicago Median Income by Neighborhood
![Seattle Comparison](img/seattle_comparison.png)
Comparison between Seattle’s Pokemon appearances vs Seattle Median Income by Neighborhood
![Denver Comparison](img/denver_comparison.png)
Comparison between Denver’s Pokemon appearances vs Denver Median Income by Neighborhood

> For all maps, orange dots are Pokemon that appeared during the day, while teal dots are Pokemon that appeared at night.

> Looking across all five maps, it is clear that some places have a correlation, while others do not. For example, New York City and Chicago seem to be the most egregious when it comes to Pokemon sightings appearing in wealthier areas as opposed to low-income areas. There are, however, small clusters of outliers. Los Angeles, on the other hand, doesn’t seem to have this problem. The highest-income neighborhoods actually seem to have the least amount of Pokemon sightings, while middle-to-moderate income areas seem to have more.
Denver doesn’t seem to have any correlation, and Seattle doesn’t seem to have much of one either.

> When researching our problem, we found out that Pokestops (which are common spawn points for Pokemon) and Gyms (gathering places for Pokemon Go players, which then attracts more Pokemon) were determined by Google landmark data, as well as self-reported locations of interest. This makes a lot of sense when looking at Seattle’s map, which has huge clusters around University District, which has many landmarks. The correlation (or lack thereof) in other cities could also be attributed to different neighborhood’s amount of landmarks. This makes it understandable why the richest neighborhoods in Los Angeles don’t have any sightings, since these neighborhoods are secluded, and the residents are often celebrities. New York City, on the other hand, has rich neighborhoods that also have historic landmarks.

> While income may have a broader effect overall, in the case of these five cities, income did not always correlate with Pokemon appearances.

## Data Prep: Encoding and Splitting

> After we chose our data set, we realized that our data had no quantitative variables, and instead only had categorical variables. Due to the lack of quantitative variables, we do not have any quantitative questions. However, we were curious whether or not we could predict how many Pokemon of each type would appear, so we chose Pokemon type to be our target depndent variable.

> To address the issue of our categorical target variables, we needed to encode our variables. To do that, we used the Pandas function get_dummies(). We chose this method because both it and our data frames were managed by the pandas library. Before encoding the data, we dropped certain variables that we did not need, such as name, ID, city, weather icon, and appeared local time and day of week. Afterwards, we looped through the entire dataframe and converted all objects to floats and removed the originals.

> After we finished encoding the data, we split it into our training data and test data. We used an 80/20 split, so that 80% of the data was used to train our model and 20% was used to test its predictions.

## Feature Selection

> After splitting our data, we used forward feature selection in order to look for features with high coefficients within our dataset. Through this process, we got four variables back: longitude, sunrise, sunset, and population density. However, the process that we used for feature selection is specifically used for numeric dependent values, and our dependent value--Pokemon Type--is categorical. Since the methods didn’t correlate, we did not use any of the suggested features from our process. Instead, we used it as a data exploration step in order to further look into the data.

> There are also some possible reasons for these high correlations. While investigating the data, we found that the city labels were often quite inaccurate, with many Seattle data points being labeled as Los Angeles. We noticed this was a difference in latitude, which led us to believe that the creator of the data set must have sorted cities by longitude instead. This places greater precedence on the longitude value, rather than latitude.

> Population density may be an effect because of Pokemon Go’s game mechanics. Developers (and avid players) have always maintained that the more Pokemon Go players in one area, the more Pokemon will spawn. This inclusion of population density would make sense if this is true. Lastly, sunrise and sunset may be times during the day in which more people are active on Pokemon Go. However, this is purely conjecture.

> While we did not go with the features that were returned, we did use it as a jumping off point and decided to look into Pokemon type from there.

## Modeling

> We decided to go with three different models and three different approaches. Of the available methods, we chose to use Decision Trees, K Nearest Neighbors, and SVC Regression. We chose the first two because of what we learned in class, and we chose the latter because it is specifically used for working with categorical data.

> Before creating our models, we used Grid Search in order to find the optimal depth for our Decision Tree and the optimal number of neighbors for our KNN approach. When we ran these grid searches, however, we found that the results were quite unsatisfactory. For Decision Tree, we got a result of a max depth of 1, with an accuracy score of 18.9%. For KNN, we got 9 neighbors with an accuracy score of 21.8%. Since these were abnormally low, we decided to instead go with a depth of 15 for Decision Tree and n = 8 for KNN.

> Finally, we created our models with the above parameters. For Decision Tree and KNN, we used the entirety of our data set. However, for SVC Regression, we were unable to use the whole dataset, and instead used 1% of our data (which is ~3000 rows). We did this because the model took too long to run when using all 300,000 rows, so we opted to create a smaller sample instead.


## Visualizations and Conclusions

> After running our models, we got 3 very different accuracy scores. For Decision Tree, we were surprised to get an accuracy score of 100%. For KNN, we got an accuracy score of 55.8%. And for SVC Regression, we got an accuracy score of 19.4%.

![Accuracy Scores](img/accuracy_scores.PNG)
Our 3 different accuracy scores.

> Out of our 3 accuracy scores, Decision Tree was by far the most accurate. In fact, we were quite shocked that we managed to get 100% accuracy. We assume that the high accuracy is attributed to the depth we chose, as well as the sheer amount of data that we provided it. We were a bit concerned with possibly having overfit the data, but since our training data and test data was split, modeling the decision tree and the test results were independent of each other.

![Decision Tree Predictions](img/decision_tree_preds.PNG)

> As seen in the graph above, the orange bar represents the data that was accurately predicted. Since there is no yellow or red in the bar chart, it means our Decision Tree model predicted 100% of the data correctly.

> The next highest accuracy score we got was K Nearest Neighbor at 55.8%. Since we were not as accurate with this model, it actually has some more interesting conclusions.

![KNN Predictions](img/knn_occurances_vs_preds.PNG)

> As seen in the graph above, this model did better in some places than it did others. KNN grossly over-predicted the number of Normal type Pokemon that would occur. However, this makes sense because of how much more common they are than the rest of the other Pokemon types. Electric and Bug types were the other two that were over-predicted, but not nearly as much. The remaining types were under-predicted, with the model missing a lot of the data. Some types fared better than others--the model got most Psychic, Water, and Ground types correctly. However, it missed practically all of the Dragon and Ghost types, and more than half of Rock, Grass, and Fairy.

> Looking at these severely under-predicted types, however, yields interesting conclusions. Since Pokemon Go, at the time this data was collected, only had the original first generation of Pokemon, there are far fewer Dragon, Ghost, and Fairy types. This is because Dragon types were not as common in the first few iterations of the Pokemon franchise, and Fairy is a type that only came into existence in 2013 (whereas the rest of the franchise has existed since 1998). This could be why there are far fewer of these Pokemon, which also led to less data for the model to use for its predictions.

> Finally, our SVC model had a pretty dismal accuracy score of 19.4%. We attribute that mostly to the fact that we used a sample subset of the data, as opposed to the entirety of the data like we did with the previous two models. This subset was also very small--only 1% of the entire data set. This most likely had a large effect on the model's accuracy, but our inexperience using the SVC Regression model may have also played into it (despite our best efforts).

> Overall, we can conclude that there are far more Normal type Pokemon in Pokemon Go than any others in the game. The second and third largest--Bug and Water--don't even come close. While this data set is fairly dated (in terms of the lifespan of the Pokemon Go app), it is still interesting to see the distribution of types around the globe.