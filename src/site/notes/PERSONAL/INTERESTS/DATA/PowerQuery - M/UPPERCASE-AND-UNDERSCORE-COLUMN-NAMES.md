---
{"dg-publish":true,"permalink":"/personal/interests/data/power-query-m/uppercase-and-underscore-column-names/","tags":["Power_query","Data"],"noteIcon":""}
---

[[PROFESSIONAL/CODE_SNIPPETS/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

Table.TransformColumnNames( Source, each Text.Upper( _ ) )
// CAPITALIZES All Column Names

Table.TransformColumnNames(UppercasedText, each Text.Replace( _, " ", "_" ) )
// Replaces all full stops with a space

EXAMPLE IN EDITOR
UppercasedText = Table.TransformColumnNames(#"Renamed Columns4", each Text.Upper( _ ) ),
    AddUnderScore = Table.TransformColumnNames(UppercasedText, each Text.Replace( _, ".", " " ))