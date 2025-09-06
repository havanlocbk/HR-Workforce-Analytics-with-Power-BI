# I. 📊 Project Title: HR Workforce Analytics with Power BI

*Applied Power Query, DAX, and Power BI to analyze HR workforce data,
enabling insights on employee retention, satisfaction, and performance
for data-driven HR decision-making.*

**Author:** Ha Van Loc\
**Date:** 2025-09-06

## 🛠 Tools Used

![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)\
![Power
BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)\
![DAX](https://img.shields.io/badge/DAX-0A66C2?style=for-the-badge&logoColor=white)

------------------------------------------------------------------------

## II. 📑 Table of Contents

I. [📊 Project
Title](#i--project-title-hr-workforce-analytics-with-power-bi)\
II. [📌 Background & Overview](#ii--background--overview)\
III. [📂 Dataset Description & Data
Structure](#iii--dataset-description--data-structure)\
IV. [🧠 Design Thinking Process](#iv--design-thinking-process)\
V. [⚒️ Main Process](#v--main-process)\
VI. [📊 Key Insights &
Visualizations](#vi--key-insights--visualizations)\
VII. [🔎 Final Conclusion &
Recommendations](#vii--final-conclusion--recommendations)

------------------------------------------------------------------------

# II. 📌 Background & Overview

### Objective

This project analyzes HR workforce data to uncover patterns in employee
retention, satisfaction, and performance.

✔️ Identify turnover rate across departments and demographics\
✔️ Understand key drivers of employee satisfaction and engagement\
✔️ Provide actionable insights for HR decision-making and workforce
planning

### 👤 Who is this project for?

✔️ HR Managers & Workforce Planners\
✔️ Data Analysts & BI Professionals\
✔️ Business Leaders & Decision Makers

------------------------------------------------------------------------

# III. 📂 Dataset Description & Data Structure

### 📌 Data Source

-   **Source**: Internal file `HRDataset.xlsx`\
-   **Size**: 300+ employee records, multiple lookup tables (Position,
    Department, Manager, MaritalStatus, Performance)\
-   **Format**: `.xlsx`

### 📊 Table Schema (Simplified)

  -------------------------------------------------------------------------------
  Table Name      Key Columns (selected)                        Purpose
  --------------- --------------------------------------------- -----------------
  Employee        EmployeeId, Name, ManagerID, PositionID,      Main fact table
                  MaritalStatusID, PerformanceScoreID, Salary,  with workforce
                  EngagementScore, SatisfactionScore,           data
                  AbsenceDays                                   

  Position        PositionID, Position, DeptID                  Job titles,
                                                                linked to
                                                                Department

  Department      DeptID, Department                            Department info

  Manager         ManagerID, ManagerName                        Manager lookup

  MaritalStatus   MaritalStatusID, MaritalDesc                  Marital status
                                                                dimension

  Performance     PerfScoreID, PerformanceScore                 Performance
                                                                ratings
  -------------------------------------------------------------------------------

### 🔗 Relationships

-   Employee ↔ Position (PositionID)\
-   Position ↔ Department (DeptID)\
-   Employee ↔ MaritalStatus (MaritalStatusID)\
-   Employee ↔ Performance (PerfScoreID)\
-   Employee ↔ Manager (ManagerID)

👉 Star schema with **Employee** as fact table and others as dimensions.

------------------------------------------------------------------------

# IV. 🧠 Design Thinking Process

1️⃣ Empathize → HR needs to reduce attrition and improve workforce
satisfaction\
2️⃣ Define → Identify key HR KPIs (turnover, satisfaction, engagement,
salary distribution)\
3️⃣ Ideate → Build a Power BI dashboard with drill-down by department,
manager, demographic factors\
4️⃣ Prototype & Review → Create HR Workforce Dashboard and refine based
on HR stakeholder feedback

------------------------------------------------------------------------

# V. ⚒️ Main Process

1️⃣ **Data Cleaning & Preprocessing (Power Query)**\
- Removed duplicates, null values, and invalid entries.\
- Transformed columns (split, merge, change data types) for consistency.

2️⃣ **Exploratory Data Analysis (EDA)**\
- Conducted summary statistics (Salary distribution, Absence days,
Engagement scores).\
- Identified patterns of employee retention and performance.

3️⃣ **DAX Analysis**

💡 Example DAX Measure:

``` dax
Employee Turnover Rate = 
VAR TotalEmployees = DISTINCTCOUNT(Employee[EmployeeID])
VAR TerminatedEmployees = 
    COUNTROWS(FILTER(Employee, NOT(ISBLANK(Employee[DateofTermination]))))
RETURN
    DIVIDE(TerminatedEmployees, TotalEmployees, 0)
```

✔️ Calculates the proportion of terminated employees vs. total
workforce.

4️⃣ **Power BI Visualization**\
- Built dashboards with KPIs: employee turnover, satisfaction
vs. engagement, salary distribution, absence trends.\
- Applied slicers (Department, Manager, Performance) for interactive
analysis.

------------------------------------------------------------------------

# VI. 📊 Key Insights & Visualizations

### 🔍 Dashboard Preview

#### 1️⃣ Executive Summary Dashboard

![Executive Summary](Screenshot-Executive-Summary.png)

-   **Observation**:
    -   Employees: **299**, Salary: **\$21M**, Turnover: **34.78%**\
    -   Female: **56.67%**, Male: **43.33%**\
    -   Production has highest turnover (**40.69%**)\
-   **Recommendation**: Focus retention initiatives in Production and
    Admin Offices.

------------------------------------------------------------------------

#### 2️⃣ Workforce Metrics by Dimension

![Workforce Database](Screenshot-Workforce-Database.png)

-   **Observation**:
    -   Executive Office: longest tenure (**13y**) but lowest
        satisfaction (**3.0**)\
    -   Recruitment heavily relies on Indeed & LinkedIn\
-   **Recommendation**: Diversify recruitment and improve executive
    engagement.

------------------------------------------------------------------------

#### 3️⃣ Data Model & Relationships

![Data Model](Screenshot-Data-Model.png)

-   **Observation**: Star schema centered on Employee table.\
-   **Recommendation**: Optimize with calculated measures (Turnover,
    Absenteeism, Engagement).

------------------------------------------------------------------------

# VII. 🔎 Final Conclusion & Recommendations

📌 Key Takeaways:\
✔️ Production & Admin Offices need urgent retention actions.\
✔️ Monitor satisfaction closely in Executive Office.\
✔️ Recruitment channels should be diversified.\
✔️ Power BI dashboards provide actionable insights for HR planning.
