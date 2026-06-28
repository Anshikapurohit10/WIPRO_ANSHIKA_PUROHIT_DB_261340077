# Mini Project - Normalization

## Question 1: Normalize the Table into First Normal Form (1NF)

### Given Table

| Member_Id | First_Name | Last_Name | Hobbies |
|-----------|------------|-----------|--------------------------------|
| 101 | Jayson | Mark | Cricket, Swimming, Football |
| 102 | Ram | Ganesh | Swimming, Running, Music |
| 103 | Raj | Kishore | Dancing, Singing, Running |
### SQL Query

```sql
CREATE TABLE MEMBER_1NF (
    MEMBER_ID NUMBER,
    FIRST_NAME VARCHAR2(30),
    LAST_NAME VARCHAR2(30),
    HOBBY VARCHAR2(30)
);

INSERT INTO MEMBER_1NF VALUES (101,'Jayson','Mark','Cricket');
INSERT INTO MEMBER_1NF VALUES (101,'Jayson','Mark','Swimming');
INSERT INTO MEMBER_1NF VALUES (101,'Jayson','Mark','Football');
INSERT INTO MEMBER_1NF VALUES (102,'Ram','Ganesh','Swimming');
INSERT INTO MEMBER_1NF VALUES (102,'Ram','Ganesh','Running');
INSERT INTO MEMBER_1NF VALUES (102,'Ram','Ganesh','Music');
INSERT INTO MEMBER_1NF VALUES (103,'Raj','Kishore','Dancing');
INSERT INTO MEMBER_1NF VALUES (103,'Raj','Kishore','Singing');
INSERT INTO MEMBER_1NF VALUES (103,'Raj','Kishore','Running');

COMMIT;

SELECT * FROM MEMBER_1NF;
```
### Answer (1NF)

| Member_Id | First_Name | Last_Name | Hobby |
|-----------|------------|-----------|---------|
| 101 | Jayson | Mark | Cricket |
| 101 | Jayson | Mark | Swimming |
| 101 | Jayson | Mark | Football |
| 102 | Ram | Ganesh | Swimming |
| 102 | Ram | Ganesh | Running |
| 102 | Ram | Ganesh | Music |
| 103 | Raj | Kishore | Dancing |
| 103 | Raj | Kishore | Singing |
| 103 | Raj | Kishore | Running |

---

## Question 2: Normalize the Table into Second Normal Form (2NF)

### Given Table

| EmpNo | Training | Training_Date | Dept |
|-------|----------|---------------|------|
| 101 | Oracle SQL | 12-Aug-2015 | TT |
| 101 | Java | 21-Aug-2015 | BU |
| 102 | Oracle SQL | 18-Sep-2014 | TT |
### SQL Query

```sql
CREATE TABLE EMPLOYEE (
    EMPNO NUMBER PRIMARY KEY,
    DEPT VARCHAR2(10)
);

INSERT INTO EMPLOYEE VALUES (101,'TT');
INSERT INTO EMPLOYEE VALUES (102,'TT');

CREATE TABLE TRAINING (
    EMPNO NUMBER,
    TRAINING VARCHAR2(30),
    TRAINING_DATE DATE,
    PRIMARY KEY (EMPNO, TRAINING),
    FOREIGN KEY (EMPNO) REFERENCES EMPLOYEE(EMPNO)
);

INSERT INTO TRAINING
VALUES (101,'Oracle SQL',TO_DATE('12-AUG-2015','DD-MON-YYYY'));

INSERT INTO TRAINING
VALUES (101,'Java',TO_DATE('21-AUG-2015','DD-MON-YYYY'));

INSERT INTO TRAINING
VALUES (102,'Oracle SQL',TO_DATE('18-SEP-2014','DD-MON-YYYY'));

COMMIT;

SELECT * FROM EMPLOYEE;

SELECT * FROM TRAINING;
```
### Answer (2NF)

#### Employee Table

| EmpNo | Dept |
|-------|------|
| 101 | TT |
| 102 | TT |

#### Training Table

| EmpNo | Training | Training_Date |
|-------|----------|---------------|
| 101 | Oracle SQL | 12-Aug-2015 |
| 101 | Java | 21-Aug-2015 |
| 102 | Oracle SQL | 18-Sep-2014 |

---

## Question 3: Normalize the Table into Third Normal Form (3NF)

### Given Table

| Member_Id | First_Name | Last_Name | Sports | Fees |
|-----------|------------|-----------|--------|------|
| 101 | Rajesh | Chand | Cricket | 100 |
| 102 | Jayesh | Raj | Hockey | 80 |
| 103 | Mark | Dorsson | Football | 90 |

### Answer (3NF)

#### Member Table

| Member_Id | First_Name | Last_Name | Sports |
|-----------|------------|-----------|---------|
| 101 | Rajesh | Chand | Cricket |
| 102 | Jayesh | Raj | Hockey |
| 103 | Mark | Dorsson | Football |

#### Sports Fee Table

| Sports | Fees |
|---------|------|
| Cricket | 100 |
| Hockey | 80 |
| Football | 90 |
### SQL Query

```sql
CREATE TABLE SPORTS_FEE (
    SPORTS VARCHAR2(30) PRIMARY KEY,
    FEES NUMBER
);

INSERT INTO SPORTS_FEE VALUES ('Cricket',100);
INSERT INTO SPORTS_FEE VALUES ('Hockey',80);
INSERT INTO SPORTS_FEE VALUES ('Football',90);

CREATE TABLE MEMBER (
    MEMBER_ID NUMBER PRIMARY KEY,
    FIRST_NAME VARCHAR2(30),
    LAST_NAME VARCHAR2(30),
    SPORTS VARCHAR2(30),
    FOREIGN KEY (SPORTS) REFERENCES SPORTS_FEE(SPORTS)
);

INSERT INTO MEMBER VALUES (101,'Rajesh','Chand','Cricket');
INSERT INTO MEMBER VALUES (102,'Jayesh','Raj','Hockey');
INSERT INTO MEMBER VALUES (103,'Mark','Dorsson','Football');

COMMIT;

SELECT * FROM MEMBER;

SELECT * FROM SPORTS_FEE;
```
---

## Conclusion

The given tables have been successfully normalized into **1NF**, **2NF**, and **3NF**, reducing data redundancy and improving database consistency.
