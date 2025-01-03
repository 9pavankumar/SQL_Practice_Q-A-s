
---

1. **Display all the information of the EMP table**

```sql
-- Method 1
SELECT * FROM EMPY;
-- Method 2
SELECT EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO, GRADE FROM EMPY;
```

---

2. **Display unique Jobs from EMP table**

```sql
-- Method 1
SELECT DISTINCT JOB FROM EMPY;
-- Method 2
SELECT JOB FROM EMPY GROUP BY JOB;
```

---

3. **List the employees in the ascending order of their Salaries**

```sql
-- Method 1
SELECT * FROM EMPY ORDER BY SAL ASC;
-- Method 2
SELECT * FROM EMPY ORDER BY SAL;
```

---

4. **List the details of the employees in ascending order of Deptnos and descending order of Jobs**

```sql
-- Method 1
SELECT * FROM EMPY ORDER BY DEPTNO ASC, JOB DESC;
-- Method 2
SELECT * FROM EMPY ORDER BY DEPTNO, JOB DESC;
```

---

5. **Display all the unique job groups in the descending order**

```sql
-- Method 1
SELECT JOB FROM EMPY GROUP BY JOB ORDER BY COUNT(JOB) DESC;
-- Method 2
SELECT JOB FROM EMPY GROUP BY JOB ORDER BY JOB DESC;
```

---

6. **Display all the details of all ‘Mgrs’**

```sql
-- Method 1
SELECT DISTINCT MGR FROM EMPY;
-- Method 2
SELECT JOB FROM EMPY GROUP BY JOB;
```

---

7. **List the employees who joined before 1981**

```sql
-- Method 1
SELECT * FROM EMPY WHERE YEAR(HIREDATE) < 1981;
-- Method 2
SELECT * FROM EMPY WHERE HIREDATE < '1981-01-01';
```

---

8. **List the Empno, Ename, Sal, Daily sal of all employees in the ascending order of Annual Salary**

```sql
-- Method 1
SELECT EMPNO, ENAME, SAL, SAL / 30 AS DAILY_SAL, SAL * 365 AS ANNUAL_SAL 
FROM EMPY 
ORDER BY ANNUAL_SAL ASC;

```

---

9. **Display the Empno, Ename, job, Hiredate, Exp of all Managers**

```sql
-- Method 1
SELECT EMPNO, ENAME, JOB, HIREDATE, YEAR(CURRENT_DATE()) - YEAR(HIREDATE) AS EXP FROM EMPY WHERE JOB = 'MANAGER';
-- Method 2
SELECT EMPNO, ENAME, JOB, HIREDATE, DATEDIFF(CURRENT_DATE(), HIREDATE) / 365 AS EXP FROM EMPY WHERE JOB = 'MANAGER';
```

---

10. **List the Empno, Ename, Sal, Exp of all employees working for Manager 7369**

```sql

-- Method 1
SELECT EMPNO, ENAME, SAL, YEAR(CURRENT_DATE()) - YEAR(HIREDATE) AS EXP FROM EMPY WHERE MGR = 7369;
```

---

11. **Display all the details of the employees whose Comm. is more than their Sal**

```sql
-- Method 1
SELECT * FROM EMPY WHERE COMM > SAL;
-- Method 2
SELECT * FROM EMPY WHERE (COMM IS NOT NULL) AND COMM > SAL;
```

---

12. **List the employees in the ascending order of Designations of those who joined after the second half of 1981**

```sql
-- Method 1
SELECT ENAME, JOB FROM EMPY WHERE YEAR(HIREDATE) > 1981 AND MONTH(HIREDATE) > 6 ORDER BY JOB ASC;
-- Method 2
SELECT ENAME, JOB FROM EMPY WHERE HIREDATE > '1981-06-30' ORDER BY JOB ASC;
```

---

13. **List the employees along with their Exp and Daily Sal greater than Rs.100**

```sql
-- Method 1
SELECT *, YEAR(CURRENT_DATE()) - YEAR(HIREDATE) AS EXP FROM EMPY WHERE SAL / 30 > 100;
-- Method 2
SELECT *, DATEDIFF(CURRENT_DATE(), HIREDATE) / 365 AS EXP FROM EMPY WHERE SAL / 30 > 100;
```

---

14. **List the employees who are either ‘CLERK’ or ‘ANALYST’ in descending order**

```sql
-- Method 1
SELECT * FROM EMPY WHERE JOB = 'CLERK' OR JOB = 'ANALYST' ORDER BY JOB DESC;
-- Method 2
SELECT * FROM EMPY WHERE JOB IN ('CLERK', 'ANALYST') ORDER BY JOB DESC;
```

