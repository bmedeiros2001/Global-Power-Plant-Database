# Global-Power-Plant-Database

## Data Overview
- **34,937 records** of **164 countries**.
-   **72%** of the world’s electricity generation capacity

Each record contains:
- **Power plant details** (2013 to 2019):
-   geolocations
-   energy source
-   plant capacity
-   yearly actual and estimated energy generation
-   ownership

**Data Quality**
- **> 90% of plants in the US** reported energy generation data.
- **< 50% of plants for other countries** reported their energy generation data

<img width="424" alt="Image" src="https://github.com/user-attachments/assets/a4fc80df-8c24-4343-aeac-f762efca8d6a" />

---

## Executive Summary
The global energy sector is undergoing a significant transformation: increasing focus on renewable energy sources and sustainable practices. 

**Goal:** To provide data-driven insights that support renewable energy investment, emission compliance, and economic impact analysis for informed decision-making by energy stakeholders.

## Business-Use Cases
**Identify regions leading in adding renewable energy sources over the past few years** to get policymakers to replicate successful strategies in other areas and allocate resources more effectively.

**Identify fuel types with the highest CO₂ emissions** to strategize on transitioning to cleaner, low-emission alternatives.

**Analyze the economic contribution of power plants by fuel type in terms of employment:**

---

## Normalization:

<img width="512" alt="Image" src="https://github.com/user-attachments/assets/d6c72d97-03a9-4340-9c02-7f95cf18cf7c" />

## EER Diagram
<img width="532" alt="image" src="https://github.com/user-attachments/assets/2759b897-81dc-459b-9ee3-f5edf8e80a63" />

---

## Visualization

### Report Query 1: Identifying Renewable Energy Hotspots

<img width="907" alt="Image" src="https://github.com/user-attachments/assets/751679d4-215f-4101-a56b-b39cda2b94d8" />

**Top 3 Hotspot Countries per Energy Source:**

- Hydro: China, Venezuela and Brazil 
- Solar: China, India, and United States 
- Wind: China, United Kingdom and United States

### Report Query 2: Emissions Compliance Monitoring

<img width="825" alt="Image" src="https://github.com/user-attachments/assets/c3ed9b49-d6c2-47cb-bf9f-cf95b2ae49cd" />

Breakdown of CO₂ emissions per fuel type.

**Insights:**
- Petcoke and Coal remain the largest contributors to emissions.
- Overall decrease in emissions throughout the years.

<img width="707" alt="Image" src="https://github.com/user-attachments/assets/60ae47c2-12c5-4fef-8e1f-049786a9f101" />
Breakdown of CO₂ emissions of renewable vs. non-renewables.

**Insights:**
- Stark contrast between renewable and non-renewable CO2 emissions.
- Decrease between non-renewables from 2016-2018 but sharp increase in 2019.

### Report Query 3: Economic Impact by Fuel Type

<img width="873" alt="image" src="https://github.com/user-attachments/assets/5697492f-46c9-4659-87c2-dd5fbb594909" />

**Top Employment Trends:**
- **Gas** consistently employs **2-3 times more** workers than other fuel types.
- **Oil, coal,** and **petcoke** have seen an **18.15% decline** in employees over the past 6 years.
- **Employment **in** all renewable energy fuel types** has remained **stagnant** over the same period.

### Report Query 4: Economic Impact for Non-Renewable Energy - Gender Gap


