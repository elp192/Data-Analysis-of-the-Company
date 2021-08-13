# Data Analysis of Large Company 
## Overview of Project
### Background
The database consists of six .csv files ([department](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/departments.csv), [dept_emp](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/dept_emp.csv), [dept_manager](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/dept_manager.csv), [employees](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/employees.csv), [salaries](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/salaries.csv), and [titles](https://github.com/elp192/Pewlett-Hackard-Analysis/blob/7c562f62adee8a1efa754a05779b5df5a674cec0/Data/titles.csv)) which provide information about department number, department name, employee number, the date of hire, the birth date of employees, salaries, and so on. QuickDBD is used to visually demonstrate the relational database (Figure 1). 
### Purpose
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

## Result
In the following created tables determining the eligible employees for retirement and participation in the mentorship program are demonstrated.

**Retirement titles table** (Figure 2):<br>
- This table is created by merging the employees and title tables (using ```INNER JOIN ``` statement).<br>
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
- ```DISTINCT_ON ``` statement is used to uniquely select the employees. 
- The table is sorted (using ```ORDER BY ``` statement) by emp_no (ascending order) and to_date (descending order). So, the table shows the most recent titles of employees.
<p img align="center" width="100%">
<img width="250" alt="unique_titles" src="https://user-images.githubusercontent.com/85843401/129268047-aa27cd24-33ff-4af7-b4c0-5646f4193276.png">
<img width="200" alt="unique_titles_SQLcode" src="https://user-images.githubusercontent.com/85843401/129374663-aedf3ce8-62c0-4a2f-b094-3e86bf538643.png">
<figcaption>Figure 3: Demonstration of left) unique titles table and right) SQL code. </figcaption></figure/> 
<p align="center">
</p>

**Retiring titles table** (Figure 4):<br>
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

**Mentorship eligibility table** (Figure 5):<br>
- This table represents the number of employees who will be retired soon and are eligible for mentoring new employees in the mentorship program.
- This table is created using merging employees, titles, and dept_emp tables (using ```INNER JOIN``` statement). Also, duplication is eliminated using the ```DISTINCT ON``` statement, and the table is filtered by birth date (using ```WHERE``` statement).
- 1549 (number of rows) employees were born in 1965 and are eligible to be leaders in the mentorship program. 

<p img align="center" width="100%">
<img width="300" alt="mentorship eligibility" src="https://user-images.githubusercontent.com/85843401/129268843-13ab9c3c-92ba-406c-9e63-f219547f9ae0.png">
<img width="200" alt="mentorship_eligibility tale_SQLcode" src="https://user-images.githubusercontent.com/85843401/129375731-e2559f60-0d78-4475-93a9-2c0bf7364b12.png">
<figcaption>Figure 5: Demonstration of Left) mentorship eligibility table and Right) SQL code.  
</figcaption></figure/> 
<p align="center">
</p>

## Summary
In this section, two important questions will be discussed: what is the number of roles that need to be filled and whether we have qualified members for leading the next generation of employees or not. In doing so, vacant job titles and related departments are determined. Also, eligible employees for mentorship are counted and can be compared to the number of vacant jobs.

**Vacant job title and department table** (Figure 6):<br>
- This table shows that 39 job titles in different departments need to be filled in the next few years.<br>
 - The total number of jobs in different departments that need to be filled is 36619.<br>
 - The highest number of employees that should be hired is in the development department and for senior engineer positions (6834 employees).<br>
 - The lowest number of employees that need to be hired is in the research and sale department and for manager positions (1 employee).

<p img align="center" width="100%">
 <img width="200" alt="vacant_job_title_department" src="https://user-images.githubusercontent.com/85843401/129385824-51da27e7-024e-41a8-b16a-b6379b2d6103.png">
<img width="200" alt="vacant_job_title_department_SQLcode" src="https://user-images.githubusercontent.com/85843401/129385835-3520ba2e-2dc8-45e9-b9c4-239bcf8165ed.png">
<figcaption>Figure 6: Demonstration of left) vacant job title and department table and right) SQL code.</figcaption></figure/> 
<p align="center">

**Number of eligible employees for mentorship program table** (Figure 7): <br>
- This table is created using the information obtained from the mentorship eligibility table.
- The total number of qualified employees for leading the next generation is 1549. Out of this number, 779 employees have higher positions (i.e., manager, senior, and technical leader) which be necessary to guide the new employees.
- The highest number of qualified employees for mentorship is related to senior staff positions (397 employees).<br>


  
 <p img align="center" width="100%">
<img width="150" alt="counted_eligible_mentorship" src="https://user-images.githubusercontent.com/85843401/129405788-ea56dd8f-54fc-445a-9118-5b889d25ea2d.png">
<img width="200" alt="counted_eligible_mentorship_SQLcode" src="https://user-images.githubusercontent.com/85843401/129405793-8b5b08ab-7d1b-4971-8c6c-8167473cd015.png">
<figcaption>Figure 7: Demonstration of left) number of eligible employees for mentorship program table and right) SQL code.</figcaption></figure/> 
<p align="center">
