# Experiment_2

## 1. List all distinct job in Employee.

## Query
```sql
      SELECT DISTINCT(job) FROM employee;
```

## Output
+-----------+
| job       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
+-----------+

## 2. List all information about employee in Department Number 30.

## Query
```sql
     SELECT * FROM employee WHERE Deptno = 30;
```

## Output
+-------+--------+----------+------+------------+------+------+--------+
| Empno | Ename  | Job      | Mgr  | Hiredate   | Sal  | Comm | Deptno |
+-------+--------+----------+------+------------+------+------+--------+
|  7499 | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 3135 | NULL |     30 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 | 1045 | NULL |     30 |
+-------+--------+----------+------+------------+------+------+--------+

## 3. Find all department number with department names greater than 20.

## Query
```sql
      SELECT Deptno, Dname FROM department WHERE Deptno > 30;
```

## Output
+--------+------------+
| Deptno | Dname      |
+--------+------------+
|     40 | OPERATIONS |
+--------+------------+

## 4. Find all information about all the managers as well as the clerks in department 30.

## Query
```sql
      SELECT * FROM employee WHERE Deptno = 30 AND Job in ("Manager", "Clerk");
```

## Output
+-------+-------+---------+------+------------+------+------+--------+
| Empno | Ename | Job     | Mgr  | Hiredate   | Sal  | Comm | Deptno |
+-------+-------+---------+------+------------+------+------+--------+
|  7698 | BLAKE | MANAGER | 7839 | 1981-05-01 | 3135 | NULL |     30 |
|  7900 | JAMES | CLERK   | 7698 | 1981-12-03 | 1045 | NULL |     30 |
+-------+-------+---------+------+------------+------+------+--------+

## 5. List the Employee name, Employee numbers and department of all clerks.

## Query
```sql
     SELECT Ename, Empno, Deptno FROM employee WHERE Job = "Clerk";
```

## Output
+--------+-------+--------+
| Ename  | Empno | Deptno |
+--------+-------+--------+
| SMITH  |  7369 |     20 |
| ADAMS  |  7876 |     20 |
| JAMES  |  7900 |     30 |
| MILLER |  7934 |     10 |
+--------+-------+--------+

## 6. Find all managers not in department 30.

## Query
```sql
     SELECT * FROM employee WHERE Job='Manager' AND Deptno != 30;
```

## Output
+-------+-------+---------+------+------------+------+------+--------+
| Empno | Ename | Job     | Mgr  | Hiredate   | Sal  | Comm | Deptno |
+-------+-------+---------+------+------------+------+------+--------+
|  7566 | JONES | MANAGER | 7839 | 1981-04-02 | 3273 | NULL |     20 |
|  7782 | CLARK | MANAGER | 7839 | 1981-06-09 | 2695 | NULL |     20 |
+-------+-------+---------+------+------------+------+------+--------+

## 7. List information about all Employees in department 10 who are not manager or clerks.

## Query
```sql
     SELECT * FROM employee WHERE Deptno = 10 AND Job NOT IN ('Manager', 'Clerk');
```

## Output
Empty set (0.001 sec)

## 8. Find Employees and jobs earning between 1200 and 1400.

## Query
```sql
     SELECT Ename, Job FROM employee WHERE Sal BETWEEN 1200 AND 1400;
```

## Output
+--------+----------+
| Ename  | Job      |
+--------+----------+
| WARD   | SALESMAN |
| MARTIN | SALESMAN |
| ADAMS  | CLERK    |
+--------+----------+

## 9. List Name and Department Number of employee who are clerks, analyst or salesman.

## Query
```sql
     SELECT Ename, Deptno FROM employee WHERE Job IN ('Clerk', 'Analyst', 'Salesman');
```

## Output
+--------+--------+
| Ename  | Deptno |
+--------+--------+
| SMITH  |     20 |
| ALLEN  |     30 |
| WARD   |     30 |
| MARTIN |     30 |
| SCOTT  |     40 |
| TURNER |     30 |
| ADAMS  |     20 |
| JAMES  |     30 |
| FORD   |     20 |
| MILLER |     10 |
+--------+--------+

## 10. List Name and Department Number of employee whose names began with M.

## Query
```sql
      SELECT Ename, Deptno FROM employee WHERE Ename LIKE 'M%';
```

## Output
+--------+--------+
| Ename  | Deptno |
+--------+--------+
| MARTIN |     30 |
| MILLER |     10 |
+--------+--------+