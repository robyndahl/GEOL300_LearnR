3.10 Exercises
1. Hall of Fame Pitching Dataset

The hof_pitching data frame in the abdwr3edata package contains the career pitching statistics for all of the pitchers inducted in the Hall of Fame. The variable BF is the number of batters faced by a pitcher in his career. Suppose we group the pitchers by this variable using the intervals (0, 10,000), (10,000, 15,000), (15,000, 20,000), (20,000, 30,000). One can reexpress the variable BF to the grouped variable BF_group by use of the cut() function.

hofpitching <- hofpitching |>
  mutate(
    BF_group = cut(
      BF, 
      c(0, 10000, 15000, 20000, 30000),
      labels = c("Less than 10000", "(10000, 15000)", 
                 "(15000, 20000)", "more than 20000")
    )
  )

Construct a frequency table of BF.group using the summarize() function.
Construct a bar graph of the output from summarize(). How many HOF pitchers faced more than 20,000 pitchers in their career?
Construct an alternative graph of the BF.group variable. Compare the effectiveness of the bar graph and the new graph in comparing the frequencies in the four intervals.


2. Hall of Fame Pitching Dataset (Continued)

The variable WAR is the total wins above replacement of the pitcher during his career.

Using the geom_histogram() function, construct a histogram of WAR for the pitchers in the Hall of Fame dataset.

There are two pitchers who stand out among all of the Hall of Famers on the total WAR variable. Identify these two pitchers.


3. Hall of Fame Pitching Dataset (Continued)

To understand a pitcher’s season contribution, suppose we define the new variable WAR_Season defined by

hofpitching <- hofpitching |>
  mutate(WAR_Season = WAR / Yrs)

Use the geom_point() function to construct parallel one-dimensional scatterplots of WAR.Season for the different levels of BP.group.
Use the geom_boxplot() function to construct parallel boxplots of WAR.Season across BP.group.
Based on your graphs, how does the wins above replacement per season depend on the number of batters faced?


4. Hall of Fame Pitching Dataset (Continued)

Suppose we limit our exploration to pitchers whose mid-career was 1960 or later. We first define the MidYear variable and then use the filter() function to construct a data frame consisting of only these 1960+ pitchers.

hofpitching <- hofpitching |>
  mutate(MidYear = (From + To) / 2)
hofpitching.recent <- hofpitching |>
  filter(MidYear >= 1960)

By use of the arrange() function, order the rows of the data frame by the value of WAR_Season.
Construct a dot plot of the values of WAR_Season where the labels are the pitcher names.
Which two 1960+ pitchers stand out with respect to wins above replacement per season?


5. Hall of Fame Pitching Dataset (Continued)

The variables MidYear and WAR_Season are defined in the previous exercises.

Construct a scatterplot of MidYear (horizontal) against WAR_Season (vertical).
Is there a general pattern in this scatterplot? Explain.
There are two pitchers whose mid careers were in the 1800s who had relatively low WAR_Season values. By use of the filter() and geom_text() functions, add the names of these two pitchers to the scatterplot.


6. Working with the Lahman Batting Dataset

Read the Lahman People and Batting data frames into R.
Collect in a single data frame the season batting statistics for the great hitters Ty Cobb, Ted Williams, and Pete Rose.
Add the variable Age to each data frame corresponding to the ages of the three players.
Using the geom_line() function, construct a line graph of the cumulative hit totals against age for Pete Rose.
Using the geom_line() function, overlay the cumulative hit totals for Cobb and Williams.
Write a short paragraph summarizing what you have learned about the hitting pattern of these three players.


7. Working with the Lahman Teams Dataset

The Lahman Teams dataset contains yearly statistics and standing information for all teams in MLB history.

Read the Teams data frame into R.
Create a new variable win_pct defined to be the team winning percentage W / (W + L).
For the teams in the 2022 season, construct a scatterplot of the team ERA and its winning percentage.
Use the geom_mlb_scoreboard_logos() function from the mlbplotR package to put the team logos on the scatterplot as plotting marks.
Use this function to redo the graph in part (c), plotting using the team logos.


8. Working with the Retrosheet Play-by-Play Dataset

In Section 3.8, we used the Retrosheet play-by-play data to explore the home run race between Mark McGwire and Sammy Sosa in the 1998 season. Another way to compare the patterns of home run hitting of the two players is to compute the spacings, the number of plate appearances between home runs.

Following the work in Section 3.8, create the two data frames mac_data and sosa_data containing the batting data for the two players.

Use the following R commands to restrict the two data frames to the plays where a batting event occurred. (The relevant variable bat_event_fl is either TRUE or FALSE.)

mac_data <- filter(mac_data, bat_event_fl == TRUE)
sosa_data <- filter(sosa_data, bat_event_fl == TRUE)

For each data frame, create a new variable PA that numbers the plate appearances 1, 2, … (The function nrow() gives the number of rows of a data frame.)
mac_data <- mutate(mac_data, PA = 1:nrow(.))
sosa_data <- mutate(sosa_data, PA = 1:nrow(.))

The following commands will return the numbers of the plate appearances when the players hit home runs.
mac_HRPA <- mac.data |>
  filter(event_cd == 23) |>
  pull(PA)
sosa_HRPA <- sosa.data |>
  filter(event_cd == 23) |>
  pull(PA)

Using the R function diff(), the following commands compute the spacings between the occurrences of home runs.
mac_spacings <- diff(c(0, mac_HRPA))
sosa_spacings <- diff(c(0, sosa_HRPA))  

Create a new data frame HR_Spacing with two variables, Player, the player name, and Spacing, the value of the spacing. f. By use of the summarize() and geom_histogram() functions on the data frame HR_Spacing, compare the home run spacings of the two players.
