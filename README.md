
# 2023 World Layoffs Analysis using MySQL

## Project Overview
This project focuses on analyzing global layoffs in 2023 using MySQL. The dataset is cleaned, standardized, and explored using SQL queries to identify patterns in job layoffs across industries, locations, and time periods.

## Dataset
The dataset contains information about company layoffs, including:
- **Company**: Name of the company
- **Location**: Where the layoffs occurred
- **Industry**: The sector of the company
- **Total Laid Off**: The number of employees laid off
- **Percentage Laid Off**: The percentage of workforce affected
- **Date**: When the layoffs happened
- **Stage**: Company growth stage
- **Country**: Country of the company
- **Funds Raised (in millions)**: The total funding raised by the company

## SQL Queries

### 1. Data Cleaning
- Created a staging table (`layoffs_staging`) for data cleaning.
- Identified and removed duplicate entries.
- Standardized industry names (e.g., "CryptoCurrency" → "Crypto").
- Standardized country names (e.g., "United States." → "United States").
- Converted date column to `DATE` format.
- Handled missing values by populating industry column based on company name.

### 2. Exploratory Data Analysis (EDA)
- Identified companies with the **largest layoffs**.
- Found industries with the highest number of layoffs.
- Examined layoffs **by country** and **by location**.
- Analyzed layoffs **over time** to detect trends.
- Identified the **biggest layoffs in a single event**.
- Found the total layoffs per **month and year**.
- Created a rolling total of layoffs over time.

## Key Insights
- **Tech and Crypto industries** were among the most affected sectors.
- **Startups** and high-growth companies had significant layoffs.
- **Layoffs peaked at certain months**, indicating seasonal trends.
- **Certain countries and locations** had disproportionately high layoffs.
- **Companies with high funding were also impacted**, indicating broader economic factors.

## Technologies Used
- **MySQL** for querying and analysis
- **SQL Window Functions** for ranking and aggregations
- **Data Cleaning Techniques** for handling missing/duplicate data

## How to Run the Project
1. Load the dataset into MySQL.
2. Execute the SQL scripts in sequence:
   - Data Cleaning queries
   - Standardization queries
   - Exploratory Analysis queries
3. Visualize insights using MySQL queries or export results for dashboarding.

## Future Enhancements
- Build a **Power BI or Tableau dashboard** for better visualization.
- Integrate data from **job postings** to correlate layoffs with hiring trends.
- Perform **predictive analysis** using machine learning models.

---

## Author
Diwakar - Electronics & Communication Engineering Student at Jyothy Institute of Technology, Bengaluru. Passionate about **SQL, Python, and Data Analytics**.

For queries, feel free to connect with me!
