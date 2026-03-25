# Experiment_5

## 1. Display the total number of employee working in the company.


## Query
```sql
      SELECT COUNT(*) FROM employee;
```

## Output
+----------+
| COUNT(*) |
+----------+
|       14 |
+----------+

## 2. Display the total salary being paid to all employees.

## Query
```sql
     SELECT SUM(Sal) AS Total_Sal FROM employee;
```

## Output
+-----------+
| Total_Sal |
+-----------+
|     33946 |
+-----------+

## 3. Display the maximum salary from employee table.

## Query
```sql
     SELECT MAX(Sal) AS Max_Sal FROM employee;
```

## Output
+---------+
| Max_Sal |
+---------+
|    6050 |
+---------+

## 4. Display the minimum salary from employee table.


## Query
```sql
     SELECT MIN(Sal) AS Min_Sal FROM employee;
```

## Output
+---------+
| Min_Sal |
+---------+
|     968 |
+---------+

## 5. Display the average salary from employee table.

## Query
```sql
     SELECT AVG(Sal) AS Avg_Sal FROM employee;
```

## Output
+-----------+
| Avg_Sal   |
+-----------+
| 2424.7143 |
+-----------+

## 6. Display the maximum salary being paid to clerk.

## Query
```sql
     SELECT MAX(Sal) FROM employee WHERE Job = 'Clerk';
```

## Output
+----------+
| MAX(Sal) |
+----------+
|     1573 |
+----------+

## 7. Display the maximum salary being paid in dept no 20.

## Query
```sql
     SELECT MAX(Sal) FROM employee WHERE Deptno = 20;
```

## Output
+----------+
| MAX(Sal) |
+----------+
|     6050 |
+----------+

## 8. Display the minimum salary paid to any salesman.


## Query
```sql
      SELECT MIN(Sal) FROM employee WHERE Job='Salesman';
```

## Output
+----------+
| MIN(Sal) |
+----------+
|     1250 |
+----------+

## 9. Display the average salary drawn by managers. giving 20% increment.

## Query
```sql
      SELECT AVG(Sal) AS Avg_Sal FROM employee WHERE Job='Manager';
```

## Output
+-----------+
| Avg_Sal   |
+-----------+
| 3338.0000 |
+-----------+

## 10. Display the total salary drawn by analyst working in dept no 40.

## Query
```sql
      SELECT SUM(Sal) AS Total_Sal FROM employee WHERE Job='Analyst' AND Deptno = 40;
```

## Output
+-----------+
| Total_Sal |
+-----------+
|      3630 |
+-----------+

## 11. Display the names of the employee in Uppercase.

## Query
```sql
       SELECT UPPER(Ename) FROM employee;
```

## Output
+--------------+
| UPPER(Ename) |
+--------------+
| SMITH        |
| ALLEN        |
| WARD         |
| JONES        |
| MARTIN       |
| BLAKE        |
| CLARK        |
| SCOTT        |
| KING         |
| TURNER       |
| ADAMS        |
| JAMES        |
| FORD         |
| MILLER       |
+--------------+

## 12. Display the names of the employee in Lowercase.

## Query
```sql
     SELECT LOWER(Ename) FROM employee;
```

## Output
+--------------+
| LOWER(Ename) |
+--------------+
| smith        |
| allen        |
| ward         |
| jones        |
| martin       |
| blake        |
| clark        |
| scott        |
| king         |
| turner       |
| adams        |
| james        |
| ford         |
| miller       |
+--------------+

## 13. Display the names of the employee in Proper case.

## Query
```sql
     SELECT CONCAT(UPPER(LEFT(Ename,1)), LOWER(SUBSTRING(Ename,2))) FROM employee;
```

## Output
+---------------------------------------------------------+
| CONCAT(UPPER(LEFT(Ename,1)), LOWER(SUBSTRING(Ename,2))) |
+---------------------------------------------------------+
| Smith                                                   |
| Allen                                                   |
| Ward                                                    |
| Jones                                                   |
| Martin                                                  |
| Blake                                                   |
| Clark                                                   |
| Scott                                                   |
| King                                                    |
| Turner                                                  |
| Adams                                                   |
| James                                                   |
| Ford                                                    |
| Miller                                                  |
+---------------------------------------------------------+

## 14. Display the length of Your name using appropriate function

## Query
```sql
     SELECT LENGTH('Drishti Chauhan') AS Name_Length;
```

## Output
+-------------+
| Name_Length |
+-------------+
|          15 |
+-------------+

## 15. Display the length of all the employee names.

## Query
```sql
     SELECT Ename, LENGTH(Ename) FROM employee;
```

## Output
+--------+---------------+
| Ename  | LENGTH(Ename) |
+--------+---------------+
| SMITH  |             5 |
| ALLEN  |             5 |
| WARD   |             4 |
| JONES  |             5 |
| MARTIN |             6 |
| BLAKE  |             5 |
| CLARK  |             5 |
| SCOTT  |             5 |
| KING   |             4 |
| TURNER |             6 |
| ADAMS  |             5 |
| JAMES  |             5 |
| FORD   |             4 |
| MILLER |             6 |
+--------+---------------+
