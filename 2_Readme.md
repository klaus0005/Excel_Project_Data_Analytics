
# Project 2 Analysis

### Questions to Analyze

To understand the data science job market, I asked the following:

1. **Do more skills get you better pay?**
2. **What’s the salary for data jobs in different regions?**
3. **What are the top skills of data professionals?**
4. **What’s the pay for the top 10 skills?**

### Excel Skills Used

The following Excel skills were utilized for analysis:

- **Pivot Tables**
- **Pivot Charts**
- **DAX (Data Analysis Expressions)**
- **Power Query**
- **Power Pivot**

### Data Jobs Dataset

The dataset used for this project contains real-world data science job information from 2023.

It includes detailed information on:

- **Job titles**
- **Salaries**
- **Locations**
- **Skills**

## 1. Do more skills get you better pay?

### Skill: Power Query (ETL)

#### Extract

- I first used Power Query to extract the original data (`data_salary_all.xlsx`) and create two queries

#### Transform

- I transformed each query by changing column types, removing unnecessary columns, cleaning text to eliminate specific words, and trimming excess whitespace.
    - data_jobs_all

    - data_job_skills

#### Load

- I loaded both transformed queries into the workbook, setting the foundation for my subsequent analysis.
    - data_jobs_all

    - data_job_skills


#### Insights

-  Positive correlation between the number of skills requested in job postings and the median salary, particularly in roles like Senior Data Engineer and Data Scientist.
- Roles that require fewer skills, like Business Analyst, tend to offer lower salaries, suggesting that more specialized skill sets command higher market value.


## 2️. What’s the salary for data jobs in different regions?

### Skills: PivotTables & DAX

#### Pivot Table

- I created a PivotTable using the Data Model I created with Power Pivot.
- I moved the `job_title_short` to the rows area and `salary_year_avg` into the values area.
- I added new measure to calculate the median salary for United States jobs.
    ```
    =CALCULATE(
        MEDIAN(data_jobs_all[salary_year_avg]),
        data_jobs_all[job_country] = "United States")
    ```

DAX

- To calculate the median year salary I used DAX.

    ```
    Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
    ```

### Analysis

#### Insights

- Job roles like Senior Data Engineer and Data Scientist command higher median salaries both in the US and internationally, showcasing the global demand for high-level data expertise.
- The salary disparity between US and Non-US roles is particularly notable in high-tech jobs, which might be influenced by the concentration of tech industries in the US.


## 3. What are the top skills of data professionals?

### Skill: Power Pivot

#### Power Pivot

- I created a data model by integrating the `data_jobs_all` and `data_jobs_skills` tables into one model.
- Power Pivot created a relationship between these two tables.

#### Data Model

- I created a relationship between my two tables using the `job_id` column.

### Analysis

#### Insights

-SQL and Python dominate as top skills in data-related jobs, reflecting their foundational role in data processing and analysis.
-Emerging technologies like AWS and Azure also show significant presence, underlining the industry's shift towards cloud services and big data technologies.


## 4.What’s the pay of the top 10 skills?

### Skill: Advanced Charts (Pivot Chart)

#### PivotChart

- I created a combo PivotChart to plot median salary and skill likelihood (%) from my PivotTable.
    - **Primary Axis:** Median Salary
    - **Secondary Axis:** Skill Likelihood (as a Line with Markers)
- To customize the chart, I added a title axis title, removed the lines (skill likelihood), and changed the markers to diamonds.

### Analysis

#### Insights

- Higher median salaries are associated with skills like Python, Oracle, and SQL, suggesting their critical role in high-paying tech jobs.
- Skills like PowerPoint and Word have the lowest median salaries and likelihood, indicating less specialization and demand in high-salary sectors.


## Conclusion

Using a dataset I've curated from real-world job postings, I analyzed job titles, salaries, locations, and essential skills. By leveraging Excel features like Power Query, PivotTables, DAX, and charts, I discovered key correlations between multiple skills and higher salaries, particularly in Python, SQL, and cloud technologies. 