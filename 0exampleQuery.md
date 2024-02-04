
## Examples of Queries

```
SELECT 
 ORIGIN,
 COUNT(*) AS num_flights
FROM dsongcp123ass4.flights
GROUP BY ORIGIN
ORDER BY num_flights DESC
LIMIT 10
```

