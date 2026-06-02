# HR Analytics & Employee Attrition Analysis

## Project Overview

This project analyzes employee workforce data to identify attrition trends, workforce distribution, compensation impact, and employee retention drivers.

The analysis was performed using PostgreSQL, SQL, Python, Pandas, and Seaborn, with a focus on converting raw HR data into actionable business insights.

---

## Business Problem

Employee attrition can significantly impact organizational productivity and hiring costs.

The objective of this project was to:

* Measure overall employee attrition
* Identify departments with high turnover
* Identify job roles with high turnover
* Analyze the impact of compensation on attrition
* Evaluate the effect of work-life balance and job satisfaction
* Provide data-driven recommendations for employee retention

---

## Tools & Technologies

* PostgreSQL
* SQL
* Python
* Pandas
* Seaborn
* Matplotlib
* Jupyter Notebook
* VS Code

---

## Dataset Information

* Total Employees: 2,000
* Employee Attributes:

  * Employee ID
  * Age
  * Gender
  * Department
  * Job Role
  * Monthly Income
  * Attrition
  * Work-Life Balance
  * Job Satisfaction
  * Overtime
  * Years At Company

---

## Project Workflow

### 1. Data Extraction

* Imported HR dataset into PostgreSQL
* Created indexes for performance optimization
* Created analytics views for reporting

### 2. Data Cleaning

* Data type validation
* Null value analysis
* Duplicate record validation
* Data profiling using Pandas

### 3. Exploratory Data Analysis

* Department Distribution
* Job Role Distribution
* Gender Distribution
* Work-Life Balance Analysis
* Job Satisfaction Analysis
* Overtime Analysis
* Attrition Analysis

### 4. Visualization

Created visualizations using Seaborn and Matplotlib:

* Employee Distribution by Department
* Employee Distribution by Job Role
* Gender Distribution
* Work-Life Balance Distribution
* Job Satisfaction Distribution
* Overtime Distribution
* Attrition Rate by Department
* Attrition Rate by Job Role
* Income Quartile vs Attrition

---

## Key SQL Analysis

### Overall Attrition Rate

Calculated organization-wide employee attrition percentage.

### Department-wise Attrition

Identified departments with the highest turnover rates.

### Job Role Attrition Analysis

Measured attrition rates across all job roles.

### Overtime vs Attrition

Evaluated the relationship between overtime and employee turnover.

### Work-Life Balance vs Attrition

Measured the impact of work-life balance on retention.

### Job Satisfaction vs Attrition

Analyzed whether job satisfaction influences employee turnover.

### Income Quartile Analysis

Compared attrition rates across salary quartiles.

---

## Key Findings

### Overall Attrition Rate

* 18.10%

### Highest Attrition Department

* Research & Development (21.86%)

### Lowest Attrition Department

* Sales (13.83%)

### Highest Attrition Job Role

* Data Analyst (31.34%)

### Lowest Attrition Job Role

* Recruiter (10.59%)

### Work-Life Balance Insight

Employees with lower work-life balance exhibited higher attrition rates.

### Compensation Insight

Employees in lower income quartiles experienced higher attrition compared to higher income groups.

### Job Satisfaction Insight

Job satisfaction showed only a weak relationship with attrition.

---

## Business Recommendations

1. Improve retention programs within Research & Development teams.
2. Review compensation structures for high-attrition job roles.
3. Introduce initiatives to improve employee work-life balance.
4. Focus retention strategies on lower-income employee groups.
5. Monitor attrition metrics through periodic HR dashboards.

---

## Repository Structure

```text
HR-Analytics-Employee-Attrition-Analysis

├── README.md
├── HR Analytics Report.pdf
├── SQL_Queries.sql
├── load_hr_data.ipynb

├── data/
│   └── HR_Analytics_Database.csv

└── charts/
    ├── department_distribution.png
    ├── jobrole_distribution.png
    ├── attrition_by_department.png
    ├── attrition_by_jobrole.png
    └── income_quartile_attrition.png
```

---

## Author

Shivam Mishra

LinkedIn: [www.linkedin.com/in/shivam-mishra05](http://www.linkedin.com/in/shivam-mishra05)

GitHub: github.com/Shivam88Mishra
