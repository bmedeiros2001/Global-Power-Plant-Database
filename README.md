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

<img width="600" alt="Image" src="https://github.com/user-attachments/assets/a4fc80df-8c24-4343-aeac-f762efca8d6a" />

---

## Executive Summary
The global energy sector is undergoing a significant transformation: increasing focus on renewable energy sources and sustainable practices. 

**Goal:** To provide data-driven insights that support renewable energy investment, emission compliance, and economic impact analysis for informed decision-making by energy stakeholders.

## Business-Use Cases
- **Identify regions leading in adding renewable energy sources over the past few years** to get policymakers to replicate successful strategies in other areas and allocate resources more effectively.

- **Identify fuel types with the highest CO₂ emissions** to strategize on transitioning to cleaner, low-emission alternatives.

- **Analyze the economic contribution of power plants by fuel type in terms of employment:**

---

## Normalization:
- 1NF
- 2NF
- 3NF

<img width="600" alt="Image" src="https://github.com/user-attachments/assets/d6c72d97-03a9-4340-9c02-7f95cf18cf7c" />

## EER Diagram
<img width="600" alt="image" src="https://github.com/user-attachments/assets/2759b897-81dc-459b-9ee3-f5edf8e80a63" />

---

## Visualization

### Report Query 1: Identifying Renewable Energy Hotspots

```sql
SELECT
  c.country_name
  p.name AS power_plant_name,
  ft.fuel_type,
  p.capacity_mw,
  p.latitude,
  p.longitude
FROM
  power_plant p
JOIN
  fuel_type ft ON p.fuel_type_id = ft.fuel_type_id
JOIN
  country c ON p.country_id = c.country_id
WHERE
  ft.fuel_type IN ('solar', 'wind', 'hydro')
ORDER BY
  p.capacity_mw DESC;
```
<img width="600" alt="Image" src="https://github.com/user-attachments/assets/751679d4-215f-4101-a56b-b39cda2b94d8" />

**Top 3 Hotspot Countries per Energy Source:**

- Hydro: China, Venezuela and Brazil 
- Solar: China, India, and United States 
- Wind: China, United Kingdom and United States

---

### Report Query 2: Emissions Compliance Monitoring

```sql
SELECT
    pp.power_plant_id,
    c.country_code,
    eg.generation_year,
    ft.fuel_type,
    ROUND(ce.kg_CO2_per_gwh * eg.actual_generation_gwh, 4) AS emmissions
FROM co2_emissions ce
    JOIN fuel_type ft ON ft.fuel_type_id = ce.fuel_type_id
    JOIN power_plant pp ON pp.fuel_type_id = ft.fuel_type_id
    JOIN country c ON c.country_id = pp.country_id
    JOIN electricity_generation eg ON pp.power_plant_id = eg.power_plant_id
WHERE
    c.country_code = 'USA'
      AND ROUND(ce.kg_CO2_per_gwh * eg.actual_generation_gwh, 4) != 0
ORDER BY
    emmissions DESC;
```
<img width="600" alt="Image" src="https://github.com/user-attachments/assets/c3ed9b49-d6c2-47cb-bf9f-cf95b2ae49cd" />

- Petcoke and Coal remain the largest contributors to emissions.
- Overall decrease in emissions throughout the years.

<img width="600" alt="Image" src="https://github.com/user-attachments/assets/60ae47c2-12c5-4fef-8e1f-049786a9f101" />

- Stark contrast between renewable and non-renewable CO2 emissions.
- Decrease between non-renewables from 2016-2018 but sharp increase in 2019.

---

### Report Query 3: Economic Impact by Fuel Type

```sql
SELECT
    YEAR(e.date) AS year,
    SUM(e.total_employees) AS total_employees_per_fuel_type,
    ft.fuel_type
FROM
    employee e
JOIN fuel_type ft ON ft.fuel_type_id = e.fuel_type_id
GROUP BY
    year,
    ft.fuel_type
ORDER BY
    year DESC;
```

<img width="600" alt="image" src="https://github.com/user-attachments/assets/5697492f-46c9-4659-87c2-dd5fbb594909" />

- **Gas** consistently employs **2-3 times more** workers than other fuel types.
- **Oil, coal,** and **petcoke** have seen an **18.15% decline** in employees over the past 6 years.
- **Employment **in** all renewable energy fuel types** has remained **stagnant** over the same period.

---

### Report Query 4: Economic Impact for Non-Renewable Energy - Gender Gap

```sql
SELECT
    SUM(e.total_women_employees) AS total_women_by_fuel_type,
    (SUM(e.total_women_employees) / SUM(e.total_employees)) * 100 AS percentage_female_employees,
    100 - (SUM(e.total_women_employees) / SUM(e.total_employees)) * 100 AS percentage_male_employees,
    f.fuel_type
FROM
    employee e
INNER JOIN fuel_type f ON e.fuel_type_id = f.fuel_type_id
GROUP BY
    e.fuel_type_id,
    f.fuel_type
ORDER BY
    total_women_by_fuel_type DESC;
```

<img width="600" alt="Image" src="https://github.com/user-attachments/assets/8c355d63-9728-4b4a-9bee-317f5acd13c6" />

- **Significant gender gap**, with men dominating the field, hinting at systemic issues in recruiting or retaining female employees.
- In **coal, oil, and petcoke sectors**, female employment is **below 21%**, indicating significant gender disparity.
- Near-equal distribution in the aggregate of all power plants.

---

## Lessons Learned

- Women are still underrepresented in employment.
- **Hydro** is still **most popular** within renewable energy sources for efficiency and cost.
- **Gas remains dominant in the employment sector**, highlighting its continued importance in the energy mix.
- Employment data suggests **no significant increase in the number of plants generating renewable energy**.
- Stagnation in renewables emphasizes the importance of innovation and strategic investment to drive growth.
