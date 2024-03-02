---
{"dg-publish":true,"permalink":"/personal/data/remove-duplicates-in-power-query-m/","tags":["Power_query","Data"],"noteIcon":""}
---


[[PROFESSIONAL/CODE_SNIPPETS/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

# [How to Remove Duplicates in Power Query M (Complete Guide)](https://gorilla.bi/power-query/removing-duplicates/)

## Basics for Removing Duplicates

So, how can you remove duplicates using the Power Query Editor? Under the hood, the operation uses the [Table.Distinct](https://powerquery.how/table-distinct/) function to remove duplicates. The syntax for the function is as follows:

```
= Table.Distinct(
    table as table, 
    optional equationCriteria as any
   )
```

