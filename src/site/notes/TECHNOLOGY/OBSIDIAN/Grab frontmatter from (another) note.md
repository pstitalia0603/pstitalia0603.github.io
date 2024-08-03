---
{"dg-publish":true,"permalink":"/technology/obsidian/grab-frontmatter-from-another-note/","tags":["Obsidian","code"],"created":"2024-05-28T00:00:00","updated":"2024-05-28 9:45:35 am"}
---



- [x] Difference in Hours 🛫 2024-05-28 ✅ 2024-05-28 
 

## Yesterday is relative
<span><span>NOTES/DAILY NOTES/2024/08-Aug/2024-08-02.md</span></span>


## Yesterday is relative, but grabs frontmatter from yesterday
<span><span>IF_START: 2024-08-02T18:27:00.000-04:00</span></span>

## Yesterday is relative, but does calculation between notes
<span><span>IF_END not found for today.</span></span>



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


## Without Metaedit Plugin
<span><span><strong>Fasting overnight Hours:</strong> 13</span></span>

## With Metaedit Plugin
<pre class="dataview dataview-error">Evaluation Error: TypeError: Cannot read properties of undefined (reading 'api')
    at eval (eval at &lt;anonymous&gt; (plugin:dataview), &lt;anonymous&gt;:63:57)
    at DataviewInlineApi.eval (plugin:dataview:18885:16)
    at evalInContext (plugin:dataview:18886:7)
    at asyncEvalInContext (plugin:dataview:18896:32)
    at DataviewJSRenderer.render (plugin:dataview:18922:19)
    at DataviewJSRenderer.onload (plugin:dataview:18464:14)
    at e.load (http://localhost/app.js:1:1171693)
    at DataviewApi.executeJs (plugin:dataview:19465:18)
    at DataviewCompiler.eval (plugin:digitalgarden:10760:23)
    at Generator.next (&lt;anonymous&gt;)
    at fulfilled (plugin:digitalgarden:77:24)</pre>


REFERENCE:
https://chatgpt.com/share/38311efa-b7d5-4844-826c-f2193e555f0b