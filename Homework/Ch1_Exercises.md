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

In the question, Gibson's stats are given. If you wanted to pull these stats up on your own, use the following:

````r
# Create tibble of Pitching data from Lahman dataset
Pitching <- as_tibble(Pitching)

# subset Gibson's stats from 1968
Gibson.1968 <- subset(Pitching, yearID == 1968 & playerID == "gibsobo01")

Gibson.1968
# A tibble: 1 × 30
  playerID yearID stint teamID lgID      W     L     G    GS    CG   SHO    SV
  <chr>     <int> <int> <fct>  <fct> <int> <int> <int> <int> <int> <int> <int>
1 gibsobo…   1968     1 SLN    NL       22     9    34    34    28    13     0
# ℹ 18 more variables: IPouts <int>, H <int>, ER <int>, HR <int>, BB <int>,
#   SO <int>, BAOpp <dbl>, ERA <dbl>, IBB <int>, WP <int>, HBP <int>,
#   BK <int>, BFP <int>, GF <int>, R <int>, SH <int>, SF <int>, GIDP <int>
````
*a. Gibson started 34 games for the Cardinals in 1968. What fraction of these games were completed by Gibson?*

28 of 34 starts were complete games (as indicated by the "CG" column above). You can also directly call up that information:

````r
Gibson.1968$CG
[1] 28
````
*b. What was Gibson’s ratio of strikeouts to walks this season?*

He had 268 strikeouts to 62 walks, or a 4.32 k:bb ratio.

````r
Gibson.1968$SO
[1] 268

Gibson.1968$BB
[1] 62

268/62
[1] 4.322581
````
*c. One can compute Gibson’s innings pitched by dividing IPouts by three. How many innings did Gibson pitch this season?*

He pitched 304 and 2/3 innings

````r
Gibson.1968$IPouts / 3
[1] 304.6667
````
*d. A modern measure of pitching effectiveness is WHIP, the average number of hits and walks allowed per inning. What was Gibson’s WHIP for the 1968 season?*

His WHIP was 0.854

````r
(Gibson.1968$H + Gibson.1968$BB) / (Gibson.1968$IPouts / 3)
[1] 0.8533917
````

**3. Retrosheet Game Log**

Loading Retrosheet data into R is a little advanced for our lessons at this point, so let's just work with the information provided in the question.

*a. What was the time in hours and minutes of this particular game?*

The "Duration" field is 139, so that would be 2 hours and 19 minutes.

*b. Why is the attendance value in this record equal to zero?*

Attendance was not recorded for this game.

*c. How many extra base hits did the Phillies have in this game?*

Three (two doubles and one homerun)

*d. What was the Phillies' on-base percentage during this game?*
.375 on base percentage (8 hits, 4 walks, 32 at-bats)

**4. Retrosheet Play-by-Play Record**

