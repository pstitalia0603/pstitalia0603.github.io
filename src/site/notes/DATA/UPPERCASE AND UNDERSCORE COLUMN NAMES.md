---
{"dg-publish":true,"permalink":"/data/uppercase-and-underscore-column-names/","tags":["Power_query","Data"],"noteIcon":""}
---

[[PROJECTS/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

Table.TransformColumnNames( Source, each Text.Upper( _ ) )
// CAPITALIZES All Column Names

Table.TransformColumnNames(UppercasedText, each Text.Replace( _, " ", "_" ) )
// Replaces all full stops with a space

EXAMPLE IN EDITOR
UppercasedText = Table.TransformColumnNames(#"Renamed Columns4", each Text.Upper( _ ) ),
    AddUnderScore = Table.TransformColumnNames(UppercasedText, each Text.Replace( _, ".", " " ))