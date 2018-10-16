# Predicting NBA Salary

Using linear regression, I try to predict an NBA player's salary for the upcoming season based on his statistical performance. For more details on my process, please check out my [blog post](https://douglas-l.github.io/grass_analytics/journal/Prediciting-NBA-Salary.html).

# Scenario

In a hypothetical scenario, I am an agent for NBA players and I want to identify the the most important statistics my clients can improve on to receive a bigger contract. 

# Data

## Scraping

In the Luther Scraper notebook, I utilize the Requests and BeautifulSoup python libraries to gather NBA player statistics from basketball-reference.com.  I scraped basic biological information, basic per game averages, some advanced stats, and of course their salary information. I collected the information into a pandas dataframe.

## Cleaning

Linear regression does poorly with null values and outliers, so the Luther data exploration notebook focuses on visualizing the data and cleaning those up. Rookies had to be removed because they did not have statistics for a previous season, and they were also a common cause for outliers because of their limited playing time, resulting in extreme values. 

# Modeling

My target value was their current season salary. 

## Establish baseline

My single variable linear regression model using previous season's average points (P_PTS) had a respectable R^2 score of 0.47, which suggests that about 47% of the variation in player salaries can be explained by their average points per game alone. To improve the model, I added three more features: previous season rebounds per game, previous season assists per game, and current age. I skipped many features that were next on the list in terms of correlation to the target, such as field goals per game, because they were also closely related to points per game. The four variable model had a R^2 score of 0.51, which waS a slight boost.   
  
## Engineer features 

The next step was feature engineering, such as taking polynomials of various features. I won't go into detail but the main idea is that while they did boost the R^2 score slightly, they were adding a lot of complexity to the model, thus decreasing interpretability. I also tested techniques such as standardizing the features and transforming the target to a log scale. Unfortunately, both of these techniques failed to improve the model within my setup. I was particularly disappointed in the logarithmic transformation of the target because the distribution did look a bit more symmetrical, if still skewed, after the transformation.   

## Select model to match problem

In the end, in consideration of my scenario of identifying key statistics for a player to improve on, I decided to pick the four variable model for the simple interpretation despite its relatively poor performance. 

I also concluded that salary prediction likely requires a non-linear model because there was still a strong trend in the residual plot of the model despite my attempts to add more complexity.






Last worked on July 20, 2018

Project Luther for Metis