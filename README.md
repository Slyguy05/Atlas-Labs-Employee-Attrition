# Atlas Labs Employee Attrition Analysis 📉🕴️


##  🪜 Table of Contents

- [Project Overview](#-project-overview)
- [Data Sources](#-data-sources)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Recommendations](#recommendations)
<br><br><br>

### 🌠 Project Overview 
---
Atlas Lab needs help to reduce the rate at which employees leave their company. This project provides a detailed analysis for just that purpose. By analyzing various aspects of the employees data, we seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the company's performance. 
<br><br><br>

### 📂 Data Sources 
---
I was given three excel files to work on, each of course serving their own purpose but ultimately offered legitimate connections in the data.
- Education Level.xlsx  
- Employees.xlsx
- Perfomamce.xlsx
<br><br>

### Tools & Technologies Used
- Microsoft Excel - Data Cleaning/Preparation
- Tableau - Exploratory Data Analysis & Visualizations
- Figma - Creating Reports & Dashboards
<br><br>

### Data Cleaning & Preparation

In the initial data preparation phase, I performed the following tasks:
1. Data loading and inspection
\- I imported all the excel workbooks/files into one workbook and named it `"June.xlsx"` - it was ideal for me to name it this because this project was due in June. So, I now had three sheets in one excel workbook (Employees, Performance & Education Level), this was really what was needed in order for me to have a link between the data when I import it into Tableau.
2. Handled missing values carefully.
3. Data cleaning and formatting.
\- I made sure all the data became well represented and interpretable i.e  the salary column was not in the right format but was later changed to be in currency format.
<br><br>

### Exploratory Data Analysis

So what do we want to achieve?

Reduce the attrition by discovering patterns or trends in the data

EDA involved exploring the employees data to answer key questions, such as:

- Are they leaving because they aren't offered enough compensation?
- Are they leaving because they are burnt out due to too much work?
- Are they living far from where the company is situated, this could be a major reason too?
<br><br>

### Data Analysis

There was a link between the Employees sheet and Perfomance sheet, the `"Employee ID" column`, and also a link between the employees sheet and the Education Level sheet, the `"Education level" column`. This would be key in creating joins to establish a connection/relationship between the data.

![](https://github.com/Slyguy05/Atlas-Labs-Employee-Attrition/blob/main/Performance%20Sheet.png?raw=true)
![](https://github.com/Slyguy05/Atlas-Labs-Employee-Attrition/blob/main/Performance%20Sheet.png?raw=true)
<br><br>

In tableau I used a Full/Inner Join for the Employees Sheet and Perfomance Sheet paired with a Left Join on the Eduction level sheet using the columns mentioned above to establish a relationship in the data respectively.   

I divided the ages into age groups; **18-24, 24-30, 30-36........48-54.**
- with age group `18-24` & `24-30` representing the younger employees


I used some DAX(Data Analysis Expressions) queries to make more sense of the data I'm dealing with;

- **Attrition Flag** - Converted the `"yes"` & `"no"` answers into `0's` & `1's`. This will be useful to calculate the **attrition rate**.     
```
  IF [Attrition] = "Yes"
  THEN 1
  ELSE 0
  END
```
<br>

- **Attrition Rate** - Calculates the rate at which employees leave the company. This helps us observe attrition behaviour in the company.    
```
SUM([Attrition Flag]) / COUNTD([Employee ID])
```
<br>

- **Normalized Salary** - This scales down the salary to a scale 0-1 to provide direct comparison with the attririon. This give us more accuracy compared to using just raw averages, which in all honesty could work just fine here but could also dilute context as it is influence by group sizes and salary magnitude. Normalization preserves the shape of the salary trend and enables a clear, relative comparison across groups, ensuring the relationship between compensation and attrition is accurately represented.   
```
AVG([Salary]) / WINDOW_MAX(AVG([Salary]))
```
<br>

- **Promotion Status** - This gives us a clearer representation of the data to see how employees fare in the company.
```diff
# Spending the same amount of years since the last promotion and in the most recent role can explain there was promotion 
IF [Years Since Last Promotion] = [Years In Most Recent Role]
THEN "Likely Promotion"

# Spending less years in a role compared to the last time the employee was promoted can explain there was Demotion/Transfer
ELSEIF [Years Since Last Promotion] > [Years In Most Recent Role]
THEN "Likely Demotion/Transfer"
END
```
<br><br>

### Results/Findings

The analysis results are summarized as follows:
1. **Salary and Compensation**   
   Younger employees earn significantly below the company average, especially in roles like Data Scientists, Software Engineers, Sales Representatives, and Recruiters. Where salaries are lowest, attrition is highest
2. **Promotion and Career Growth**   
   Employees who do not see promotion opportunities within their first year — or who are transferred quickly instead of promoted — are more likely to leave. Early instability in career progression creates frustration and leads to churn.
   
   * Early promotions - Fast-track recognition (positive for some).
   * Early transfers - Instability or misplacement (negative for many).
4. **Workload and Overtime**  
   Overtime by itself is not the strongest driver. Employees are willing to put in extra hours, but when effort is not matched with fair compensation or recognition, dissatisfaction rises.
5. **Department and Role Effects**  
  Attrition is concentrated in Technology and Sales, particularly among junior/mid-level roles where pay lags behind expectations. Senior roles and management positions show both lower attrition and higher compensation, highlighting the importance of career progression.
6. **Marital Status and Lifestyle Factors**  
   Single employees show higher attrition rates, which may reflect different career expectations or mobility compared to married and employees. Distance from the workplace may also contribute, though the evidence here is weaker.










