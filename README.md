# Daily Fantasy Football Team Generation

![Alt text](download.jpg?raw=true "DFS")

---------------------------------------------------------------------------------------------------------------------------------
## Abstract

Daily Fantasy Football is a great way to increase entertainment value for professional sports. And, for some people Daily Fantasy Football is a way of life and maybe even considered a revenue stream. In this project I am exploring data in relation to Daily Fantasy Football from the website Draftkings to explore different ways to create teams. Leveraging the data I look at different ways to filter player pools in hopes of finding a method of filtering that will increase teams scores. 


---------------------------------------------------------------------------------------------------------------------------------

## Background and Motivation

As an expert in Fantasy Football, I am deeply motivated by the idea of making money. And, week in and week out Daily Fantasy Football offers the biggest returns for your dollar(if you create a good enough team). My best finish in a single contest is 2nd place out of 250,000 people earning me a 2,000% return on entrance fee. I created 30 different teams for that specific contest, and generated those teams by manually selectng players from a pool of players I heavily filtered down based on my Fantasy Football knowledge alone (subjective approach). Starting with this project I hope to take a more objective approach and begin to truly understand how to filter a pool of players to randomly generate Daily Fantasy Football lineups. I hope to find a repeatable process of filtering a pool of players to maximize team score through the lens through Data Science.

### My Theory

Professional sports is full of so much randomness that it's difficult to predict. I believe to be successful in Daily Fantasy Football we need to combat the randomness in sports with a little randomness of my own. The success of our randomness depends entirely on how we filter the available pool of players that we generate out lineups from. For the purpose of this projects exploration, I created an initial base pool of players by filtering out anyone with an injury or Covid-19 (Because they are not going to play). From this base pool what ways can we filter players out to make the pool of players as small as possible, while still maximizing potential team score.


---------------------------------------------------------------------------------------------------------------------------------

## Research Question & Data


Question: Which position's top 5 players increase the average score for a Daily Fantasy Football team during week 13 in the 2020 NFL season?

What is a top 5 player? A top 5 player for the purpose of this project is based on the cost of that player for that position. I chose thise way to define the top 5 player catagory because the more expensive a player in daily fantasy the more points they are projected to score.

What is the Base Pool of players? The base pool of players I used as my sample population is all of the available players minus any players with injuries (not playing), or player with COVID-19 with respect to 2020 Pandemic. It should be noted that there are still many players active on NFL rosters that recieve 0 points because they maybe a backup or have little playing time. This inherently brings down the mean score and should be considered when formulating other methods of player filtration. 


---------------------------------------------------------------------------------------------------------------------------------


## The Process 

I combined the Draft King's player information with week 15 player results from RotoGuru, a website dedicated to strategy in fantasy sports. Draft offers CVS's downloads for player information for each week. However, I had to convert RotoGuru's data from HTML to JSON to CSV and then to a Panda's Dataframe. Once, I had both website's data I combined them into a single dataframe on a player name after some string manipulation to make player's names equal in both Dataframes. I then filtered out all of the players in said Dataframe who had COVID-19 or wasn't playing to create my base pool. Using the base pool I filtered out players to create four different sub-pools to test against the base pool of players. Each sub-pool had a single position filtered down to only the top 5 players for that position. The four sub-groups consist of the top 5 Quarterback pool, top 5 Wide Reciever pool, top 5 Running Back pool, and a top 5 Tight End pool to help answer the question, "Which position's top 5 players increase the average score for a Daily Fantasy Football team during week 13 in the 2020 NFL season?". For example, the top 5 Quarterback pool consists of all the players from the base pool while only selecting one of the top 5 quarter backs to fill the quarterback position. 

---------------------------------------------------------------------------------------------------------------------------------

## Creating The Samples

I wrote a function that randomly generates a Fantasy Football team filling in each required position with a player of that position. The function took player's cost into consideration. For, example with respect to salary cap the function never generated a team that costed more that $50,000 because that would be invalid. Furthermore, the function never generated a team that costed less than $44,000 to maximize player value. I then created a function that would call the previous function 1000 times. With that said, I generated 1000 samples for each pool of players to generate the data I need to test each pool against the base pool.





![Alt text](Boxplt.jpg?raw=true "Distribution of each player pool team's score")



---------------------------------------------------------------------------------------------------------------------------------


## Hypothesis Testing 


### Top 5 Quarterback Pool  against Base Pool

*For Week 13

Top 5 QBs against Base Pool

Ho: Top 5 Quarterbacks do not increase the average score for a Daily Fantasy Football Team.
Ha: Top 5 Quarterbacks do increase the average score for a Daily Fantasy Football Team.

Null: Not Rejected
Reason: Even though the pvalue is small enough to reject, top 5 QB's actually bring down the team's average score, and don't. 

Ttest_indResult(statistic=3.357846009870451, pvalue=0.000800262874062739)


### Top 5 WRs Pool against Base Pool

Ho: Top 5 Wide Recievers do not increase the average score for a Daily Fantasy Football Team.
Ha: Top 5 Quarterbacks do increase the average score for a Daily Fantasy Football Team.

Null: Not Rejected
Reason: The p-value is too high, meaning that the mean scores of the base pool and top 5 wide reciever pool are not different enough to reject.


Ttest_indResult(statistic=0.11571656241969287, pvalue= 0.9078888079698677)

![Alt text](wr_vs_base.jpg?raw=true "Distribution around the mean of base pool and top 5 WR pool")


### Top 5 RBs Pool against Base Pool

Ho:: Top 5 Running Backs do not increase the average score for a Daily Fantasy Football Team.
Ha: Top 5 Running Backs do increase the average score for a Daily Fantasy Football Team.

Null: Rejected
Reason: The p-value is low enough that the two pools have two different means.

Ttest_indResult(statistic=-8.6441945913627, pvalue= 1.0910917663295008e-17)

### Top 5 Tight End Pool against Base Pool

Ho:: Top 5 Tight Ends do not increase the average score for a Daily Fantasy Football Team.
Ha: Top 5 Tight Ends do increase the average score for a Daily Fantasy Football Team.

Null: Rejected
Reason: The p-value is low enough that the two pools have two different means.

Ttest_indResult(statistic=-7.249347511955615, pvalue= 5.957726836616097e-13)





![Alt text](bootstrap_te.jpg?raw=true "Bootstrap Mean Score of Base Pool vs Tight End Pool")


---------------------------------------------------------------------------------------------------------------------------------

## Conclusion

For week 13 in the NFL the top 5 tight ends and the top 5 running backs increase the average score of your team. Top 5 wide recievers did not. And, top 5 Quarterbacks actually lowered the fantay teams score on average.

---------------------------------------------------------------------------------------------------------------------------------


## Further Study

Test Different Methods Of Filtering.
Expand to include more weeks of the NFL to see if these finding stay true over time
Expand to include past seasons of the NFL to see if these findings stay true over time
Include predictive modeling to assist in pool filtering



