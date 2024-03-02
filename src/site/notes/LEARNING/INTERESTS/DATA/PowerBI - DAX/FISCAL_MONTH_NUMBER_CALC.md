---
{"dg-publish":true,"permalink":"/learning/interests/data/power-bi-dax/fiscal-month-number-calc/","tags":["Power_bi","Data"],"noteIcon":""}
---

[[PROFESSIONAL/PortfolioNotes/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

POWER PIVOT DAX

FISCAL_MONTH_NUMBER
=if('Calendar'[Month Number]<7,'Calendar'[Month Number]+6,MOD('Calendar'[Month Number],7)+1)