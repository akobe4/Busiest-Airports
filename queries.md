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


**Average number of arrivals at each airport from 1995 to 2020**
SELECT country_name
	  ,AVG(y_1995 + y_1996 + y_1997 + y_1998 + y_1999 + y_2000 + y_2001 + y_2002
		  + y_2003 + y_2004 + y_2005 + y_2006 + y_2007 + y_2008 + y_2009 + y_2010
		  + y_2011 + y_2012 + y_2013 + y_2014 + y_2015 + y_2016 + y_2017 + y_2018
		  + y_2019 + y_2020) AS av_arrivals
FROM no_arrivals
GROUP BY country_name