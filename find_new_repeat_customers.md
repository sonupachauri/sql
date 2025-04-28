```sql

create table customer_orders (
order_id integer,
customer_id integer,
order_date date,
order_amount integer
);
select * from customer_orders
insert into customer_orders values(1,100,'2022-01-01',2000),(2,200,'2022-01-01',2500),(3,300,'2022-01-01',2100)
,(4,100,'2022-01-02',2000),(5,400,'2022-01-02',2200),(6,500,'2022-01-02',2700)
,(7,100,'2022-01-03',3000),(8,400,'2022-01-03',1000),(9,600,'2022-01-03',3000);




with first_visit_date as 
(select customer_id, min(order_date) as first_visit_date from customer_orders
group by customer_id)

select co.order_id
   , SUM(case when co.order_date = fv.first_visit_date then 1 else 0 end) as new_customer
   , SUM(case when co.order_date != fv.first_visit_date then 1 else 0 end ) as repeat_customer
from customer_orders as co
join first_visit_date as fv on co.customer_id = fv.customer_id
GROUP by co.order_date
order by order_id


```
