---
{"dg-publish":true,"permalink":"/data/remove-duplicates-power-bi/","tags":["dax","Power_bi","Data"],"noteIcon":"","created":"2023-12-03 10:12","updated":"2024-03-01 19:44"}
---

[[DATA/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

remove duplicates from an individual cell PowerBi


=Text.Combine (List.Distinct(List.Transform (Text.Split([EMAIL],","),each Text.Trim(_))),", ")