---

15. **List the employees who joined on 1-MAY-81, 3-DEC-81, 17-DEC-81, 19-JAN-80 in ascending order of seniority**

```sql
-- Method 1
SELECT * FROM EMPY WHERE DATE_FORMAT(HIREDATE, '%d-%b-%y') IN ('01-MAY-81', '03-DEC-81', '17-DEC-81', '19-JAN-80') ORDER BY HIREDATE ASC;
-- Method 2
SELECT * FROM EMPY WHERE HIREDATE IN ('1981-05-01', '1981-12-03', '1981-12-17', '1980-01-19') ORDER BY HIREDATE ASC;
```

---

16. **List the employees who are working for Deptno 10 or 20**

```sql
-- Method 1
SELECT * FROM EMPY WHERE DEPTNO IN (10, 20);
-- Method 2
SELECT * FROM EMPY WHERE DEPTNO = 10 OR DEPTNO = 20;
```

---

17. **List the employees who joined in the year 81**

```sql
-- Method 1
SELECT * FROM EMPY WHERE YEAR(HIREDATE) = 1981;
-- Method 2
SELECT * FROM EMPY WHERE HIREDATE BETWEEN '1981-01-01' AND '1981-12-31';
```

---

18. **List the employees who joined in the month of August 1980**

```sql
-- Method 1
SELECT *, DATE_FORMAT(HIREDATE, '%e-%b-%Y') FROM EMPY WHERE MONTH(HIREDATE) = 8 AND YEAR(HIREDATE) = 1980;
-- Method 2
SELECT *, DATE_FORMAT(HIREDATE, '%e-%b-%Y') FROM EMPY WHERE HIREDATE BETWEEN '1980-08-01' AND '1980-08-31';
```

---

19. **List the employees whose annual salary ranges from 220000 and 450000**

```sql
-- Method 1
SELECT *, SAL * 12 AS ANNUAL_SAL FROM EMPY WHERE SAL * 12 BETWEEN 220000 AND 450000;
```

---

20. **List the employees whose names have exactly five characters**

```sql
-- Method 1
SELECT ENAME FROM EMPY WHERE ENAME LIKE '_____';
-- Method 2
SELECT ENAME FROM EMPY WHERE LENGTH(ENAME) = 5;
```

---

21. **List the employees whose names start with ‘S’ and have five characters**

```sql
-- Method 1
SELECT ENAME FROM EMPY WHERE ENAME LIKE 'S____';
-- Method 2
SELECT ENAME FROM EMPY WHERE ENAME LIKE 'S%' AND LENGTH(ENAME) = 5;
```

---

22. **List the employees whose names have four characters and the third character is ‘r’**

```sql
-- Method 1
SELECT ENAME FROM EMPY WHERE ENAME LIKE '___r';
-- Method 2
SELECT ENAME FROM EMPY WHERE LENGTH(ENAME) = 4 AND SUBSTRING(ENAME, 3, 1) = 'r';
```

---

23. **List the five character names starting with ‘S’ and ending with ‘H’**

```sql
-- Method 1
SELECT ENAME FROM EMPY WHERE ENAME LIKE 'S___H';
-- Method 2
SELECT ENAME FROM EMPY WHERE ENAME LIKE 'S%H' AND LENGTH(ENAME) = 5;
```

---

24. **List the employees who joined in January**

```sql
-- Method 1
SELECT * FROM EMPY WHERE DATE_FORMAT(HIREDATE, '%M') = 'January';
-- Method 2
SELECT * FROM EMPY WHERE MONTH(HIREDATE) = 1;
```

---

25. **List the employees who joined in the month whose second character is ‘a’**

```sql
-- Method 1
SELECT * , DATE_FORMAT(HIREDATE, '%M') AS MONTHS FROM EMPY WHERE DATE_FORMAT(HIREDATE, '%M') LIKE '_a%';
-- Method 2
SELECT * FROM EMPY WHERE MONTHNAME(HIREDATE) LIKE '_a%';
```

---

26. **List the employees whose salary is a four-digit number ending with zero**

```sql
-- Method 1
SELECT ENAME FROM EMPY WHERE SAL LIKE '___0';
-- Method 2
SELECT ENAME FROM EMPY WHERE SAL % 10 = 0 AND SAL BETWEEN 1000 AND 9999;
```

---

27. **List the employees whose names contain the character set ‘ll’ together**

