


# Job-Market-dashboard
Requires Excel 2016 or newer (Microsoft 365 desktop) with Power Query and Power Pivot enabled. Will not work in Excel Online free version or Excel 2010.

## Introduction

As a  job seeker and Data Analyst / Business Analyst, I am trying to showcase what skills top employers request and how to land more pay while you search for particular job role.

### Questions to Analyze

To understand the data science job market, I asked the following:

1. **Do more skills get you better pay?**
2. **What’s the salary for data jobs in different regions?**
3. **What are the top skills of data professionals?**
4. **What’s the pay for the top 10 skills?**

### Excel Skills Used

The following Excel skills were utilized for analysis:

- **📊 Pivot Tables**
- **📈 Pivot Charts**
- **🧮 DAX (Data Analysis Expressions)**
- **🔍 Power Query**
- **💪 Power Pivot**

### Data Jobs Dataset

The dataset used for this project contains real-world data science job information from 2023. 

It includes detailed information on:

- **👨‍💼 Job titles**
- **💰 Salaries**
- **📍 Locations**
- **🛠️ Skills**

## 1️⃣ Do more skills get you better pay?

### 🔍 Skill: Power Query (ETL)

#### 📥 Extract

- I first used Power Query to extract the original data (`data_salary_all.xlsx`) and create two queries:
    - 🗃️ First one with all the data jobs information.
    - 🔧 The second listing the skills for each job ID.

#### 🔄 Transform

- Then, I transformed each query by changing column types, removing unnecessary columns, cleaning text to eliminate specific words, and trimming excess whitespace.
    - 📊 data_jobs_all

     <img width="242" height="313" alt="image" src="https://github.com/user-attachments/assets/8d59d572-88c7-4aba-b40a-af1326095b26" />

    - 🛠️ data_job_skills

       <img width="243" height="325" alt="image" src="https://github.com/user-attachments/assets/1b94e0e1-1a4e-456b-a124-1a844ffbcf58" />

#### 🔗 Load

- Finally, I loaded both transformed queries into the workbook, setting the foundation for my subsequent analysis.
    - 📊 data_jobs_all
    - 
     <img width="866" height="293" alt="image" src="https://github.com/user-attachments/assets/34f9bc50-cb6f-4ea1-b7bc-cbcf0d40655f" />

    - 🛠️ data_job_skills

      <img width="864" height="316" alt="image" src="https://github.com/user-attachments/assets/6cf63781-2c1f-424a-b762-29c53ead7c9e" />


### 📊 Analysis

#### 💡 Insights

- 📈 There is a positive correlation between the number of skills requested in job postings and the median salary, particularly in roles like Senior Data Engineer and Data Scientist.
- 💼 Roles that require fewer skills, like Business Analyst, tend to offer lower salaries, suggesting that more specialized skill sets command higher market value.

   <img width="703" height="425" alt="image" src="https://github.com/user-attachments/assets/538b7f5a-952a-4645-96c1-424804c66efb" />

#### 🤔 So What

- This trend emphasizes the value of acquiring multiple relevant skills, particularly for individuals aiming for higher-paying roles.

## 2️⃣ What’s the salary for data jobs in different regions?

### 🧮 Skills: PivotTables & DAX

#### 📈Pivot Table

- 🔢 I created a PivotTable using the Data Model I created with Power Pivot.
- 📊 I moved the `job_title_short` to the rows area and `salary_year_avg` into the values area.
- 🧮 Then I added new measure to calculate the median salary for United States jobs.
    ```
    =CALCULATE(
        MEDIAN(data_jobs_all[salary_year_avg]),
        data_jobs_all[job_country] = "United States")
    ```

#### 🧮 DAX

- To calculate the median year salary I used DAX.

    ```
    Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
    ```

### 📊 Analysis

#### 💡 Insights

- 💼 Job roles like Senior Data Engineer and Data Scientist command higher median salaries both in the US and internationally, showcasing the global demand for high-level data expertise.
- 💰 The salary disparity between US and Non-US roles is particularly notable in high-tech jobs, which might be influenced by the concentration of tech industries in the US.

   <img width="781" height="329" alt="image" src="https://github.com/user-attachments/assets/ea6e9f57-c37c-4215-86bd-1b4dcdba359d" />

#### **🤔 So What**

- These salary insights are important for planning and salary negotiations, helping professionals and companies align their offers with market standards while considering geographical variations.

## 3️⃣ What are the top skills of data professionals?

### 🔧 Skill: Power Pivot

#### 💪 Power Pivot

- 🔗 I created a data model by integrating the `data_jobs_all` and `data_jobs_skills` tables into one model.
- 🧹 Since I had already cleaned the data using Power Query; Power Pivot created a relationship between these two tables.

#### 🔗 Data Model

- I created a relationship between my two tables using the `job_id` column.

 <img width="608" height="453" alt="image" src="https://github.com/user-attachments/assets/12ba1954-436c-4ec0-88ad-f90d57a23e1c" />

#### 📃 Power Pivot Menu

- The Power Pivot menu was used to refine my data model and makes it easy to create measures.

  <img width="1172" height="453" alt="image" src="https://github.com/user-attachments/assets/6745f49d-45f6-442f-a2f5-867ca887bc96" />


### 📊Analysis

#### 💡Insights

- 💻 SQL and Python dominate as top skills in data-related jobs, reflecting their foundational role in data processing and analysis.
- ☁️ Emerging technologies like AWS and Azure also show significant presence, underlining the industry's shift towards cloud services and big data technologies.

  <img width="739" height="442" alt="image" src="https://github.com/user-attachments/assets/c5934ddb-1480-441a-ba13-af01f12742bd" />


#### 🤔So What

- Understanding prevalent skills in the industry not only helps professionals stay competitive but also guides training and educational programs to focus on the most impactful technologies.

## 4️⃣ What’s the pay of the top 10 skills?

### 📊 Skill: Advanced Charts (Pivot Chart)

#### 📈 PivotChart

- I created a combo PivotChart to plot median salary and skill likelihood (%) from my PivotTable.
    - 🪙 **Primary Axis:** Median Salary (as a Clustered Column)
    - 👍 **Secondary Axis:** Skill Likelihood (as a Line with Markers)
- To customize the chart, I added a title axis title, removed the lines (skill likelihood), and changed the markers to diamonds.

### 📊 Analysis

#### 💡Insights

- 💰 Higher median salaries are associated with skills like Python, Oracle, and SQL, suggesting their critical role in high-paying tech jobs.
- 📉 Skills like PowerPoint and Word have the lowest median salaries and likelihood, indicating less specialization and demand in high-salary sectors.

  <img width="859" height="449" alt="image" src="https://github.com/user-attachments/assets/d9892c0f-7d8a-483c-a2d8-e7c14b862c8b" />


### 🤔So What

- This chart highlights the importance of investing time in learning high-value skills like Python and SQL, which are evidently tied to higher paying roles, especially for those looking to maximize their salary in the tech industry.

## Conclusion

As a data enthusiast , I embarked on this Excel-based project to uncover valuable insights about the data science job market. Using a dataset I've curated from real-world job postings, I analyzed job titles, salaries, locations, and essential skills. By leveraging Excel features like Power Query, PivotTables, DAX, and charts, I discovered key correlations between multiple skills and higher salaries, particularly in Python, SQL, and cloud technologies. 
