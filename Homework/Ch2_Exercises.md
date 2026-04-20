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
