# Experiment_3

## 1. List all employees and jobs in Department 30 in descending order by salary.

## Query
```sql
      SELECT Ename, Job FROM employee WHERE Deptno = 30 ORDER BY Sal DESC;
```

## Output
+--------+----------+
| Ename  | Job      |
+--------+----------+
| BLAKE  | MANAGER  |
| ALLEN  | SALESMAN |
| TURNER | SALESMAN |
| WARD   | SALESMAN |
| MARTIN | SALESMAN |
| JAMES  | CLERK    |
+--------+----------+

## 2. List job and Department Number of employees whose name are five letters long begin with “A” and end with “N”.

## Query
```sql
     SELECT Job, Deptno FROM employee WHERE Ename LIKE "A___N";
```

## Output
+----------+--------+
| Job      | Deptno |
+----------+--------+
| SALESMAN |     30 |
+----------+--------+

## 3. Display the name of employees whose name start with alphabet S.

## Query
```sql
      SELECT Ename FROM employee WHERE Ename LIKE "S%";
```

## Output
+-------+
| Ename |
+-------+
| SMITH |
| SCOTT |
+-------+

## 4. Display the names of employees whose name ends with alphabet S.

## Query
```sql
      SELECT Ename FROM employee WHERE Ename LIKE "%S";
```

## Output
+-------+
| Ename |
+-------+
| JONES |
| ADAMS |
| JAMES |
+-------+

## 5. Display the names of employees working in department number 10 or 20 or 40 or employees working as clerks, salesman or analyst.

## Query
```sql
     SELECT Ename FROM employee WHERE Deptno IN (10, 20, 40) OR Job IN ('Clerk', 'Salesman', 'Analyst');
```

## Output
+--------+
| Ename  |
+--------+
| SMITH  |
| ALLEN  |
| WARD   |
| JONES  |
| MARTIN |
| CLARK  |
| SCOTT  |
| KING   |
| TURNER |
| ADAMS  |
| JAMES  |
| FORD   |
| MILLER |
+--------+

## 6. Display employee number and names for employees who earn commission.

## Query
```sql
     SELECT Empno, Ename FROM employee WHERE Comm > 0 AND Comm IS NOT NULL;
```

## Output
+-------+--------+
| Empno | Ename  |
+-------+--------+
|  7499 | ALLEN  |
|  7521 | WARD   |
|  7654 | MARTIN |
+-------+--------+

## 7. Display employee number and total salary for each employee.

## Query
```sql
      SELECT Empno, Sal + IfNULL(Comm, 0) AS Total_Sal FROM employee;
```

## Output
+-------+-----------+
| Empno | Total_Sal |
+-------+-----------+
|  7369 |       880 |
|  7499 |      1900 |
|  7521 |      1550 |
|  7566 |      3273 |
|  7654 |      2650 |
|  7698 |      3135 |
|  7782 |      2695 |
|  7788 |      3300 |
|  7839 |      5500 |
|  7844 |      1500 |
|  7876 |      1210 |
|  7900 |      1045 |
|  7902 |      3300 |
|  7934 |      1430 |
+-------+-----------+

## 8. Display employee number and annual salary for each employee.

## Query
```sql
      SELECT Empno, Sal*12 AS Annual_Sal FROM employee;
```

## Output
+-------+------------+
| Empno | Annual_Sal |
+-------+------------+
|  7369 |      10560 |
|  7499 |      19200 |
|  7521 |      15000 |
|  7566 |      39276 |
|  7654 |      15000 |
|  7698 |      37620 |
|  7782 |      32340 |
|  7788 |      39600 |
|  7839 |      66000 |
|  7844 |      18000 |
|  7876 |      14520 |
|  7900 |      12540 |
|  7902 |      39600 |
|  7934 |      17160 |
+-------+------------+

## 9. Display the names of all employees working as clerks and drawing a salary more than 3,000.

## Query
```sql
     SELECT Ename FROM employee WHERE Job = 'Clerk' AND Sal > 3000;
```

## Output
Empty set (0.001 sec)

## 10.  Display the names of employees who are working as clerk, salesman or analyst and drawing a salary more than 3,000.

## Query
```sql
      SELECT Ename FROM employee WHERE Job IN ('Clerk', 'Salesman', 'Analyst') AND Sal > 3000;
```

## Output
+-------+
| Ename |
+-------+
| SCOTT |
| FORD  |
+-------+