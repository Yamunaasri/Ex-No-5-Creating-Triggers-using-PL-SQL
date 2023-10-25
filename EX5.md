# Ex. No: 5 Creating Triggers using PL/SQL

### AIM: 
To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
### Create employee table
![image](https://github.com/Yamunaasri/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/115707860/b7877222-1e60-42aa-b89b-595445e76123)

### Create salary_log table
![image](https://github.com/Yamunaasri/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/115707860/bb60170f-7aa7-480e-a081-75f6a764a8e2)

### PLSQL Trigger code
```
DEVELOPED BY: T S YAMUNAASRI
REG NO:212222240117

-- Create the trigger
CREATE OR REPLACE TRIGGER log_sal_update
BEFORE UPDATE ON employee
FOR EACH ROW
BEGIN
  IF :OLD.salary != :NEW.salary THEN
    INSERT INTO sal_log (empid, empname, old_salary, new_salary, update_date)
    VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
  END IF;
END;
/
-- Insert the values in the employee table
insert into employee values(1,'Aarthi','IT',1000000);
insert into employee values(2,'Pooja','SALES',500000);

-- Update the salary of an employee
UPDATE employee
SET salary = 60000
WHERE empid = 1;
-- Display the employee table
SELECT * FROM employee;

-- Display the salary_log table
SELECT * FROM sal_log;
```
### Output:
![image](https://github.com/Yamunaasri/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/115707860/8eeb2df0-d506-4858-ab7d-73ef0d59164e)

### Result:
    A trigger is created using PL/SQL.
