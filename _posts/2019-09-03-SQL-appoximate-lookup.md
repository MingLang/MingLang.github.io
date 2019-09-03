---
layout: post
title: SQL approximate lookup
category: SQL
tags: [SQL, lookup]
--- 

Assume we have two tables as below: tblStudents and tblGroup.

### tblStudents

| Name | Age |
| --- | --- |
| Adam | 3 |
| Bob | 5 |
| Chris | 8 |
| David | 12 |
| Eric | 18 |

### tblGroup

|Age|AgeGroup|
|---|---|
|0|A|
|5|B|
|10|C|
|15|D|

Now we want to add a column of AgeGroup in tblStudents showing which age group each student is in. What we need here is basically an Excel true vlookup. Via using `OUTER APPLY` the age group can be calculated and added in tblStudents. The full query is like this:
```sql
DECLARE @tblStudents table
(
    Name NVARCHAR(50),
    Age int
)

Insert Into @tblStudents
VALUES
('Adam',3),
('Bob',5),
('Chris',8),
('David',12),
('Eric',18)

DECLARE @tblGroup table
( 
    Age INT,
    AgeGroup NVARCHAR(50)
)

Insert Into @tblGroup
VALUES
(0,'A'),
(5,'B'),
(10,'C'),
(15,'D')

SELECT *
FROM @tblStudents AS s
OUTER APPLY (SELECT TOP 1 AgeGroup
				 FROM @tblGroup AS g
				 WHERE s.Age >= g.Age
				 ORDER BY AgeGroup DESC 
				 ) AS g
```

And the output is:

| Name | Age | AgeGroup |
| --- | --- | --- |
| Adam | 3 | A |
| Bob | 5 | B |
| Chris | 8 | B |
| David | 12 | C |
| Eric | 18 | D |
