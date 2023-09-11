**airports**

Data taken from: https://www.kaggle.com/datasets/batrosjamali/top-100-airports-of-the-world

- airport_rank
- airport_name
- code (airport code)
- city (city where the airport is located)
- country (country where the airport is located)
- no_passengers (number of passengers)


**gdp**

Data taken from: https://data.worldbank.org/indicator/NY.GDP.MKTP.CD
Figures from 2022 - GDP by country 

- country_name
- country_code (alpha-3 iso code of the country)
- gdp (USD)

**metadata**

Data taken from: https://data.worldbank.org/indicator/ST.INT.ARVL 

- country_code (alpha-3 iso code of the country)
- region (East Asia & Pacific, Middle East & North Africa, Europe & Central Asia, Latin America & Caribbean, North America, Sub_Saharan Africa, South Asia, NULL)
- income_group (upper middle income, lower middle income, low income, high income, NULL)
- name (country name)

**no_arrivals**

Data taken from: https://data.worldbank.org/indicator/NY.GDP.MKTP.CD

- country_name
- country_code (alpha-3 iso code of the country)
- y_1995 to y_2020 (number of international tourism arrivals per year)


**population**

Data taken from:  https://simplemaps.com/data/world-cities
Went through populaltion table in comparison to the airports table and deleted the cities that have the same name, but are not the correct city as per airport name. These rows were deleted from the population table prior to importing to SQL.

- city 
- lat (latitude of the city/town)
- long (longitude of the city/town)
- country (country name)
- country_code (alpha-3 iso code of the country)
- population (estimate of the city's urban population, where urban population is not available the municipal population is used)