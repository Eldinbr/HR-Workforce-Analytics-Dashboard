# Power BI Build Guide

## Recommended model
FactEmployee -> DimEmployee (Employee ID)
FactEmployee -> DimDepartment (Department ID)
FactEmployee -> DimJobRole (Job Role ID)
FactEmployee[Hire Date] -> DimDate[Date]

Use single-direction, one-to-many relationships from dimensions to FactEmployee.

## Dashboard pages
1. Executive Overview
   - KPI cards: Total Employees, Active Employees, Employees Left, Attrition Rate, Average Salary, Average Tenure
   - Headcount by Department
   - Attrition Rate by Department
   - Employee distribution by Age Group
   - Sales/R&D/HR workforce split
   - Top job roles by headcount

2. Attrition Analysis
   - Attrition Rate by Department
   - Attrition Rate by Job Role
   - Attrition by Age Group
   - Attrition by Gender
   - Attrition by Overtime
   - Attrition by Job Level
   - Attrition by Tenure Group
   - Attrition by Business Travel

3. Workforce & Compensation
   - Average Salary by Department
   - Average Salary by Job Role
   - Salary vs Years at Company
   - Headcount by Job Level
   - Workforce by Education
   - Workforce by Gender
   - Workforce by Job Role

## Suggested slicers
Department, Job Role, Gender, Age Group, Job Level, Overtime,
Business Travel, Education Field, Marital Status.

## Note
The supplied dataset is synthetic and intended for portfolio/learning use.
