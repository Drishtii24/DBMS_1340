# Experiment_4

## 1. Display the list of employees who have joined the company before 30th June 80 or after 31st Dec 81.

## Query
```sql
     SELECT * FROM employee WHERE Hiredate < "1980-06-30" or Hiredate > "1981-12-31";
```

## Output
+-------+--------+---------+------+------------+------+------+--------+
| Empno | Ename  | Job     | Mgr  | Hiredate   | Sal  | Comm | Deptno |
+-------+--------+---------+------+------------+------+------+--------+
|  7788 | SCOTT  | ANALYST | 7566 | 1982-12-09 | 3300 | NULL |     40 |
|  7876 | ADAMS  | CLERK   | 7788 | 1983-01-12 | 1210 | NULL |     20 |
|  7934 | MILLER | CLERK   | 7782 | 1982-01-23 | 1430 | NULL |     10 |
+-------+--------+---------+------+------------+------+------+--------+

## 2. Display the names of employees whose names have second alphabet A in their names.

## Query
```sql
     SELECT Ename FROM employee WHERE Ename LIKE "_A%";
```

## Output
+--------+
| Ename  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+

## 3. Display the names of employees whose name is exactly five characters in length

## Query
```sql
     SELECT Ename FROM employee WHERE Ename LIKE "_____";
```

## Output
+-------+
| Ename |
+-------+
| SMITH |
| ALLEN |
| JONES |
| BLAKE |
| CLARK |
| SCOTT |
| ADAMS |
| JAMES |
+-------+

## 4. Display the names of employees whose names have second alphabet A in their names.


## Query
```sql
     SELECT Ename FROM employee WHERE Ename LIKE "_A%";
```

## Output
+--------+
| Ename  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+

## 5. Display the names of employees who are not working as salesman or clerk or analyst.

## Query
```sql
     SELECT Ename FROM employee WHERE Job NOT IN ('Salesman', 'Clerk', 'Analyst');
```

## Output
+-------+
| Ename |
+-------+
| JONES |
| BLAKE |
| CLARK |
| KING  |
+-------+

## 6. Display the name of the employee along with their annual salary (sal*12). The name of the employee earning highest salary should appear first.

## Query
```sql
     SELECT Ename, (Sal*12) AS Annual_Sal FROM employee ORDER BY Annual_Sal DESC;
```

## Output
+--------+------------+
| Ename  | Annual_Sal |
+--------+------------+
| KING   |      66000 |
| SCOTT  |      39600 |
| FORD   |      39600 |
| JONES  |      39276 |
| BLAKE  |      37620 |
| CLARK  |      32340 |
| ALLEN  |      19200 |
| TURNER |      18000 |
| MILLER |      17160 |
| MARTIN |      15000 |
| WARD   |      15000 |
| ADAMS  |      14520 |
| JAMES  |      12540 |
| SMITH  |      10560 |
+--------+------------+

## 7. Display name, sal, hra, pf, da, totalsal for each employee. The output should be in the order of total sal, hra 15% of sal, da 10% of sal, pf 5% of sal. Total salary will be (sal*hra*da)-pf.

## Query
```sql
     SELECT Ename, (Sal*(0.15*Sal)*(0.1*Sal))-(0.5*Sal) AS Total_Sal,
     (0.15*Sal) AS hra, (0.1*Sal) AS da, (0.5*Sal) AS pf FROM employee;
```

## Output
+--------+----------------+--------+-------+--------+
| Ename  | Total_Sal      | hra    | da    | pf     |
+--------+----------------+--------+-------+--------+
| SMITH  |   10221640.000 | 132.00 |  88.0 |  440.0 |
| ALLEN  |   61439200.000 | 240.00 | 160.0 |  800.0 |
| WARD   |   29296250.000 | 187.50 | 125.0 |  625.0 |
| JONES  |  525929974.755 | 490.95 | 327.3 | 1636.5 |
| MARTIN |   29296250.000 | 187.50 | 125.0 |  625.0 |
| BLAKE  |  462170713.125 | 470.25 | 313.5 | 1567.5 |
| CLARK  |  293606438.125 | 404.25 | 269.5 | 1347.5 |
| SCOTT  |  539053350.000 | 495.00 | 330.0 | 1650.0 |
| KING   | 2495622250.000 | 825.00 | 550.0 | 2750.0 |
| TURNER |   50624250.000 | 225.00 | 150.0 |  750.0 |
| ADAMS  |   26572810.000 | 181.50 | 121.0 |  605.0 |
| JAMES  |   17116969.375 | 156.75 | 104.5 |  522.5 |
| FORD   |  539053350.000 | 495.00 | 330.0 | 1650.0 |
| MILLER |   43862390.000 | 214.50 | 143.0 |  715.0 |
+--------+----------------+--------+-------+--------+

## 8. Update the salary of each employee by 10% increment who are not eligible for commission.


## Query
```sql
      UPDATE employee SET Sal = 1.1*Sal WHERE Comm IS NULL;
```

## Output
Query OK, 10 rows affected (0.048 sec)
Rows matched: 10  Changed: 10  Warnings: 0

## 9. Display those employees whose salary is more than 3000 after.
giving 20% increment.

## Query
```sql
     SELECT * FROM employee WHERE (Sal*1.2) > 3000;
```

## Output
+-------+-------+-----------+------+------------+------+------+--------+
| Empno | Ename | Job       | Mgr  | Hiredate   | Sal  | Comm | Deptno |
+-------+-------+-----------+------+------------+------+------+--------+
|  7566 | JONES | MANAGER   | 7839 | 1981-04-02 | 3600 | NULL |     20 |
|  7698 | BLAKE | MANAGER   | 7839 | 1981-05-01 | 3449 | NULL |     30 |
|  7782 | CLARK | MANAGER   | 7839 | 1981-06-09 | 2965 | NULL |     20 |
|  7788 | SCOTT | ANALYST   | 7566 | 1982-12-09 | 3630 | NULL |     40 |
|  7839 | KING  | PRESIDENT | NULL | 1981-11-17 | 6050 | NULL |     20 |
|  7902 | FORD  | ANALYST   | 7566 | 1981-12-03 | 3630 | NULL |     20 |
+-------+-------+-----------+------+------------+------+------+--------+

## 10. Display those employees whose salary contains atleast 3 digits.

## Query
```sql
       SELECT * FROM employee WHERE Sal >= 100;
```

## Output
+-------+--------+-----------+------+------------+------+------+--------+
| Empno | Ename  | Job       | Mgr  | Hiredate   | Sal  | Comm | Deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  968 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 3600 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 3449 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2965 | NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3630 | NULL |     40 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 6050 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1331 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 | 1150 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3630 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1573 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+