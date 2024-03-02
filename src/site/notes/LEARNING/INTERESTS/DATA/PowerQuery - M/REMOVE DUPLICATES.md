---
{"dg-publish":true,"permalink":"/learning/interests/data/power-query-m/remove-duplicates/","tags":["Power_query","Data"],"noteIcon":""}
---

[[PROFESSIONAL/PortfolioNotes/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

remove duplicates from an individual cell




=Text.Combine (List.Distinct(List.Transform (Text.Split([EMAIL],","),each Text.Trim(_))),", ")