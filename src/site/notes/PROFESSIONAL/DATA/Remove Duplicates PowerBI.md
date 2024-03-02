---
{"dg-publish":true,"permalink":"/professional/data/remove-duplicates-power-bi/","tags":["dax","Power_bi","Data"],"noteIcon":""}
---

[[PROFESSIONAL/CODE_SNIPPETS/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

remove duplicates from an individual cell PowerBi


=Text.Combine (List.Distinct(List.Transform (Text.Split([EMAIL],","),each Text.Trim(_))),", ")