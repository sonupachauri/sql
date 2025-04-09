https://www.youtube.com/watch?v=G-5Mm8ezt3I&list=PLBTZqjSKn0IcR6DhoLUibOG8frnWbZdSH&index=6

```sql
create table products (
  id int,
  name varchar(10)
);
insert into products VALUES 
(1, 'A'),
(2, 'B'),
(3, 'C'),
(4, 'D'),
(5, 'E');

create table colors (
  color_id int,
  color varchar(50)
);
insert into colors values (1,'Blue'),(2,'Green'),(3,'Orange');

create table sizes
(
  size_id int,
  size varchar(10)
);

insert into sizes values (1,'M'),(2,'L'),(3,'XL');

create table transactions
(
  order_id int,
  product_name varchar(20),
  color varchar(10),
  size varchar(10),
  amount int
);
insert into transactions values (1,'A','Blue','L',300),(2,'B','Blue','XL',150),(3,'B','Green','L',250),(4,'C','Blue','L',250),
(5,'E','Green','L',270),(6,'D','Orange','L',200),(7,'D','Green','M',250);


with master_data as (
select p.name as product_name,c.color, s.size from products p , colors c , sizes s),
sales as (
select product_name,color,size,sum(amount) as total_amount from transactions
group by product_name,color,size)

select md.product_name,md.color,md.size, IFNULL(s.total_amount,0) as total_amount from master_data md
left JOIN sales s on md.product_name = s.product_name and  md.color = s.color and md.size = s.size
order by s.total_amount desc
;

```
