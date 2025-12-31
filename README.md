# Optimization & Transformations  
**By: Taran Schlichtmann**
**Date: 11/02/2025**

SQL, Snowflake Features, and Data Engineering Workflows

Applying SQL techniques, Snowflake optimization features, and data‑engineering‑oriented transformations. The assignment required writing SQL, performing controlled table modifications, rolling back changes using Snowflake Time Travel, and exporting results into Excel for documentation.

------------------------------------------------------------
Overview
------------------------------------------------------------

This assignment demonstrates proficiency in:

- Window functions and analytical SQL  
- Multi‑step transformations using subqueries  
- Time‑based calculations (DATEDIFF, MONTH)  
- Snowflake Time Travel (UNDROP, BEFORE STATEMENT)  
- Table cloning for development environments  
- Query history inspection via `information_schema.query_history()`  
- Clean SQL formatting following a style guide  
- Exporting reproducible results to Excel  

All work was executed in Snowflake using the **CLASSWORK** warehouse and the **WEATHER** database.

------------------------------------------------------------
Repository Contents
------------------------------------------------------------

GB882_Assignment 6_Optimization & Transformation_Schlichtmann_T.txt  
    All SQL statements written for the assignment.

GB883_Assignment 6 - Optimization & Transformations_Schlichtmann_T.xlsx  
    Excel workbook containing results for Queries #1–5.

GB883_Assignment 6 - Optimization & Transformations_Query 11_Schlichtmann_T.xlsx  
    Excel workbook containing query history results.

README.md  
    Documentation and context for the assignment.

------------------------------------------------------------
Assignment Summary
------------------------------------------------------------

Query 1 — Storm Events & Crop Damage by Reference Location  
Counted storm events and summed crop damage, concatenating state and county FIPS codes to form a unified reference location.  
Filtered to county‑level events (cz_type = 'C') and sorted by damage and event count.

Result Insight:  
The reference location with the most crop damage was **48 - 409 - ST PAUL**.

------------------------------------------------------------

Query 2 — Event Duration in Minutes  
Calculated event duration using `DATEDIFF(MINUTES, ...)` and sorted from longest to shortest.

Result Insight:  
The longest event lasted **44,639 minutes**.

------------------------------------------------------------

Query 3 — Categorizing Events by Duration  
Used a subquery to classify events as **“under an hour”** or **“at least an hour”**, then counted each category.

Result Insight:  
There were **36,432** events under an hour.

------------------------------------------------------------

Query 4 — Storm Events by Weather Forecast Office (WFO) and Month  
Grouped events by WFO and month using `event_begin_time`.

Result Insight:  
The Albany office (ALY) recorded **79** storm events in October.

------------------------------------------------------------

Query 5 — Monthly and Annual Event Totals by WFO  
Extended the previous query with a window function to compute total annual events per WFO.

Result Insight:  
The Bismarck office (BIS) recorded **850** total storm events during the year.

------------------------------------------------------------
Snowflake Feature Demonstrations
------------------------------------------------------------

Query 6 — Dropping the `severe_weather` Table  
Executed a controlled table drop.

Query 7 — Restoring the Table  
Used **UNDROP TABLE** to restore the dataset and verified the restoration.

Query 8 — Updating All Event Types  
Updated all event types to `"spilled milk"` for demonstration purposes.

Query 9 — Rolling Back Changes  
Used **Time Travel** with `BEFORE (statement => ...)` to restore the table to its pre‑update state.  
Verified rollback accuracy.

Query 10 — Cloning a Table for Development  
Created a development copy:  
`CREATE TABLE state_sizes_dev CLONE state_sizes;`

Query 11 — Query History  
Retrieved recent query history using `information_schema.query_history()` and exported results.

------------------------------------------------------------
Tools & Technologies
------------------------------------------------------------

- Snowflake (SQL execution, Time Travel, table cloning, staging)
- Excel (result storage & reporting)
- SQL Style Guide (formatting & readability standards)

------------------------------------------------------------
Skills Demonstrated
------------------------------------------------------------

- Analytical SQL (window functions, subqueries, CASE logic)
- Data engineering workflows in Snowflake
- Time Travel rollback and table restoration
- Controlled schema changes and environment cloning
- Query performance awareness via query history
- Clean, maintainable SQL following best practices
- Reproducible result documentation in Excel
