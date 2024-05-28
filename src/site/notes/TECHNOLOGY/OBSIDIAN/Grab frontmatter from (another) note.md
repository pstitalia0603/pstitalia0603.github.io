---
{"dg-publish":true,"permalink":"/technology/obsidian/grab-frontmatter-from-another-note/","tags":["Obsidian","code"],"noteIcon":"","created":"2024-05-28T00:00:00","updated":"2024-05-28 9:45:35 am"}
---

## Yesterday is relative
<span><span>NOTES/DAILY NOTES/2024/05-May/2024-05-27.md</span></span>


## Yesterday is relative, but grabs frontmatter from yesterday
<span><span>IF_START: 2024-05-27T17:45:00.000-04:00</span></span>

## Yesterday is relative, but does calculation between notes
<span><span>Time difference between IF_START and IF_END: 13.00 hours</span></span>



## Grabs frontmatter from date_created today (not relative)
<span>2024-05-28</span>


## Calculates non-relative yesterday
<span><span>2024-05-27</span></span>

## Non-relative yesterday and today
<span><span>Today: 2024-05-28, Yesterday: 2024-05-27</span></span>


## Best way to grab frontmatter from current note:
dv.current().date_created


## This is the final correct code!
<span><span>Difference in hours between IF_START from yesterday and IF_END from today: 13</span></span>


REFERENCE:
https://chatgpt.com/share/38311efa-b7d5-4844-826c-f2193e555f0b