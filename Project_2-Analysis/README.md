
# Project 2 Analysis

## Introduction
This file consists of multiple analyses that provide insights into the relationship between skills and salaries in the data science job market. It helps users identify the essential skills based on their job and their location.

### Questions to Analyze
1. What are the top skills for data professionals?
2. Do more skills equal higher pay?
3. What is the median salary for data science jobs across regions?
4. What’s the pay for the top 10 skills?


### Excel Skills Used

- Pivot Tables
- Pivot Charts
- DAX (Data Analysis Expressions)
- Power Query
- Power Pivot

### Data Jobs Dataset

The dataset used for this project was obtained from a Youtube video(Excel for Data Analytics - Full Course for Beginners by Luke Barousse), which contains real-world data science job information from 2023.

## What are the top skills for data professionals?

### Skill: Power Pivot

#### Power Pivot

- I created a data model by integrating the `data_jobs_salary` and `data_jobs_skills` tables into one model by building a relationship betwen the two.
  
#### Data Model

- I created a relationship between my two tables using the `job_id` column.
    <img width="578" height="462" alt="relat" src="https://github.com/user-attachments/assets/68f22948-9bb2-47c6-9faf-34bee5ecb5ba" />

#### 📃 Power Pivot Menu

- I made several DAX measures for my analysis to gain deeper insights on the salary trends based on skills. 
    <img width="638" height="757" alt="powerpiv" src="https://github.com/user-attachments/assets/6e2290d5-d947-4e65-a60b-0c25aeeffd88" />

### Analysis

#### Insights
- The required skills that remained integral for most of the data science jobs are SQL and Python.
- Engineer roles demand skills in AWS and Azure.
- This analysis will help users identify the top skills needed to satisfy their job roles, as well as it will assist them on which area to expand on when applying to higher-level roles.

## Do more skills equal higher pay?

### Skill: Power Query (ETL)

-  I extracted data from data_salary_all.xlsx in Power Query and generated two queries:
    - Data jobs information
    - Skills for each job ID

#### Transform

- Then, I transformed each query by modifying the column types, removing irrelevant columns, standardizing text by removing specific words, and trimming extra whitespaces.
- The transformed queries were loaded into the workbook to create the analyses.


### Analysis

#### Insights

- Jobs that require fewer skills, such as Business Analyst roles, tend to offer lower salaries compared to Senior Data Engineer positions that demands a broader skill set.
- There is a clear distinction between Data Engineers and Data Scientists in terms of their job skills requirements. Data Engineers require more skills than Data Scientists, yet their salaries remain comparable. In some countries, Data Scientists even surpass the median salary of Data Engineers.

## What is the median salary for data science jobs across regions?

### Skills: PivotTables & DAX

#### Pivot Table

- I created a PivotTable using the Data Model I generated with Power Pivot.
- I moved the `job_title_short` to the rows area and `salary_year_avg` into the values area.
- Then I added new measures to calculate the median salary for United States and non-United States jobs.
    ```
    =CALCULATE(
        MEDIAN(data_jobs_all[salary_year_avg]),
        data_jobs_all[job_country] = "United States")
    ```
   ```
   =CALCULATE(
       [Median Salary],data_jobs_salary[job_country]<>"United States") 
   ```

#### DAX

- I also used DAX to calculate the overall median salary average.

    ```
    Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
    ```

### Analysis

#### Insights
- Senior Data Scientists and Senior Data Engineers both have the highest median salaries compared to other job titles, indicating that higher-level roles are vital in the data science job market.
- These salary insights help people and companies have a basis for planning and negotiating pay, making sure offers match the market and take location differences into account.

## What’s the pay of the top 10 skills?

### Skill: Advanced Charts (Pivot Chart)

#### PivotChart

- Using a combo PivotChart, I plotted median salary alongside skill likelihood (%) based on my PivotTable data.
    - Primary Axis: Median Salary (Clustered Column)
    - Secondary Axis: Skill Likelihood (Line with diamond markers)

### Analysis

#### Insights

- Data shows that professionals with skills in Python, SQL, and AWS tend to earn higher median salaries.
- This goes to show how important it is to research the top skills needed for a particular job and to invest time in honing those skills to achieve higher salaries.

