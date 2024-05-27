---
dg-publish: true
dg-home: false
date_created: 2023-12-03T10:12:00
date_modified: 2024-03-01 19:44
tags:
  - Power_query
  - Data
---
[[DATA/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

{"Count", each Table.RowCount(_), Int64.Type}})


{"Count", each List.NonNullCount(_), Int64.Type}})


List.Count(List.RemoveNulls(Record.ToList(Record.RemoveFields(_,"Total Sales"))))


Table.RowCount(Table.SelectRows(_,(x)=>x[Total Sales]<>null)),

SOLUTION --> GroupBY Table count of non null values
{"Count", each Table.RowCount(Table.SelectRows(_,(x)=>x[Total Price]<>null)), Int64.Type}}



https://community.fabric.microsoft.com/t5/Desktop/Distinct-Count-with-no-blank-values-using-power-query/td-p/2211994