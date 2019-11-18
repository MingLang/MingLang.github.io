---
layout: post
title: Temp table vs table variable vs cte
category: SQL
tags: [SQL, Temp table]
--- 

All are used to store data temporarily.

Below are some points about the differences and when to use which.

<https://www.linkedin.com/pulse/cte-vs-temp-table-variable-ajay-kumar>:
>**Note**
>* Temp Tables are physically created in the Tempdb database. These tables act as the normal table and also can have constraints, index-like normal tables.
>* CTE is a named temporary result set which is used to manipulate the complex sub-queries data. This exists for the scope of a statement. This is created in memory rather than Tempdb database. You cannot create any index on CTE.
>* Table Variable acts like a variable and exists for a particular batch of query execution. It gets dropped once it comes out of a batch. This is also created in the Tempdb database but not the memory.

<https://www.mssqltips.com/sqlservertip/5118/sql-server-cte-vs-temp-table-vs-table-variable-performance-test/>:
>As mentioned at the start of the article, a CTE is not quite as versatile as temporary tables and table variables, but we’ve shown here that for individual queries that require temporary/staged data it can be a good option to improve performance.  Remember though when dealing with query performance to always test with your own queries/data as there are many variables that can affect performance and different use cases could lead to another option giving better performance.


<https://www.mssqltips.com/sqlservertip/1556/differences-between-sql-server-temporary-tables-and-table-variables/>:
>An unofficial rule-of-thumb for usage is to use table variables for returning results from user-defined functions that return table values and to use temporary tables for storage and manipulation of temporary data; particularly when dealing with large amounts of data. However, when lesser row counts are involved, and when indexing is not a factor, both table variables and temporary tables perform comparably. It then comes down to preference of the individual responsible for the coding process.



