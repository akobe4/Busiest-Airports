**Code for table creatation**

**Airport Table** 
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

**Metadata Table**
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

**Number of Arrivals Table** 
```SQL
CREATE TABLE no_arrivals (
     country_name varchar(255)
    ,country_code varchar(3)
    ,y_1995 numeric
    ,y_1996 numeric
    ,y_1997 numeric
    ,y_1998 numeric
    ,y_1999 numeric
    ,y_2000 numeric
    ,y_2001 numeric
    ,y_2002 numeric
    ,y_2003 numeric
    ,y_2004 numeric
    ,y_2005 numeric
    ,y_2006 numeric
    ,y_2007 numeric
    ,y_2008 numeric
    ,y_2009 numeric
    ,y_2010 numeric
    ,y_2011 numeric
    ,y_2012 numeric
    ,y_2013 numeric
    ,y_2014 numeric
    ,y_2015 numeric
    ,y_2016 numeric
    ,y_2017 numeric
    ,y_2018 numeric
    ,y_2019 numeric
    ,y_2020 numeric
);
```

```SQL
COPY no_arrivals
FROM 'C:\Users\akobe\OneDrive\Desktop\Lighthouse\After\Busiest-Airports\Data\arrival_info.csv'
DELIMITER ','
CSV Header;
```

**Population Table** 
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
```SQL
CREATE TABLE gdp (
     country_name varchar(255)
    ,country_code varchar(3)
    ,gdp numeric
);
```

```SQL
COPY gdp
FROM 'C:\Users\akobe\OneDrive\Desktop\Lighthouse\After\Busiest-Airports\Data\country_gdp.csv'
DELIMITER ','
CSV Header;
```