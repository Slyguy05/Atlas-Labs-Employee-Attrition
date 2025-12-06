# Atlas Labs Employee Attrition Analysis 📉🕴️


##  🪜 Table of Contents

- [Project Overview](#-project-overview)
- [Data Sources](#-data-sources)
- [Recommendations](#recommendations)
<br><br>

### 🌠 Project Overview 
---
Atlas Lab needs help to reduce the rate at which employees leave their company. This project provides a detailed analysis for just that purpose. By analyzing various aspects of the employees data, we seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the company's performance. 
<br><br>

### 📂 Data Sources 
---
I was given three excel files to work on, each of course serving their own purpose but ultimately offered legitimate connections in the data.
- Education Level.xlsx  
- Employees.xlsx
- Perfomamce.xlsx

### Tools & Technologies Used
- Microsoft Excel - Data Cleaning/Preparation
- Tableau - Exploratory Data Analysis
- Figma - Creating Reports & Dashboards
<br><br>

### Data Cleaning & Preparation

In the initial data preparation phase, I performed the following tasks:
1. Data loading and inspection
\- I imported all the excel workbooks/files into one workbook and named it `"June.xlsx"` - it was ideal for me to name it this because this project was due in June. So, I now had three sheets in one excel workbook (Employees, Performance & Education Level), this was really what was needed in order for me to have a link between the data when I import it into Tableau.
2. Handled missing values carefully.
3. Data cleaning and formatting.
\- I made sure all the data became well represented and interpretable i.e  the salary column was not in the right format but was later changed to be in currency format.


### Exploratory Data Analysis

So what do we want to achieve?

Reduce the attrition by discovering patterns or trends in the data

EDA involved exploring the employees data to answer key questions, such as:

- Are they leaving because they aren't offered enough compensation?
- Are they leaving because they are Burnt out due to too much work?
- Are they living far from where the company is situated, this could be a major reason too?

### Data Analysis

There was a link between the Employees sheet and Perfomance sheet, the `"Employee ID" column`, and also a link between the employees sheet and the Education Level sheet, the `"Education level" column`. This would be key in creating joins to establish a connection/relationship between the data.


In tableau I used a Full/Inner Join for the Employees Sheet and Perfomance Sheet paired with a Left Join on the Eduction level sheet using the columns mentioned above to establish a relationship in the data respectively.

- Attrition Rate
SUM([Attrition Flag]) / COUNT([Employee ID])


- Attrition Flag
IF [Attrition] = "Yes" THEN 1
ELSE 0
END











