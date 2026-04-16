# Experiment_8

## 1. Display all employees with their dept name.


## Query
```sql
     SELECT Empno, Ename, Dname
    -> FROM Employee e JOIN Department d
    -> ON e.Deptno = d.Deptno;
```

## Output
| Empno | Ename  | Dname      |
|-------|--------|------------|
|  7934 | MILLER | RESEARCH   |
|  7369 | SMITH  | ACCOUNTING |
|  7566 | JONES  | ACCOUNTING |
|  7782 | CLARK  | ACCOUNTING |
|  7839 | KING   | ACCOUNTING |
|  7876 | ADAMS  | ACCOUNTING |
|  7902 | FORD   | ACCOUNTING |
|  7499 | ALLEN  | SALES      |
|  7521 | WARD   | SALES      |
|  7654 | MARTIN | SALES      |
|  7698 | BLAKE  | SALES      |
|  7844 | TURNER | SALES      |
|  7900 | JAMES  | SALES      |
|  7788 | SCOTT  | OPERATIONS |


## 2. Display those employees whose manager names is jones, and also display their manager name.

## Query
```sql
     SELECT e.Ename AS Employee, m.Ename AS Manager
    -> FROM Employee e JOIN Employee m
    -> ON e.MGR = m.Empno
    -> WHERE m.Ename = 'Jones';
```

## Output
| Employee | Manager |
|----------|---------|
| SCOTT    | JONES   |
| FORD     | JONES   |

## 3. Display employee name, his job, his dept name, his manager name, his grade and make out of an under department wise.

## Query
```sql
     SELECT e.Ename, e.Job, d.Dname,
    -> m.Ename AS Manager, s.grade
    -> FROM Employee e
    -> LEFT JOIN Employee m ON e.Mgr = m.Empno
    -> JOIN Department d ON e.Deptno = d.Deptno
    -> JOIN Salgrade s ON e.Sal BETWEEN s.LOSAL AND s.HISAL
    -> ORDER BY d.Deptno;
```

## Output
| Ename  | Job       | Dname      | Manager | grade |
|--------|-----------|------------|---------|-------|
| MILLER | CLERK     | RESEARCH   | CLARK   | C     |
| SMITH  | CLERK     | ACCOUNTING | FORD    | A     |
| CLARK  | MANAGER   | ACCOUNTING | KING    | D     |
| JONES  | MANAGER   | ACCOUNTING | KING    | E     |
| ADAMS  | CLERK     | ACCOUNTING | SCOTT   | B     |
| KING   | PRESIDENT | ACCOUNTING | NULL    | E     |
| FORD   | ANALYST   | ACCOUNTING | JONES   | E     |
| MARTIN | SALESMAN  | SALES      | BLAKE   | B     |
| BLAKE  | MANAGER   | SALES      | KING    | E     |
| JAMES  | CLERK     | SALES      | BLAKE   | A     |
| ALLEN  | SALESMAN  | SALES      | BLAKE   | C     |
| WARD   | SALESMAN  | SALES      | BLAKE   | B     |
| TURNER | SALESMAN  | SALES      | BLAKE   | C     |
| SCOTT  | ANALYST   | OPERATIONS | JONES   | E     |

## 4. List out all the employees name, job, and salary grade and department name for everyone in the company except ‘clerk’. Sort on salary display the highest salary.

## Query
```sql
    SELECT e.Ename, e.Job, d.Dname, s.grade, e.Sal
    -> FROM Employee e
    -> JOIN Department d ON e.Deptno = d.Deptno
    -> JOIN Salgrade s ON e.Sal BETWEEN s.LOSAL AND s.HISAL
    -> WHERE e.Job <> 'Clerk'
    -> ORDER BY e.Sal DESC;
```

