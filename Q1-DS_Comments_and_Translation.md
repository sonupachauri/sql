```sql
 Write an SQL query to display the correct message (meaningful message) from the input
comments_and_translation table. */

drop table comments_and_translations;
create table comments_and_translations
(
	id				int,
	comment			varchar(100),
	translation		varchar(100)
);

insert into comments_and_translations values
(1, 'very good', null),
(2, 'good', null),
(3, 'bad', null),
(4, 'ordinary', null),
(5, 'cdcdcdcd', 'very bad'),
(6, 'excellent', null),
(7, 'ababab', 'not satisfied'),
(8, 'satisfied', null),
(9, 'aabbaabb', 'extraordinary'),
(10, 'ccddccbb', 'medium');
commit;


SELECT  (case
         when translation is null then comment else translation 
      END)  output FROM comments_and_translations

   SELECT coalesce(translation,comment) as outputs
      from comments_and_translations
```
