## FIFA-World-Cup-Analysis
##### I had never coded before, and I took an Intro to Python course whilst pursuing my MBA. We were allowed to choose a project that we were passionate about, and so I chose the FIFA World Cup, since I've always been a massive fan of the sport, and to be able to do an analysis on the history of the World Cup would be a fun experience.

##### See below for a few examples of the code and charts present in the analysis.

#### **Expected Goals Comparison (2018 vs. 2022)**

The expected goals metric was introduced at the 2018 world cup, and it is one of the more important metrics used today in the world of soccer. It provides insight on the level of play by that team, according to the type of chances that they created throughout the game. Even though expected goals data is only included for the previous two world cups, due to its relevance, we will keep these data points for further analysis.

matches_2018_2022= world_cup_matches[world_cup_matches["Year"].isin([2018, 2022])]

expected_goals_2018_2022= matches_2018_2022[["Year", "Round", "home_xg", "away_xg"]]

expected_goals_2018_2022["sum"]= expected_goals_2018_2022["home_xg"] + expected_goals_2018_2022["away_xg"]

expected_goals_per_stage= expected_goals_2018_2022.groupby(["Year", "Round"])["sum"].mean()

sns.barplot(data=expected_goals_2018_2022, x="Year", y="sum", hue="Round", palette= "RdBu");

![World Cup Image](https://raw.githubusercontent.com/dmangwani23/FIFA-World-Cup-Analysis/main/Screenshot%202025-02-23%20184443.png)

We can notice that in **2018**, (excluding the Round of 16), the hypothesis is correct in that the later the stage it is in the World Cup, the less expected goals there are per game. The "Third Place Match" can be disregarded since it is a one-off game for the semifinal losing teams (with very little to play for, considering the trophy is not on the line anymore).

Now in 2022, we see the complete opposite and the null hypothesis is rejected. As the World Cup rounds progressed, the more expected goals per game was seen. From a fanatic standpoint, this is always more entertaining, as one of the key highlights of a game is the ball entering the net.
