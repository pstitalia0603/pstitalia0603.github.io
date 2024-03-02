---
{"dg-publish":true,"permalink":"/professional/data/addressee-couple-lastnames/","tags":["Power_query","Data"],"noteIcon":""}
---

[[PROFESSIONAL/CODE_SNIPPETS/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

ADDRESSEE_SLN (SAME LAST NAME)

if [Spouse Nickname] = null then 
Text.Combine({[Nickname]," ", [Last Name]})
else if [Spouse Nickname] <> null and [Last Name] = [Spouse Last Name] then 
Text.Combine({[Nickname]," and ", [Spouse Nickname], " ", [Last Name]}) 
else if [Last Name] <> [Spouse Last Name] then null 
else null

ADDRESSEE DIFFERENT LASTNAME
if [Spouse Nickname] = null then 
null
else if [Spouse Nickname] <> null and [Last Name] = [Spouse Last Name] then 
null
else if [Last Name] <> [Spouse Last Name] then 
Text.Combine({[Nickname]," ",[Last Name], " and ",[Spouse Nickname]," ",[Spouse Last Name]})
else null


let
    Source = Excel.CurrentWorkbook(){[Name="Table1"]}[Content],
    #"Added Custom" = Table.AddColumn(Source, "SAME_LASTNAME", each if [Last Name] = [Spouse Last Name] then "Y" else "N"),
    #"Added Custom1" = Table.AddColumn(#"Added Custom", "ADDRESSEE_SLN", each if [Spouse Nickname] = null then 
Text.Combine({[Nickname]," ", [Last Name]})
else if [Spouse Nickname] <> null and [Last Name] = [Spouse Last Name] then 
Text.Combine({[Nickname]," and ", [Spouse Nickname], " ", [Last Name]}) 
else if [Last Name] <> [Spouse Last Name] then null 
else null),
    #"Added Custom2" = Table.AddColumn(#"Added Custom1", "DIFF_LASTNAME", each if [Spouse Nickname] = null then 
null
else if [Spouse Nickname] <> null and [Last Name] = [Spouse Last Name] then 
null
else if [Last Name] <> [Spouse Last Name] then 
Text.Combine({[Nickname]," ",[Last Name], " and ",[Spouse Nickname]," ",[Spouse Last Name]})
else null),
    #"Merged Columns" = Table.CombineColumns(#"Added Custom2",{"ADDRESSEE_SLN", "DIFF_LASTNAME"},Combiner.CombineTextByDelimiter("", QuoteStyle.None),"ADDRESSEE"),
    #"Removed Columns" = Table.RemoveColumns(#"Merged Columns",{"SAME_LASTNAME"}),
    #"Reordered Columns" = Table.ReorderColumns(#"Removed Columns",{"ADDRESSEE", "Constituent ID", "Nickname", "Last Name", "Spouse Nickname", "Spouse Last Name", "Constituency Code", "Primary Addressee", "Alumnae Council", "Alumnae Council Date", "Alumnae Class Reps", "Alumnae Class Reps Date", "HouseholdID"}),
    #"Removed Columns1" = Table.RemoveColumns(#"Reordered Columns",{"Primary Addressee", "HouseholdID"}),
    #"Changed Type" = Table.TransformColumnTypes(#"Removed Columns1",{{"Constituent ID", type text}}),
    #"Promoted Headers" = Table.PromoteHeaders(#"Changed Type", [PromoteAllScalars=true]),
    #"Changed Type1" = Table.TransformColumnTypes(#"Promoted Headers",{{"Alumnae Class Reps Date", type date}, {"Alumnae Council Date", type date}}),
    #"Replaced Value" = Table.ReplaceValue(#"Changed Type1","Maryland","MD",Replacer.ReplaceText,{"Preferred State"}),
    #"Replaced Value1" = Table.ReplaceValue(#"Replaced Value","District of Columbia","DC",Replacer.ReplaceText,{"Preferred State"}),
    #"Replaced Value2" = Table.ReplaceValue(#"Replaced Value1","Virginia","VA",Replacer.ReplaceText,{"Preferred State"}),
    #"Replaced Value3" = Table.ReplaceValue(#"Replaced Value2","Colorado","CO",Replacer.ReplaceText,{"Preferred State"}),
    #"Replaced Value4" = Table.ReplaceValue(#"Replaced Value3","South Carolina","SC",Replacer.ReplaceText,{"Preferred State"}),
    #"Replaced Value5" = Table.ReplaceValue(#"Replaced Value4","Florida","FL",Replacer.ReplaceText,{"Preferred State"}),
    #"Replaced Value6" = Table.ReplaceValue(#"Replaced Value5","Indiana","IN",Replacer.ReplaceText,{"Preferred State"}),
    #"Replaced Value7" = Table.ReplaceValue(#"Replaced Value6","North Carolina","NC",Replacer.ReplaceText,{"Preferred State"}),
    #"Changed Type2" = Table.TransformColumnTypes(#"Replaced Value7",{{"Alumnae Council Date", type text}, {"Alumnae Class Reps Date", type text}}),
    #"Merged Columns1" = Table.CombineColumns(Table.TransformColumnTypes(#"Changed Type2", {{"Alumnae Council", type text}}, "en-US"),{"Alumnae Council", "Alumnae Council Date"},Combiner.CombineTextByDelimiter(" - ", QuoteStyle.None),"ALUM_COUNCIL"),
    #"Merged Columns2" = Table.CombineColumns(#"Merged Columns1",{"Alumnae Class Reps", "Alumnae Class Reps Date"},Combiner.CombineTextByDelimiter(" - ", QuoteStyle.None),"ALUM_CLASS_REPS"),
    #"Renamed Columns" = Table.RenameColumns(#"Merged Columns2",{{"Nickname Last Name and Spouse Nickname Spouse Last Name", "ADDRESSEE"}}),
    #"Changed Type4" = Table.TransformColumnTypes(#"Renamed Columns",{{"Preferred ZIP", type text}}),
    #"Grouped Rows" = Table.Group(#"Changed Type4", {"ADDRESSEE","Household_NAME"}, {{"ADDRESS", each Text.Combine(List.Distinct([Preferred Address Line 1]),", "), type text}, {"CITY", each Text.Combine(List.Distinct([Preferred City]),", "), type text}, {"STATE", each Text.Combine(List.Distinct([Preferred State]),", "), type nullable text}, {"ZIP", each Text.Combine(List.Distinct([Preferred ZIP]),", "), type text}}),
    #"Uppercased Text" = Table.TransformColumns(#"Grouped Rows",{{"Household_NAME", Text.Upper, type text}}),
    #"Changed Type3" = Table.TransformColumnTypes(#"Uppercased Text",{{"ZIP", type text}})
in
    #"Changed Type3"