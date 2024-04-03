---
{"dg-publish":true,"permalink":"/data/list-repeat-power-query-m/","tags":["Data","Power_query"],"noteIcon":""}
---

2024-03-14 13:47 -

# [List.Repeat - PowerQuery M](https://learn.microsoft.com/en-us/powerquery-m/list-repeat)

## List.Repeat

```
List.Repeat( { [col1] }, [col2] )
```

This produces a column with a list in each row where the elements of the list are `[col1]` listed `[col2]` number of times.


## Syntax

List.Repeat(**list** as list, **count** as number) as list

## About

Returns a list that is `count` repetitions of the original list, `list`.

## Example 1

Create a list that has {1, 2} repeated 3 times.

**Usage**

```
List.Repeat({1, 2}, 3)
```

**Output**

`{1, 2, 1, 2, 1, 2}`

---


