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
ORDER BY gdp_rank; 
```

![Alt text](image-1.png)


**Number of passengers at each airport as a percentage of their country's 2019 total number of international tourism arrivals*
need to keep in mind that the number of passesngers might include both incoming and outgoing as well as domestic travellers. We also don't know what year the number of passengers at each airport is from. 

```SQL
SELECT ai.airport_name
	  ,ROUND((ai.no_passengers/n.y_2019)* 100, 2) AS perc_total_passengers
FROM airports ai
LEFT JOIN no_arrivals n ON ai.country = n.country_name
ORDER BY airport_name;
```

![Alt text](image-2.png)

As seen in the results some airports have a percentage of over 100 of their country's total international arrivals, this is not the best way to view this data. 


**Query of airports, their region and income group**

```SQL
SELECT ai.airport_rank
	  ,ai.airport_name
	  ,ai.country
	  ,me.region
	  ,me.income_group
FROM airports ai
LEFT JOIN metadata me ON ai.country = me.name;
```

![Alt text](image-3.png)


**Query of which regions have the highest total number of airline passengers**

```SQL
SELECT me.region
	  ,SUM(ai.no_passengers) AS total_passengers 
FROM airports ai 
LEFT JOIN metadata me ON ai.country = me.name
GROUP BY me.region
ORDER BY total_passengers DESC;
```

![Alt text](image-6.png)


**Query of which income group has the highest average number of passengers**

```SQL
SELECT me.income_group
	  ,ROUND(AVG(ai.no_passengers)) AS av_passengers 
FROM airports ai 
LEFT JOIN metadata me ON ai.country = me.name
GROUP BY me.income_group
ORDER BY av_passengers DESC;
```

![Alt text](image-5.png)

