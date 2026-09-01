Employee Management System – SQL

📌 Project Overview

The Employee Management System is a SQL-based database project designed to manage and analyze employee-related information such as departments, salaries, bonuses, qualifications, leaves, and payroll.
The project demonstrates how relational database concepts and SQL queries can be used to answer practical HR and business questions.

🎯 Objectives

Manage employee information in a structured database.
Maintain job department and role details.
Track salary, annual compensation, and bonuses.
Store employee qualifications.
Track employee leave records.
Maintain payroll information.
Analyze workforce, salary, payroll, qualification, and leave patterns.
Generate HR-focused insights such as salary review, promotion, retention, and burnout-risk indicators.

🛠️ Technologies Used
SQL
Relational Database Management System
SQL DDL (CREATE TABLE)
SQL DML (INSERT)
SQL Joins
Aggregate Functions
GROUP BY
ORDER BY

CASE
Window Functions
Foreign Keys and Constraints

🗂️ Database Structure
The database contains the following six tables:
Table
Purpose
JobDepartment
Stores department, job role, description, and salary range
SalaryBonus
Stores salary, annual salary, and bonus information
Employee
Stores employee personal and job information
Qualification
Stores employee qualifications and job requirements
Leaves
Stores employee leave records and reasons
Payroll
Stores payroll transactions and total salary amounts

🔗 Table Relationships
JobDepartment
      │
      ├──────────────> SalaryBonus
      │
      └──────────────> Employee
                           │
                           ├──────────────> Qualification
                           │
                           ├──────────────> Leaves
                           │
                           └──────────────> Payroll
                                            │
                          SalaryBonus ──────┤
                          JobDepartment ────┤
                          Leaves ───────────┘

Main Relationships
Employee.Job_ID → JobDepartment.Job_ID

SalaryBonus.Job_ID → JobDepartment.Job_ID

Qualification.Emp_ID → Employee.emp_ID

Leaves.emp_ID → Employee.emp_ID

Payroll.emp_ID → Employee.emp_ID

Payroll.job_ID → JobDepartment.job_ID

Payroll.salary_ID → SalaryBonus.salary_ID

Payroll.leave_ID → Leaves.leave_ID

The database also uses foreign-key actions such as CASCADE and SET NULL to control related records when referenced records are updated or deleted.

📊 Database Tables

1. JobDepartment

Stores available departments and job roles.

Key columns:

Job_ID – Primary Key

jobdept – Department

name – Job role

description – Job description

salaryrange – Salary range

Example departments include:

IT

HR

Finance

Sales

Marketing

2. SalaryBonus

Stores salary and bonus information for job roles.

Key columns:

salary_ID – Primary Key

Job_ID – Foreign Key

amount – Monthly salary

annual – Annual salary

bonus – Bonus amount

3. Employee

Stores employee details.

Key columns:

emp_ID – Primary Key

firstname

lastname

gender

age

contact_add

emp_email

emp_pass

Job_ID – Foreign Key

The employee email is defined as UNIQUE.

4. Qualification

Stores employee qualifications and role requirements.

Key columns:

QualID – Primary Key

Emp_ID – Foreign Key

Position

Requirements

Date_In

5. Leaves

Stores employee leave records.

Key columns:

leave_ID – Primary Key

emp_ID – Foreign Key

date

reason

6. Payroll

Stores payroll processing information.

Key columns:

payroll_ID – Primary Key

emp_ID – Foreign Key

job_ID – Foreign Key

salary_ID – Foreign Key

leave_ID – Foreign Key

date

report

total_amount

🔍 Key SQL Analysis

The project includes queries that answer practical business questions.

Workforce Analysis

Total number of employees.

Department with the highest number of employees.

Salary & Compensation Analysis

Department with the highest total monthly salary allocation.

Top 3 employees by total compensation (salary + bonus).

Average payroll amount by department.

Departments consuming the highest payroll budget.

Payroll per employee.

Qualification Analysis

Most common employee qualification.

Comparison of employee qualifications with their current job roles and salary levels.

Leave Analysis

Most common reasons employees take leave.

Leave patterns used as an indicator in the burnout-risk analysis.

Employee Compensation Analysis

The project uses a SQL window function to compare employee salary against the average salary for the same job role.

Employees are classified as:

Above Average

Below Average

Average

HR Decision Analysis

The project also produces an HR action category based on payroll amount and leave count:

Promotion Candidate

Salary Review

Retention Monitor

📈 Business Insights Supported by the Project

The SQL analysis can help HR or management understand:

Which departments have the largest workforce.

Which departments require the highest payroll budget.

Which employees have the highest total compensation.

Which qualifications are most common.

Common employee leave reasons.

Average payroll across departments.

Salary differences among employees performing similar roles.

Potential employee burnout indicators based on leave and compensation patterns.

Employees who may require promotion, salary review, or retention attention.

Workforce efficiency using payroll, employee count, and leave records.

▶️ How to Run

Step 1: Open a SQL Environment

Open a MySQL-compatible SQL environment such as:

MySQL Workbench

MySQL Command Line

Another compatible SQL client

Step 2: Create/Select the Database

The SQL script begins by selecting:

USE UNIVERSITY;

Make sure the UNIVERSITY database exists in your SQL environment before running the script.

Step 3: Run the SQL Script

Execute the SQL file:

EMPLOYEE MANAGEMENT SYSTEM - SQL.sql

The script creates the required tables, inserts sample records, and executes analytical queries.

Step 4: Explore the Results

Run the analytical queries individually to examine:

Employee count

Department workforce

Salary allocation

Compensation

Qualifications

Leaves

Payroll

Burnout risk

Salary status

HR actions

📁 Project Structure

Employee-Management-System/
│
├── EMPLOYEE MANAGEMENT SYSTEM - SQL.sql
└── README.md

🧠 SQL Concepts Demonstrated

This project demonstrates practical usage of:

CREATE TABLE

INSERT INTO

SELECT

JOIN

LEFT JOIN

GROUP BY

ORDER BY

COUNT()

SUM()

AVG()

ROUND()

CONCAT()

CASE

LIMIT

Foreign Keys

Primary Keys

Unique Constraints

ON DELETE CASCADE

ON DELETE SET NULL

ON UPDATE CASCADE

Window Functions

AVG() OVER(PARTITION BY ...)

💡 Example Business Questions

The project is designed around questions such as:

Which department has the highest number of employees?

Which department has the highest salary allocation?

Who are the top 3 highest-paid employees based on salary + bonus?

What qualification is most common?

What are the most common leave reasons?

Which department has the highest average payroll?

Which departments consume the highest payroll budget?

Which employees may show burnout indicators?

Are employee qualifications aligned with their roles and salary levels?

Who may be overcompensated or undercompensated compared with others in similar roles?

Which departments have better workforce efficiency?

Which employees should HR prioritize for promotion, salary review, or retention?

⚠️ Notes

This is an academic/demo SQL project using sample employee data. The emp_pass column contains sample password values in plain text; a production employee system should not store passwords this way.

The burnout-risk and HR-action classifications in this project are rule-based SQL indicators, not validated HR or medical assessments.

👩‍💻 Author

Swetha

Engineering Student
SQL / Database Project
