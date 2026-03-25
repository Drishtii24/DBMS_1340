# Experiment_6

## 1. Display empno, ename, deptno from employee table. Instead of display department numbers display the related department name.      


## Query
```sql
     SELECT Empno, Ename, CASE Deptno 
     WHEN 10 THEN 'RESEARCH' 
     WHEN 20 THEN 'ACCOUNTING' 
     WHEN 30 THEN 'SALES' 
     WHEN 40 THEN 'OPERATIONS' 
     END AS Deptno FROM employee;
```

## Output
+-------+--------+------------+
| Empno | Ename  | Deptno     |
+-------+--------+------------+
|  7369 | SMITH  | ACCOUNTING |
|  7499 | ALLEN  | SALES      |
|  7521 | WARD   | SALES      |
|  7566 | JONES  | ACCOUNTING |
|  7654 | MARTIN | SALES      |
|  7698 | BLAKE  | SALES      |
|  7782 | CLARK  | ACCOUNTING |
|  7788 | SCOTT  | OPERATIONS |
|  7839 | KING   | ACCOUNTING |
|  7844 | TURNER | SALES      |
|  7876 | ADAMS  | ACCOUNTING |
|  7900 | JAMES  | SALES      |
|  7902 | FORD   | ACCOUNTING |
|  7934 | MILLER | RESEARCH   |
+-------+--------+------------+

## 2. Display your age in days.

## Query
```sql
     SELECT TIMESTAMPDIFF(DAY, '2006-05-24', CURDATE());
```

## Output
+---------------------------------------------+
| TIMESTAMPDIFF(DAY, '2006-05-24', CURDATE()) |
+---------------------------------------------+
|                                        7246 |
+---------------------------------------------+

## 3. Display your age in months.

## Query
```sql
     SELECT TIMESTAMPDIFF(MONTH, '2006-05-24', CURDATE());
```

## Output
+-----------------------------------------------+
| TIMESTAMPDIFF(MONTH, '2006-05-24', CURDATE()) |
+-----------------------------------------------+
|                                           238 |
+-----------------------------------------------+

## 4. Display the current date as 15th August Friday Nineteen Ninety-Seven.

## Query
```sql
     SELECT DATE_FORMAT(CURDATE(), "%D %M %W %Y");
```

## Output
+---------------------------------------+
| DATE_FORMAT(CURDATE(), "%D %M %W %Y") |
+---------------------------------------+
| 26th March Thursday 2026              |
+---------------------------------------+

## 5, 6. Display the following output for each row from employee table. Scott has joined the company on Wednesday 13th August Nineteen Ninety.

## Query
```sql
     SELECT CONCAT(Ename, " ", "has joined the company on"," ", DATE_FORMAT(Hiredate, "%W %D %M %Y")) FROM employee;
```

## Output
+-------------------------------------------------------------------------------------------+
| CONCAT(Ename, " ", "has joined the company on"," ", DATE_FORMAT(Hiredate, "%W %D %M %Y")) |
+-------------------------------------------------------------------------------------------+
| SMITH has joined the company on Wednesday 17th December 1980                              |
| ALLEN has joined the company on Friday 20th February 1981                                 |
| WARD has joined the company on Sunday 22nd February 1981                                  |
| JONES has joined the company on Thursday 2nd April 1981                                   |
| MARTIN has joined the company on Monday 28th September 1981                               |
| BLAKE has joined the company on Friday 1st May 1981                                       |
| CLARK has joined the company on Tuesday 9th June 1981                                     |
| SCOTT has joined the company on Thursday 9th December 1982                                |
| KING has joined the company on Tuesday 17th November 1981                                 |
| TURNER has joined the company on Tuesday 8th September 1981                               |
| ADAMS has joined the company on Wednesday 12th January 1983                               |
| JAMES has joined the company on Thursday 3rd December 1981                                |
| FORD has joined the company on Thursday 3rd December 1981                                 |
| MILLER has joined the company on Saturday 23rd January 1982                               |
+-------------------------------------------------------------------------------------------+

## 7. Find the date for nearest Saturday after current date. 

## Query
```sql
      SELECT DATE_ADD(CURDATE(), INTERVAL (5-WEEKDAY(CURDATE())+7)%7 DAY);
```

## Output
+--------------------------------------------------------------+
| DATE_ADD(CURDATE(), INTERVAL (5-WEEKDAY(CURDATE())+7)%7 DAY) |
+--------------------------------------------------------------+
| 2026-03-28                                                   |
+--------------------------------------------------------------+

## 8. Display current time.

## Query
```sql
     SELECT CURTIME();
```

## Output
+-----------+
| CURTIME() |
+-----------+
| 01:10:56  |
+-----------+

## 9. Display the date three months Before the current date.

## Query
```sql
      SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH);
```

## Output
+---------------------------------------+
| DATE_SUB(CURDATE(), INTERVAL 3 MONTH) |
+---------------------------------------+
| 2025-12-26                            |
+---------------------------------------+

## 10. Display those employees who joined in the company in the month of Dec.

## Query
```sql
     SELECT * FROM employee WHERE MONTHNAME(Hiredate) = 'December';
```

## Output
+-------+-------+---------+------+------------+------+------+--------+
| Empno | Ename | Job     | Mgr  | Hiredate   | Sal  | Comm | Deptno |
+-------+-------+---------+------+------------+------+------+--------+
|  7369 | SMITH | CLERK   | 7902 | 1980-12-17 |  968 | NULL |     20 |
|  7788 | SCOTT | ANALYST | 7566 | 1982-12-09 | 3630 | NULL |     40 |
|  7900 | JAMES | CLERK   | 7698 | 1981-12-03 | 1150 | NULL |     30 |
|  7902 | FORD  | ANALYST | 7566 | 1981-12-03 | 3630 | NULL |     20 |
+-------+-------+---------+------+------------+------+------+--------+

## 11. Display those employees whose first 2 characters from hire date -last 2 characters of salary.

## Query
```sql
     SELECT * FROM employee WHERE LEFT(Hiredate, 2) = RIGHT(Sal, 2);
```

## Output
Empty set (0.001 sec)

## 12. Display those employees whose 10% of salary is equal to the year of joining.

## Query
```sql
     SELECT * FROM employee WHERE (0.1*Sal) = YEAR(Hiredate);
```

## Output
Empty set (0.001 sec)

## 13, 14. Display those employees who joined the company before 15 of the months.

## Query
```sql
     SELECT * FROM employee WHERE DAY(Hiredate) < 15;
```

## Output
+-------+--------+----------+------+------------+------+------+--------+
| Empno | Ename  | Job      | Mgr  | Hiredate   | Sal  | Comm | Deptno |
+-------+--------+----------+------+------------+------+------+--------+
|  7566 | JONES  | MANAGER  | 7839 | 1981-04-02 | 3600 | NULL |     20 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 3449 | NULL |     30 |
|  7782 | CLARK  | MANAGER  | 7839 | 1981-06-09 | 2965 | NULL |     20 |
|  7788 | SCOTT  | ANALYST  | 7566 | 1982-12-09 | 3630 | NULL |     40 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK    | 7788 | 1983-01-12 | 1331 | NULL |     20 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 | 1150 | NULL |     30 |
|  7902 | FORD   | ANALYST  | 7566 | 1981-12-03 | 3630 | NULL |     20 |
+-------+--------+----------+------+------------+------+------+--------+

## 15. Display those employees who has joined before 15th of the month.

## Query
```sql
     SELECT * FROM employee WHERE DAY(Hiredate) =Deptno;
```

## Output
Empty set (0.001 sec)