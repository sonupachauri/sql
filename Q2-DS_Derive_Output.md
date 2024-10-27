```sql
DROP TABLE source;
CREATE TABLE source
    (
        id      int,
        name    varchar(1)
    );

DROP TABLE target;
CREATE TABLE target
    (
        id      int,
        name    varchar(1)
    );

INSERT INTO source VALUES (1, 'A');
INSERT INTO source VALUES (2, 'B');
INSERT INTO source VALUES (3, 'C');
INSERT INTO source VALUES (4, 'D');

INSERT INTO target VALUES (1, 'A');
INSERT INTO target VALUES (2, 'B');
INSERT INTO target VALUES (4, 'X');
INSERT INTO target VALUES (5, 'F');

COMMIT;

select s.id, 'Mismatch' as outputs from source s
JOIN target t on s.id = t.id and s.name <> t.name

UNION
select s.id, 'New in source' as outputs from source s
left JOIN target t on s.id = t.id
where t.id is NULL

UNION
select t.id, 'New in target' as outputs from source s
RIGHT JOIN target t on s.id = t.id
where s.id is NULL
```