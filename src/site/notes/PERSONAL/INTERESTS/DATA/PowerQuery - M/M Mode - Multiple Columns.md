---
{"dg-publish":true,"permalink":"/personal/interests/data/power-query-m/m-mode-multiple-columns/","tags":["Data","m-code","dax","Power_query"],"noteIcon":""}
---

[[PROFESSIONAL/CODE_SNIPPETS/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

//let
//    Source = #"Families-Parents-Students-LIST",
  //  #"Renamed Columns" = Table.RenameColumns(Source,{{"CHILD GRADE", "GRADE"}})
//in
  //  #"Renamed Columns"

         let

//Read in the data and set data types
    Source = Excel.CurrentWorkbook(){[Name="FAM"]}[Content],
    #"Changed Type" = Table.TransformColumnTypes(Source,{
        {"C_FNAME", type text}, {"C_LNAME", type text}, {"GRADE", type text}, 
        {"FAMILY", type text}, {"EMAIL", type text},{"ADDRESS", type text},{"PHONE", type text },{"DONATION", type text}}),

//Unpivot columns other than the two Parent columns
    #"Unpivoted Other Columns" = Table.UnpivotOtherColumns(#"Changed Type", 
        {"EMAIL", "PHONE", "ADDRESS", "DONATION", "FAMILY"}, "Attribute", "Value"),

//Group by the Parent Columns
//Then add an index colum to each sub-table
    #"Grouped Rows" = Table.Group(#"Unpivoted Other Columns", {"EMAIL", "PHONE", "ADDRESS", "DONATION", "FAMILY"}, {
        {"idx", each  Table.AddIndexColumn(_,"idx"),Int64.Type}}),

//Add integer/divide by 3 column to each subtable to differentiate the different children
//Note that we set the data type to Text for later combining with the Attributes
    #"Added Custom" = Table.AddColumn(#"Grouped Rows", "int/div", 
        each Table.TransformColumnTypes(
            Table.AddColumn([idx], "Integer-Division", 
                each Number.IntegerDivide([idx], 3)),{"Integer-Division",Text.Type})),

//Combine Attribute and int/divide column to create unique names for each child/column
    #"Added Custom1" = Table.AddColumn(#"Added Custom", "childNum", 
        each Table.CombineColumns([#"int/div"],
            {"Attribute","Integer-Division"},
                Combiner.CombineTextByDelimiter("."),"Attribute")),

//Remove unneeded columns
    #"Removed Columns" = Table.RemoveColumns(#"Added Custom1",{"idx", "int/div"}),

//Pivot each sub-table
    #"Added Custom2" = Table.AddColumn(#"Removed Columns", "pivot subtable", each 
        let 
            //Remove columns we don't want when we pivot
            x=Table.RemoveColumns([childNum],{"EMAIL", "PHONE", "ADDRESS", "DONATION", "FAMILY", "idx"})
        in 
            Table.Pivot(x,x[Attribute],"Attribute","Value")),

//Remove unneeded columns and expand the pivot subtables
//May need to generate the list of expanded column names dynamically
    #"Removed Columns1" = Table.RemoveColumns(#"Added Custom2",{"childNum"}),
    #"Expanded pivot subtable" = Table.ExpandTableColumn(#"Removed Columns1", "pivot subtable", 
        {"C_FNAME.0", "C_LNAME.0", "GRADE.0", "C_FNAME.1", "C_LNAME.1", "GRADE.1", "C_FNAME.2", "C_LNAME.2", "GRADE.2", "C_FNAME.3", "C_LNAME.3", "GRADE.3","C_FNAME.4", "C_LNAME.4", "GRADE.4","C_FNAME.5", "C_LNAME.5", "GRADE.5"}, 
        {"C_FNAME.0", "C_LNAME.0", "GRADE.0", "C_FNAME.1", "C_LNAME.1", "GRADE.1", "C_FNAME.2", "C_LNAME.2", "GRADE.2", "C_FNAME.3", "C_LNAME.3", "GRADE.3","C_FNAME.4", "C_LNAME.4", "GRADE.4","C_FNAME.5", "C_LNAME.5", "GRADE.5"})
in
    #"Expanded pivot subtable"

