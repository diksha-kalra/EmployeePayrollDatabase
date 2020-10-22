# EmployeePayrollDatatbase

### Create payroll service database
```
create payroll_service;
show databases;
use payroll_service;
```

### Create Employee Payroll table in Payroll Service Database
```
create table employee_payroll
(
id          INT unsigned NOT NULL AUTO_INCREMENT,
name        VARCHAR(150) NOT NULL,
salary      Double NOT NULL,
start       DATE NOT NULL,
PRIMARY KEY (id)
);
```
