**Number of passengers per capita**
The number of passengers per capita (city) 

```SQL
SELECT ai.airport_name
	  ,ai.city
	  ,ai.country
	  ,TRUNC((ai.no_passengers::numeric/po.population::numeric), 1) AS passengers_per_capita 
FROM airports ai
LEFT JOIN population po ON ai.city = po.city
ORDER BY ai.city;
```

![Alt text](image.png)


**Do countries with the busiest airports (by number of passengers) have higher GDP**

```SQL
SELECT ai.country 
	   ,SUM(ai.no_passengers) AS total_passengers
	   , RANK () OVER(
	    ORDER BY SUM(ai.no_passengers) DESC
	   ) passenger_rank
	   	,SUM(gd.gdp) AS total_gdp 
	   ,RANK () OVER(
	    ORDER BY SUM(gd.gdp) DESC NULLS LAST
	   ) gdp_rank 
FROM airports ai
LEFT JOIN gdp gd ON ai.country = gd.country_name
GROUP BY ai.country
ORDER BY gdp_rank 
```

![Alt text](image-1.png)

