MIST-4610-Proj-Group-4
#Team Name:
---
21482 Group 4
---
Team Members
---
1. Firdows Abdulwahab
2. Dylan Klinghoffer
3. Girish Saravanan
4. Joseph Tapp
5. Munil Vaishnav
---
Database Scenario
---
The NFL Combine Database models the annual NFL Scouting Combine process, capturing the full pipeline from college prospect evaluation through to draft day selection. Each year, hundreds of college football players are invited to Indianapolis where they undergo standardized physical and cognitive drills,  with every result logged against the specific player, drill, and combine event. The database tracks each player's college affiliation, the position or positions they play, their participation and drill results at the combine, and ultimately the NFL team and draft round in which they were selected. This structure makes it possible to query insights such as positional performance averages, college program output, historical draft trends by team, and individual athlete profiles, supporting the needs of front office personnel, scouts, and analysts who rely on accurate combine data to make informed decisions.
Data Model
---
The NFL Combine Database is composed of ten entities whose relationships collectively model the full journey of a college football prospect through the scouting combine and into the NFL Draft.
At the center of the model is the Players entity, which stores each prospect's name, height, weight, and college affiliation. Every player is linked to a College, which records the school name, conference, state, and city. Since a player can play more than one position, a junction table called PlayerPosition sits between Players and Positions, creating a many-to-many relationship that allows a single player to be associated with multiple position codes and names, such as both Linebacker and Defensive End.

When a player attends the combine, their attendance is recorded in CombineParticipation, which links the player, their position at the time of the event, and the specific CombineEvent they attended. The CombineEvent entity stores the year, location, and start and end dates of each annual combine. From there, every individual drill result a player produces is stored in CombineResults, which connects each result back to the specific participation record and to the CombineDrills entity which defines the drill name, category such as Speed or Agility, and the unit of measurement used such as seconds or inches.
On the draft side, DraftPicks records each selection made by an NFL team, storing the draft year, round, overall pick number, and pick within the round. Each draft pick is linked to the Team that made the selection and optionally to the Players entity through a nullable foreign key, meaning that players who attended the combine but went undrafted are still fully represented in the database without requiring a corresponding draft pick record.

The database is specifically scoped to the combine evaluation and draft selection process, meaning it supports storage of player biographical and physical data, college and university information, positional data including multi-position players, combine event details, drill definitions and performance results, and draft pick records linked to both the selecting NFL team and the player chosen. It does not, however, support storage of data outside this scope such as post-draft career statistics, player contracts or salaries, injury or medical history, scouting evaluations and film grades, coaching staff information, player transactions or trades, roster and depth chart data, or players who did not attend the combine at all.

<img width="1138" height="833" alt="image" src="https://github.com/user-attachments/assets/9ff41f0a-b076-4dc4-95d8-ab7f933d4fda" />
