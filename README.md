# SqlCaseStudy_IPL

## Project Highlights

✔ Created a relational database using SQLite

✔ Performed advanced SQL analytics on IPL auction data

✔ Used Window Functions for player ranking and spending analysis

✔ Compared Indian and Overseas player valuations

✔ Generated business insights from auction strategies

# IPL Players Auction Analysis using SQL

## Overview

This project analyzes IPL (Indian Premier League) player auction data using SQL queries and SQLite. The goal is to explore team spending patterns, player valuations, auction strategies, and performance insights through advanced SQL analysis.

The dataset contains information about IPL players, including their teams, roles, acquisition methods, and auction prices.

---

## Dataset

The dataset includes the following attributes:

| Column | Description |
|----------|------------|
| Player | Player name |
| Price_in_cr | Auction price (in Crores) |
| Type | Indian or Overseas player |
| Acquisition | Acquisition method |
| Role | Player role (Batter, Bowler, All-rounder, Wicketkeeper) |
| Team | IPL team |

---

## Technologies Used

- SQL
- SQLite
- Python
- Jupyter Notebook
- Pandas

---

## Database Structure

A table named `IPLPlayers` was created to store player auction information.

```sql
CREATE TABLE IPLPlayers (
    Player TEXT,
    Price_in_cr REAL,
    Type TEXT,
    Acquisition TEXT,
    Role TEXT,
    Team TEXT
);
```

---

## Analysis Performed

### Team Spending Analysis
- Total spending by each IPL team
- Average spending per team

### Player Value Analysis
- Most expensive player in each team
- Most expensive player in each role
- Players priced above their team average

### Role-Based Insights
- Highest-paid All-rounders
- Salary distribution by role

### Ranking and Window Functions
- Ranking players within each team by auction price
- Calculating each player's percentage contribution to team spending

### Classification Analysis
Players categorized into:

- High Value
- Medium Value
- Low Value

based on their auction prices.

### Indian vs Overseas Comparison
- Average auction price of Indian players
- Average auction price of Overseas players

---

## Sample SQL Queries

### Total Spending by Team

```sql
SELECT Team,
       SUM(Price_in_cr) AS Total_Spending
FROM IPLPlayers
GROUP BY Team
ORDER BY Total_Spending DESC;
```

### Most Expensive Player in Each Team

```sql
SELECT *
FROM (
    SELECT Team,
           Player,
           Price_in_cr,
           ROW_NUMBER() OVER (
               PARTITION BY Team
               ORDER BY Price_in_cr DESC
           ) AS rn
    FROM IPLPlayers
)
WHERE rn = 1;
```

---

## Key SQL Concepts Demonstrated

- Aggregate Functions
- GROUP BY
- ORDER BY
- CASE Statements
- Common Table Expressions (CTEs)
- Window Functions
  - ROW_NUMBER()
  - RANK()
  - PARTITION BY
- Subqueries
- Data Classification
- Analytical Queries

---

## Project Structure

```text
├── project1.ipynb
├── IPL Players.csv
└── README.md
```

---

## Learning Outcomes

Through this project, I practiced:

- Database creation using SQLite
- Data loading and preprocessing
- Writing analytical SQL queries
- Using Window Functions for ranking and comparisons
- Extracting business insights from sports auction data

---

## Author

Shide Hajirahimi

GitHub: https://github.com/your-username
