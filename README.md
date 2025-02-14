# World Layoffs 2023 - SQL Data Cleaning & Analysis

## Project Overview
This project analyzes global layoffs data using MySQL. It involves data cleaning, removing duplicates, standardizing values, handling missing data, and performing exploratory data analysis (EDA) to extract insights.

## Technologies Used
- MySQL
- SQL Queries for Data Cleaning & Analysis

## Dataset
The dataset contains records of layoffs across various companies, industries, locations, and dates.

## Steps Performed

### 1. Data Cleaning
#### **Checking for Duplicates:**
```sql
SELECT company, industry, total_laid_off, `date`,
       ROW_NUMBER() OVER (
           PARTITION BY company, industry, total_laid_off, `date`
       ) AS row_num
FROM world_layoffs.layoffs_staging;
```
#### **Deleting Duplicates:**
```sql
WITH DELETE_CTE AS (
    SELECT *,
           ROW_NUMBER() OVER (
               PARTITION BY company, location, industry, total_laid_off, `date`
           ) AS row_num
    FROM world_layoffs.layoffs_staging
)
DELETE FROM world_layoffs.layoffs_staging
WHERE row_num > 1;
```

### 2. Standardizing Data
#### **Handling Null Values:**
```sql
UPDATE world_layoffs.layoffs_staging2
SET industry = NULL
WHERE industry = '';
```
#### **Standardizing Country Names:**
```sql
UPDATE world_layoffs.layoffs_staging2
SET country = TRIM(TRAILING '.' FROM country);
```
#### **Converting Date Format:**
```sql
UPDATE world_layoffs.layoffs_staging2
SET `date` = STR_TO_DATE(`date`, '%m/%d/%Y');
ALTER TABLE world_layoffs.layoffs_staging2
MODIFY COLUMN `date` DATE;
```

### 3. Exploratory Data Analysis (EDA)
#### **Companies with the Highest Layoffs:**
```sql
SELECT company, SUM(total_laid_off) AS total_laid_off
FROM world_layoffs.layoffs_staging2
GROUP BY company
ORDER BY total_laid_off DESC
LIMIT 10;
```
#### **Layoffs by Industry:**
```sql
SELECT industry, SUM(total_laid_off) AS total_laid_off
FROM world_layoffs.layoffs_staging2
GROUP BY industry
ORDER BY total_laid_off DESC;
```
#### **Layoffs Over Time:**
```sql
SELECT YEAR(`date`) AS year, SUM(total_laid_off) AS total_laid_off
FROM world_layoffs.layoffs_staging2
GROUP BY YEAR(`date`)
ORDER BY year ASC;
```
#### **Rolling Total of Layoffs Per Month:**
```sql
WITH DATE_CTE AS (
    SELECT SUBSTRING(`date`, 1, 7) AS dates, SUM(total_laid_off) AS total_laid_off
    FROM world_layoffs.layoffs_staging2
    GROUP BY dates
)
SELECT dates, SUM(total_laid_off) OVER (ORDER BY dates ASC) AS rolling_total_layoffs
FROM DATE_CTE
ORDER BY dates ASC;
```

## Conclusion
This project provides an end-to-end SQL-based approach to analyzing layoff trends, cleaning datasets, and deriving meaningful insights. The findings highlight the industries, companies, and locations most affected by global layoffs.

## Author
- **Diwakar** - Electronics and Communication Engineering, Jyothy Institute of Technology, Bengaluru
