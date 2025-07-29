# Excel Salary Dashboard

![1_Salary_Dashboard.png](/0_Resources/Images/1_Salary_Dashboard_Final_Dashboard.gif)

## Introduction

Job seekers can use this dashboard to search for roles with competitive salaries tailored to their preferred location and job type. The dashboard showcases the salary trends across job titles, helping users make informed decisions on which career path to pursue.
### Dashboard File
The dashboard is in [Salary_Dashboard.xlsx](Salary_Dashboard.xlsx).

### Excel Skills Used

The following Excel skills were utilized for analysis:

-  Charts
-  Formulas and Functions
-  Data Validation

### Data Jobs Dataset

The dataset used for this project was obtained from a Youtube video(Excel for Data Analytics - Full Course for Beginners by Luke Barousse), which contains real-world data science job information from 2023.


## Dashboard Build

### Charts

#### Data Science Job Salaries - Bar Chart

<img width="408" height="335" alt="job-bar" src="https://github.com/user-attachments/assets/425d4bb1-2a3c-4b63-b68f-1129700e7413" />

- Bar chart is used to visualize the differences in median salaries accross various jobs.
- Job titles are arranged from highest to lowest salary.
- Insights Gained: Among all the jobs, engineers and senior-level roles have higher salaries compared to others.

#### Country Median Salaries - Map Chart

<img width="348" height="466" alt="map" src="https://github.com/user-attachments/assets/41c12bfb-67cb-4b02-91db-c941d31ea920" />

- Median salaries are plotted worldwide using a map chart.
- The color intensity represents salary levels across regions. Darker shades indicate higher salaries.
- Insights Gained: The chart made it easier to spot the differing salaries across regions.

### Formulas and Functions

#### Median Salary by Job Titles

```
=MEDIAN(
IF(
    (jobs[job_title_short]=A2)*
    (jobs[job_country]=country)*
    (ISNUMBER(SEARCH(type,jobs[job_schedule_type])))*
    (jobs[salary_year_avg]<>0),
    jobs[salary_year_avg]
)
)
```

- The code consists of `MEDIAN()` function with nested `IF()` statement to calculate the median of values that meet certain conditions.
- These conditions are the job title, country, schedule type. Blank salaries are excluded.
- Insights: Provides specific salary values for job titles, regions, and schedule types.
- Formula Purpose: This formula populates the table below, returning the median salary based on job title, country, and type specified.
<img width="327" height="261" alt="excel-table" src="https://github.com/user-attachments/assets/9f0e8b21-ffaa-4859-a58b-d6028628c18a" />



#### Count of Job Schedule Type

```
=FILTER(J2#,(NOT(ISNUMBER(SEARCH("and",J2#))+ISNUMBER(SEARCH(",",J2#))))*(J2#<>0))
```

- This Excel formula utilizes the `FILTER()` function to exclude job types that contain "and" or commas, and to omit zero values.
- Formula Purpose: This formula populates the table below, which returns a list of unique job types.
<img width="207" height="222" alt="excel-table2" src="https://github.com/user-attachments/assets/0f8bc0c2-a79f-433b-9e00-e0750f726005" />

#### KPIs
<img width="1101" height="181" alt="kpis" src="https://github.com/user-attachments/assets/d5e2cd51-622b-4c60-9c09-cc356dfa3c3e" />
- The generated KPIs above were established by using the XLOOKUP() function(see the image below for the Median Salary KPI), which outputs a value based on the selected entry from the data validation drop-downs(Job Title, Country, Type)
<img width="874" height="308" alt="xlook" src="https://github.com/user-attachments/assets/94823480-465c-4183-a6f2-031988315171" />


