# Experiment_1

## 1. Create Employee_master table with data using Employee table.

## Query
```sql
     CREATE TABLE employee_master AS SELECT * FROM employee;
```

## Output
+-------+--------+-----------+------+------------+------+------+--------+
| Empno | Ename  | Job       | Mgr  | Hiredate   | Sal  | Comm | Deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  880 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 3273 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 3135 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2695 | NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3300 | NULL |     40 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5500 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1210 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 | 1045 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3300 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1430 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+

## 2. Delete all record into Employee_master whose DeptNo is 10.

## Query
```sql
     DELETE FROM employee_master WHERE Deptno = 10;
```

## Output
+-------+--------+-----------+------+------------+------+------+--------+
| Empno | Ename  | Job       | Mgr  | Hiredate   | Sal  | Comm | Deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  880 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 3273 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 3135 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2695 | NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3300 | NULL |     40 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5500 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1210 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 | 1045 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3300 | NULL |     20 |
+-------+--------+-----------+------+------------+------+------+--------+

## 3. Update 10% in his salary of DEPTNO 20 into Employee_Master.

## Query
```sql
     UPDATE employee_master SET Sal = Sal + (0.1*Sal) WHERE Deptno = 20;
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
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 3135 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2965 | NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3300 | NULL |     40 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 6050 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1331 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 | 1045 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3630 | NULL |     20 |
+-------+--------+-----------+------+------------+------+------+--------+

## 4. Alter SAL with size 10,2 in Employee_Master

## Query
```sql
      ALTER TABLE employee_master MODIFY Sal DECIMAL(10,2);
```

## Output
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| Empno    | int(4)        | NO   |     | NULL    |       |
| Ename    | varchar(20)   | NO   |     | NULL    |       |
| Job      | varchar(20)   | YES  |     | NULL    |       |
| Mgr      | int(4)        | YES  |     | NULL    |       |
| Hiredate | date          | YES  |     | NULL    |       |
| Sal      | decimal(10,2) | YES  |     | NULL    |       |
| Comm     | int(7)        | YES  |     | NULL    |       |
| Deptno   | int(2)        | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+

## 5. Drop Employee_master Table.

## Query
```sql
     DROP TABLE employee_master;
```

## Output
Query OK, 0 rows affected (0.020 sec)
