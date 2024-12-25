# T20 World Cup Match Analysis: India vs Pakistan

## Project Overview

**Project Title**: T20 WORLD CUP IND VS PAK MATCH ANALYSIS

**Level**: Beginner

**Schema**: [T20_WORLDCUP_IND_VS_PAK]

The India vs Pakistan 2024 Project aims to explore and develop avenues for collaboration, competition, or engagement between the two nations in areas such as sports, diplomacy, business, or cultural exchange. The initiative seeks to leverage the unique dynamics between the two countries to foster mutual growth, highlight competitive strengths, or deepen relationships.

## Objectives

   1.	**Sports**:
     o	Showcase iconic cricket or other sporting events, emphasizing unity and rivalry.
     o	Promote sporting diplomacy through shared initiatives.
   2.	**Geopolitics**:
     o	Encourage peace-building through dialogue and joint programs.
     o	Highlight key policies for regional stability in South Asia.
   3.	**Economic Collaboration**:
     o	Identify potential trade and investment opportunities.
     o	Explore joint ventures in technology, agriculture, and other key industries.
   4.	**Cultural Exchange**:
     o	Celebrate shared heritage through films, literature, or festivals.
     o	Organize events for cross-border cultural understanding.
   5.	**Technological Partnerships**:
     o	Collaborate on innovative solutions for common challenges like climate change or healthcare.
     o	Promote research and development initiatives involving experts from both countries.

## Project structure

### 1.Database Setup

 •	**Schema Creation**: The project starts by creating named `[T20_WORLDCUP_IND_VS_PAK]`.
 •	**Table Creation**: I create two tables [bowling.info] and [bowlers.info] using keys
        [primary key & foreign key],`[T20_WORLDCUP_IND_VS_PAK].[BATTING.INFO1]`.
 •	`[T20_WORLDCUP_IND_VS_PAK].[BOWLING.INFO3]`is created to store the players data. The table structure includes Columns for PLAYER_ID [PRIMARY KEY], 
    PLAYER_NAME,RUNS,BALLS_PLAYED,FOURS,SIXES,STRIKE_RATE.   
```sql    
CREATE TABLE [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1](
PLAYER_ID INT PRIMARY KEY,
PLAYER_NAME NVARCHAR(80),
RUNS INT,
BALLS_PLAYED INT,
FOURS INT,
SIXES INT,
STRIKE_RATE DECIMAL(5,2),
TEAM NVARCHAR(80)
);

CREATE TABLE [T20_WORLDCUP_IND_VS_PAK].[BOWLING_INFO3](
PLAYER_ID INT PRIMARY KEY,
PLAYER_NAME NVARCHAR(80),
OVERS INT,
MAIDENS INT,
GIVEN_RUNS INT,
WICKETS INT,
ECONOMY DECIMAL(3,2),
TEAM NVARCHAR(80),
FOREIGN KEY(PLAYER_ID) REFERENCES [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1](PLAYER_ID)
);
```
### 2.Data Exploration
 •	**Players count in batting**: Find out how many unique players in the dataset.
 
 •	**Players count in bowling**: Find out how many unique players in the dataset.
 
 •	**Best Score**: Identify best score player name in the dataset.
     
 ```sql
  SELECT PLAYER_NAME,TEAM 
  FROM [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1] ;
     
  SELECT PLAYER_NAME,TEAM 
  FROM [T20_WORLDCUP_IND_VS_PAK].[BOWLING_INFO3];

  SELECT PLAYER_NAME,TEAM,MAX(RUNS) AS BEST_SCORE 
  FROM [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1] 
   GROUP BY PLAYER_NAME,TEAM;
   ```

 ### 3.Data Analysis & Findings
 The following SQL queries were developed to answer specific players questions:
 
--Q1 WHICH PLAYERS SCORED <15 FOR INDIA?    
```sql
SELECT PLAYER_NAME,RUNS FROM [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1]
WHERE RUNS<15 AND TEAM = 'IND';
```

--Q2 WHO FROM INDIA SCORED >10 ,LIST IN Alphabatical ORDER?
```sql
SELECT PLAYER_NAME,RUNS FROM [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1]
WHERE RUNS>10 AND TEAM= 'IND'
ORDER BY PLAYER_NAME ASC;
```

--Q3 WHICH BOWLER HAS <4 ECONOMY FROM BOTH TEAMS?
```sql
SELECT PLAYER_NAME,ECONOMY FROM [T20_WORLDCUP_IND_VS_PAK].[BOWLING_INFO3]
WHERE ECONOMY<4 ;
```

--Q4 WHAT IS THE HIGHEST BATTING SCORE FROM BOTH TEAMS?
```sql
SELECT TEAM,MAX(RUNS) AS HIGHEST_BATTING_SCORE 
FROM [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1]
GROUP BY TEAM;
```

--Q5 WHICH TEAM HAS >40 RUNS AS HIGHEST BATTING SCORE? 
```sql
SELECT TEAM,MAX(RUNS) AS HIGHEST_BATTING_SCORE 
FROM [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1]
GROUP BY TEAM HAVING MAX(RUNS)>40;
 ```

--Q6 WHAT ARE THE RUNS SCORED AND WICKETS TAKEN BY AKSHER PATEL?
```sql
SELECT [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1].PLAYER_NAME,
[T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1].RUNS,
[T20_WORLDCUP_IND_VS_PAK].[BOWLING_INFO3].WICKETS 
FROM [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1]
INNER JOIN [T20_WORLDCUP_IND_VS_PAK].[BOWLING_INFO3]
ON [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1].PLAYER_ID =
[T20_WORLDCUP_IND_VS_PAK].[BOWLING_INFO3].PLAYER_ID
WHERE [T20_WORLDCUP_IND_VS_PAK].[BATTING_INFO1].PLAYER_NAME ='AXAR';
```
## Findings Player Performance Analysis:
1.**Top performs in T20 world cup ind vs pak match**: 
•	Highest runs score in ind vs pak match.
•	Most wickets taken in ind vs pak match.

2.**consistancy metrics**:
•	Players with the highest batting average or strike rate.
•	Bowlers with the best bowling average or economy rates.

3.**Record breakers**:
•	Players with the highest individual runs scores in T20 world cup match.
•	Who get 5 wickets or above taken wickets in this match .

## Reports
  
•	**Players summary**: A detailed  report summarizing  total matches,players total runs and cricket performance.

•	**Trend analysis**: insight into runs score across the matches.

•	**Match insights**: Report on best T20 batsmen and unique batsmen runs score per T20  matches.

## Conclusion:
The India vs Pakistan 2024 Project represents a unique opportunity to channel the complex dynamics between the two nations into constructive and impactful outcomes. By leveraging their shared history, cultural ties, and competitive spirit, this initiative can serve as a platform for fostering collaboration, promoting dialogue, and celebrating mutual achievements

**How to use**

1.**clone the Repository**: Clone this project repository from GitHub.

2.**Set Up the Database**: Run the SQL scripts provided in the database_setup.sql file to create and populate the database.

3.**Run the Queries**: Use the SQL queries provided in the analysis_queries.sql file to perform your analysis.

4.**Explore and Modify**: Feel free to modify the queries to explore different aspect of the dataset or answer
Additional business questions.


