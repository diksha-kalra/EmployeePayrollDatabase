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

### Create Employee Payroll data in Payroll Service Database as a part of CRUD operation
```
insert into employee_payroll (name,salary,start) VALUES
('mark', 50000, '2020-01-02'),
('bill', 50000, '2018-01-03'),
('terisa', 200000, '2019-11-13');
```
