---
{"dg-publish":true,"permalink":"/data/errors-in-pq/","tags":["Data","Power_query"],"noteIcon":"","created":"2024-04-10T11:00:00","updated":"2024-04-10T15:56:00"}
---

[[DATA/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

# [New way of Dealing with errors in Power Query – Curbal](https://curbal.com/curbal-learning-portal/new-way-of-dealing-with-errors-in-power-query)


*There is now a new way (Released in May 2020) to manage errors with more granularity in Power Query.

Before you could use **try** **otherwise** to capture the error and convert it to null or something else:

```
= Table.AddColumn(#"Expanded Error", "Custom", 
each try [#"a/B"] otherwise null)
```

but with the new keyword catch, you can now specify how to treat each error.  
In the example below we will substitute the error # REF! by Column A and error # DIV0! by 0, other errors will be converted to nulls:

```
= Table.AddColumn(#"Added Custom1", "Custom.1",
 each try [#"a/B"] catch(f)=> 
    if f[Message] = "Invalid cell value '#REF!'." then [Value A] else 
    if f[Message] = "Invalid cell value '#DIV/0!'." then 0
      else null)
```

https://www.youtube.com/watch?v=la9Kc7zfPFs&embeds_referring_euri=https%3A%2F%2Fcurbal.com%2F

