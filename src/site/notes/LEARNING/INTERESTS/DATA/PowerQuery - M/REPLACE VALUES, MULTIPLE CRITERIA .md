---
{"dg-publish":true,"permalink":"/learning/interests/data/power-query-m/replace-values-multiple-criteria/","tags":["Power_query","Data"],"noteIcon":""}
---

[[PROFESSIONAL/PortfolioNotes/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

REPLACE VALUES, MULTIPLE CRITERIA 

https://gorilla.bi/power-query/replace-values/ 

= Table.ReplaceValue(#"Added Custom",
each [Amount],
//each if [ConditionTrue] = "YES" then 0 else [Amount],
each if [id] = 1 and [First Name] = "joe" then 0 else [Amount],
Replacer.ReplaceValue,{"Amount"})