

```sql 
CREATE TABLE employees2  (employee_id int,employee_name varchar(15), email_id varchar(15) );
INSERT INTO employees2 (employee_id,employee_name, email_id) VALUES ('101','Liam Alton', 'li.al@abc.com');
INSERT INTO employees2 (employee_id,employee_name, email_id) VALUES ('102','Josh Day', 'jo.da@abc.com');
INSERT INTO employees2 (employee_id,employee_name, email_id) VALUES ('103','Sean Mann', 'se.ma@abc.com'); 
INSERT INTO employees2 (employee_id,employee_name, email_id) VALUES ('104','Evan Blake', 'ev.bl@abc.com');
INSERT INTO employees2 (employee_id,employee_name, email_id) VALUES ('105','Toby Scott', 'jo.da@abc.com');
INSERT INTO employees2 (employee_id,employee_name, email_id) VALUES ('106','Anjali Chouhan', 'JO.DA@ABC.COM');
INSERT INTO employees2 (employee_id,employee_name, email_id) VALUES ('107','Ankit Bansal', 'AN.BA@ABC.COM');

select * , ASCII(email_id) as ascii_email, rank() over(partition by email_id order by ascii(email_id
as rn from employees2 where email_id = Lower(email_id

--- Case senstive will work after below  query

ALTER TABLE employees2
ALTER COLUMN email_id VARCHAR(15) COLLATE SQL_Latin1_General_CP1_CS_AS;

select * , Lower(email_id) from employees2
where email_id = Lower(email_id)

```
