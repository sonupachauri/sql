```sql
create table emp_compensation (
emp_id int,
salary_component_type varchar(20),
val int
);
insert into emp_compensation
values (1,'salary',10000),(1,'bonus',5000),(1,'hike_percent',10)
, (2,'salary',15000),(2,'bonus',7000),(2,'hike_percent',8)
, (3,'salary',12000),(3,'bonus',6000),(3,'hike_percent',7);
select * from emp_compensation;
```
################################################################
```sql
SELECT emp_id,
sum(case WHEN salary_component_type='salary' then val end) as salary ,
sum(case WHEN salary_component_type='bonus' then val end) as bonus ,
sum(case WHEN salary_component_type='hike_percent' then val end) as hike_percent
FROM emp_compensation
group by emp_id
```
################################################################
```
select * from (
select emp_id, 'salary' as salary_coomponent_type, salary as val from emp_compensation_pivot
union all
select emp_id, 'bonus' as salary_coomponent_type, bonus as val from emp_compensation_pivot
union all 
select emp_id, 'hike_percent' as salary_coomponent_type, hike_percent as val from emp_compensation_pivot
) a

order by emp_id
```
