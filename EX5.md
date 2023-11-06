# Ex. No: 5 Creating Triggers using PL/SQL
# DATE:12.9.23
### AIM: To create a Trigger using PL/SQL.

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
```
NAME: Ronick Aakshath P
Reg.no: 212222240084
```
```
CREATE TABLE sal_log (
  log_id NUMBER GENERATED ALWAYS AS IDENTITY,
  empid NUMBER,
  empname VARCHAR2(10),
  old_salary NUMBER,
  new_salary NUMBER,
  update_date DATE
);
```
### Create employee table:

```
CREATE TABLE employed(
  empid NUMBER,
  empname VARCHAR2(10),
  dept VARCHAR2(10),
  salary NUMBER
);
```
![11](https://github.com/Ronick2005/Ex-5-Creating-Triggers-using-PL-SQL/assets/83219341/35e445b8-694f-4a88-8f4c-472ce032415e)

### Create salary_log table:
```
CREATE TABLE sal_log (
  log_id NUMBER GENERATED ALWAYS AS IDENTITY,
  empid NUMBER,
  empname VARCHAR2(10),
  old_salary NUMBER,
  new_salary NUMBER,
  update_date DATE
);
```
![12](https://github.com/Ronick2005/Ex-5-Creating-Triggers-using-PL-SQL/assets/83219341/9753bda2-a6ea-4236-b99f-685f468763ff)

### PLSQL Trigger code
->create trigger 
```
CREATE OR REPLACE TRIGGER sal_log_update
BEFORE UPDATE ON employed
FOR EACH ROW
BEGIN
  IF :OLD.salary != :NEW.salary THEN
    INSERT INTO sal_log (empid, empname, old_salary, new_salary, update_date)
    VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
  END IF;
END;
/
```
->Update the salary of an employee
```
UPDATE employed
SET salary = 60000
WHERE empid = 1;
```
->Display the employee table
```
SELECT * FROM employed;
```
->Display the salary_log table
```
SELECT * FROM sal_log;
```
### Output:
![13](https://github.com/Ronick2005/Ex-5-Creating-Triggers-using-PL-SQL/assets/83219341/77ea01b3-3716-48c6-99eb-04c5214e0667)

### Result:
The program has been implemented successfully.
