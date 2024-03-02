---
{"dg-publish":true,"permalink":"/personal/interests/data/power-query-m/how-to-remove-duplicates-in-power-query-m-complete-guide/","tags":["Power_query","Data"],"noteIcon":""}
---


[[PROFESSIONAL/CODE_SNIPPETS/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]


# [How to Remove Duplicates in Power Query M (Complete Guide)](https://gorilla.bi/power-query/removing-duplicates/)

In this article, we’ll explore **how to remove duplicates in Power Query**. We’ll cover basic and advanced methods for removing duplicates, including how to remove duplicates from single and multiple columns, how to remove duplicates case-insensitively, and how to keep values based on a condition.

We’ll also delve into an inconsistency problem, often related to sort order, that can occur when removing duplicates and how to solve it. By the end of this article, you’ll have a thorough understanding of how to remove duplicates in Power Query.

**Table of contents**

-   [Importance of Removing Duplicates](https://gorilla.bi/power-query/removing-duplicates/#importance)
-   [Basics for Removing Duplicates](https://gorilla.bi/power-query/removing-duplicates/#basics)
    -   [Removing Duplicates from a Single Column](https://gorilla.bi/power-query/removing-duplicates/#single-column)
    -   [Removing Duplicates from Multiple Columns](https://gorilla.bi/power-query/removing-duplicates/#multiple-columns)
    -   [Removing Duplicates Case-Insensitive](https://gorilla.bi/power-query/removing-duplicates/#case-insensitive)
-   [Inconsistent Results](https://gorilla.bi/power-query/removing-duplicates/#inconsistent-results)
-   [Advanced Techniques for Removing Duplicates](https://gorilla.bi/power-query/removing-duplicates/#advanced-techniques)
    -   [Keep First or Last Value](https://gorilla.bi/power-query/removing-duplicates/#first-or-last-value)
    -   [Keep Earliest or Latest Value](https://gorilla.bi/power-query/removing-duplicates/#earliest-or-latest-value)
    -   [Keep Lowest or Highest Value](https://gorilla.bi/power-query/removing-duplicates/#lowest-or-highest-value)
-   [Conclusion](https://gorilla.bi/power-query/removing-duplicates/#conclusion)

## Importance of Removing Duplicates

Eliminating duplicate rows is a critical step when cleaning your data in Power Query. Duplicates can cause problems in many situations. For example, when:

-   **Performing a join:** duplicates in your join table, result in duplicate rows in the destination table.
-   **Creating a dimension table:** you can’t make a one-to-many relationship with duplicates on the one side.
-   **Inspecting Values:** duplicates can be an indication that an earlier join had duplicate values.

To prevent this, we need an expression to check for duplicates and filter our dataset only to include unique values.

## Basics for Removing Duplicates

So, how can you remove duplicates using the Power Query Editor? Under the hood, the operation uses the [Table.Distinct](https://powerquery.how/table-distinct/) function to remove duplicates. The syntax for the function is as follows:

```
= Table.Distinct(
    table as table, 
    optional equationCriteria as any
   )
```

This function has two arguments: the first argument is the **table to remove duplicates from**, and the second argument is an **optional equationCriteria that tells the function which columns to look at when removing duplicates**. You can provide a column name, or instruct the function to respect or ignore capitals. If you omit the equationCriteria, the function will remove duplicates from the entire table.

### Removing Duplicates from a Single Column

Let’s start with removing duplicates from a single column. This is one of the most basic methods for removing duplicates in Power Query, and it’s really easy to do.

To remove duplicates from a single column, you:

-   Right-click on the column that contains duplicates
-   Select the “**Remove Duplicates**” option.
-   Now click OK.

That’s it! Power Query will remove all duplicates from the selected column.

[![Remove Duplicates Single Column in Power Query](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-Single-Column-in-Power-Query.png)](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-Single-Column-in-Power-Query.png)

The remove duplicates operation makes use of the [Table.Distinct](https://powerquery.how/table-distinct/ "Table.Distinct") function in Power Query. When performing the operation on a single-column table, the above operation will show:

```
= Table.Distinct( Source )
```

This removes duplicates from the entire table. When your table has multiple columns, the code below removes the duplicates from only the “**Fruit**” column.

```
= Table.Distinct( Source, { "Fruit" } )
```

But what if you have duplicate values across multiple columns? No problem!

### Removing Duplicates based on Multiple Columns

The easiest way to remove duplicates based on multiple columns is:

-   Hold down the CTRL Key.
-   **Select the columns** you want to remove duplicates from.
-   Click on **Remove Duplicates**.

Now, Power Query will delete all rows with duplicated values across the selected columns. This operation focuses on returning unique combinations of values.

[![Remove Duplicates Multiple Column in Power Query](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-Multiple-Column-in-Power-Query.png)](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-Multiple-Column-in-Power-Query.png)

```
= Table.Distinct(
     Source, 
     { "Brand", "Country"} )
```

Performing this operation still uses the [Table.Distinct](https://powerquery.how/table-distinct/ "Table.Distinct") function. This time, the second argument contains both column names within a list. If you could use a refresher, have a look at [list use-cases and syntax](https://gorilla.bi/power-query/list-functions/).

So you know how to remove duplicates from one or more columns, but what if you want to remove duplicates case-insensitive?

### Removing Duplicates Case-Insensitive

To remove duplicates in a manner that is case-insensitive, you can make use of the optional equation argument of [Table.Distinct](https://powerquery.how/table-distinct/). Whether you’re working with one or multiple columns or even the entire table, you can easily remove duplicates case-insensitive.

So, what if you have a dataset that contains duplicates, and you want to perform a case-sensitive removing duplicates operation on the **Wood** column? Removing duplicates (case sensitive) then only removes a row for the value ‘**Cedar**‘.

[![Data with Duplicates in Power Query](https://gorilla.bi/wp-content/uploads/2023/03/Data-with-Duplicates-in-Power-Query.png)](https://gorilla.bi/wp-content/uploads/2023/03/Data-with-Duplicates-in-Power-Query.png)

To achieve this, you can use [Table.Distinct](https://powerquery.how/table-distinct/ "Table.Distinct") function and provide the column name **“Wood”** in the second argument. The result is a case-sensitive removal of duplicates as below.

[![Remove Duplicates Case Sensitive in Power Query](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-Case-Sensitive-in-Power-Query.png)](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-Case-Sensitive-in-Power-Query.png)

Now, let’s say you want to **ignore the capitalization when removing duplicates**. The easiest way to remove duplicates case-insensitive is by adding a [comparer function](https://powerquery.how/comparer-functions/):

-   Right-click on the column that contains duplicates
-   Select **Remove Duplicates**
-   Provide the column name and **[Comparer.OrdinalIgnoreCase](https://powerquery.how/comparer-ordinalignorecase/ "Comparer.OrdinalIgnoreCase")** as equation criteria.
-   Use format: { “ColumnName”, [Comparer.OrdinalIgnoreCase](https://powerquery.how/comparer-ordinalignorecase/ "Comparer.OrdinalIgnoreCase") }

The result is a case-insensitive removal of duplicates.

```
= Table.Distinct(
   Source, 
   { "Wood", Comparer.OrdinalIgnoreCase } )
```

[![Remove Duplicates Ignore Case in Power Query](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-Ignore-Case-in-Power-Query.png)](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-Ignore-Case-in-Power-Query.png)

But what if you want to apply this method to multiple columns?

```
= Table.Distinct(
     Source, 
     { { "Wood", Comparer.OrdinalIgnoreCase },
       { "Area", Comparer.OrdinalIgnoreCase } } )
```

[![Remove Duplicates Cases Insensitive on Multiple Columns in Power Query](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-Cases-Insensitive-on-Multiple-Columns-in-Power-Query.png)](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-Cases-Insensitive-on-Multiple-Columns-in-Power-Query.png)

You can use the [Table.Distinct](https://powerquery.how/table-distinct/ "Table.Distinct") function and provide the method to look for duplicates for every column. This allows you to specify whether to ignore capitalization ([Comparer.OrdinalIgnoreCase](https://powerquery.how/comparer-ordinalignorecase/)) or respect capitalization ([Comparer.Ordinal](https://powerquery.how/comparer-ordinal/)) for each column individually.

So there you have it – some basic methods for removing duplicates in Power Query. Whether you’re working with a single column, with multiple columns, or whether you check capital sensitive, Power Query makes it easy to get rid of the duplicates and get your data in tip-top shape.

But be aware that the methods shown so far don’t always return the same results. Let’s see why that is in the next section.

## Inconsistent Results

Did you know that the remove duplicates operation in Power Query often returns inconsistent results? It might sound strange, but it’s actually a side effect of certain optimizations that Power Query uses to be as efficient as possible.

One of these optimizations is **Query Folding, which sends certain operations to the data source to be processed instead of in Power Query**. While this can help make things faster and more efficient, it can also cause problems when it comes to removing duplicates. Without using additional measures, **there’s no guarantee that removing duplicates** **returns the same records**. That means you can’t assume that removing duplicates will return only the first duplicate row in your dataset.

But there’s a simple solution to this randomness problem. To make the remove duplicates operation predictable, you can use [Table.Buffer](https://powerquery.how/table-buffer/). This function forces Power Query to cache the data in memory, which means that you can control which records are returned when removing duplicates.

So, if you want to ensure that you’re getting consistent results when removing duplicates, be sure to use [Table.Buffer](https://powerquery.how/table-buffer/ "Table.Buffer"). We’ll dive deeper into this topic and explore advanced methods in the next chapter.

## Advanced Techniques for Removing Duplicates

Sometimes, removing duplicates isn’t as straightforward as it seems, and you may need more advanced methods to get the job done. That’s where this chapter comes in – we’re going to explore some advanced methods for removing duplicates in Power Query.

In this chapter, we’ll dive into how you can **remove duplicates based on a condition**. We’ll look at retrieving the first or last value, the earliest or latest value and the lowest or highest value.

### Keep First or Last Value

First, let’s talk about how to delete duplicates and keep the first or last value in your dataset. **By default, [Table.Distinct](https://powerquery.how/table-distinct/ "Table.Distinct") returns the first duplicate row it finds**. But as we learned in the previous chapter, the sorting order of your table isn’t guaranteed, which can cause issues.

To ensure that we’re keeping the first or last value, we need to sort our data and make sure it stays sorted.

To remove duplicates and retrieve the first value in a dataset, you:

-   Sort your data
-   Select columns to remove duplicates from
-   Wrap the data in [Table.Buffer](https://powerquery.how/table-buffer/)
-   Remove duplicates

You can do that with this dataset.

[![Remove Duplicates with Table.Buffer to Guarantee Sort Order in Power Query](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-with-Table.Buffer-to-Guarantee-Sort-Order-in-Power-Query-1.png)](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-with-Table.Buffer-to-Guarantee-Sort-Order-in-Power-Query-1.png)

Prepare your data by sorting the table and wrapping it in [Table.Buffer](https://powerquery.how/table-buffer/ "Table.Buffer"). You can then select the Category column and click Remove duplicates, returning:

[![Removing Duplicates and Return First Value in Power Query](https://gorilla.bi/wp-content/uploads/2023/03/Removing-Duplicates-and-Return-First-Value-in-Power-Query.png)](https://gorilla.bi/wp-content/uploads/2023/03/Removing-Duplicates-and-Return-First-Value-in-Power-Query.png)

You will end up removing duplicates but keeping the first instance within your category. So to return the first value when removing duplicates, you sort your code with:

```
= Table.Buffer( 
    Table.Sort( Dataset,
                { {"Category",    Order.Ascending },
                  {"Description", Order.Ascending } } ) )
```

If you want to keep the last value instead, you can simply [sort your data in descending order](https://gorilla.bi/power-query/how-list-sort-works-in-m/) by the column you want to keep the last value of. Then, wrap your data in [Table.Buffer](https://powerquery.how/table-buffer/ "Table.Buffer"), and remove duplicates.

```
= Table.Buffer( 
    Table.Sort( Dataset,
                { {"Category",    Order.Ascending },
                  {"Description", Order.Descending } } ) )
```

### Keep Earliest or Latest Value

In case you want to return the earliest or the latest value, you can perform something similar. To return unique rows for the category with the latest date, you:

1.  Sort your data by Category and in a Descending order for your Date Column.
2.  Remove Duplicates from the relevant column(s).

[![Remove Duplicates and Return Latest Row](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-and-Return-Latest-Row.png)](https://gorilla.bi/wp-content/uploads/2023/03/Remove-Duplicates-and-Return-Latest-Row.png)

```
// Sorts and buffers data, so removing duplicates returns the latest category row
= Table.Buffer( 
    Table.Sort( Dataset,
                { {"Category",    Order.Ascending }, 
                  {"Date",        Order.Descending } } ) )

// Sorts and buffers data, so removing duplicates returns the earliest category row
= Table.Buffer( 
    Table.Sort( Dataset,
                { {"Category",    Order.Ascending }, 
                  {"Date",        Order.Ascending } } ) )
```

### Keep Lowest or Highest Value

The last advanced method returns [**the lowest or highest value within a group**](https://gorilla.bi/power-query/using-table-max/). We could make use of the above method to achieve this. Yet, since I’m certain you will know how to sort your data in a similar way, let’s explore an alternative.

To remove duplicates and return the lowest value, you can:

1.  Group your data.
2.  Perform an All Rows operation.
3.  Adjust the M-code to return the row with the lowest value.
4.  Expand the record column to get your result.

Let’s see how that can work. The Group By operation returns only unique rows for the columns selected.

To group your data, go to the Home Tab, and select Group By.

[![Group Your Data to Remove Duplicates in Power Query](https://gorilla.bi/wp-content/uploads/2023/03/Group-Your-Data-to-Remove-Duplicates-in-Power-Query.png)](https://gorilla.bi/wp-content/uploads/2023/03/Group-Your-Data-to-Remove-Duplicates-in-Power-Query.png)

To keep the lowest value for each Category, you can **group your data by Category** and perform an **All Rows operation**. This creates a table object with all summarized rows for each Category. This produces below code:

[![Group Rows and use All Rows operation in Power Query](https://gorilla.bi/wp-content/uploads/2023/03/Group-Rows-and-use-All-Rows-operation-in-Power-Query.png)](https://gorilla.bi/wp-content/uploads/2023/03/Group-Rows-and-use-All-Rows-operation-in-Power-Query.png)

We’re going to change the formula above. A useful function is [Table.Min](https://powerquery.how/table-min/). The **[Table.Min](https://powerquery.how/table-min/ "Table.Min") function returns the table row that contains the lowest value of a column**. In other words, you can delete duplicate rows based on the column value.

To achieve this, adjust the code like in the below picture. Then, expand [the record](https://gorilla.bi/power-query/records/) column by selecting the arrows in the column header.

[![Return Row with Lowest Value using Table.Group in Power Query](https://gorilla.bi/wp-content/uploads/2023/06/Return-Row-with-Lowest-Value-using-Table.Group-in-Power-Query.png)](https://gorilla.bi/wp-content/uploads/2023/06/Return-Row-with-Lowest-Value-using-Table.Group-in-Power-Query.png)

After clicking OK, you’ll end up with the desired result:

[![Rows returning the Lowest Value using Table.Group](https://gorilla.bi/wp-content/uploads/2023/03/Rows-returning-the-Lowest-Value-using-Table.Group_.png)](https://gorilla.bi/wp-content/uploads/2023/03/Rows-returning-the-Lowest-Value-using-Table.Group_.png)

To instead keep the highest value when removing duplicates, you can simply swap out [Table.Min](https://powerquery.how/) for [Table.Max](https://powerquery.how/table-max/). That means you either use:

```
// Sorts and buffers data, so removing duplicates returns the latest category row
= Table.Group( Dataset, 
    {"Category"}, 
    {{"Details", each Table.Min( _, "Amount" ) , type record }} )

// Sorts and buffers data, so removing duplicates returns the earliest category row
= Table.Group( Dataset, 
    {"Category"}, 
    {{"Details", each Table.Max( _, "Amount" ) , type record }} )
```

You can learn more about the [Group By Operation](https://gorilla.bi/power-query/grouping-data/) or also read into the [All Rows operation](https://gorilla.bi/power-query/group-by-to-concatenate-text/) and how it works.

## Conclusion

And there, you have everything you need to know about removing duplicates in Power Query. Whether you’re dealing with a single column or multiple columns, case-sensitive or case-insensitive duplicates, or advanced methods for keeping the first, last, earliest, latest, lowest or highest values, Power Query has you covered.

Remember, removing duplicates is an important step in cleaning your data. By removing duplicates, you can avoid issues with joins, dimension tables, and prepare your data for your data model.

Just be aware of the randomness problem that can occur with the [Table.Distinct](https://powerquery.how/table-distinct/) function, and use [Table.Buffer](https://powerquery.how/table-buffer/) to ensure consistent results.

Happy querying!