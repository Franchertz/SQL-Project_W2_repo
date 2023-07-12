Question 1: find the total number of unique  visitors (fullVisitorID)

SQL Queries:

select		country,
			count(fullvisitorid) TotalCount_Fullisitorid
from		all_sessions_copy
where		fullvisitorid is not null
and			country is not null
group by	country
order by	country
;

Answer: 136 rows



Question 2: find the total number of unique visitors by referring sites

SQL Queries:

select		distinct(fullvisitorid) UniqueVisitorid,
			count(*),
			timeonsite
from		all_sessions_copy
where		timeonsite is not null
and			fullvisitorid is not null
group by	1, 3
order by	2 desc;


Answer: 11313 rows



Question 3: find each unique product viewed by each visitor

SQL Queries:

select		distinct(alc.productsku) UniqueProduct,
			alc.city,
			alc.country,
			count(alc.fullvisitorid) VisitorCount
from		sales_report_copy src
join		all_sessions_copy alc
on			src.productsku = alc.productsku
where		alc.country is not null
and 		alc.city is not null
group by	1, 2, 3
---order by	UniqueProduct desc
;


Answer: 4894 rows



