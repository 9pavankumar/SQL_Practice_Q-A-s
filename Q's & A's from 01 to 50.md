
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
