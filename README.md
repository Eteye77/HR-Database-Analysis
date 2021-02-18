# Sorting-and-Grouping---SQL
CREATE TABLE EMPLOYEES (
                            EMP_ID CHAR(9) NOT NULL, 
                            F_NAME VARCHAR(15) NOT NULL,
                            L_NAME VARCHAR(15) NOT NULL,
                            SSN CHAR(9),
                            B_DATE DATE,
                            SEX CHAR,
                            ADDRESS VARCHAR(30),
                            JOB_ID CHAR(9),
                            SALARY DECIMAL(10,2),
                            MANAGER_ID CHAR(9),
                            DEP_ID CHAR(9) NOT NULL,
                            PRIMARY KEY (EMP_ID));
                            
  CREATE TABLE JOB_HISTORY (
                            EMPL_ID CHAR(9) NOT NULL, 
                            START_DATE DATE,
                            JOBS_ID CHAR(9) NOT NULL,
                            DEPT_ID CHAR(9),
                            PRIMARY KEY (EMPL_ID,JOBS_ID));
 
 CREATE TABLE JOBS (
                            JOB_IDENT CHAR(9) NOT NULL, 
                            JOB_TITLE VARCHAR(15) ,
                            MIN_SALARY DECIMAL(10,2),
                            MAX_SALARY DECIMAL(10,2),
                            PRIMARY KEY (JOB_IDENT));

CREATE TABLE DEPARTMENTS (
                            DEPT_ID_DEP CHAR(9) NOT NULL, 
                            DEP_NAME VARCHAR(15) ,
                            MANAGER_ID CHAR(9),
                            LOC_ID CHAR(9),
                            PRIMARY KEY (DEPT_ID_DEP));

CREATE TABLE LOCATIONS (
                            LOCT_ID CHAR(9) NOT NULL,
                            DEP_ID_LOC CHAR(9) NOT NULL,
                            PRIMARY KEY (LOCT_ID,DEP_ID_LOC));
SELECT * FROM EMPLOYEES;

SELECT * FROM JOB_HISTORY;

SELECT * FROM JOBS;

SELECT * FROM DEPARTMENTS;

SELECT * FROM LOCATIONS;

SELECT F_NAME, L_NAME from EMPLOYEES
WHERE ADDRESS LIKE '%ELGIN,IL%';

SELECT F_NAME, L_NAME from EMPLOYEES
WHERE B_DATE LIKE '%197%';

select * from EMPLOYEES
where (SALARY BETWEEN 60000 and 70000)  and DEP_ID = 5 ;

SELECT * from EMPLOYEES
ORDER BY DEP_ID;

SELECT F_NAME, L_NAME, DEP_ID from EMPLOYEES
ORDER BY DEP_ID DESC, L_NAME DESC;

SELECT DEP_ID, COUNT(DEP_ID)
AS COUNT FROM EMPLOYEES GROUP BY DEP_ID;

SELECT DEP_ID, AVG(SALARY), COUNT(DEP_ID)
AS COUNT FROM EMPLOYEES GROUP BY DEP_ID;

SELECT DEP_ID, AVG(SALARY) AS 'AVG_SALARY', COUNT(DEP_ID) 
AS 'NUM_EMPLOYEES' FROM EMPLOYEES GROUP BY DEP_ID;

SELECT DEP_ID, AVG(SALARY) AS 'AVG_SALARY', COUNT(DEP_ID) 
AS 'NUM_EMPLOYEES' FROM EMPLOYEES GROUP BY DEP_ID
ORDER BY AVG_SALARY;

SELECT DEP_ID, AVG(SALARY) AS 'AVG_SALARY', COUNT(DEP_ID)
AS 'NUM_EMPLOYEES' FROM EMPLOYEES GROUP BY DEP_ID
HAVING COUNT(DEP_ID) < 4;

SELECT F_NAME, L_NAME, DEP_ID from EMPLOYEES
ORDER BY DEP_ID DESC, L_NAME DESC;

select D.DEP_NAME , E.F_NAME, E.L_NAME
from EMPLOYEES as E, DEPARTMENTS as D
where E.DEP_ID = D.DEPT_ID_DEP;
