# Chapter 1 Exercises
Use this page as an example for how you should format your weekly homework assignments

**1. Which Datafile?**

*a. How has the rate of walks (per team for nine innings) changed over the history of baseball?*

*b. What fraction of baseball games in 1968 were shutouts? Compare this fraction with the fraction of shutouts in the 2012 baseball season.*

10.43% of games in 1968 were shutouts:

````r
library(Lahman)
library(tidyverse)

# Create tibble of Teams data
Teams <- as_tibble(Teams)

# Subset the 1968 games
Teams.1968 <- subset(Teams, yearID == 1968)

# Calcuate the percentage of shuthouts
sum(Teams.1968$SHO)/sum(Teams.1968$G)
[1] 0.1043077
````

Using the same steps as above, I determined that 6.38% of games in 2012 were shutouts.

*c. What percentage of first pitches are strikes? If the count is 2-0, what fraction of the pitches are strikes?*

*d. Which players are most likely to hit groundballs? Of these players, compare the speeds at which these groundballs are hit.*

*e. Is it easier to steal second base or third base? (Compare the fraction of successful steals of second base with the fraction of successful steals of third base.)*


**2. Lahman Pitching Data**

*a. Gibson started 34 games for the Cardinals in 1968. What fraction of these games were completed by Gibson?*


b. What was Gibson’s ratio of strikeouts to walks this season?
c. One can compute Gibson’s innings pitched by dividing IPouts by three. How many innings did Gibson pitch this season?
d. A modern measure of pitching effectiveness is WHIP, the average number of hits and walks allowed per inning. What was Gibson’s WHIP for the 1968 season?