## Output
| Ename  | Job       | Dname      | grade | Sal  |
|--------|-----------|------------|-------|------|
| KING   | PRESIDENT | ACCOUNTING | E     | 6050 |
| SCOTT  | ANALYST   | OPERATIONS | E     | 3630 |
| FORD   | ANALYST   | ACCOUNTING | E     | 3630 |
| JONES  | MANAGER   | ACCOUNTING | E     | 3600 |
| BLAKE  | MANAGER   | SALES      | E     | 3449 |
| CLARK  | MANAGER   | ACCOUNTING | D     | 2965 |
| ALLEN  | SALESMAN  | SALES      | C     | 1600 |
| TURNER | SALESMAN  | SALES      | C     | 1500 |
| MARTIN | SALESMAN  | SALES      | B     | 1250 |
| WARD   | SALESMAN  | SALES      | B     | 1250 |

## 5. Display employee name, his job and his manager. Display also employees who are without manager.

## Query
```sql
     SELECT e.Ename, e.Job,
    -> NVL(m.Ename, 'No Manager') AS Manager
    -> FROM Employee e
    -> LEFT JOIN Employee m
    -> ON e.Mgr = m.Empno;
```

## Output
| Ename  | Job       | Manager    |
|--------|-----------|------------|
| SMITH  | CLERK     | FORD       |
| ALLEN  | SALESMAN  | BLAKE      |
| WARD   | SALESMAN  | BLAKE      |
| JONES  | MANAGER   | KING       |
| MARTIN | SALESMAN  | BLAKE      |
| BLAKE  | MANAGER   | KING       |
| CLARK  | MANAGER   | KING       |
| SCOTT  | ANALYST   | JONES      |
| KING   | PRESIDENT | No Manager |
| TURNER | SALESMAN  | BLAKE      |
| ADAMS  | CLERK     | SCOTT      |
| JAMES  | CLERK     | BLAKE      |
| FORD   | ANALYST   | JONES      |
| MILLER | CLERK     | CLARK      |

## 6. List the employee name, job, annual salary, deptno, dept name and grade who earn 36000 a year or who are not clerks.


## Query
```sql
     SELECT e.Ename, e.Job, e.Sal*12 AS Annual_Sal,
    -> d.Deptno, d.Dname, s.Grade
    -> FROM Employee e
    -> JOIN Department d ON e.Deptno = d.Deptno
    -> JOIN Salgrade s ON e.Sal BETWEEN s.LOSAL AND s.HISAL
    -> WHERE e.Sal*12 = 36000 or e.Job <> 'Clerk';
```

## Output
| Ename  | Job       | Annual_Sal | Deptno | Dname      | Grade |
|--------|-----------|------------|--------|------------|-------|
| WARD   | SALESMAN  |      15000 |     30 | SALES      | B     |
| MARTIN | SALESMAN  |      15000 |     30 | SALES      | B     |
| ALLEN  | SALESMAN  |      19200 |     30 | SALES      | C     |
| TURNER | SALESMAN  |      18000 |     30 | SALES      | C     |
| CLARK  | MANAGER   |      35580 |     20 | ACCOUNTING | D     |
| JONES  | MANAGER   |      43200 |     20 | ACCOUNTING | E     |
| KING   | PRESIDENT |      72600 |     20 | ACCOUNTING | E     |
| FORD   | ANALYST   |      43560 |     20 | ACCOUNTING | E     |
| BLAKE  | MANAGER   |      41388 |     30 | SALES      | E     |
| SCOTT  | ANALYST   |      43560 |     40 | OPERATIONS | E     |

## 7. List ename, job, annual sal, deptno, dname and grade who earn 30000 per year and who are not clerks.


## Query
```sql
      SELECT e.Ename, e.Job, e.Sal*12 AS Annual_Sal,
    -> d.Deptno, d.Dname, s.Grade
    -> FROM Employee e
    -> JOIN Department d ON e.Deptno = d.Deptno
    -> JOIN Salgrade s ON e.Sal BETWEEN s.LOSAL AND s.HISAL
    -> WHERE e.Sal*12 = 30000 AND e.Job <> 'Clerk';
```

