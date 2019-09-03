---
layout: post
title: Cannot run SQL with table variables or temp tables in Excel
category: SQL
tags: [SQL, Excel, SET NOCOUNT ON]
--- 

Using `SET NOCOUNT ON` at the top of the query.

When a table variable or a temp table is used in a query, the server returns a *X row(s) affected* message where *X* is the number of rows of the table variable or the temp table. `SET NOCOUNT ON` stops the server returning this message.

Treb explained the reason [here](https://stackoverflow.com/a/25743182/8403973):

>It was caused by a *... row(s)* affected message being returned from the server. Apparently, Excel can't deal with this message correctly, and the returned data is ignored. Once I used SET NOCOUNT ON in my SP, the data was displayed correctly in Excel.



