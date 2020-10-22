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

### Retrive all employee payroll data from payroll service database
```
select * from employee_payroll;
```

### Retrive salary data from payroll service database based on name and employee payroll details based on joining date
```
select salary from employee_payroll where name='bill';
select * from employee_payroll where start between cast('2018-01-01' as date) and date(now());
```

### Alter table to add gender and update rows to reflect correct employee gender
```
alter table employee_payroll add gender CHAR(1) after name;
update employee_payroll set gender='F' where name='terisa';
update employee_payroll set gender='M' where name='bill' or name='mark';
```
