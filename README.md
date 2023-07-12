# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project
This project is about Transforming and Analyzing Data with SQL

## Goals
The goal is to use the various techniques and skills learned to:

a. Load datasets into a database.

b. Clean, transform and analyze dataset, and 

c. Validate transformed dataset by developing and implementing a QA process.

## Process
A. Loading Datasets into Database

Please note Postgresql will be the SQL language used and pgadmin4 will be the database tool that will be used.

       1. Log into pgadmin4
       2. Create the ecommerce database 
       
       3. Five datasets in csv format have
          been provided that 
          represent the tables that will be created in the ecommerce database. 
          The csv files are:
          all_seesions.csv,
          analytics.csv,
          products.csv,
          sales_report.csv and 
          sales_by_sku.csv.

        4. Open each file in excel to 
           study and then extract the column 
           names as well as determine data type for each column.


        5. In pgadmin4, tables were created 
           based on the file names and each
           csv file was inserted into their respective tables. See filename 
           Loading cvs files for the query used.


### B. Clean, transform and analyze datasets

        1.  Created copies of each table.
            This will help
            make changes to each tables
            to compare tables with orignal tables
            I can drop the tables where necessary.

        2. Cleaned tables and made 
           changes,following the giude below
           Remove irrelevant data;
           Remove duplicates;
           Fix structural errors;
           Data type conversions where necessary;
           Deal with missing data;
           Deal with outliers.

        3. Analysing the data
           Looking out for relationships





## Results
        This database provided:
        Information or data on revenue by product 
        How each site visit interacted with the various products
        Information or data on site vists with Country and their respective cities
        Information or data on number of pages viewed while on site
        Information or data tarnsactions with each site visit
        
       Once the relationship with the tables where established, that is figuring out the 
       primary and foreign keys

## Challenges 
         Challenges incldue:
         a. The datssets were missing alot
            of information.
         b. Alot of errors while insertin
            the values into the tables in pgadmin4,
            was resolved by getting the right data types.
         c. Writing the queries

## Future Goals
    If I had more time, I would say it is relative.
     I would like to say, if I had more practice, my result would be better than this.
     Hence, practice, practice, practice is my future goal.
