---
{"dg-publish":true,"permalink":"/data/remove-duplicates-power-bi/","tags":["dax","Power_bi","Data"],"noteIcon":""}
---

[[DATA/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

remove duplicates from an individual cell PowerBi


=Text.Combine (List.Distinct(List.Transform (Text.Split([EMAIL],","),each Text.Trim(_))),", ")