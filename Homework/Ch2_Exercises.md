# Chapter 2 Excercises
1. Top Base Stealers in the Hall of Fame

The following table gives the number of stolen bases (SB), the number of times caught stealing (CS), and the number of games played (G) for nine players currently inducted in the Hall of Fame.

Player	SB	CS	G
Rickey Henderson	1406	335	3081
Lou Brock	938	307	2616
Ty Cobb	896	178	3035
Tim Raines	808	146	2502
Eddie Collins	741	173	2826
Max Carey	738	92	2476
Joe Morgan	689	162	2649
Ozzie Smith	580	148	2573
Barry Bonds	514	141	2986
Ichiro Suzuki	509	117	2653
Luis Aparicio	506	136	2601
Paul Molitor	504	131	2683
Roberto Alomar	474	114	2379

a) In R, place the stolen base, caught stealing, and game counts in the vectors SB, CS, and G.

SB <- c(1406, 938, 896, 808, 741, 738, 689, 580, 514, 509, 506, 504, 474)

CS <- c(335, 307, 178, 146, 173, 92, 162, 148, 141, 117, 136, 131, 114)

G <- c(3081, 2616, 3035, 2502, 2826, 2476, 2649, 2573, 2986, 2653, 2601, 2683, 2379)

Players <- c("Henderson", "Brock", "Cobb", "Raines", "Collins", "Carey", "Morgan", "Smith", "Bonds", "Suzuki", "Aparicio", "Molitor", "Alomar")

b) For all players, compute the number of stolen base attempts SB + CS and store in the vector SB.Attempt.

SB.Attempt <- SB + CS

c) For all players, compute the success rate Success.Rate = SB / SB.Attempt.

Success.Rate <- SB / SB.Attempt

d) Compute the number of stolen bases per game SB.Game = SB / Game.

SB.Game <- SB / G

e) Construct a scatterplot of the stolen bases per game against the success rates. Are there particular players with unusually high or low stolen base success rates? Which player had the greatest number of stolen bases per game?

ggplot(Base.Stealers, aes(x = SB, y = Success.Rate)) + geom_point(size = 3) + geom_smooth(color = crcblue) + geom_text(aes(label = Players), vjust = 2.75)

Player Max Carey had a very high success rate when stealing bases, while player Lou Brock had low success rate when compared to the other players on this list. Ricky Henderson had the greatest number of stolen bases per game. 


2. Character, Factor, and Logical Variables in R

Suppose one records the outcomes of a batter in ten plate appearances:

Single, Out, Out, Single, Out, Double, Out, Walk, Out, Single

Use the c() function to collect these outcomes in a character vector outcomes.
Use the table() function to construct a frequency table of outcomes.
In tabulating these results, suppose one prefers the results to be ordered from least-successful to most-successful. Use the following code to convert the character vector outcomes to a factor variable f.outcomes.
f.outcomes <- factor(outcomes, levels = c("Out", "Walk", "Single", "Double"))

My work: 
Single <- "Single"
Out <- "Out"
Double <- "Double"
Walk <- "Walk"

Outcomes <- c(Single, Out, Out, Single, Out, Double, Out, Walk, Out, Single)

freq_table <- table(Outcomes)

print(freq_table)
Outcomes
Double    Out Single   Walk 
1      5      3      1 

> print(f.outcomes)
 [1] Single Out    Out    Single Out   
 [6] Double Out    Walk   Out    Single
Levels: Out Walk Single Double

f.outcomes <- factor(Outcomes, levels = c("Out", "Walk", "Single", "Double"))
Use the table() function to tabulate the values in f.outcomes. How does the output differ from what you saw in part (b)?

The outputs create two different tables. One gives you numerical counts of the number of times each outcome occurres, while the other gives you columns with each outcome spelled out.

Suppose you want to focus only on the walks in the plate appearances. Describe what is done in each of the following statements.
outcomes == "Walk"
sum(outcomes == "Walk")



3. Pitchers in the 350-Wins Club

The following table lists all nine pitchers who have won at least 350 career wins.

Player	W	L	SO	BB
Pete Alexander	373	208	2198	951
Roger Clemens	354	184	4672	1580
Pud Galvin	365	310	1807	745
Walter Johnson	417	279	3509	1363
Greg Maddux	355	227	3371	999
Christy Mathewson	373	188	2507	848
Kid Nichols	362	208	1881	1272
Warren Spahn	363	245	2583	1434
Cy Young	511	315	2803	1217
In R, place the wins and losses in the vectors W and L, respectively. Also, create a character vector Name containing the last names of these pitchers.
Compute the winning percentage for all pitchers defined by 
 and put these winning percentages in the vector win_pCT.
By use of the command
wins_350 <- tibble(Name, W, L, win_pCT)

create a data frame wins_350 containing the names, wins, losses, and winning percentages. d. By use of the arrange() function, sort the data frame wins_350 by winning percentage. Among these pitchers, who had the largest and smallest winning percentages?

4. Pitchers in the 350-Wins Club, Continued

In R, place the strikeout and walk totals from the 350 win pitchers in the vectors SO and BB, respectively. Also, create a character vector Name containing the last names of these pitchers.
Compute the strikeout-walk ratio by 
 and put these ratios in the vector SO.BB.Ratio.
By use of the command
SO.BB <- tibble(Name, SO, BB, SO.BB.Ratio)

create a data frame SO.BB containing the names, strikeouts, walks, and strikeout-walk ratios. d. By use of the filter() function, find the pitchers who had a strikeout-walk ratio exceeding 2.8. e. By use of the arrange() function, sort the data frame by the number of walks. Did the pitcher with the largest number of walks have a high or low strikeout-walk ratio?

5. Pitcher Strikeout/Walk Ratios

Read the Lahman Pitching data into R.
The following script computes the cumulative strikeouts, cumulative walks, mid career year, and the total innings pitched (measured in terms of outs) for all pitchers in the data file.
career_pitching <- Pitching |> 
  group_by(playerID) |> 
  summarize(
    SO = sum(SO, na.rm = TRUE),
    BB = sum(BB, na.rm = TRUE),
    IPouts = sum(IPouts, na.rm = TRUE),
    midYear = median(yearID, na.rm = TRUE)
  ) 

This new data frame is named career_pitching. Run this code and use the inner_join() function to merge the Pitching and career_pitching data frames.

Use the filter() function to construct a new data frame career_10000 consisting of data for only those pitchers with at least 10,000 career IPouts.

For the pitchers with at least 10,000 career IPouts, construct a scatterplot of mid career year and ratio of strikeouts to walks. Comment on the general pattern in this scatterplot.

FIP is a measure of pitching performance dependent only on plays that do not involve fielders.↩︎

The function seq(a, b, s) will generate a vector of values from a to b in steps of s.↩︎

The expression round(x, n) rounds x to n decimal places.↩︎
