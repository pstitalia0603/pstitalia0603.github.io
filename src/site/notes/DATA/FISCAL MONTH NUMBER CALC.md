---
{"dg-publish":true,"permalink":"/data/fiscal-month-number-calc/","tags":["Power_bi","Data"]}
---

[[DATA/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

POWER PIVOT DAX

FISCAL_MONTH_NUMBER
=if('Calendar'[Month Number]<7,'Calendar'[Month Number]+6,MOD('Calendar'[Month Number],7)+1)