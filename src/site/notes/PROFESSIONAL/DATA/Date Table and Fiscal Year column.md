---
{"dg-publish":true,"permalink":"/professional/data/date-table-and-fiscal-year-column/","tags":["Power_bi","Power_query","m-code","dax","Data"],"noteIcon":""}
---

[[PROFESSIONAL/CODE_SNIPPETS/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

FISCAL YEAR M CODE
https://www.youtube.com/watch?v=bo-43zg1R8U

if [Month] <7 then "FY" &
Text.End(Number.ToText([Year]-1),2) 
else 
"FY" & Text.End(Number.ToText([Year]),2)


DAX
NEW TABLE -->

DateTable = 
VAR MinYear = YEAR ( MIN ( AF_DASHBOARD[GIFT DATE] ) )
VAR MaxYear = YEAR ( MAX ( AF_DASHBOARD[GIFT DATE] ) )
RETURN
ADDCOLUMNS (
    FILTER (
        CALENDARAUTO( ),
        AND ( YEAR ( [Date] ) >= MinYear, YEAR ( [Date] ) <= MaxYear )
    ),
    "Calendar Year", YEAR ( [Date] ),
    "Month Name", FORMAT ( [Date], "mmmm" ),
    "Month Number", MONTH ( [Date] ),
    "Weekday", FORMAT ( [Date], "dddd" ),
    "Weekday number", WEEKDAY( [Date] )//,
  //  "Quarter", "Q" & TRUNC ( ( MONTH ( [Date] ) - 1 ) / 3 ) + 1
)



//Column
FISCAL_YEAR = 
    VAR _FiscalMonthStart=7
    RETURN
        IF(
            DateTable[Month Number] >= _FiscalMonthStart,
            DateTable[Calendar Year] + 1,
            DateTable[Calendar Year]
        )

//Column
FYMONTH_NUM = IF(MONTH(DateTable[Date])>6, MONTH(DateTable[Date])-6, MONTH(DateTable[Date]) +6)
