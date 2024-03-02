---
{"dg-publish":true,"permalink":"/personal/data/power-query-m/remove-duplicates/","tags":["Power_query","Data"],"noteIcon":""}
---

[[PROFESSIONAL/CODE_SNIPPETS/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

### Remove duplicates from an individual cell


=Text.Combine (List.Distinct(List.Transform (Text.Split([EMAIL],","),each Text.Trim(_))),", ")