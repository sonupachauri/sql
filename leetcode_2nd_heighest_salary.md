```sql 
Table: Employee

+-------------+------+
| Column Name | Type |
+-------------+------+
| id          | int  |
| salary      | int  |
+-------------+------+
id is the primary key (column with unique values) for this table.
Each row of this table contains information about the salary of an employee.

Write a solution to find the second highest distinct salary from the Employee table. If there is no second highest salary, return null (return None in Pandas).

The result format is in the following example.

Example 1:

Input: 
Employee table:
+----+--------+
| id | salary |
+----+--------+
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |
+----+--------+
Output: 
+---------------------+
| SecondHighestSalary |
+---------------------+
| 200                 |
+---------------------+
Example 2:

Input: 
Employee table:
+----+--------+
| id | salary |
+----+--------+
| 1  | 100    |
+----+--------+
Output: 
+---------------------+
| SecondHighestSalary |
+---------------------+
| null                |
+---------------------+

select ifnull((
select salary from Employee order by salary desc limit 1,1), null) as  SecondHighestSalary;

select ifnull(
(select x.salary from 
  (select salary, row_number() over(order by salary desc) as rn from Employee) x
where x.rn = 2),null) as SecondHighestSalary

SELECT 
  (
    SELECT DISTINCT salary AS SecondHighestSalary
    FROM Employee
    ORDER BY salary DESC
    LIMIT 1, 1
  ) AS SecondHighestSalary;

```
