What are your risk areas? Identify and describe them.

My risk areas are as follows:

    1. Duplicate data: alot of multiple records 
       belonging to the same entity were stored.

    2. Incomplete data: important fields
       were empty in the datasets provided.

    3. Inconsistent formats and patterns: 
       The same data were stored in multiple formats and patterns, rather than following the standardized format and pattern.

    4. Missing dependencies: Certain data 
       fields were left blank since their dependent fields are empty. For example, transactionrevenue column in all_sessions_copy table.

    5. Different measurement units: data field
       in multiple measuring units, causing you to lack a standardized unit scale of measurement.



QA Process:
Describe your QA process and include the SQL queries used to execute it.

#### Task 1.  data profiling: Checking data type, Null values and unique values

select		*
from		information_schema.tables
where		table_schema = 'public'
;

-- To check for data types and null values

select		column_name,
			data_type,
			is_nullable
from		information_schema.columns
where		table_name = 'all_sessions_copy'
;

select		column_name,
			data_type,
			is_nullable
from		information_schema.columns
where		table_name = 'all_sessions_copy'
;

select		column_name,
			data_type,
			is_nullable
from		information_schema.columns
where		table_name = 'analytics_copy'
;

select		column_name,
			data_type,
			is_nullable
from		information_schema.columns
where		table_name = 'products_copy'
;

select		column_name,
			data_type,
			is_nullable
from		information_schema.columns
where		table_name = 'sales_by_sku_copy'
;

select		column_name,
			data_type,
			is_nullable
from		information_schema.columns
where		table_name = 'sales_report_copy'
;

--- to count unique values for the country column

select		count(distinct country)
from		all_sessions_copy
;

#### Task 2. Data Validation: checking for missing values and duplicates

--   Missing Values - Alot of missing values

select		*
from		all_sessions_copy
where		transactionrevenue is null
;

--  Duplicates _ Alot of Duplicates

select		fullvisitorid,
			count(*)
from		all_sessions_copy
group by	fullvisitorid
having 		count(*) > 1
;


#### Task 3. Data Cleansing: missing or inconsistent data

--  Standardize the transactionrenevenu column in the all_sessions_copy table data by dividing 1,000,000.

select		*
from		all_sessions_copy
where		transactionrevenue is not null;

update		all_sessions_copy
set			transactionrevenue = cast(transactionrevenue/1000000 as decimal(10, 2));


#### Task 4.  Testing

--  Testing the dates in all_sessions_copy table

select		*
from		all_sessions_copy
where		date < '1900-01-01'
;