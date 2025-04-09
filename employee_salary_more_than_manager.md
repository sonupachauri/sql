-- https://www.youtube.com/watch?v=G7v7TZ3ylDI&list=PLBTZqjSKn0IcR6DhoLUibOG8frnWbZdSH&index=4

create table emp_manager(emp_id int,emp_name varchar(50),salary int(20),manager_id int(10));
insert into emp_manager values(	1	,'Ankit',	10000	,4	);
insert into emp_manager values(	2	,'Mohit',	15000	,5	);
insert into emp_manager values(	3	,'Vikas',	10000	,4	);
insert into emp_manager values(	4	,'Rohit',	5000	,2	);
insert into emp_manager values(	5	,'Mudit',	12000	,6	);
insert into emp_manager values(	6	,'Agam',	12000	,2	);
insert into emp_manager values(	7	,'Sanjay',	9000	,2	);
insert into emp_manager values(	8	,'Ashish',	5000	,2	);

SELECT e1.emp_id,e1.emp_name, e2.salary,e2.emp_name  from emp_manager e1
join emp_manager e2 on e1.manager_id = e2.emp_id and e1.salary > e2.salary;
