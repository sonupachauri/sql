https://www.youtube.com/watch?v=O6mDdUIvx9k&list=PLBTZqjSKn0IcR6DhoLUibOG8frnWbZdSH&index=2
```sql
 create table emp(
    emp_id int not null AUTO_INCREMENT,
    emp_name varchar(255),
    department_id int,
    salary int,
    manager_id int,
    PRIMARY KEY (emp_id) 
 );

 insert into emp(emp_name,department_id,salary,manager_id) values('Ankit',100,10000,4);
 insert into emp(emp_name,department_id,salary,manager_id) values('Mohit',100,15000,5);
 insert into emp(emp_name,department_id,salary,manager_id) values('Vikas',100,10000,4);
 insert into emp(emp_name,department_id,salary,manager_id) values('Rohit',100,5000,2);
 insert into emp(emp_name,department_id,salary,manager_id) values('Mudit',200,12000,6);
 insert into emp(emp_name,department_id,salary,manager_id) values('Agam',200,12000,2);
 insert into emp(emp_name,department_id,salary,manager_id) values('Sanjay',200,9000,2);
 insert into emp(emp_name,department_id,salary,manager_id) values('Ashish',200,5000,2);


 select * from emp;
 where salary  > 10000;

 select department_id, avg(salary) from emp
 group by department_id
 having(avg(salary)) > 9500

select department_id,avg(salary) from emp
where salary > 10000
group by department_id
having avg(salary) > 12000

```

