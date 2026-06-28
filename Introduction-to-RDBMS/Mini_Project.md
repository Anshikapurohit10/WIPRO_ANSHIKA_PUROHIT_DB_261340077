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

---

## Conclusion

The given tables have been successfully normalized into **1NF**, **2NF**, and **3NF**, reducing data redundancy and improving database consistency.
