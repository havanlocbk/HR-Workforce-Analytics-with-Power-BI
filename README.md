# 📊 HR Workforce Analytics with Power BI

*Applied Power Query, DAX, and Power BI to analyze HR workforce data,
enabling insights on employee retention, satisfaction, and performance
for data-driven HR decision-making.*

**Author:** Loc Ha\
**Date:** 2025 June

## 🛠 Tools Used

![Excel](https://img.shields.io/badge/Microsoft-Excel-217346?logo=microsoft-excel&logoColor=white)  ![Power BI](https://img.shields.io/badge/Microsoft-Power%20BI-F2C811?logo=powerbi&logoColor=black)  ![DAX](https://img.shields.io/badge/Language-DAX-0A66C2)  


------------------------------------------------------------------------

## 📑 Table of Contents

- [📌 I. Background & Overview](#-i-background--overview)  
- [📂 II. Dataset Description & Data Structure](#-ii-dataset-description--data-structure)  
- [🧠 III. Design Thinking Process](#-iii-design-thinking-process)  
- [⚒️ IV. Main Process](#-iv-main-process)  
- [📊 VI. Key Insights & Visualizations](#-vi-key-insights--visualizations)  
- [🔎 VI. Final Conclusion & Recommendations](#-vi-final-conclusion--recommendations)  


------------------------------------------------------------------------

# 📌 I. Background & Overview

### 🎯 Objective

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

# 📂 II. Dataset Description & Data Structure

### 📌 Data Source

-   **Source**: Internal file `HRDataset.xlsx`
-   **Size**: 300+ employee records, multiple lookup tables (Position,
    Department, Manager, MaritalStatus, Performance)
-   **Format**: `.xlsx`

### 📊 Data Structure

**Dataset Overview**  

| File Name        | Sheets Included                                                   | Rows  | Columns | Format |  
|------------------|-------------------------------------------------------------------|-------|---------|--------|  
| HRDataset.xlsx   | Employee, EmployeeNew, Position, Department, Manager, MaritalStatus, Performance | ~300+ | 20+     | .xlsx  |  

**Key Tables**  

| Table Name     | Key Columns (selected)                                                                 | Purpose                          |  
|----------------|-----------------------------------------------------------------------------------------|----------------------------------|  
| Employee       | EmployeeId, Name, ManagerID, PositionID, MaritalStatusID, PerformanceScoreID, Salary, EngagementScore, SatisfactionScore, AbsenceDays | Main fact table with workforce data |  
| Position       | PositionID, Position, DeptID                                                            | Job titles, linked to Department |  
| Department     | DeptID, Department                                                                      | Department info                  |  
| Manager        | ManagerID, ManagerName                                                                  | Manager lookup                   |  
| MaritalStatus  | MaritalStatusID, MaritalDesc                                                            | Marital status dimension         |  
| Performance    | PerfScoreID, PerformanceScore                                                           | Performance ratings              |  


------------------------------------------------------------------------

# 🧠 III. Design Thinking Process

1️⃣ **Empathize** → HR needs to reduce attrition and improve workforce
satisfaction\
2️⃣ **Define** → Identify key HR KPIs (turnover, satisfaction, engagement,
salary distribution)\
3️⃣ **Ideate** → Build a Power BI dashboard with drill-down by department,
manager, demographic factors\
4️⃣ **Prototype & Review** → Create HR Workforce Dashboard and refine based
on HR stakeholder feedback

------------------------------------------------------------------------

# ⚒️ IV. Main Process

1️⃣ **Data Cleaning & Preprocessing (Power Query)**
- Removed duplicates, null values, and invalid entries.
- Transformed columns (split, merge, change data types) for consistency.

2️⃣ **Exploratory Data Analysis (EDA)**
- Conducted summary statistics (Salary distribution, Absence days,
Engagement scores).
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

4️⃣ **Power BI Visualization**
- Built dashboards with KPIs: employee turnover, satisfaction
vs. engagement, salary distribution, absence trends.
- Applied slicers (Department, Manager, Performance) for interactive
analysis.

------------------------------------------------------------------------

#  📊 VI. Key Insights & Visualizations

### 🔍 Dashboard Preview

#### 1️⃣ Executive Summary Dashboard

<img width="2782" height="1551" alt="Screenshot 2025-09-06 134406" src="https://github.com/user-attachments/assets/faeedba6-7de2-45ac-81ba-9b4562c9330a" />

-   **Observation**:
    -   Employees: **299**, Salary: **\$21M**, Turnover: **34.78%**
    -   Female: **56.67%**, Male: **43.33%**
    -   Production has highest turnover (**40.69%**)
-   **Recommendation**: Focus retention initiatives in Production and
    Admin Offices and Software Engineering.
    
📌 **Usage & Insights**:  
- Overview of **headcount, salary, turnover, tenure, and absence**.  
- Highlights **gender ratio** and **department-level attrition**.  
- Helps HR quickly spot overall workforce trends before drilling deeper.      

------------------------------------------------------------------------

#### 2️⃣ Workforce Metrics by Dimension

<img width="2770" height="1549" alt="Screenshot 2025-09-06 134411" src="https://github.com/user-attachments/assets/cd6528af-5bfa-4631-a88b-5ac85254bfad" />


📌 **Usage & Insights**:  
- Filter workforce metrics by **department, manager, or recruitment source**.  
- Compare **turnover, satisfaction, engagement, tenure** across dimensions.  
- Supports targeted HR actions in departments with high attrition or low scores.  

👉 By interacting with slicers and filters, decision-makers can quickly identify areas of concern (e.g., high attrition in specific departments/managers) and take targeted actions.  

------------------------------------------------------------------------

#### 3️⃣ Data Model & Relationships

<img width="1607" height="927" alt="Screenshot 2025-09-06 134420" src="https://github.com/user-attachments/assets/52eb7277-5a9e-4172-9a9d-bd09565d4e09" />


👉 Star schema centered on Employee table.

------------------------------------------------------------------------

# 🔎 VI. Final Conclusion & Recommendations

📌 Key Takeaways:\
✔️ Production & Admin Offices need urgent retention actions.\
✔️ Monitor satisfaction closely in Executive Office.\
✔️ Recruitment channels should be diversified.\
✔️ Power BI dashboards provide actionable insights for HR planning.
