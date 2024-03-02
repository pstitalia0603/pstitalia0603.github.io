---
{"dg-publish":true,"permalink":"/learning/interests/data/excel/transform-column-names-in-bulk-in-power-query-bi-gorilla/","tags":["Power_query","Data"],"noteIcon":""}
---

[[PROFESSIONAL/PortfolioNotes/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]
# [Transform Column Names in Bulk in Power Query - BI Gorilla](https://gorilla.bi/power-query/transform-column-names/)

In this article, we’ll show you some simple and advanced techniques for **replacing column names in bulk**. From basic find and replace to more complex formulas, you can apply your logic to multiple columns at the same time.

**Table of contents**

-   [1\. Basic Transformations](https://gorilla.bi/power-query/transform-column-names/#basic-transformations)
    -   [1.1. Replacing Characters](https://gorilla.bi/power-query/transform-column-names/#replacing-characters)
    -   [1.2. Adding a Prefix or Suffix](https://gorilla.bi/power-query/transform-column-names/#prefix-and-suffix)
    -   [1.3. Changing Capitalization](https://gorilla.bi/power-query/transform-column-names/#capitalization)
    -   [1.4. Clean or Trim Strings](https://gorilla.bi/power-query/transform-column-names/#clean-or-trim)
-   [2\. Advanced Transformations](https://gorilla.bi/power-query/transform-column-names/#advanced-transformations)
    -   [2.1. Conditionally Transform Column Names](https://gorilla.bi/power-query/transform-column-names/#conditionally-rename)
    -   [2.2. Split by Capital Letter / Uppercase to Lowercase](https://gorilla.bi/power-query/transform-column-names/#uppercase-to-lowercase)
    -   [2.3. Rename with Translation Table](https://gorilla.bi/power-query/transform-column-names/#custom-renaming)
-   [Conclusion](https://gorilla.bi/power-query/transform-column-names/#conclusion)

![Transform Column Names in Bulk in Power Query](Transform%20Column%20Names%20in%20Bulk%20in%20Power%20Query.webp)

## 1\. Basic Transformations

The easiest way to transform column names is by using the [Table.TransformColumnNames](https://powerquery.how/table-transformcolumnnames/) function. This function is useful when applying a similar transformation to each of your columns.

Examples are adding a prefix, capitalizing the first letters of a word, replacing underscores, etc. Let’s look at a few examples.

The syntax for this function is:

```
= Table.TransformColumnNames(
  table as table, 
  nameGenerator as function, 
  optional options as nullable record
)
```

### 1.1. Replacing Characters

Sometimes, column names come with characters you want to remove. For example, underscores or full stops in between words. To replace a character in all your column names at once, you can provide the following code:

```
= Table.TransformColumnNames( Source,  each Text.Replace( _, "_", " " ) )
// Replaces all underscores with a space

= Table.TransformColumnNames( Source,  each Text.Replace( _, ".", " " ) )
// Replaces all full stops with a space
```

### 1.2. Adding a Prefix or Suffix

In some cases, it is useful to differentiate columns that come from different tables. Let’s say you have multiple calendars in your data model.

To make it clear columns come from a specific calendar, you add a prefix or suffix to the column names with the following code:

```
= Table.TransformColumnNames( Source,  each "Prefix." & _ )
// Adds the text "Prefix." in front of each column name

= Table.TransformColumnNames( Source,  each _ & ".Suffix" )
// Adds the text ".Suffix" after each column name
```

### 1.3. Changing Capitalization

In a similar fashion, you can perform other transformations on your column names. Here are a few examples that work on the capitalization of letters:

```
= Table.TransformColumnNames( Source,  each Text.Lower( _ ) )
// Transforms column names to lowercase

= Table.TransformColumnNames( Source,  each Text.Upper( _ ) )
// Transforms column names to uppercase

= Table.TransformColumnNames( Source,  each Text.Proper( _ ) )
// Capitalizes each word in the column names
```

### 1.4. Clean or Trim Strings

When your data has unnecessary characters or spacing, [Text.Trim](https://powerquery.how/text-trim/) or [Text.Clean](https://powerquery.how/text-clean/) can help.

```
= Table.TransformColumnNames( Source,  each Text.Trim( _ ) )
// Removes leading and trailing whitespaces in column names

= Table.TransformColumnNames( Source,  each Text.Clean( _ ) )
// Removes non printable characters in column names
```

These are just a few examples to give you an idea. For more specific requirements, you can apply [other text functions](https://gorilla.bi/power-query/text-functions/) to your columns.

## 2\. Advanced Transformations

This chapter deals with the more advanced transformations. The code may be a bit more complex, but it can really benefit your Power Query solution.

### 2.1. Conditionally Transform Column Names

So far, we applied the transformations on each of the columns. Yet you may find it useful to restrict the transformation to only columns that meet a certain condition.

Let’s say you have a calendar table that has some columns that contain the word “date”. You decide you want to mark all the columns that contain the word “date” with the prefix “Bingo.”. You can add your condition in your code by writing:

```
Table.TransformColumnNames( Source,
                            each if Text.Contains(_, "date" ) then "Bingo." & _ else _ )
// Adds a prefix to each column name that contains the text "date" 
```

The function first tests the condition and only prefixes any value where the condition is true. In all other cases, the original values are returned, represented by the underscore (\_).

### 2.2. Split by Capital Letter / Uppercase to Lowercase

You may have columns with names like “ProductType”, “DueDate”, and “ProductColor”. To make these more readable, you can split column names at each transition from lowercase to uppercase. This is a more advanced transformation; the easiest way to do that is the following.

Select a text column in your model, go to **Transform**, select **Split Column** and select By Lowercase to Uppercase. This generates a formula like:

```
Table.SplitColumn(
  #"Split Column by Character Transition",
  "Product Color",
  Splitter.SplitTextByCharacterTransition({"a" .. "z"}, {"A" .. "Z"}),
  {"Product Color.1", "Product Color.2"}
)

// From here you only need to copy the following part: 
 = Splitter.SplitTextByCharacterTransition({"a" .. "z"}, {"A" .. "Z"})
```

This gives you a template for the function that splits your column names. You can use this template and combine it with the [Table.TransformColumnNames](https://powerquery.how/table-transformcolumnnames/) function.

The [Splitter.SplitTextByCharacterTransition](https://powerquery.how/splitter-splittextbycharactertransition/) function returns a function that splits text into a list of text values. Notice in the below example how I included “(\_)” behind the splitter function. This instructs Power Query to perform the function on each of the current elements.

Also, since [Splitter.SplitTextByCharacterTransition](https://powerquery.how/splitter-splittextbycharactertransition/) returns a list of strings you can wrap the results in a [Text.Combine](https://powerquery.how/text-combine/) function that concatenates the values into a single text value.

```
Table.TransformColumnNames(
    Source, 
    each Text.Combine(
         Splitter.SplitTextByCharacterTransition({"a" .. "z"}, {"A" .. "Z"})(_)
        , " ")
)
```

[![Transform Column Name by Capital Letter](Transform%20Column%20Name%20by%20Capital%20Letter.png)](https://gorilla.bi/wp-content/uploads/2022/07/Transform-Column-Names-Lowercase-to-Uppercase.png)

### 2.3. Rename with Translation Table

In some cases, no general transformation will suffice. In a scenario like that, you can use a translation table to indicate rename your columns. This is not as dynamic but can prove useful if you work with multiple languages or just very specific needs. How does this work?

This solution makes use of the [Table.RenameColumns](https://powerquery.how/table-renamecolumns/) function. The syntax for this function is:

```
= Table.RenameColumns( table as table,      // the table to rename columns on
                       renames as list,     // pairs of old and new colum names as list
                       optional missingField )
```

For your translation table, you can create a separate query called **Rename** that contains a column with the Old column names (**OldName**) and a column with the new column names (**NewName**).

[![Translation table for renaming](Translation%20table%20for%20renaming.png)](https://gorilla.bi/wp-content/uploads/2022/07/Translate-Table.png)

The [Table.RenameColumns](https://powerquery.how/table-renamecolumns/ "Table.RenameColumns") function needs these values in the format:

```
{ { OldName1, NewName1}, 
  { OldName2, NewName2}, 
  { OldName3, NewName3}, 
  { OldName4, NewName4}, 
  { OldName5, NewName5} } 
```

Since the **Rename** table contains two columns, you first need to transform these columns into the right format. You can do that either with [List.Zip](https://powerquery.how/list-zip/) or with [Table.ToRows](https://powerquery.how/table-torows/).

In your main query, where you want to rename your columns, you can add one of the following two formulas.

```
= Table.RenameColumns( Source,
                       List.Zip( { Rename[OldName], Rename[NewName] } ),
                       MissingField.Ignore )
 
= Table.RenameColumns( Source,
                       Table.ToRows( Rename[[OldName],[NewName]] ),
                       MissingField.Ignore )
```

In case you try to rename a column that does not exist in your table, or when you make a spelling error, [MissingField.Ignore](https://docs.microsoft.com/en-us/powerquery-m/missingfield-type) makes sure this step does not throw an error. And when you need any changes to column names in the future, you can simply adjust the Replace table.

## Conclusion

Well, there you have it! Now you know how to rename lots of columns at once using Power Query. And remember, you can form conditions in any desired form. It’s just your creativity limiting the possibilities.

Happy quering!