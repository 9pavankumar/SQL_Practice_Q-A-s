# SQL_Practice_Qs_As

##  FOLLOW AS BELOW

1. **Create Database and Use it:**
```sql
CREATE DATABASE 240qs;
USE 240qs;
```

2. **Create `EMPY` Table:**
```sql
CREATE TABLE EMPY
(
    EMPNO INT, 
    ENAME VARCHAR(10), 
    JOB VARCHAR(9), 
    MGR INT, 
    HIREDATE DATE, 
    SAL INT, 
    COMM INT, 
    DEPTNO INT, 
    GRADE INT
);
```

3. **Insert Data into `EMPY` Table:**
```sql
INSERT INTO EMPY VALUES (7369, 'SMITH', 'CLERK', 7902, CAST('1980-12-17' AS DATE), 800, NULL, 20, 5);
INSERT INTO EMPY VALUES (7499, 'ALLEN', 'SALESMAN', 7698, CAST('1981-02-20' AS DATE), 2000, 300, 30, 3);
INSERT INTO EMPY VALUES (7521, 'WARD', 'SALESMAN', 7698, CAST('1981-02-22' AS DATE), 1250, 500, 30, 4);
INSERT INTO EMPY VALUES (7566, 'JONES', 'MANAGER', 7839, CAST('1981-04-02' AS DATE), 2975, NULL, 20, 2);
INSERT INTO EMPY VALUES (7654, 'MARTIN', 'SALESMAN', 7698, CAST('1981-09-28' AS DATE), 1250, 1400, 30, 4);
INSERT INTO EMPY VALUES (7698, 'BLAKE', 'MANAGER', 7839, CAST('1981-05-01' AS DATE), 2850, NULL, 30, 2);
INSERT INTO EMPY VALUES (7782, 'CLARK', 'MANAGER', 7839, CAST('1981-06-09' AS DATE), 2450, NULL, 10, 2);
INSERT INTO EMPY VALUES (7788, 'SCOTT', 'ANALYST', 7566, CAST('1982-12-09' AS DATE), 3000, NULL, 20, 1);
INSERT INTO EMPY VALUES (7839, 'KING', 'PRESIDENT', NULL, CAST('1981-11-17' AS DATE), 5000, NULL, 10, 1);
INSERT INTO EMPY VALUES (7844, 'TURNER', 'SALESMAN', 7698, CAST('1981-09-08' AS DATE), 1500, NULL, 30, 3);
INSERT INTO EMPY VALUES (7876, 'ADAMS', 'CLERK', 7788, CAST('1983-01-12' AS DATE), 1100, NULL, 20, 4);
INSERT INTO EMPY VALUES (7900, 'JAMES', 'CLERK', 7698, CAST('1981-12-03' AS DATE), 950, NULL, 30, 5);
INSERT INTO EMPY VALUES (7902, 'FORD', 'ANALYST', 7566, CAST('1981-12-03' AS DATE), 3000, NULL, 20, 1);
INSERT INTO EMPY VALUES (7934, 'MILLER', 'CLERK', 7782, CAST('1982-01-23' AS DATE), 1300, NULL, 10, 3);
```

4. **Select Data from `EMPY` Table:**
```sql
SELECT * FROM EMPY;
```

5. **Create `DEPT` Table:**
```sql
CREATE TABLE DEPT
(
    DEPTNO INT, 
    DNAME VARCHAR(14), 
    LOC VARCHAR(13)
);
```

6. **Insert Data into `DEPT` Table:**
```sql
INSERT INTO DEPT VALUES (10, 'ACCOUNTING', 'NEWYORK');
INSERT INTO DEPT VALUES (20, 'RESEARCH', 'DALLAS');
INSERT INTO DEPT VALUES (30, 'SALES', 'CHICAGO');
INSERT INTO DEPT VALUES (40, 'OPERATIONS', 'BOSTON');
```

7. **Select Data from `DEPT` Table:**
```sql
SELECT * FROM DEPT;
```

8. **Disable SQL Safe Updates:**
```sql
SET SQL_SAFE_UPDATES = 0;
```
