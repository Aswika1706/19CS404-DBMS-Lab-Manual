## Experiment 6: Joins
## AIM
To study and implement different types of joins.

## THEORY
SQL Joins are used to combine records from two or more tables based on a related column.

1. INNER JOIN
Returns records with matching values in both tables.

Syntax:
```
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;

```
2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

Syntax:
```
SELECT columns
FROM table1
LEFT JOIN table2

ON table1.column = table2.column;

```
3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

Syntax:
```
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;

```
4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

Syntax:
```
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;

```
## Question 1
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005

        Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001

Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12

```
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount",
    s.name ,
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```
Output:
<img width="1268" height="260" alt="Screenshot 2025-11-19 164902" src="https://github.com/user-attachments/assets/c584bef9-f017-49ba-b521-5f5e99fc50a6" />

## Question 2
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-01-01' and '2024-01-31'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date,discharge_date, doctor_id
```
SELECT p.*
FROM patients p
INNER JOIN appointments a ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';

```
Output:
<img width="1269" height="253" alt="Screenshot 2025-11-19 165324" src="https://github.com/user-attachments/assets/97d8390c-e915-4afd-acb0-5b4456f81cab" />

## Question 3
From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005

Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```
SELECT c.cust_name AS "Customer Name", 
       c.City AS "city", 
       s.name AS "Salesman", 
       s.commission
FROM customer c
INNER JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```

Output:
<img width="1161" height="636" alt="Screenshot 2025-11-19 170020" src="https://github.com/user-attachments/assets/a1fb379d-861a-455c-83c9-5c6cfdfbbf21" />

## Question 4
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column.

PATIENTS TABLE:

* ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id

* APPOINTMENTS TABLE:

* ATTRIBUTES - appointment_id, patient_id, doctor_id, appointment_date

```
SELECT p.first_name AS patient_name, 
       a.*
FROM patients p
INNER JOIN appointments a ON p.patient_id = a.patient_id;

```
Output:
<img width="1056" height="976" alt="Screenshot 2025-11-19 171249" src="https://github.com/user-attachments/assets/c614014b-5324-4296-a35f-dcb651e77473" />

## Question 5
From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.

Sample table: customer
```
SELECT c.cust_name AS "Customer Name",
       c.city AS "city",
       s.name AS "Salesman",
       s.commission AS "commission"
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```
Ouput:
<img width="1049" height="948" alt="Screenshot 2025-11-19 171452" src="https://github.com/user-attachments/assets/be63708b-7c13-41cc-abd8-dba04bcb2c39" />

## Question 6
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.
```
SELECT
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM
    salesman s
INNER JOIN
    customer c ON s.city = c.city;

```
Output:
<img width="1056" height="915" alt="Screenshot 2025-11-19 173038" src="https://github.com/user-attachments/assets/73f0c5eb-46e8-435a-ba78-b561f3ee36a8" />


## Question 7
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id.

SELECT c.cust_name,
       c.city,
       c.grade,
       s.name AS Salesman,
       s.city AS city
```       
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;

```
Output:
<img width="1056" height="890" alt="Screenshot 2025-11-19 173457" src="https://github.com/user-attachments/assets/736bfa62-cff0-469d-8de9-3719146447db" />

## Question 8
From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.
```
SELECT c.cust_name AS "Customer Name",
       c.city,
       s.name AS "Salesman",
       s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id;

```
Output:
<img width="1040" height="939" alt="Screenshot 2025-11-19 173618" src="https://github.com/user-attachments/assets/cc5955ca-8c3a-49bc-a14e-8a71ed7dc73f" />

## Question 9
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned.
```
SELECT o.ord_no,
       o.purch_amt,
       o.ord_date,
       c.cust_name,
       c.city AS customer_city,
       c.grade,
       s.name AS salesman_name,
       s.city AS salesman_city,
       s.commission
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
JOIN salesman s ON o.salesman_id = s.salesman_id;

```
Output:
<img width="1061" height="943" alt="Screenshot 2025-11-19 173917" src="https://github.com/user-attachments/assets/c2e4654a-de76-4654-b93b-107834938f31" />

## Question 10
Question 10
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.
```
SELECT p.first_name AS patient_name,
       d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d ON p.doctor_id = d.doctor_id
WHERE p.date_of_birth > '1990-01-01';

```
Output:
<img width="1053" height="515" alt="Screenshot 2025-11-19 174200" src="https://github.com/user-attachments/assets/ba001a6f-18bc-4fb0-b5d0-0cb861be5cc7" />

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
