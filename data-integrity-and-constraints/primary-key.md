1. Type of Keys in SQL DB:

1.1 Primary Key
A primary key is a column or set of columns that uniquely identifies each row in a table. It is the combination of two constraints: UNIQUE (no duplicate values) and NOT NULL (must always contain a value).
In Oracle SQL, a table can have only one primary key, which can span single or multiple columns (composite primary key).

Characteristics of Primary Key:
  Must contain unique values
  Cannot contain NULL values
  Automatically creates a unique clustered index
  Enforces entity integrity
  Only one per table

Oracle SQL Implementation:

  -- Single Column Primary Key at Table Creation
    CREATE TABLE employees (
        emp_id NUMBER PRIMARY KEY,
        emp_name VARCHAR2(100) NOT NULL,
        emp_salary NUMBER(10,2)
    );

-- Composite Primary Key (Multiple Columns)
    CREATE TABLE student_courses (
        student_id NUMBER NOT NULL,
        course_id NUMBER NOT NULL,
        enrollment_date DATE,
        CONSTRAINT pk_student_courses PRIMARY KEY (student_id, course_id)
    );

-- Adding Primary Key to Existing Table
    ALTER TABLE employees
    ADD CONSTRAINT pk_emp PRIMARY KEY (emp_id);

-- Deleting the existing primary key
  ALTER TABLE Employees DROP PRIMARY KEY ;

​
