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
- This table is created by merging the employees and title tables (using INNER JOIN statement).<br>
- This table provides the employees' information who will be retired in the upcoming years (employees born between 1-1-1952 and 31-12-1955).<br>
- This table consists of 133777 rows and 6 columns.<br>
- Some employees have more than one job title because of changing the job position during years.

<p img align="center" width="100%">
<img width="300" alt="retirement_titles" src="https://user-images.githubusercontent.com/85843401/129267909-e535edcd-0bd0-4bb0-b239-6cd1cd05466a.png">
<img width="200" alt="retirement_titles_SQLcode" src="https://user-images.githubusercontent.com/85843401/129361791-4f31fb0d-2ce3-4e19-971e-3446575f8544.png">
<figcaption>Figure 2: Demonstration of left) retirement titles table and right) SQL code.</figcaption></figure/>
<p align="center">
</p>

**Unique titles table** (Figure 3):<br>
To eliminate the duplicates rows that result from changing job position of some employees, unique titles table is created. 
- In this table the real number of employees who will be ready for retirement is dmeonstrated.
- The rows (number of retiring employees) is reduced to 90,398 rows.
- DISTINCT_ON statement is used to uniquely select the employees. 
- The table is sorted (using ORDER BY statement) by emp_no (ascending order) and to_date (descending order). So, the table shows the most recent titles of employees.
<p img align="center" width="100%">
<img width="250" alt="unique_titles" src="https://user-images.githubusercontent.com/85843401/129268047-aa27cd24-33ff-4af7-b4c0-5646f4193276.png">
<img width="200" alt="unique_titles_SQLcode" src="https://user-images.githubusercontent.com/85843401/129374663-aedf3ce8-62c0-4a2f-b094-3e86bf538643.png">
<figcaption>Figure 3: Demonstration of left) unique titles table and right) SQL code. </figcaption></figure/> 
<p align="center">
</p>

**Retiring titles table** (Figure 4)<br>
- In this table, the job titles that their employees will be retired are determined. Also, the number of employees for each title is counted. 
- 7 job titles are recognized in this company that their employees will be retired soon.
- The two highest number of future retired employees are the senior engineer and senior staff (29414 and 28254 employees).
- Only 2 positions with manager title will be vacant in the next few years.
<p img align="center" width="100%">
<img width="120" alt="retiring_titles" src="https://user-images.githubusercontent.com/85843401/129268355-19c45b79-bb5b-4529-b89f-0ed85da81723.png">
<img width="200" alt="retiring_titles_SQLcode" src="https://user-images.githubusercontent.com/85843401/129375080-e23e0513-90c8-442b-8f30-b4349337b9a3.png">
<figcaption>Figure 4: Demonstration of Left) retiring titles table and Right) SQL code. </figcaption></figure/> 
<p align="center">
</p>



