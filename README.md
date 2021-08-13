# Data Analysis of Large Company 
# Overview of Project
## Background
The database consists of six .csv files ([department](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/departments.csv), [dept_emp](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/dept_emp.csv), [dept_manager](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/dept_manager.csv), [employees](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/employees.csv), [salaries](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/salaries.csv), and [titles](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/titles.csv)) which provide information about department number, department name, employee number, the date of hire, the birth date of employees, salaries, and so on. QuickDBD is used to visually demonstrate the relational database (Figure 1). 
## Purpose
This project aims to provide insight into the retirement aspect of employees in the Pewlett-Hackard company. In this large company, many employees are going to be retired in the next few years. So, data analysis is necessary to do thoughtful planning for the future. For example, we want to determine the following items:<br> 
- The number of employees per job title who will be retired,<br>
- Infomration about eligible employees for the mentorship program,<br> 
- The number of job titles and departments that need to be filled, and <br>
- The number of qualified future retired employees who can lead the next generation of employees.<br>

PostgreSQL is used as an object-relational database system, and PgAdmin is utilized as a management tool for PostgreSQL.

<p img align="center" width="100%">
<img width="200" alt="DB" src="https://user-images.githubusercontent.com/85843401/129275876-ae455f66-0823-45e4-995d-4b400e075d16.png">
<figcaption>Figure 1: Entry-relationship diagram (ERD) </figcaption></figure/> 
<p align="center">
</p>

# Result
In the following created tables determining the eligible employees for retirement and participation in the mentorship program are demonstrated.

**Retirement titles table** (Figure 2):<br>
- This table is created by merging the employees and title tables (using INNER JOIN).<br>
- This table provides the employees' information who will be retired in the upcoming years (employees born between 1-1-1952 and 31-12-1955).<br>
- This table consists of 133777 rows and 6 columns.<br>
- Some employees have more than one job title because of changing the job position during years.

<p img align="center" width="100%">
<img width="300" alt="retirement_titles" src="https://user-images.githubusercontent.com/85843401/129267909-e535edcd-0bd0-4bb0-b239-6cd1cd05466a.png">
<img width="200" alt="retirement_titles_SQLcode" src="https://user-images.githubusercontent.com/85843401/129361791-4f31fb0d-2ce3-4e19-971e-3446575f8544.png">
<figcaption>Figure 2: Demonstration of left) retirement titles table and right) SQL code.</figcaption></figure/>
<p align="center">
</p>


