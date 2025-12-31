Foreign Key:

  A foreign key is a column or set of columns in one table that references the primary key or unique key of another table. 
  It maintains referential integrity, ensuring that every foreign key value corresponds to a valid primary key value in the referenced table.

Characteristics of Foreign Key:

  Can contain duplicate values
  ​Can contain NULL values
  ​Can have multiple foreign keys per table
  ​Establishes one-to-many relationships
  ​Must reference a primary key or unique key

Oracle SQL implementation :
  -- Creating Foreign Key at Table Creation
    CREATE TABLE orders (
        order_id NUMBER PRIMARY KEY,
        customer_id NUMBER NOT NULL,
        order_date DATE,
        CONSTRAINT FK_Customer FOREIGN KEY (customer_id)
        REFERENCES customers(customer_id)
        ON DELETE CASCADE
    );

-- Adding Foreign Key to Existing Table
    ALTER TABLE Orders
    ADD CONSTRAINT FK_Customer FOREIGN KEY (customer_id)
    REFERENCES customers(customer_id)
    ON DELETE SET NULL;

-- Composite Foreign Key
  -- Parent table with composite primary key
      CREATE TABLE dept_mgr (
          department_id NUMBER(10)   NOT NULL,
          manager_id    NUMBER(10)   NOT NULL,
          dept_name     VARCHAR2(100),
          CONSTRAINT dept_mgr_pk PRIMARY KEY (department_id, manager_id)
      );

  -- Child table with composite foreign key
        CREATE TABLE emp_assignments (
            employee_id   NUMBER(10)   NOT NULL,
            department_id NUMBER(10)   NOT NULL,
            manager_id    NUMBER(10)   NOT NULL,
            start_date    DATE         NOT NULL,
            CONSTRAINT emp_assign_pk  PRIMARY KEY (employee_id, department_id, manager_id),
            CONSTRAINT emp_assign_dept_mgr_fk FOREIGN KEY (department_id, manager_id)
            REFERENCES dept_mgr (department_id, manager_id)
        );
NOTE :
The parent table has a composite primary key on (department_id,manager_id).
​The child table’s FOREIGN KEY lists the same columns, in the same order, and references those parent columns.
​