```sql
-- Method 1
SELECT * FROM EMPY WHERE ENAME LIKE '%ll%';
-- Method 2
SELECT * FROM EMPY WHERE ENAME REGEXP 'll';
```

---

28. **List the employees who joined in the 1980s**

```sql
-- Method 1
SELECT * FROM EMPY WHERE YEAR(HIREDATE) BETWEEN 1980 AND 1989;
-- Method 2
SELECT * FROM EMPY WHERE HIREDATE >= '1980-01-01' AND HIREDATE < '1990-01-01';
```

---

29. **List the employees who do not belong to Deptno 20**

```sql
-- Method 1
SELECT * FROM EMPY WHERE DEPTNO != 20;
-- Method 2
SELECT * FROM EMPY WHERE DEPTNO <> 20;
```

---

30. **List all the employees except ‘PRESIDENT’ & ‘MGR’ in ascending order of Salaries**

```sql
-- Method 1
SELECT * FROM EMPY WHERE JOB NOT IN ('PRESIDENT', 'MANAGER') ORDER BY SAL ASC;
-- Method 2
SELECT * FROM EMPY WHERE JOB <> 'PRESIDENT' AND JOB <> 'MANAGER' ORDER BY SAL ASC;
```


---

### 31. List all the employees who joined before or after 1981.

```sql
-- Method 1
SELECT * FROM EMPY WHERE YEAR(HIREDATE) != 1981;

-- Method 2
SELECT * FROM EMPY WHERE HIREDATE < '1981-01-01' OR HIREDATE > '1981-12-31';
```

---

### 32. List the employees whose Empno does not start with digit 78.

```sql
-- Method 1
SELECT * FROM EMPY WHERE EMPNO NOT LIKE '78%';

-- Method 2
SELECT * FROM EMPY WHERE LEFT(EMPNO, 2) != '78';
```

---

### 33. List the employees who are working under 'MGR'.

```sql
-- Method 1
SELECT E1.EMPNO AS Empno, E1.ENAME AS EmpName, E2.ENAME AS Manager 
FROM EMPY AS E1
INNER JOIN EMPY AS E2 ON E1.MGR = E2.EMPNO;

-- Method 2
SELECT * FROM EMPY WHERE MGR IS NOT NULL;
```

---

### 34. List the employees who joined in any year but not in March.

```sql
-- Method 1
SELECT * FROM EMPY WHERE MONTH(HIREDATE) != 3;

-- Method 2
SELECT * FROM EMPY WHERE HIREDATE NOT LIKE '____-03-%';
```

---

### 35. List all the Clerks of Deptno 20.

```sql
-- Method 1
SELECT * FROM EMPY WHERE JOB = 'CLERK' AND DEPTNO = 20;

-- Method 2
SELECT * FROM EMPY WHERE JOB = 'CLERK' AND DEPTNO IN (20);
```

---

### 36. List the employees of Deptno 30 or 10 who joined in the year 1981.

```sql
-- Method 1
SELECT * FROM EMPY WHERE YEAR(HIREDATE) = 1981 AND DEPTNO IN (10, 30);

-- Method 2
SELECT * FROM EMPY WHERE DEPTNO = 30 OR DEPTNO = 10 AND YEAR(HIREDATE) = 1981;
```

---

### 37. Display the details of SMITH.

```sql
-- Method 1
SELECT * FROM EMPY WHERE ENAME = 'SMITH';

-- Method 2
SELECT * FROM EMPY WHERE LOWER(ENAME) = 'smith';
```

---

### 38. Display the location of SMITH.

```sql
-- Method 1
SELECT D.LOC 
FROM EMPY E
JOIN DEPT D ON E.DEPTNO = D.DEPTNO
WHERE E.ENAME = 'SMITH';

-- Method 2
SELECT LOC 
FROM DEPT 
WHERE DEPTNO = (SELECT DEPTNO FROM EMPY WHERE ENAME = 'SMITH');
```

---

### 39. List the total information of EMP table along with DNAME and LOC of all the employees working under 'ACCOUNTING' and 'RESEARCH'.

```sql
-- Method 1
SELECT E.*, D.DNAME, D.LOC 
FROM EMPY E
JOIN DEPT D ON E.DEPTNO = D.DEPTNO
WHERE D.DNAME IN ('ACCOUNTING', 'RESEARCH')
ORDER BY E.DEPTNO ASC;

-- Method 2
SELECT * FROM EMPY 
JOIN DEPT ON EMPY.DEPTNO = DEPT.DEPTNO 
WHERE DNAME = 'ACCOUNTING' OR DNAME = 'RESEARCH';
```

