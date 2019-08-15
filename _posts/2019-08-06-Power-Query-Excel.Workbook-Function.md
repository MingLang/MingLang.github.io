---
layout: post
title: Power Query Excel.Workbook Function
category: Power Query
tags: [Power Query, Excel.Workbook]
---


[Excel.Workbook](https://docs.microsoft.com/en-us/powerquery-m/excel-workbook)

## Syntax
```Excel.Workbook(workbook as binary, optional useHeaders as nullable logical, optional delayTypes as nullable logical) as table```

## Return value
Returns a record of Sheets from the Excel workbook.

## Example
```Excel.Workbook(File.Contents([Folder Path]&[Name]), true, true)```




The first parameter of Excel.Workbook() needs to be a binary format Excel workbook, and the funciton [File.Contents](https://docs.microsoft.com/en-us/powerquery-m/file-contents) returns the contents of a file as binary.

The second parameter "useHeaders" is to decide if headers will be prompted automatically. It is nullable and when the value is null it means false, i.e. the headers will not be used.

Regarding the third parameter, [an artical](https://blog.crossjoin.co.uk/2019/02/02/excel-workbook-and-the-delaytypes-option-in-power-query-power-bi/) from Chris Webb has a good explaination. In his bolg, he quoted a forums post from Guy Hunkin of the Excel Power Query team

>Originally, Excel.Workbook used to read the entire workbook data to accurately assign types to the columns. This was EXTREMELY slow on large workbooks.
>
>Having this in mind, we added this flag to delay the behavior. When set to "true", we don't infer any column types.

So, the third parameter "delayTypes" is used to delay the type assigning behavior. It is nullable and is set to be false by default if not specified. According to Chris, Setting delayTypes to true results in much better performance.
