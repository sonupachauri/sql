```sql

CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN

declare M INT;
set N = N-1;
  RETURN (
      # Write your MySQL query statement below.
          SELECT DISTINCT salary
        FROM Employee e1
        WHERE (
            SELECT COUNT(DISTINCT salary)
            FROM Employee e2
            WHERE e2.salary >= e1.salary
        ) = N
    );

   RETURN (
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

END

```
