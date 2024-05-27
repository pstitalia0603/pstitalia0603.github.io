---
dg-publish: true
dg-home: false
date_created: 2023-12-04 16:08
date_modified: 2024-03-01 19:43
tags:
  - Power_query
  - Data
---
[[DATA/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

https://gorilla.bi/power-query/replace-values/ 

= Table.ReplaceValue(#"Added Custom",
each [Amount],
//each if [ConditionTrue] = "YES" then 0 else [Amount],
each if [id] = 1 and [First Name] = "joe" then 0 else [Amount],
Replacer.ReplaceValue,{"Amount"})