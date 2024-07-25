---
{"dg-publish":true,"permalink":"/data/fiscal-month-number-calc/","tags":["Power_bi","Data"],"created":"2023-12-03 10:12","updated":"2024-03-01 19:43"}
---

[[DATA/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

POWER PIVOT DAX

FISCAL_MONTH_NUMBER
=if('Calendar'[Month Number]<7,'Calendar'[Month Number]+6,MOD('Calendar'[Month Number],7)+1)