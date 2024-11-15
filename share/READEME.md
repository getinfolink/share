# Setting for PDF Export only 
## style.css 
```css
/* Font and color */
body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
  color: #333;
  font-size: 12pt;
  margin: 1.5cm;
}

/* Header styling */
h1, h2, h3, h4, h5, h6 {
  color: #333;
  font-weight: bold;
  margin-top: 1.5em;
  margin-bottom: 0.5em;
}
h1 { font-size: 24pt; border-bottom: 2px solid #444; padding-bottom: 5px; }
h2 { font-size: 20pt; border-bottom: 1px solid #777; padding-bottom: 3px; }
h3 { font-size: 16pt; color: #555; }
h4 { font-size: 14pt; color: #666; }
p {
  margin: 0.8em 0;
}
a {
  color: #1a73e8;
  text-decoration: none;
}
ul, ol {
  margin: 0.8em 0;
  padding-left: 1.5em;
}
li {
  margin-bottom: 0.5em;
}
pre {
  background-color: #f5f5f5;
  padding: 10px;
  border-radius: 5px;
  overflow-x: auto;
}
code {
  font-family: 'Courier New', monospace;
  color: #d63384;
}
table {
  width: 100%;
  border-collapse: collapse;
  margin: 1em 0;
}
th, td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}
th {
  background-color: #f4f4f4;
  font-weight: bold;
}
blockquote {
  color: #555;
  border-left: 4px solid #ddd;
  padding-left: 1em;
  margin: 1em 0;
  font-style: italic;
}
 
```


## Markdown PDF header Original 
```html
<div style="font-size: 9px; margin-left: 1cm;"> <span class='title'></span></div> <div style="font-size: 9px; margin-left: auto; margin-right: 1cm; ">%%ISO-DATE%%</div> 





<div style="font-size: 9px; margin-left: 1cm;"> <span class='title'>InfoLink</span></div> <div style="font-size: 9px; margin-left: auto; margin-right: 1cm; ">Aung Thu Oo</div> 
```

## Markdown pdf header custom 
```html
<div style="font-size: 12px; font-weight:bold;margin-left: 0.5cm;"> <span class=''>InfoLink</span></div> <div style="font-size: 9px; margin-left: auto; margin-right: 0.5cm; ">#DevNote</div> 
```

## Markdown pdf footer custom 
```html
<div style="font-size: 12px; margin-left: 0.5cm;"> <span class=''>Save post</span></div> Page <span class="pageNumber"></span> of ---- <span class="totalPages"></span><div style="font-size: 9px; margin-left: auto; margin-right: 0.5cm; ">Swipe </div> 


<span class=''>Save post</span> Page <span class="pageNumber"></span> of ---- <span class="totalPages"></span>

```

<div style="font-size: 9px; text-align: center;">
    Page %%PAGE_NUMBER%% of %%TOTAL_PAGES%%
</div>

<div style="font-size: 12px; margin: 0 auto; color:black"> <span class='pageNumber'></span> / <span class='totalPages'></span></div>


<div style="color:black"> <span class='pageNumber'></span> / <span class='totalPages'></span></div>