# Miniproject 2

### [Assignment](assignment.md)

## Project/Goals
For this miniproject my goal was to retrieve data from Foursquare and Yelp's APIs, store that data locally in a SQLite3 database, then examine the data for interesting discoveries.

## Process

First, I explored the documentation for both APIs to learn not only their endpoints but also the kind of information I could expect to recieve. In doing so I selected a number of categories which had crossover between the two APIs for later comparison. I decided to examine how each API looks at as similar a request as I could make for my analysis.

Next, I called the the APIs giving them the same Lat/Long, search radius, and result limit. The results of these calls were stored in pandas dataframes for cleaning. I went through the data to make sure it could be considered "tidydata".

(Also got sidetracked trying to create a one-size-fits-all recurssive function to handle this for both APIs at once before realizing that was probably a bad idea given the timelimit)

After tidying, I examined the nature of the data I had gathered to plan out how I wanted to build my database schema. I stored the dataframes into a database using SQlite. Using SQL, I sorted the data into tables according to my schema design.

<img src="/images/ERD.png">

Finally, I was ready for analysis... until I realized that my computer permissions were not letting me write to my database and wouldn't update the permissions of the file...
I went back and did some analysis using pandas to find the top 10 points of interest by rating across both APIs. To normalize the rating system (Foursquare's 10 point vs Yelp's 5 point) I divided each rating by the max rating in the API, before multiplying by 10 to return to a 10 point system. I pulled the top 10 by rank from a combined list of each API.


## Results

I found that the 10 (11 with ties) highest rated points of interest between the two APIs are:

1. (10.00)
Manoush'eh
Incognito Coffee
Gotham Steakhouse & Cocktail Bar
4th (9.89)
Commodore Ballroom
5th (9.78)
Victoria's Secret
Sephora
Hawksworth Restaurant
8th (9.67)
The Orpheum
Le Crocodile Restaurant
Indigo - Robson
Abercrombie & Fitch

I had issues writing to my database (writing would change permissions not allowing me to write/change again without overwiting).
I am looking for a solution and will update this section when I do so.

## Challenges 

###Pulling nested dictionaries and lists out of the APIs:
My brain still has a hard time actually visualizing where stuff is within the JSON file returned and how to pull the information I actually need out of it. This portion of the project took longer than I hoped though, I know with practice it will get faster.

I also had issues with SQLite changing permissions on my computer so that I couldn't write more than once to any database I created. Still haven't figured out why

## Future Goals

I would have liked to pull specific places of interest to do a direct comparison between the two APIs.

I also would like to incorperate the City of Vancouvers API to see the relation between zoning and local social economic status plays on the rating of different poits of interest.
Examining local chains located in different locations around the city and see how they compare against each other in aggregate. (Main St vs Commercial vs Kits etc.)

I would also be interested in using UBER Eats or Skip the Dishes API to get restraunt ratings to see if restraunts do better or worse if their patrons are there in person.

I would also like to try the stretch "travelling salesman" problem