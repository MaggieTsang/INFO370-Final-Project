
# [Project Proposal](https://canvas.uw.edu/courses/1256522/assignments/4527104)
> **Group**: A7 <br>
> **Team members**: JT Anderson, Alaina Kwan, Maggie Tsang, Ben Walchenbach <br>
> **Topic**: Pokemon Go Data

<br>


## Papers Sources: 
* [Source 1 - greaterdc.urban.org](https://greaterdc.urban.org/blog/pokemon-go-changing-how-cities-use-public-space-could-it-be-more-inclusive)
* [Source 2 - tandfonline.com](https://www.tandfonline.com/doi/abs/10.1080/10095020.2017.1368200)
* [Source 3 - springer.com](https://link.springer.com/chapter/10.1007/978-3-319-71470-7_15)

<br>



## Project Description
 
**What is the overarching purpose of your research project, and why is it an important undertaking?**

We will be attempting to generate a model that will be able to predict where Pokemons will appear.

**How does your research fit into the broader problem domain? You should cite at least 3 papers that help contextualize your research.**

* The research we’re conducting is focused around how geo-gaming uses geographical information and other socioeconomic factors to cultivate their platforms. Pokemon-Go utilizes publicly provided ‘points of interests’ to create ‘PokeStops’ and ‘gyms’. We plan to investigate how socioeconomic variables and land-use categories “affect the density of PokeStops, and how PokeStops and gyms cluster relative to each other” (Source 1). 
* Pokemon Go utilizes an algorithm to create the stops and could exemplify algorithmic redlining by making certain locations / pokemon more inclusive (Source 2 ). Therefore, we plan to investigate the purpose, nature, and characteristics of our dataset to investigate potential redlining (Source 3).

**What specific hypothesis (hypotheses) are you going to test?**

Are the number of pokemon sightings affected by the wealth of each neighborhood? (Redlining etc)

**What are the datasets you'll be working with to answer this question? Please include relevant background describing the datasets you identify.**

* Predict ‘em All dataset
* Possible extra dataset identifying neighborhoods

**What statistical and machine learning methods do you plan on using to test your hypothesis?**

Linear regression and K Nearest Neighbor

**Who is your target audience for the resource you will build? Depending on the domain of your data, there may be a variety of audiences interested in using the dataset. You should hone in on one of these audiences.**

* Over the last three years since Pokemon Go was released, it became a worldwide phenomenon. While its initial popularity and craze has died down in recent years, it is still a prominently played app among children and their parents. As such, we would like to focus on Pokemon Go players as our target audience.
* Within our personal lives, we have seen an impressive increase in the number of people walking outside due to the video game Pokemon Go. We believe that our local transportation services would be interested in where these players walk. This could provide insight to the city about population concentration throughout the day, as well as what parts of town public transportation services should target.

**What should your audience learn from your resource? Consider specific questions they may want to answer.**

* Learn whether or not neighborhood wealth affects frequency of pokemon sited
* How to accurately predict where Pokemon will show up
 
<br>
<br>

## Technical Description
> _This section of your proposal is an opportunity to think through the specific analytical steps you'll need to complete throughout the project._


**What will be the format of your final web resource (Shiny app, HTML page or slideshow compiled with KnitR, etc.)?**

We will do our analysis and visualizations in Python using a Jupyter Notebook. Our final report format will be in a html file, hosted on the repository’s github pages.

**Do you anticipate any specific data collection / data management challenges?**

In terms of deciding the most prominent features in the dataset, there is a good number (around 20 or more) of features to choose from; however, there could be a concern of the accuracy of the data because some columns are blank of have dummy data. Otherwise, the data is well documented and we have around 300,000 rows to dabble around.

**What new technical skills will need to learn in order to complete your project?**

Efficiently clean up and prepare large data sets
Geolocation manipulation
We expect team members will need more practice with GridSearchCV and Pipelines
Working with categorical data

**How will you conduct you analysis? Please include a detailed description of your intended modeling approach.**

* Normalize and scale data.
* Split data set into training and testing data using the `sklearn.model_seletion.train_test_split()` method.
* Further split the training data in order to have training and validation data.
* Select best features through [L1-based feature selection](https://scikit-learn.org/stable/modules/feature_selection.html#feature-selection-using-selectfrommodel).
* Develop several models and compare results:
    * K nearest neighbor
    * Multivariate regression
* Tune Model with parameter grid search
* Determine the validity and accuracy of our model

**What major challenges do you anticipate?**

Some members of the team are not familiar with the features and intricacies of Pokemon Go. We expect that there will be some challenges interpreting results at first. In order to minimize this each member will be responsible for downloading the application and becoming more familiar with the game.