Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
select		*
from		all_sessions_copy
where		transactionrevenue is not null
;

select		city,
			country,
			max(transactionrevenue) HighestTransactionLevel
from		all_sessions_copy
where		transactionrevenue is not null
group by	country, city
order by	HighestTransactionLevel desc
;


Answer:
City is unknown or blanck
Country is United States with 1015(x1000000) transactions



**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:
select		*
from		sales_report_copy;

select		*
from		all_sessions_copy;

select		alc.city,
			alc.country,
			Round(Avg(src.total_ordered), 2) AverageNumber_Products
from		sales_report_copy src
join		all_sessions_copy alc
on			src.productsku = alc.productsku
where		alc.country is not null
and 		alc.city is not null
group by	alc.country, alc.city
order by	AverageNumber_Products desc
;


Answer: a total of 366 rows





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:

select		*
from		all_sessions_copy
;

select		city,
			country
			----v2productcategory
from		all_sessions_copy
where		v2productcategory ~ '^.*$'
and			city is not null
and 		country is not null
group by	1, 2
order by	2 desc
;

Answer: a total of 417 rows




**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries: 

select		*
from		all_sessions_copy;

select		city,
			country,
			alc.v2productcategory,
			max(src.total_ordered) TopSellingProduct
from		sales_report_copy src
join		all_sessions_copy alc
on			src.productsku = alc.productsku
where		alc.v2productcategory ~ '^.*$'
and			city is not null
and 		country is not null
group by	2, 1, 3
order by	TopSellingProduct desc
--limit		100;



Answer: The pattern of products sold are in the Home/Office products





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:

select		*
from		all_sessions_copy;


select		city,
			country,
			case
				when	transactionrevenue <= 200 then 'low'
				else 'high'
			end	RevenueImpact
from		all_sessions_copy
where		transactionrevenue is not null
and			city is not null
and 		country is not null
group by	2, 1, 3
order by	RevenueImpact ---desc
;



Answer: 
Lowest impact is in sunnyvale and
Highest impact is in the United States, city not identified







