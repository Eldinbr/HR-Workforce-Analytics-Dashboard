# Project Title: **HR-Workforce-Analytics-Dashboard**

An interactive HR Workforce Analytics Dashboard built in Microsoft Power BI. This project analyses employee demographics, workforce composition, attrition, compensation, job roles, departments, and employee satisfaction to provide actionable HR insights.

The project transforms raw employee data into an interactive business intelligence solution using Power Query, data modelling, DAX, and Power BI visualisations.

The dashboard focuses on key HR metrics including employee headcount, attrition rate, average age, average salary, employee tenure, department performance, job-role distribution, and workforce demographics.

---

## Preview
<img width="913" height="460" alt="Screenshot 2026-08-25 at 11 52 29 AM" src="https://github.com/user-attachments/assets/656d6f1d-3dc1-4535-ad66-1d443a61a7d8" />


### Power BI Dashboard

Open the `.pbix` file from the `PowerBI` folder to explore the complete interactive dashboard.

---

## Table of Contents

* [Overview](#overview)
* [Business Questions](#business-questions)
* [Dataset](#dataset)
* [Data Preparation](#data-preparation)
* [Data Model](#data-model)
* [Technologies Used](#technologies-used)
* [DAX Measures](#dax-measures)
* [Installation](#installation)
* [Usage](#usage)
* [Analysis & Visualizations](#analysis--visualizations)
* [Key Insights](#key-insights)
* [Business Value](#business-value)
* [Conclusion](#conclusion)
* [Future Improvements](#future-improvements)
* [Credits](#credits)
* [License](#license)

---

# Overview

## Motivation

Organisations generate large amounts of employee data, but raw HR records alone do not provide an efficient way to understand workforce trends, employee retention, and organisational performance.

This project was created to transform employee data into an interactive Power BI dashboard that allows HR teams and management to monitor workforce composition, employee attrition, compensation, job roles, and employee demographics.

## Objective

The main objective of this project is to analyse workforce data and identify patterns that can support **data-driven HR and workforce planning decisions**.

The dashboard provides users with the ability to:

* Monitor total employee headcount
* Track employee attrition
* Analyse attrition trends
* Compare departments
* Analyse employee demographics
* Identify high-attrition job roles
* Analyse salary distribution
* Evaluate employee tenure
* Analyse employee satisfaction
* Compare workforce characteristics
* Identify areas requiring HR attention

## Learning Outcomes

While building this project, I developed practical experience in:

* Power Query data cleaning
* Data transformation
* Data modelling
* Star-schema design
* Creating relationships between tables
* DAX calculations
* HR KPI development
* Time and tenure analysis
* Interactive Power BI dashboard design
* Workforce analytics
* Business-focused data analysis
* Data storytelling

---

# Business Questions

The dashboard was designed to answer the following business questions:

1. What is the total employee headcount?
2. What percentage of employees have left the organisation?
3. Which departments have the highest attrition?
4. Which job roles have the highest attrition?
5. What is the average employee salary?
6. How does salary vary across departments and job roles?
7. What is the average employee tenure?
8. Which employee age groups are most represented?
9. How does attrition vary by age group?
10. How does attrition vary by gender?
11. Which departments have the highest employee satisfaction?
12. Is there a relationship between employee tenure and attrition?
13. Which job roles have high employee numbers but high attrition?
14. Which areas should HR focus on to improve employee retention?

---

# Dataset

## Dataset Information

* **Dataset Type:** Employee / HR Analytics Dataset
* **Records:** Employee-level records
* **Data Format:** CSV
* **Primary Business Areas:** Employees, Departments, Job Roles, Compensation, Attrition

## Features Included

The dataset contains information such as:

* Employee ID
* Age
* Gender
* Department
* Job Role
* Education
* Education Field
* Marital Status
* Job Level
* Monthly Income
* Years at Company
* Years in Current Role
* Years Since Last Promotion
* Years with Current Manager
* Job Satisfaction
* Environment Satisfaction
* Work-Life Balance
* OverTime
* Business Travel
* Attrition

---

# Data Preparation

Data preparation was performed using **Power Query**.

## Power Query Transformations

The following transformations were applied:

1. Imported the raw CSV dataset
2. Promoted the first row as headers
3. Changed column data types
4. Removed unnecessary columns
5. Removed duplicate employee records
6. Handled null and missing values
7. Standardised department and job-role names
8. Validated numerical fields
9. Created age-group categories
10. Created tenure categories
11. Standardised Yes/No fields
12. Prepared the data for analytical modelling
13. Loaded the cleaned dataset into Power BI

This process ensures that the dashboard is based on consistent and reliable employee data.

---

# Data Model

A **star-schema approach** was used to structure the Power BI data model.

## Fact Table

### FactEmployee

Contains employee-level information:

* Employee ID
* Age
* Department ID
* Job Role ID
* Salary
* Years at Company
* Job Satisfaction
* Attrition

## Dimension Tables

### DimDepartment

* Department ID
* Department Name

### DimJobRole

* Job Role ID
* Job Role
* Job Level

### DimEmployee

* Employee ID
* Gender
* Age Group
* Education
* Marital Status

### DimDate

* Date
* Year
* Quarter
* Month
* Month Number
* Year-Month

The dimension tables connect to the central employee fact table using appropriate relationships.

This structure improves:

* Data organisation
* Filtering
* DAX performance
* Dashboard scalability
* Analytical flexibility

---

# Technologies Used

## Tools & Platforms

* **Microsoft Power BI**
* **Power Query**
* **DAX**
* **Microsoft Excel / CSV**
* **Git**
* **GitHub**

## Skills Applied

* Data Cleaning
* Power Query
* Data Transformation
* Data Modelling
* Star Schema
* DAX
* KPI Development
* HR Analytics
* Workforce Analytics
* Data Visualisation
* Business Intelligence
* Dashboard Design
* Business Analysis
* Data Storytelling

---

# DAX Measures

Several DAX measures were created to calculate the key HR performance indicators.

## Total Employees

```DAX
Total Employees =
DISTINCTCOUNT(FactEmployee[Employee ID])
```

## Employees Left

```DAX
Employees Left =
CALCULATE(
    [Total Employees],
    FactEmployee[Attrition] = "Yes"
)
```

## Attrition Rate

```DAX
Attrition Rate =
DIVIDE(
    [Employees Left],
    [Total Employees],
    0
)
```

## Average Salary

```DAX
Average Salary =
AVERAGE(FactEmployee[Monthly Income])
```

## Average Age

```DAX
Average Age =
AVERAGE(FactEmployee[Age])
```

## Average Tenure

```DAX
Average Tenure =
AVERAGE(FactEmployee[Years at Company])
```

## Employees Currently Working

```DAX
Active Employees =
CALCULATE(
    [Total Employees],
    FactEmployee[Attrition] = "No"
)
```

## Attrition by Overtime

```DAX
Overtime Attrition Rate =
DIVIDE(
    CALCULATE(
        [Employees Left],
        FactEmployee[OverTime] = "Yes"
    ),
    CALCULATE(
        [Total Employees],
        FactEmployee[OverTime] = "Yes"
    ),
    0
)
```

---

# Installation

To explore this project locally:

```bash
# Clone the repository
git clone https://github.com/eldinbr/HR-Workforce-Analytics-Dashboard.git

# Navigate into the project directory
cd HR-Workforce-Analytics-Dashboard
```

Open the following file:

```text
PowerBI/HR_Workforce_Analytics.pbix
```

You will need **Microsoft Power BI Desktop** to open and interact with the `.pbix` file.

---

# Usage

Instructions for using the project:

1. Clone or download the repository
2. Open the Power BI `.pbix` file
3. Refresh the data if required
4. Navigate between dashboard pages
5. Use slicers to filter the data
6. Select charts to cross-filter other visuals
7. Analyse employees, departments, job roles, salaries, and attrition

## Interactive Filters

The dashboard includes filters for:

* Department
* Job Role
* Gender
* Age Group
* Education
* Job Level
* Marital Status
* Overtime
* Business Travel
* Attrition

---

# Analysis & Visualizations

## Dashboard 1 — HR Executive Overview

The Executive Overview provides a high-level summary of workforce performance.

### KPI Cards

The dashboard displays:

* Total Employees
* Active Employees
* Employees Left
* Attrition Rate
* Average Salary
* Average Tenure

### Visualizations

**1. Employee Headcount by Department**

A bar chart comparing employee numbers across departments.

**2. Attrition by Department**

A column chart showing employee attrition across departments.

**3. Attrition Rate by Job Role**

A ranked chart identifying job roles with higher attrition rates.

**4. Employee Demographics**

Charts showing employee distribution by:

* Age Group
* Gender
* Education
* Marital Status

**5. Salary Distribution**

A visual showing salary distribution across the workforce.

---

# Dashboard 2 — Attrition Analysis

The Attrition Analysis page focuses specifically on employee retention.

### Visualizations

* Attrition Rate by Department
* Attrition Rate by Job Role
* Attrition by Age Group
* Attrition by Gender
* Attrition by Overtime
* Attrition by Job Level
* Attrition by Tenure
* Attrition by Business Travel

### Key Questions

This page helps identify:

* Which departments experience the highest attrition?
* Which job roles have the highest employee turnover?
* Does overtime relate to employee attrition?
* Which age groups have higher attrition?
* Does employee tenure influence retention?
* Which job levels experience the greatest turnover?

---

# Dashboard 3 — Workforce & Compensation Analysis

This page analyses workforce composition and employee compensation.

### Visualizations

* Average Salary by Department
* Average Salary by Job Role
* Employee Count by Job Level
* Salary by Age Group
* Salary vs Years at Company
* Employees by Education
* Employees by Gender
* Employees by Job Role

### Key Questions

The analysis helps determine:

* Which departments have the highest average salaries?
* Which job roles have the highest compensation?
* How does salary change with employee tenure?
* Which job roles contain the largest workforce?
* How is the workforce distributed across job levels?

---

# Key Insights

The dashboard can be used to identify several important HR patterns.

## Workforce Composition

Employee demographics reveal the composition of the workforce across departments, job roles, age groups, education levels, and job levels.

## Attrition

Attrition analysis identifies departments, roles, and employee groups that may require additional retention attention.

## Compensation

Salary analysis highlights differences in compensation between departments, job roles, job levels, and employee groups.

## Employee Tenure

Tenure analysis helps identify workforce groups with shorter or longer periods of service.

## Overtime

Comparing overtime status with attrition provides an additional perspective for understanding potential employee retention challenges.

## Job Roles

Job-role analysis identifies positions with large employee populations as well as roles that may experience comparatively high turnover.

## Employee Satisfaction

Satisfaction metrics can be analysed alongside attrition and department information to identify potential workforce-management areas requiring further investigation.

---

# Business Value

The dashboard can support HR and management decisions in several areas.

## Workforce Planning

Identify workforce distribution across departments and job roles.

## Employee Retention

Identify departments and employee groups that may require retention strategies.

## Compensation Planning

Compare salary levels across departments, roles, and job levels.

## HR Reporting

Provide HR teams with an interactive alternative to manually prepared workforce reports.

## Management Reporting

Give leadership a consolidated view of workforce KPIs and trends.

## Employee Experience

Use satisfaction and workforce metrics to identify areas that may require further HR investigation.

---

# Conclusion

The **HR Workforce Analytics Dashboard** transforms employee-level data into an interactive business intelligence solution using **Power BI, Power Query, DAX, and data modelling**.

The project demonstrates how HR data can be cleaned, transformed, modelled, analysed, and presented through an interactive dashboard.

By combining workforce KPIs, attrition analysis, demographic analysis, compensation metrics, job-role analysis, and employee satisfaction indicators, the dashboard provides a comprehensive view of workforce performance.

The project demonstrates practical skills relevant to:

* **Data Analyst**
* **HR Data Analyst**
* **HR Reporting Analyst**
* **People Analytics Analyst**
* **BI Analyst**
* **Junior Power BI Developer**

---

# Future Improvements

Future versions of the dashboard could include:

* Employee attrition prediction
* Employee lifetime value analysis
* RFM-style employee segmentation
* Recruitment funnel analysis
* Absence analysis
* Training and development analysis
* Promotion analysis
* Compensation benchmarking
* Workforce forecasting
* Employee engagement analysis
* Automated data refresh
* Power BI Service deployment
* Row-level security
* Drill-through employee analysis
* Mobile dashboard optimisation

---

# Credits

* **Developer:** Eldin
* **Dataset:** HR Employee Dataset
* **Data Preparation:** Power Query
* **Data Analysis:** DAX
* **Visualisation:** Microsoft Power BI
* **Version Control:** GitHub

---

# License

This project is licensed under the **MIT License** – feel free to use and modify it.

---

**Thanks for visiting! 🚀**
