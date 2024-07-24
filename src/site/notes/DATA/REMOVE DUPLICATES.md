---
{"dg-publish":true,"permalink":"/data/remove-duplicates/","tags":["Power_query","Data"]}
---

[[DATA/BI and PQ DATA TIPS AND TRICKS\|BI and PQ DATA TIPS AND TRICKS]]

### Remove duplicates from an individual cell


=Text.Combine (List.Distinct(List.Transform (Text.Split([EMAIL],","),each Text.Trim(_))),", ")