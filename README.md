# Indian-Election-Dashboard-2024

## Overview
"I am proud to present this Indian Election 2024 dashboard, a first-of-its-kind interactive data visualization created entirely from scratch using Power BI. This dashboard offers unique insights and is the first in the world to provide such a comprehensive and dynamic analysis of the Indian Elections 2024."


## Features
- **Constituency-Level Insights:** Detailed information on each constituency, showcasing the leading candidate and party, margin votes, and margin percentage.
- **State/UT Breakdown:** Interactive maps and charts for exploring election results across various States and Union Territories.
- **Party Performance Analysis:** Visualizations depicting the number of constituencies won by each party and highlighting both leading and trailing candidates.
- **Dynamic Data Highlights:** Key metrics displayed through intuitive card visuals, such as total constituencies, total margin votes, and average margin percentage. Includes a gauge visual to compare the average margin percentage against a target value.
- **Dynamic Party Symbols:** Integration of dynamic party symbols using a lookup table to enhance the visual representation of data.

## Datasets
- `Indian_Electionss_2024`: Contains columns such as Constituency No., Constituency, Leading Candidate, Leading Party, Margin, Margin %, State/UT, Trailing Party, and Trailing Candidate.
- 'Lookup': Additional datasets for party symbols and state information.

## Technical Implementation
- **Data Modeling:** Established relationships between datasets to create a cohesive and interactive dashboard.
- **DAX (Data Analysis Expressions):** Utilized DAX to calculate highest margin votes and other key metrics.
- **Visualization:** Leveraged various Power BI visuals, including tables, maps, cards, and gauge visuals, to create an informative and visually appealing dashboard.
- **Dynamic Images:** Integrated party symbols dynamically using a lookup table for a richer visual context.

## Key DAX Measures
### Highest Margin Votes
```DAX
Highest Margin Votes = 
VAR MaxMargin = MAX('Indian_Electionss_2024'[Margin])
RETURN
IF(ISINSCOPE('Indian_Electionss_2024'[State/UT]), MaxMargin, BLANK())


### Party Symbol URL
```DAX
Party Symbol URL = 
VAR LeadingParty = SELECTEDVALUE('Indian_Electionss_2024'[Leading Party])
RETURN
CALCULATE(
    MAX('Indian_Electionss_2024'[Party Symbol URL]),
    FILTER('Indian_Electionss_2024', 'Indian_Electionss_2024'[Leading Party] = LeadingParty)
)

