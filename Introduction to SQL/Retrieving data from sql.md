
# Hands-on Assignment - Retrieving Data Using the SQL SELECT Statement

## Question 1

### Determine the Structure of DEPT Table and its Contents.

**Answer**

### Display the Structure of DEPT Table

```sql
DESC DEPT;
```

### Display the Contents of DEPT Table

```sql
SELECT * FROM DEPT;
```

---

## Question 2

### Determine the Structure of EMP Table and its Contents.

**Answer**

### Display the Structure of EMP Table

```sql
DESC EMP;
```

### Display the Contents of EMP Table

```sql
SELECT * FROM EMP;
```

---

## Question 3

### Display the ENAME and DEPTNO from EMP table whose EMPNO is 7788.

**Answer**

```sql
SELECT ENAME, DEPTNO
FROM EMP
WHERE EMPNO = 7788;
```
