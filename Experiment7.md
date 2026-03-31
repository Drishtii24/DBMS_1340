# Experiment_7

## 1. Compute the no. of days remaining in this year.


## Query
```sql
     SELECT DATEDIFF(LAST_DAY(MAKEDATE(YEAR(CURDATE()), 12*31)), CURDATE()) 
     -> AS days_remaining;
```

## Output
| days_remaining |
|----------------|
|            306 |

## 2. Find the highest and lowest salaries and the difference between of them.

## Query
```sql
     SELECT MAX(Sal) AS highest, 
     -> MIN(Sal) AS lowest, 
     -> (MAX(Sal) - MIN(Sal)) 
     -> AS difference 
     -> FROM employee;
```

## Output
| highest | lowest | difference |
|---------|--------|------------|
|    6050 |    968 |       5082 |

## 3. List employee whose commission is greater than 25 % of their salaries.

## Query
```sql
     SELECT ename, sal, comm 
     -> FROM employee 
     -> WHERE comm > (0.25 * sal);
```

## Output
| ename  | sal  | comm |
|--------|------|------|
| MARTIN | 1250 | 1400 |

## 4. Make a query that displays salary in dollar format.

## Query
```sql
    SELECT ename, CONCAT('$', FORMAT(sal, 2)) 
    -> AS salary_in_dollars 
    -> FROM employee;
```

## Output
| ename  | salary_in_dollars |
|--------|-------------------|
| SMITH  | $968.00           |
| ALLEN  | $1,600.00         |
| WARD   | $1,250.00         |
| JONES  | $3,600.00         |
| MARTIN | $1,250.00         |
| BLAKE  | $3,449.00         |
| CLARK  | $2,965.00         |
| SCOTT  | $3,630.00         |
| KING   | $6,050.00         |
| TURNER | $1,500.00         |
| ADAMS  | $1,331.00         |
| JAMES  | $1,150.00         |
| FORD   | $3,630.00         |
| MILLER | $1,573.00         |

## 5. Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job for all departments, giving each column an appropriate heading.

## Query
```sql
     SELECT job,
     -> SUM(CASE WHEN deptno=10 THEN sal END) AS dept10,
     -> SUM(CASE WHEN deptno=20 THEN sal END) AS dept20,
     -> SUM(CASE WHEN deptno=30 THEN sal END) AS dept30,
     -> SUM(sal) AS total
     -> FROM employee
     -> GROUP BY job;
```

## Output
| job       | dept10 | dept20 | dept30 | total |
|-----------|--------|--------|--------|-------|
| ANALYST   |   NULL |   3630 |   NULL |  7260 |
| CLERK     |   1573 |   2299 |   1150 |  5022 |
| MANAGER   |   NULL |   6565 |   3449 | 10014 |
| PRESIDENT |   NULL |   6050 |   NULL |  6050 |
| SALESMAN  |   NULL |   NULL |   5600 |  5600 |

## 6. Query that will display the total no of employees, and of that total the number who were hired in 1980,1981,1982 and 1983. Give appropriate column heading

## Query
```sql
     SELECT COUNT(*) AS total,
     -> SUM(CASE WHEN YEAR(hiredate)=1980 THEN 1 ELSE 0 END) AS hired_1980,
     -> SUM(CASE WHEN YEAR(hiredate)=1981 THEN 1 ELSE 0 END) AS hired_1981,
     -> SUM(CASE WHEN YEAR(hiredate)=1982 THEN 1 ELSE 0 END) AS hired_1982,
     -> SUM(CASE WHEN YEAR(hiredate)=1983 THEN 1 ELSE 0 END) AS hired_1983
     -> FROM employee;
```

## Output
| total | hired_1980 | hired_1981 | hired_1982 | hired_1983 |
|-------|------------|------------|------------|------------|
|    14 |          1 |         10 |          2 |          1 |

## 7. Query to get the last Sunday of Any Month.

## Query
```sql
     SELECT DATE_SUB(LAST_DAY(CURDATE()),
     -> INTERVAL (WEEKDAY(LAST_DAY(CURDATE())) + 1) DAY) AS last_sunday;
```

## Output
| last_sunday |
|-------------|
| 2026-03-29  |

## 8. Display department numbers and total number of employees working in each department.

## Query
```sql
     SELECT deptno, COUNT(*) AS total_employees
     -> FROM employee
     -> GROUP BY deptno;
```

## Output
| deptno | total_employees |
|--------|-----------------|
|     10 |               1 |
|     20 |               6 |
|     30 |               6 |
|     40 |               1 |

## 9. Display the various jobs and total number of employees within each job group.

## Query
```sql
     SELECT job, COUNT(*) AS total_employees
     -> FROM employee
     -> GROUP BY job;
```

## Output
| job       | total_employees |
|-----------|-----------------|
| ANALYST   |               2 |
| CLERK     |               4 |
| MANAGER   |               3 |
| PRESIDENT |               1 |
| SALESMAN  |               4 |

## 10. Display the depart numbers and total salary for each department.

## Query
```sql
     SELECT deptno, SUM(sal) AS total_salary
     -> FROM employee
     -> GROUP BY deptno;
```

## Output
| deptno | total_salary |
|--------|--------------|
|     10 |         1573 |
|     20 |        18544 |
|     30 |        10199 |
|     40 |         3630 |
