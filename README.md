
# Application Architecture Plan & ER Model
## Problem 
A group of people want to get together and start a pick-up hockey league. They want the league to feel realistic and want a way to track teams and players. This project aims to create a database for such a scenario and the details below provide a high-level view. 

## Architecture 
It is possible for a two-tier or a three-tier approach for this project. The two-tier provides more simplicity while the three-tier would be more complex but could be used for a web-based applicaition for the league. 

## ER Diagram

The following ER diagram represents the database structure for the league. It includes the following entities: Division, Teams, Games, Players, Seasons, Statistics, and Referees along with their relationships. 

```mermaid
erDiagram
  Division {
    division_id INT PK
    division_name VARCHAR(255)
  }
  Teams {
    team_id INT PK
    team_name VARCHAR(255)
    division_id INT FK
  }
  Players {
    player_id INT PK
    first_name VARCHAR(255)
    last_name VARCHAR(255)
    team_id INT FK
  }
  GAMES {
    game_id INT PK
    team_1 VARCHAR(255)
    team_2 VARCHAR(255)
  }
  SCORES {
    score_id INT PK
    game_id INT FK
    score_1 INT
    score_2 INT
  }
  POINTS {
    points_id INT PK
    player_id INT FK
    num_goals INT 
    num_assists INT
  }
  STANDINGS {
    standings_id INT PK
    team_id INT FK
    games_won INT 
    games_lost INT
    pts_total INT 
  }
  Division  ||--o{ Teams : "has"
  Teams ||--o{ Players : "has"
  Teams ||--o{ GAMES : "participates"
  GAMES ||--o{ SCORES : "has"
  Players ||--o{ POINTS : "records"
  Teams ||--o{ STANDINGS : "has"


```