## Output
Empty set (0.001 sec)

## 8. List out all employees by name and number along with their manager’s name and number also display ‘no manager’ who has no manager.

## Query
```sql
     SELECT e.Empno, e.Ename,
    -> NVL(m.Empno, 0) AS Mgr_no,
    -> NVL(m.Ename, 'No Manager') AS Mgr_name
    -> FROM Employee e
    -> LEFT JOIN Employee m ON e.Mgr = m.Empno;     
```

## Output
| Empno | Ename  | Mgr_no | Mgr_name   |
|-------|--------|--------|------------|
|  7369 | SMITH  |   7902 | FORD       |
|  7499 | ALLEN  |   7698 | BLAKE      |
|  7521 | WARD   |   7698 | BLAKE      |
|  7566 | JONES  |   7839 | KING       |
|  7654 | MARTIN |   7698 | BLAKE      |
|  7698 | BLAKE  |   7839 | KING       |
|  7782 | CLARK  |   7839 | KING       |
|  7788 | SCOTT  |   7566 | JONES      |
|  7839 | KING   |      0 | No Manager |
|  7844 | TURNER |   7698 | BLAKE      |
|  7876 | ADAMS  |   7788 | SCOTT      |
|  7900 | JAMES  |   7698 | BLAKE      |
|  7902 | FORD   |   7566 | JONES      |
|  7934 | MILLER |   7782 | CLARK      |

## 9. Select dept name, dept no and sum of sal

## Query
```sql
     SELECT d.Dname, d.Deptno, SUM(e.Sal) AS Total_Sal
    -> FROM Employee e
    -> JOIN Department d ON e.Deptno = d.Deptno
    -> GROUP BY d.Dname, d.Deptno;
```

## Output
| Dname      | Deptno | Total_Sal |
|------------|--------|-----------|
| ACCOUNTING |     20 |     18544 |
| OPERATIONS |     40 |      3630 |
| RESEARCH   |     10 |      1573 |
| SALES      |     30 |     10199 |

## 10. Display employee number, name and location of the department in which he is working.

## Query
```sql
     SELECT e.Empno, e.Ename, d.Loc
    -> FROM Employee e
    -> JOIN Department d
    -> ON e.Deptno = d.Deptno;     
```

## Output
| Empno | Ename  | Loc      |
|-------|--------|----------|
|  7934 | MILLER | NEW YORK |
|  7369 | SMITH  | DALLAS   |
|  7566 | JONES  | DALLAS   |
|  7782 | CLARK  | DALLAS   |
|  7839 | KING   | DALLAS   |
|  7876 | ADAMS  | DALLAS   |
|  7902 | FORD   | DALLAS   |
|  7499 | ALLEN  | CHICAGO  |
|  7521 | WARD   | CHICAGO  |
|  7654 | MARTIN | CHICAGO  |
|  7698 | BLAKE  | CHICAGO  |
|  7844 | TURNER | CHICAGO  |
|  7900 | JAMES  | CHICAGO  |
|  7788 | SCOTT  | BOSTON   |

## 11.  Display employee name and department name for each employee.

## Query
```sql
     SELECT e.Ename, d.Dname
    -> FROM Employee e
    -> JOIN Department d
    -> ON e.Deptno = d.Deptno;
```

## Output
| ename  | dname      |
|--------|------------|
| MILLER | RESEARCH   |
| SMITH  | ACCOUNTING |
| JONES  | ACCOUNTING |
| CLARK  | ACCOUNTING |
| KING   | ACCOUNTING |
| ADAMS  | ACCOUNTING |
| FORD   | ACCOUNTING |
| ALLEN  | SALES      |
| WARD   | SALES      |
| MARTIN | SALES      |
| BLAKE  | SALES      |
| TURNER | SALES      |
| JAMES  | SALES      |
| SCOTT  | OPERATIONS |
