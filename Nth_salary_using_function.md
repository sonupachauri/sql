```sql

CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN

declare M INT;
set M = N-1;
  RETURN (
      # Write your MySQL query statement below.
    select distinct salary from employee
    order by salary desc
    limit 1, M

  );

RETURN(
  
    select 
          distinct T.salary  
        from(
            select dense_rank() over (
                  order by 
                     salary desc
                ) as salary_rank, salary
            from Employee
        ) as T
        where 
        T.salary_rank = N
);

```
