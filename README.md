# EmployeePayrollDatatbase

### UC1 Create payroll service database
```
create payroll_service;
show databases;
use payroll_service;
```

### UC2 Create Employee Payroll table in Payroll Service Database
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

### UC3 Create Employee Payroll data in Payroll Service Database as a part of CRUD operation
```
insert into employee_payroll (name,salary,start) VALUES
('mark', 50000, '2020-01-02'),
('bill', 50000, '2018-01-03'),
('terisa', 200000, '2019-11-13');
```

### UC4 Retrive all employee payroll data from payroll service database
```
select * from employee_payroll;
```

### UC5 Retrive salary data from payroll service database based on name and employee payroll details based on joining date
```
select salary from employee_payroll where name='bill';
select * from employee_payroll where start between cast('2018-01-01' as date) and date(now());
```

### UC6 Alter table to add gender and update rows to reflect correct employee gender
```
alter table employee_payroll add gender CHAR(1) after name;
update employee_payroll set gender='F' where name='terisa';
update employee_payroll set gender='M' where name='bill' or name='mark';
```

### UC7 Find sum avg min max and number of male and female employees
```
select sum(salary) from employee_payroll where gender='F' group by gender;
select sum(salary) from employee_payroll where gender='M' group by gender;
select avg(salary) from employee_payroll where gender='M' group by gender;
select gender, min(salary) from employee_payroll group by gender;
select gender, max(salary) from employee_payroll group by gender;
select gender, count(name) from employee_payroll group by gender;
```

### UC8 Extend employee payroll data to store phone number, address and department
```
alter table employee_payroll add phone_number VARCHAR(250) after name;
alter table employee_payroll add address VARCHAR(250) after phone_number;
alter table employee_payroll add department VARCHAR(250) NOT NULL after address;
alter table employee_payroll alter adress set default 'TBD';
describe employee_payroll;
select * from employee_payroll;
insert into employee_payroll (name, salary, start) VALUES('Charles', 10000, '2018-01-03');
```

### UC9 Extend employee payroll table to have basic pay, deductions, taxable, income tax, and net pay
```
alter table employee_payroll rename colum salary to basic_pay;
alter table employee_payroll add deductions Double NOT NULL after basic_pay;
alter table employee_payroll add taxable_pay Double NOT NULL after deductions;
alter table employee_payroll add tax Double NOT NULL after taxable_pay;
alter table employee_payroll add net_pay Double NOT NULL after tax;
```

### UC10.1 Make terisa as a part of sales and marketing department
```
update employee_payroll set department='Sales' where name='terisa';
insert into employee_payroll (name, department, gender, basic_pay, deductions, taxable_pay, tax, net_pay, start)
VALUES('terisa', 'Marketing', 'F', 3000000, 100000, 2000000, 500000, 1500000, '2018-01-01');
```
  
### UC11 Implement ER diagram into payroll service DB
```
create table company (
company_id int NOT NULL PRIMARY KEY,
company_name VARCHAR(250) NOT NULL);

create table employee_details(
emp_id int unsigned NOT NULL AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(50) NOT NULL,
company_id int,
phone_number VARCHAR(50) NOT NULL,
address VARCHAR(250) NOT NULL,
gender CHAR(1),
start DATE NOT NULL,
FOREIGN KEY (company_id) REFERENCES company (company_id)
)ENGINE=INNODB;

create table department (
dept_id int NOT NULL PRIMARY KEY,
dep_name VARCHAR(150) NOT NULL
);

create table payroll (
emp_id int unsigned NOT NULL AUTO_INCREMENT,
basic_pay Double NOT NULL,
deductions Double NOT NULL,
taxable_pay Double NOT NULL,
tax Double NOT NULL,
net_pay Double NOT NULL,
FOREIGN KEY (emp_id) REFERENCES employee_details(emp_id)
);

create table employee_department (
emp_id int unsigned NOT NULL AUTO_INCREMENT,
dept_id int NOT NULL,
FOREIGN KEY (emp_id) REFERENCES employee_details(emp_id),
FOREIGN KEY (dept_id) REFERENCES department(dept_id)
);
```
