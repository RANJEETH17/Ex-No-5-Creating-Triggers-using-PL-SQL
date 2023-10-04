# Ex. No: 5 Creating Triggers using PL/SQL

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
![image](https://github.com/RANJEETH17/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120718823/1d02371c-81b8-4a22-be69-590ae9ac46da)



### Create employee table
![image](https://github.com/RANJEETH17/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120718823/abcaa642-1d33-4df6-952e-3e1ceeee5d0a)


### Create salary_log table
![image](https://github.com/RANJEETH17/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120718823/45b4b598-753a-46b0-8a8e-6bbde3db3fe3)



### PLSQL Trigger code
```
-- Create the trigger
CREATE OR REPLACE TRIGGER log_salary1_update
BEFORE UPDATE ON emp2
FOR EACH ROW
DECLARE
  old_salary NUMBER;
  new_salary NUMBER;
BEGIN
  old_salary := :OLD.salary;
  new_salary := :NEW.salary;
  IF v_old_salary <> v_new_salary THEN
    INSERT INTO sal_log1(empid, empname, old_salary, new_salary, update_date)
    VALUES(:OLD.empid, :OLD.empname, old_salary, new_salary, SYSDATE);
  END IF;
END;
/
-- Insert the values in the employee table
insert into emp2 values(1,'dolu','HR',50000);
insert into emp2 values(2,'Bolu','MANAGER',50000);
insert into emp2 values(3,'raju','sales',50000);

-- Update the salary of an employee
update emp2
set salary=59000
where empid=2;
-- Display the employee table
select * from emp2;

-- Display the salary_logg table
select * from sal_log1;
```

### Output:
![image](https://github.com/RANJEETH17/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120718823/619981aa-8890-4313-ad5b-e4dda1bceaab)
![image](https://github.com/RANJEETH17/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120718823/6be491f3-77a6-41ee-8e24-bcf55204c769)




### Result:
Thus , the output has been successfully verified.
