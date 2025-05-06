---
{"dg-publish":true,"permalink":"/technology/obsidian/grab-frontmatter-from-another-note/","tags":["Obsidian","code"],"noteIcon":"","created":"2024-05-28T00:00:00","updated":"2024-05-28 9:45:35 am"}
---



- [x] Difference in Hours 🛫 2024-05-28 ✅ 2024-05-28 
 

## Yesterday is relative
<span><span>NOTES/DAILY NOTES/2025/05-May/2025-05-05.md</span></span>


## Yesterday is relative, but grabs frontmatter from yesterday
<span><span>IF_START: 2025-05-05T18:45:00.000-04:00</span></span>

## Yesterday is relative, but does calculation between notes
<span><span>IF_END not found for today.</span></span>



## Grabs frontmatter from date_created today (not relative)
<span>May 28, 2024</span>


## Calculates non-relative yesterday
<span><span>2024-05-27</span></span>

## Non-relative yesterday and today
<span><span>Today: 2024-05-28, Yesterday: 2024-05-27</span></span>


## Best way to grab frontmatter from current note:
dv.current().date_created


## This is the final correct code!
<span><span>Difference in hours between IF_START from yesterday and IF_END from today: 13</span></span>


## Without Metaedit Plugin
<span><span><strong>Fasting overnight Hours:</strong> 13</span></span>

## With Metaedit Plugin
<pre class="dataview dataview-error">Evaluation Error: TypeError: Cannot read properties of undefined (reading 'api')
    at eval (eval at &lt;anonymous&gt; (plugin:dataview), &lt;anonymous&gt;:63:57)
    at DataviewInlineApi.eval (plugin:dataview:19027:16)
    at evalInContext (plugin:dataview:19028:7)
    at asyncEvalInContext (plugin:dataview:19038:32)
    at DataviewJSRenderer.render (plugin:dataview:19064:19)
    at DataviewJSRenderer.onload (plugin:dataview:18606:14)
    at e.load (app://obsidian.md/app.js:1:1214378)
    at DataviewApi.executeJs (plugin:dataview:19607:18)
    at DataviewCompiler.eval (plugin:digitalgarden:10760:23)
    at Generator.next (&lt;anonymous&gt;)</pre>


REFERENCE:
https://chatgpt.com/share/38311efa-b7d5-4844-826c-f2193e555f0b