
#  Assignment

## Question 1

### Observe the structures of a given EMPLOYEE table as below and suggest if this table can be further Normalized.

**Table Structure**

`EMPNO, ENAME, SAL, DEPTNO, DNAME, LOC`

**Explain what normal form this table is and how you can make this into next normal form.**

### Answer

**Current Normal Form:** 2NF

**Reason:**
- EMPNO is the Primary Key.
- ENAME, SAL and DEPTNO depend on EMPNO.
- DNAME and LOC depend on DEPTNO, not directly on EMPNO.
- Therefore, this table has Transitive Dependency.

**Convert into 3NF**

### EMPLOYEE Table

| EMPNO | ENAME | SAL | DEPTNO |
|-------|-------|-----|--------|
| 101 | Ram | 30000 | 10 |

### DEPARTMENT Table

| DEPTNO | DNAME | LOC |
|--------|--------|------|
| 10 | Sales | Delhi |

---

## Question 2

### Observe the structures of a given STUDENT table as below and suggest if this table can be further Normalized.

**Table Structure**

`ROLLNO, NAME, AGE, EXAM, MARKS, GRADE`

**Explain what normal form this table is and how you can make this into next normal form.**

### Answer

**Current Normal Form:** 2NF

**Reason:**
- ROLLNO is the Primary Key.
- NAME, AGE, EXAM and MARKS depend on ROLLNO.
- GRADE depends on MARKS, not directly on ROLLNO.
- Therefore, this table has Transitive Dependency.

**Convert into 3NF**

### STUDENT Table

| ROLLNO | NAME | AGE |
|--------|------|-----|
| 1 | Aaliya | 20 |

### RESULT Table

| ROLLNO | EXAM | MARKS |
|--------|------|-------|
| 1 | DBMS | 95 |

### GRADE Table

| MARKS | GRADE |
|-------|--------|
| 95 | A+ |

---

## Question 3

### Observe the structure of a given EMPLOYEE table and suggest what kind of problem this table has and how to solve the problem.

**Table Structure**

`EMPNO, PROJECT_NO, NO_OF_DAYS, CUSTOMERNAME`

**In the above table EMPNO and PROJECT_NO both are together a composite primary key.**

### Answer

**Problem:** Partial Dependency

**Reason:**
- Composite Primary Key = (EMPNO, PROJECT_NO)
- CUSTOMERNAME depends only on PROJECT_NO, not on the complete primary key.
- Therefore, this table has Partial Dependency and is only in 1NF.

**Convert into 2NF**

### EMPLOYEE_PROJECT Table

| EMPNO | PROJECT_NO | NO_OF_DAYS |
|-------|------------|------------|
| 101 | P101 | 20 |

### PROJECT Table

| PROJECT_NO | CUSTOMERNAME |
|------------|--------------|
| P101 | ABC Ltd |

