Code for table creatation

Airport Table 

```SQL
CREATE TABLE airports (
     airport_rank int
    ,airport_name varchar(255)
    ,code varchar(3)
    ,city varchar(255)
    ,country varchar(255)
	,no_passengers int
);
```

```SQL
COPY airports
FROM 'C:\Users\akobe\OneDrive\Desktop\Lighthouse\After\Busiest-Airports\Data\top_100_busiest_airports.csv'
DELIMITER ','
CSV Header;
```

Metadata Table
```SQL
CREATE TABLE metadata (
     country_code varchar(3)
    ,region varchar(255)
    ,income_group varchar(255)
    ,name varchar(255)
);
```

```SQL
COPY metadata
FROM 'C:\Users\akobe\OneDrive\Desktop\Lighthouse\After\Busiest-Airports\Data\country_metadata.csv'
DELIMITER ','
CSV Header;
```

Number of Arrivals Table 
```SQL
CREATE TABLE no_arrivals (
     country_name varchar(255)
    ,country_code varchar(3)
    ,y_1995 int
    ,y_1996 int
    ,y_1997 int
    ,y_1998 int
    ,y_1999 int
    ,y_2000 int
    ,y_2001 int
    ,y_2002 int
    ,y_2003 int
    ,y_2004 int
    ,y_2005 int  
    ,y_2006 int
    ,y_2007 int  
    ,y_2008 int
    ,y_2009 int
    ,y_2010 int
    ,y_2011 int 
    ,y_2012 int
    ,y_2013 int 
    ,y_2014 int
    ,y_2015 int 
    ,y_2016 int
    ,y_2017 bigint 
    ,y_2018 bigint
    ,y_2019 bigint 
    ,y_2020 int
);
```

```SQL
COPY no_arrivals
FROM 'C:\Users\akobe\OneDrive\Desktop\Lighthouse\After\Busiest-Airports\Data\arrival_info.csv'
DELIMITER ','
CSV Header;
```

**Population Table** 
data taken from:  https://simplemaps.com/data/world-cities
Went through populaltion table in comparison to the airports table and deleted the cities that have the same name, but are not the one as given by airport name. These rows were deleted from the population table prior to importing to SQL.

```SQL
CREATE TABLE population (
     city varchar(255)
	,lat numeric
	,long numeric
    ,country varchar(255)
    ,country_code varchar(3)
    ,population int
);
```

```SQL
COPY population
FROM 'C:\Users\akobe\OneDrive\Desktop\Lighthouse\After\Busiest-Airports\Data\worldcities.csv'
DELIMITER ','
CSV Header;
```
**GDP Table**
data taken from: https://data.worldbank.org/indicator/NY.GDP.MKTP.CD
Figures from 2022
All values are in USD

```SQL

```