---
layout: post
title: SQL approximate lookup
category: SQL
tags: [SQL, lookup]
--- 


## tblStudents

| Name | Age |
| ---- | ---- |
| Adam | 3 |
| Bob | 5 |
| Chris | 8 |
| David | 12 |
| Eric | 18 |
{:.mbtablestyle}

## tblGroup

|Age|AgeGroup|
|---|---|
|0|A|
|5|B|
|10|C|
|15|D|


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