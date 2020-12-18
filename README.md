# Daily Fantasy Football Team Generation

![Alt text](download.jpg?raw=true "DFS")

---------------------------------------------------------------------------------------------------------------------------------
## Abstract

Daily Fantasy Football is a great way to increase entertainment value for professional sport. And, for some people Daily Fantasy Football is a way of life and could be considered a revenue stream. In this project I am exploring data in relation to Daily Fantasy Football from the website Draftkings to explore different ways to create teams. Leveraging the data I look at different ways to filter player pools in hopes of finding a method of filtering that will increase teams scores. 


---------------------------------------------------------------------------------------------------------------------------------

## Background and Motivation

As an expert in Fantasy Football, I am deeply motivated by the idea of making money. And, week in and week out Daily Fantasy Football offers the biggest returns for your dollar. My best finish in a single contest is 2nd place out of 250,000 people earning me a 2,000% return on entrance fee. I created 30 different teams for that specific contest, and generated those teams by manually selectng players from a pool of players I heavily filtered based on my Fantasy Football knowledge alone (subjective approach). Starting with this project I hope to take a more objective approach and begin to truly understand how to filter a pool of players to randomly generate Daily Fantasy Football lineups to maximize team score in terms of approaching Daily Fantasy Football through Data Science.

Professional sports is full of so much randomness that it's difficult to almost impossible to predict. To be successful in Daily Fantasy Football I will combat the randomness is sports with a little randomness of my own. The success of my randomness depends entirely on how we filter the available pool of players that we generate out lineups from. Of course, we will filter out anyone with an injury, but what other ways can we filter the pool of players to make it as small as possible, while maximizing potential team score.


---------------------------------------------------------------------------------------------------------------------------------

## Research Question & Data


Question: Which position's top 5 players increase the average score for a Daily Fantasy Football team during week 13 in the 2020 NFL season?

What is a top 5 player? A top 5 player for the purpose of this project is based on the cost of that player for that position. For example, the top 5 most expensive players for a position are projected to be the top 5 scorers with the exeption of injuries. 

What is the Base Pool of players? The base pool of players I used as my sample population is all of the available players minus any players with injuries (not playing), or player with COVID-19 with respect to 2020 Pandemic. It should be noted that there are still many players active on NFL rosters that recieve 0 points because they maybe a backup or have little playing time. This inherently brings down the mean score and should be considered when formulating other methods of player filtration. 


---------------------------------------------------------------------------------------------------------------------------------


## The Process 

I combined the Draft King's player information with player results from RotoGuru, a website dedicated to strategy in fantasy sports. Draft offers CVS's downloads for player information for each week. However, I had to convert RotoGuru's data from HTML to JSON to CSV and then to a Panda's Dataframe. Once, I had both website's data I combined them into a single dataframe on a player name after some string manipulation to make player's names equal in both original Dataframes. I then filtered out all of the players in said Dataframe who had COVID-19 or wasn't playing and this created my base pool. Utilizing the base pool I filtered out players to create four different sub-pools to test against the base pool of players. Each sub-pool had each position filtered down to only the top 5 players for that position. The four sub-groups consist of the top 5 Quarterback pool, top 5 Wide Reciever pool, top 5 Running Back pool, and a top 5 Tight End pool to help answer the question, "Which position's top 5 players increase the average score for a Daily Fantasy Football team during week 13 in the 2020 NFL season?". For example, the top 5 Quarterback pool consists of all the players from the base pool while limiting the available Quarterbacks to only the top 5. 

---------------------------------------------------------------------------------------------------------------------------------

## Creating The Samples

I wrote a function that randomly generates a Fantasy Football team filling in each required position with a player of that position. The function took player's cost into consideration. For, example with respect to salary cap the function never generated a team that costed more that $50,000 because that would be invalid. Furthermore, the function never generated a team that costed less than $45,000 to maximize player value. I then created a function that would call the previous function 1000 times. With that said, I generated 1000 samples for each pool of players so that I could test them against eachother.





![Alt text](Boxplt.jpg?raw=true "Distribution of each player pool team's score")



















![Alt text](bootstrap_te.jpg?raw=true "Bootstrap Mean Score of Base Pool vs Tight End Pool")



