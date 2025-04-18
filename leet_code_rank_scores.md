```sql

select Score,
     dense_rank() over(order by Score desc) 'Rank' 
from Scores

SELECT S.Score, COUNT(S2.Score) AS 'Rank' FROM Scores S,
(SELECT DISTINCT Score FROM Scores) S2
WHERE S.Score<=S2.Score
GROUP BY S.Id 
ORDER BY S.Score DESC;


SELECT s.Score, count(distinct t.score) Rank
FROM Scores s JOIN Scores t ON s.Score <= t.score
GROUP BY s.Id
ORDER BY s.Score desc

````
