# Global-Power-Plant-Database
## Summary
- Data Overview
- Business-Use Cases
- Visualization

## Data Overview
- **34,937 records** of **164 countries**.
-   **72%** of the world’s electricity generation capacity

- Each record contains:
-   **Power plant details** (2013 to 2019):
-     geolocations
-     energy source
-     plant capacity
-     yearly actual and estimated energy generation
-     ownership

- **Data Quality:**
-   **> 90% of plants in the US** reported energy generation data.
-   **< 50% of plants for other countries** reported their energy generation data

<img width="424" alt="Image" src="https://github.com/user-attachments/assets/a4fc80df-8c24-4343-aeac-f762efca8d6a" />

## Executive Summary
The global energy sector is undergoing a significant transformation: increasing focus on renewable energy sources and sustainable practices. 

**Key challenges:**
- Uneven adoption of renewables across regions
- Compliance with emission standards
- Economic impact on economies.

**Goal:** To provide data-driven insights that support renewable energy investment, emission compliance, and economic impact analysis for informed decision-making by energy stakeholders.

## Business-Use Cases
**Identify regions leading in adding renewable energy sources over the past few years**
- Goal: Help policymakers identify thriving regions to replicate successful strategies in other areas and allocate resources more effectively.

**Identify CO₂ emissions for each energy fuel type**
- Goal: Identify energy fuel types that contribute the most to CO₂ emissions to strategize on transitioning to cleaner, low-emission alternatives.

**Analyze the economic contribution of power plants by fuel type in terms of employment.**
- Goal: Identify the fuel types generating the most employment


## Extract, Transform and Load (ETL)
**Extract:**

Primary Dataset: 
- Global Power Plant Database

Secondary Datasets:
- Employment data: US Bureau Labor Statistics
- CO2 Emissions data: Fifth Assessment Report - IPCC

**Normalization:**

Step 1: Data was initially in First Normal Form (1NF) :
- Ensured atomic values
- Ensure no repeating groups

Step 2: Transformation to Second Normal Form (2NF) :
- Removal of partial functional dependencies
  
Step 3: Transformation to Third Normal Form (3NF) :
- Removal of transitive functional dependencies

![Uploading image.png…]()