---

### 40. List the Empno, Ename, Sal, Dname of all the 'MGRS' and 'ANALYST' working in New York, Dallas with experience more than 7 years without receiving Comm, sorted by location.

```sql
-- Method 1
SELECT E.EMPNO, E.ENAME, E.SAL, D.DNAME 
FROM EMPY E
JOIN DEPT D ON E.DEPTNO = D.DEPTNO
WHERE (D.LOC IN ('NEW YORK', 'DALLAS')) 
  AND (YEAR(CURRENT_DATE()) - YEAR(E.HIREDATE)) > 7 
  AND E.COMM IS NULL 
ORDER BY D.LOC ASC;

-- Method 2
SELECT EMPNO, ENAME, SAL, DNAME 
FROM EMPY E
JOIN DEPT D ON E.DEPTNO = D.DEPTNO
WHERE D.LOC = 'NEW YORK' OR D.LOC = 'DALLAS'
  AND (YEAR(CURRENT_DATE()) - YEAR(HIREDATE)) > 7
  AND COMM IS NULL;
```
Here are the solutions for questions 41 to 50, formatted as per your example.

---

### 41. Display the Empno, Ename, Sal, Dname, Loc, Deptno, and Job of all employees working in Chicago or the Accounting department with an annual salary > 280000, excluding salaries of 3000 or 2800, and with Empno having '7' or '8' as the 3rd digit, sorted by Deptno and Job.

```sql
-- Method 1
SELECT E.EMPNO, E.ENAME, E.SAL, D.DNAME, D.LOC, E.DEPTNO, E.JOB 
FROM EMPY E
JOIN DEPT D ON E.DEPTNO = D.DEPTNO
WHERE (D.LOC = 'CHICAGO' OR D.DNAME = 'ACCOUNTING') 
  AND (E.SAL * 12) > 280000
  AND E.SAL NOT IN (3000, 2800)
  AND (E.EMPNO LIKE '__7%' OR E.EMPNO LIKE '__8%')
ORDER BY E.DEPTNO ASC, E.JOB DESC;

-- Method 2
SELECT EMPNO, ENAME, SAL, DNAME, LOC, DEPTNO, JOB 
FROM EMPY 
JOIN DEPT ON EMPY.DEPTNO = DEPT.DEPTNO 
WHERE LOC = 'CHICAGO' OR DNAME = 'ACCOUNTING'
  AND (SAL * 12) > 280000
  AND SAL NOT IN (3000, 2800)
  AND EMPNO REGEXP '^..[78].*'
ORDER BY DEPTNO ASC, JOB DESC;
```

---

### 42. Display the total information of employees along with Grades, sorted in ascending order.

```sql
-- Method 1
SELECT E.*, D.GRADE 
FROM EMPY E
JOIN SALGRADE D ON E.SAL BETWEEN D.LOSAL AND D.HISAL
ORDER BY D.GRADE ASC;

-- Method 2
SELECT EMPY.*, GRADE 
FROM EMPY
JOIN SALGRADE ON SAL BETWEEN LOSAL AND HISAL
ORDER BY GRADE;
```

---

### 43. List all Grade 2 and Grade 3 employees.

```sql
-- Method 1
SELECT E.*, D.GRADE 
FROM EMPY E
JOIN SALGRADE D ON E.SAL BETWEEN D.LOSAL AND D.HISAL
WHERE D.GRADE IN (2, 3);

-- Method 2
SELECT * 
FROM EMPY 
WHERE SAL BETWEEN (SELECT LOSAL FROM SALGRADE WHERE GRADE = 2) 
AND (SELECT HISAL FROM SALGRADE WHERE GRADE = 3);
```

---

### 44. Display all Grade 4 and 5 employees who are Analysts or Managers.

```sql
-- Method 1
SELECT E.*, D.GRADE 
FROM EMPY E
JOIN SALGRADE D ON E.SAL BETWEEN D.LOSAL AND D.HISAL
WHERE D.GRADE IN (4, 5) AND E.JOB IN ('ANALYST', 'MANAGER');

-- Method 2
SELECT EMPY.* 
FROM EMPY
JOIN SALGRADE ON SAL BETWEEN LOSAL AND HISAL
WHERE GRADE IN (4, 5) AND JOB = 'ANALYST' OR JOB = 'MANAGER';
```

---

