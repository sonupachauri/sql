```sql 
/* There are 10 IPL team. write an sql query such that each team play with every other team just once. */

drop table teams;
create table teams
    (
        team_code       varchar(10),
        team_name       varchar(40)
    );

insert into teams values ('RCB', 'Royal Challengers Bangalore');
insert into teams values ('MI', 'Mumbai Indians');
insert into teams values ('CSK', 'Chennai Super Kings');
insert into teams values ('DC', 'Delhi Capitals');
insert into teams values ('RR', 'Rajasthan Royals');
insert into teams values ('SRH', 'Sunrisers Hyderbad');
insert into teams values ('PBKS', 'Punjab Kings');
insert into teams values ('KKR', 'Kolkata Knight Riders');
insert into teams values ('GT', 'Gujarat Titans');
insert into teams values ('LSG', 'Lucknow Super Giants');
commit;


--SELECT t1.team_code,t2.team_name FROM teams t1
--JOIN teams t2 on t1.team_name <> t2.team_name

with matches as
  (SELECT row_number() over (order by team_name) as ID, team_code,team_name from teams t)
  
 SELECT m.team_name,o.team_name from matches m 
 join matches o on m.id < o.id

```
