---
{"dg-publish":true,"permalink":"/data/transform-column-names-in-bulk-in-pq-bi-gorilla/","tags":["Power_query","Data"],"noteIcon":""}
---

[[DATA/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]
# [Transform Column Names in Bulk in Power Query - BI Gorilla](https://gorilla.bi/power-query/transform-column-names/)

techniques for **replacing column names in bulk**. 
**Table of contents**

## 1\. Basic Transformations

[Table.TransformColumnNames](https://powerquery.how/table-transformcolumnnames/) 

```
= Table.TransformColumnNames(
  table as table, 
  nameGenerator as function, 
  optional options as nullable record
)
```

### 1.1. Replacing Characters

```
= Table.TransformColumnNames( Source,  each Text.Replace( _, "_", " " ) )
// Replaces all underscores with a space

= Table.TransformColumnNames( Source,  each Text.Replace( _, ".", " " ) )
// Replaces all full stops with a space
```

### 1.2. Adding a Prefix or Suffix

```
= Table.TransformColumnNames( Source,  each "Prefix." & _ )
// Adds the text "Prefix." in front of each column name

= Table.TransformColumnNames( Source,  each _ & ".Suffix" )
// Adds the text ".Suffix" after each column name
```

### 1.3. Changing Capitalization

```
= Table.TransformColumnNames( Source,  each Text.Lower( _ ) )
// Transforms column names to lowercase

= Table.TransformColumnNames( Source,  each Text.Upper( _ ) )
// Transforms column names to uppercase

= Table.TransformColumnNames( Source,  each Text.Proper( _ ) )
// Capitalizes each word in the column names
```

### 1.4. Clean or Trim Strings

```
= Table.TransformColumnNames( Source,  each Text.Trim( _ ) )
// Removes leading and trailing whitespaces in column names

= Table.TransformColumnNames( Source,  each Text.Clean( _ ) )
// Removes non printable characters in column names
```

## 2\. Advanced Transformations
### 2.1. Conditionally Transform Column Names


```
Table.TransformColumnNames( Source,
                            each if Text.Contains(_, "date" ) then "Bingo." & _ else _ )
// Adds a prefix to each column name that contains the text "date" 
```

### 2.2. Split by Capital Letter / Uppercase to Lowercase

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

```
Table.TransformColumnNames(
    Source, 
    each Text.Combine(
         Splitter.SplitTextByCharacterTransition({"a" .. "z"}, {"A" .. "Z"})(_)
        , " ")
)
```
### 2.3. Rename with Translation Table

```
= Table.RenameColumns( table as table,      // the table to rename columns on
                       renames as list,     // pairs of old and new colum names as list
                       optional missingField )
```


```
= Table.RenameColumns( Source,
                       List.Zip( { Rename[OldName], Rename[NewName] } ),
                       MissingField.Ignore )
 
= Table.RenameColumns( Source,
                       Table.ToRows( Rename[[OldName],[NewName]] ),
                       MissingField.Ignore )
```