### 45. List the Empno, Ename, Sal, Dname, Grade, Exp, and AnnSal of employees in Deptno 10 or 20.

```sql
-- Method 1
SELECT E.EMPNO, E.ENAME, E.SAL, D.DNAME, D.GRADE, 
       YEAR(CURRENT_DATE()) - YEAR(E.HIREDATE) AS EXP, E.SAL * 12 AS ANNSAL
FROM EMPY E
JOIN DEPT D ON E.DEPTNO = D.DEPTNO
JOIN SALGRADE SG ON E.SAL BETWEEN SG.LOSAL AND SG.HISAL
WHERE E.DEPTNO IN (10, 20);

-- Method 2
SELECT EMPNO, ENAME, SAL, DNAME, GRADE, EXP, SAL * 12 AS ANNSAL
FROM EMPY
JOIN DEPT USING (DEPTNO)
JOIN SALGRADE ON SAL BETWEEN LOSAL AND HISAL
WHERE DEPTNO = 10 OR DEPTNO = 20;
```

---

### 46. List all employees with Loc, Grade between 2 and 4, working in Depts not starting with 'OP' or ending with 'S', with 'a' in their designation, joined in 1981 (not March/September), and salaries not ending with '00', sorted by Grades.

```sql
-- Method 1
SELECT E.*, D.LOC, SG.GRADE
FROM EMPY E
JOIN DEPT D ON E.DEPTNO = D.DEPTNO
JOIN SALGRADE SG ON E.SAL BETWEEN SG.LOSAL AND SG.HISAL
WHERE SG.GRADE BETWEEN 2 AND 4
  AND D.DNAME NOT LIKE 'OP%' 
  AND D.DNAME NOT LIKE '%S'
  AND E.JOB LIKE '%a%'
  AND YEAR(E.HIREDATE) = 1981
  AND MONTH(E.HIREDATE) NOT IN (3, 9)
  AND E.SAL NOT LIKE '%00'
ORDER BY SG.GRADE ASC;

-- Method 2
SELECT EMPNO, ENAME, LOC, GRADE, JOB, SAL
FROM EMPY
JOIN DEPT USING (DEPTNO)
JOIN SALGRADE ON SAL BETWEEN LOSAL AND HISAL
WHERE GRADE BETWEEN 2 AND 4
  AND DNAME NOT LIKE 'OP%' 
  AND DNAME NOT LIKE '%S'
  AND JOB LIKE '%a%'
  AND YEAR(HIREDATE) = 1981
  AND MONTH(HIREDATE) NOT IN (3, 9)
  AND SAL NOT LIKE '%00'
ORDER BY GRADE;
```

---

### 47. List the details of the Depts along with Empno, Ename, or without employees.

```sql
-- Method 1
SELECT D.*, E.EMPNO, E.ENAME 
FROM DEPT D
LEFT JOIN EMPY E ON D.DEPTNO = E.DEPTNO;

-- Method 2
SELECT * 
FROM DEPT 
LEFT JOIN EMPY ON DEPT.DEPTNO = EMPY.DEPTNO;
```

---

### 48. List the employees whose Salaries are more than BLAKE.

```sql
-- Method 1
SELECT * 
FROM EMPY 
WHERE SAL > (SELECT SAL FROM EMPY WHERE ENAME = 'BLAKE');

-- Method 2
SELECT E.EMPNO, E.ENAME, E.SAL 
FROM EMPY E
JOIN EMPY BLAKE ON BLAKE.ENAME = 'BLAKE'
WHERE E.SAL > BLAKE.SAL;
```

---

### 49. List the employees whose Jobs are the same as ALLEN.

```sql
-- Method 1
SELECT * 
FROM EMPY 
WHERE JOB = (SELECT JOB FROM EMPY WHERE ENAME = 'ALLEN');

-- Method 2
SELECT E.EMPNO, E.ENAME, E.JOB 
FROM EMPY E
JOIN EMPY ALLEN ON ALLEN.ENAME = 'ALLEN'
WHERE E.JOB = ALLEN.JOB;
```

---

### 50. List the employees who are senior to KING.

```sql
-- Method 1
SELECT * 
FROM EMPY 
WHERE HIREDATE < (SELECT HIREDATE FROM EMPY WHERE ENAME = 'KING');

-- Method 2
SELECT E.EMPNO, E.ENAME, E.HIREDATE 
FROM EMPY E
JOIN EMPY KING ON KING.ENAME = 'KING'
WHERE E.HIREDATE < KING.HIREDATE;
```

---

Let me know if you need further refinement or additional queries!
