# Project Understanding
## Background:
During my childhood, I developed a deep passion for baseball with a dream to play in college and hopefully one day in the MLB. I enthusiastically followed the sport, and played competitively on various travel teams. However, my height became a hindrance to my playing aspirations. Standing out to prominent college coaches proved challenging due to my stature, as Division 1 baseball coaches typically prioritize players with perceived potential for power and speed, often initially assessing height and weight. In baseball, hitting for power is a key performance metric, with the hit that displays the most power being a home run.

This was discouraging, because I knew I could compete with the same players that were taller, so this led me to ask the question: “Does height help predict performance in baseball?”.

## Project goals:
Through this project, I work to answer the question: “Does height help predict performance in baseball?”, as well as explore other factors that may contribute to a player's power potential.

In other words, the goal of this project is to use data analysis to determine if there is a correlation between a player's height and their hitting power.

## Project success criteria:
The success of this project will be measured by using Pearson's correlation coefficient to determine the relationship between hitting power and physical metrics such as height and weight.

# Data Understanding
The Lahman database collects data on Major League Baseball statistics. Two datasets will be used for this analysis.

One dataset being 'Batting' which has season batting statistics for players. This dataset has 110,495 entries and 22 features. Each entry in the 'Batting' dataset represents the season batting statistics for a specific season of a player's career. Each player is is represented using their unique ID (`playerID`). Players that played multipled seasons will appear more than once, as each row represents a season for a specific player. Additional information is included about each player's batting stats, such as their number of at bats, hits, strike outs, homeruns, etc.

The second dataset used in this analysis is 'People'. This dataset includes 20,370 entries and 24 features. Each entry in the 'People' dataset represents an player who played in the MLB. For each player there is a unique ID associated with the specific player (`playerID`). Additional demographic information is included about each player, such as their name, height, weight, birthday, birth state, etc.

## Data Preparation
The following are keys steps I took to prepare the data for analysis:

* Compile the career statistics for each player from the batting dataframe into a new dataframe called `career_hrs`
* Create a new dataframe that only includes the career at bats and homeruns for each player called `career_hrs_abs`
* Create a new dataframe from the people dataframe that only includes each players' unique ID (`playerID`), their weight, and their height called `height_weight`
* Use panda's `.merge` method for merge the dataframes `career_hrs_abs` and `height_weight` into a single dataframe called `ab_hr_height_weight`
* Filter the merged dataframe to only include players who have more than 5000 career at bats. The purpose of this is to ensure that the analysis consists of players who played regularly, as opposed to bench players or players who only had a short stint in MLB.
  
(Players who had a short career will not have career homerun total that will be useful for analysis as their sample size is too small. I decided on the threshold of 5000 at-bats because a regular everyday player will compile between about 550-650 at-bats per season. 5000 at-bats thus corresponds to between 8-9 full seasons. This ensures that players' statistics used for analysis represent the statistics of players who had more than a short career.)

# Exploratory Data Analysis
Three key findings from the analysis below:

* Weight and height are nearly identically correlated with career home runs

 ![https://myoctocat.com/assets/images/base-octocat.svg](https://github.com/ckucewicz/Baseball_EDA/blob/main/Baseball_EDA_RegPlots.png)
  * The correlation coefficient value between height and homeruns (r = 0.527) shows a moderate, positive relationship, and the correlation coefficient value between weight and homeruns (r = 0.530) also shows a moderate, positive relationship.
  * In addition to using career homeruns to measure a player's batting power, I used home run rate, which is a rate that measures the number of home runs per at bat for each player. This measure showed a moderate, positive correlation with both player height and weight as well.

![https://myoctocat.com/assets/images/base-octocat.svg](https://github.com/ckucewicz/Baseball_EDA/blob/main/height_hr_weight.png)

The above scatterplot charts the relationship between a player's height (inches) with their career homerun total. Each point on the graph is shaded to represent their corresponding weight. The scatterplot shows that as a player's height increases we would expect them to weight more and have more career homeruns.

![https://myoctocat.com/assets/images/base-octocat.svg](https://github.com/ckucewicz/Baseball_EDA/blob/main/height_hr_hr_rate.png)

The above scatterplot charts the relationship between a player's height (inches) with their career homerun total. Each point on the scatterplot is shaded to represent their corresponding Homerun Rate (HR Rate). The scatterplot shows that as a player's height increases we would expect them to have more career homeruns as well as a higher overall homerun rate. Including homerun rate is important because it shows that career homerun totals were not high simply due to larger amount of at-bats. Instead, taller players also had a high homerun rate meaning they were better homerun hitters, not simply players with a larger number of at-bats.

From this analysis, one would expect taller players and heavier players to hit more home runs over their entire career. This makes sense when simply considering Newton's Second Law of Physics (Force = Mass x Acceleration). Heavier players, who are usually taller as well, (height and weight had a correlation coefficient of 0.658) have more mass which allows them to apply more force when they connect with the ball causing the ball to travel farther.

# Conclusion

## Limitations
This analysis uses metrics that are readily available for free online, such as height, weight, and number of extra base hits. Currently, most Major League Baseball (MLB) organizations have technology that provides advanced metrics (such as bat speed and launch angle) which help measure a player's power potential. This type of data is not as readily available to public users, so while my analysis provides factors that are related to a player's hitting power, MLB organizations may have data that indicates factors that are more strongly correlated with hitting power. In other words, the common readily available data that I used in this analysis may not provide as much insight into which factors are most strongly correlated with a player's hitting power as would data that MLB organizations use.

## Recommendations
The implication for this analysis means that when scouts and coaches are deciding on which players to make up their team, height and weight are criteria that can be used to help evaluate the player’s ability to hit the ball hard and far. Although height and weight are factors when projecting a player’s power potential, there are other factors that should also be considered such as: bat speed, launch angel, overall strength, and how often a player’s swing makes solid contact with the pitch.

## Next Steps
For future iterations of this project, I am interested in performing hypothesis tests to determine if the relationship between a player's height and number of career home runs is statistically significant. Additionally, I plan to explore more up-to-date features that are used to determine a players hitting power potential, such as average exit velocity and barrel percentage.
