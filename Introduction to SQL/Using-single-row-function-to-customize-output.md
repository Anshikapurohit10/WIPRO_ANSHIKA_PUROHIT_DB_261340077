# Built-in Functions – Hands-on Assignment

## 1. Write a query to display the current date. Label the column Date.

```sql
SELECT SYSDATE AS "Date"
FROM dual;
```

---

## 2. The HR department needs a report to display the employee number, last name, salary, and salary increased by 15.5% (expressed as a whole number) for each employee. Label the column New Salary.

```sql
SELECT employee_id,
       last_name,
       salary,
       ROUND(salary * 1.155) AS "New Salary"
FROM employees;
```

---

## 3. Modify the previous query to add a column alias that subtracts the old salary from the new salary. Label the column Increase.

```sql
SELECT employee_id,
       last_name,
       salary,
       ROUND(salary * 1.155) AS "New Salary",
       ROUND(salary * 1.155) - salary AS "Increase"
FROM employees;
```

---

## 4. Write a query that displays the ename (with the first letter uppercase and all other letters lowercase) and the length of the ename for all employees whose name starts with the letters J, A, or M. Give each column an appropriate label. Sort the results by the employees' enames.

```sql
SELECT INITCAP(last_name) AS Name,
       LENGTH(last_name) AS Length
FROM employees
WHERE UPPER(SUBSTR(last_name,1,1)) IN ('J','A','M')
ORDER BY last_name;
```

---

## 5. Rewrite the query so that the user is prompted to enter a letter that starts the last name.

```sql
SELECT last_name
FROM employees
WHERE UPPER(last_name) LIKE UPPER('&letter') || '%';
```

---

## 6. The HR department wants to find the length of employment for each employee.

```sql
SELECT last_name,
       MONTHS_BETWEEN(SYSDATE, hire_date) AS MONTHS_WORKED
FROM employees
ORDER BY MONTHS_WORKED;
```

---

## 7. Create a report that produces the following for each employee:
**earns monthly but wants Salary × 3**. Label the column Dream Salaries.

```sql
SELECT last_name || ' earns ' || salary ||
       ' monthly but wants ' || salary*3 AS "Dream Salaries"
FROM employees;
```

---

## 8. Create a query to display the last name and salary for all employees. Format the salary to be 15 characters long, left-padded with the $ symbol. Label the column SALARY.

```sql
SELECT last_name,
       LPAD(salary,15,'$') AS SALARY
FROM employees;
```

---

## 9. Display each employee's last name, hire date, and salary review date (first Monday after six months of service). Label the column REVIEW.

```sql
SELECT last_name,
       hire_date,
       NEXT_DAY(ADD_MONTHS(hire_date,6),'MONDAY') AS REVIEW
FROM employees;
```

---

## 10. Display the last name, hire date, and day of the week on which the employee started. Label the column DAY.

```sql
SELECT last_name,
       hire_date,
       TO_CHAR(hire_date,'Day') AS DAY
FROM employees
ORDER BY TO_CHAR(hire_date,'D');
```

---

## 11. Create a query that displays the employees' last names and commission amounts. If an employee does not earn commission, show "No Commission." Label the column COMM.

```sql
SELECT last_name,
       NVL(TO_CHAR(commission_pct),'No Commission') AS COMM
FROM employees;
```

---

## 12. Display the first eight characters of the employees' last names and indicate their salaries with asterisks.

```sql
SELECT RPAD(SUBSTR(last_name,1,8),8,' ') AS LAST_NAME,
       RPAD('*',TRUNC(salary/1000),'*') AS EMPLOYEES_AND_THEIR_SALARIES
FROM employees
ORDER BY salary DESC;
```

---

## 13. Using the DECODE function, display the grade of all employees based on JOB_ID.

```sql
SELECT last_name,
       job_id,
       DECODE(job_id,
              'AD_PRES','A',
              'ST_MAN','B',
              'SA_REP','C',
              'ST_CLERK','D',
              '0') AS GRADE
FROM employees;
```

---

## 14. Rewrite the previous statement using the CASE syntax.

```sql
SELECT last_name,
       job_id,
       CASE job_id
           WHEN 'AD_PRES' THEN 'A'
           WHEN 'ST_MAN' THEN 'B'
           WHEN 'SA_REP' THEN 'C'
           WHEN 'ST_CLERK' THEN 'D'
           ELSE '0'
       END AS GRADE
FROM employees;
```
