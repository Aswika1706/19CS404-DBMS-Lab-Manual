## Experiment 4: Aggregate Functions, Group By and Having Clause
## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY
Aggregate Functions
These perform calculations on a set of values and return a single value.

* MIN() – Smallest value
* MAX() – Largest value
* COUNT() – Number of rows
* SUM() – Total of values
* AVG() – Average of values
Syntax:+++ 
```
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
## GROUP BY
Groups records with the same values in specified columns.
Syntax:
```
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;

```
## HAVING
Filters the grouped records based on aggregate conditions. 
Syntax:
```
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;

```
## Question 1
How many appointments are scheduled for each patient?
```
select PatientID, COUNT(*) AS TotalAppointments
from Appointments group by PatientID;

```
Output:
<img width="1262" height="748" alt="Screenshot 2025-11-18 115731" src="https://github.com/user-attachments/assets/9e27acd9-1ace-415f-8f3b-d2f56f257915" />

## Question 2
What is the most common diagnosis among patients?
```
select Diagnosis, COUNT(*) AS DiagnosisCount
from MedicalRecords
group by Diagnosis
order by DiagnosisCount DESC LIMIT 1;

```
Output:
<img width="1062" height="387" alt="Screenshot 2025-11-18 222945" src="https://github.com/user-attachments/assets/8e3893cb-81c4-44ca-a60c-6df720983a5d" />

## Question 3
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.
```
select SUM(inventory) AS total 
from Fruits
where unit = 'LB';
```
Output:
<img width="719" height="467" alt="Screenshot 2025-11-18 223038" src="https://github.com/user-attachments/assets/382c29bb-1c62-4780-8ddc-3c47cea98fd8" />

## Question 4
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.
```
select AVG(purch_amt) as 'AVERAGE'
from orders;

```
Output:
<img width="591" height="474" alt="Screenshot 2025-11-18 225114" src="https://github.com/user-attachments/assets/371a7d07-7d21-4cae-954c-629580ed78eb" />

## Question 5
Write a SQL query to find the total number of unique cities in the customer table?
```
select COUNT(DISTINCT city) AS
unique_cities
from customer;

```
Output:
<img width="574" height="487" alt="Screenshot 2025-11-18 225737" src="https://github.com/user-attachments/assets/5b906cb7-c282-4bc3-ba08-4821388b2131" />

## Question 6
Write a SQL query to find the customer with longest name?
```
select name,LENGTH(name) as length
from customer order by length DESC limit 1

```
Output:
<img width="957" height="471" alt="Screenshot 2025-11-18 230009" src="https://github.com/user-attachments/assets/0eed2a8b-3925-436c-a247-528c3d26e2c6" />

## Question 7
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.
```
select jdate, SUM(workhour) 
from employee1
group by jdate
having SUM(workhour) > 40;

```
Output:
<img width="827" height="569" alt="Screenshot 2025-11-18 230314" src="https://github.com/user-attachments/assets/debf42a9-8953-4f7e-8ed2-7de391df18c7" />

## Question 8
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.
```
select city, SUM(income ) AS Income
from employee
group by city
having SUM(income) > 200000;

```
Ouput:
<img width="818" height="751" alt="Screenshot 2025-11-18 230528" src="https://github.com/user-attachments/assets/300a4b25-5c29-4c56-acff-945aea52beea" />

## Question 9
Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.
```
select occupation, SUM(workhour)
from employee1
group by occupation
having SUM(workhour) > 20;

```
Output:
<img width="845" height="656" alt="Screenshot 2025-11-18 231944" src="https://github.com/user-attachments/assets/812208bd-0a5f-4a6c-a790-082381fda2ce" />

## Question 10
What is the count of male and female patients?
```
SELECT Gender , COUNT(*) as TotalPatients from Patients
Group by Gender;

```
Output:
<img width="1110" height="652" alt="Screenshot 2025-11-18 232048" src="https://github.com/user-attachments/assets/19b9e9e3-37a5-488a-8b14-f398b730e0d7" />

## Result:
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
