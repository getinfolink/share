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
<div style="
  display: flex; 
  align-items: center; 
  font-size: 10px; 
  margin-left: 1em;
  font-weight:bold;
">
  <span style="display: flex; align-items: center;">
    <svg version="1.0" xmlns="http://www.w3.org/2000/svg"
         style="fill: blue;" width="13px" height="13px" viewBox="0 0 571.000000 571.000000"
         preserveAspectRatio="xMidYMid meet">
      <g transform="translate(0.000000,571.000000) scale(0.100000,-0.100000)"
         fill="blue"  stroke="none">
        <path d="M2710 5393 c-47 -21 -90 -41 -97 -46 -6 -4 -188 -96 -405 -206 -261
        -132 -404 -210 -426 -232 -54 -54 -74 -104 -79 -196 -5 -75 -3 -88 21 -137 39
        -80 76 -113 208 -185 29 -16 97 -54 152 -85 54 -31 101 -56 103 -56 3 0 17 -8
        31 -18 15 -11 56 -35 92 -54 36 -19 85 -46 110 -60 25 -14 72 -40 105 -58 33
        -17 89 -49 125 -70 36 -21 108 -61 160 -90 128 -70 174 -96 315 -175 66 -38
        149 -84 185 -103 36 -20 81 -45 100 -57 19 -11 46 -26 60 -33 45 -22 157 -87
        172 -100 9 -7 18 -38 21 -75 24 -257 259 -409 503 -325 183 63 285 267 228
        458 -39 132 -139 221 -289 255 -82 19 -171 6 -251 -36 l-55 -30 -137 77 c-75
        42 -162 90 -192 107 -80 43 -282 156 -300 167 -8 5 -28 17 -45 26 -16 9 -119
        66 -228 128 -109 61 -227 127 -262 146 -35 19 -114 63 -177 97 -62 35 -180
        101 -263 148 -82 48 -162 91 -177 98 -16 6 -28 17 -28 24 0 7 194 110 430 228
        l430 215 403 -202 402 -203 11 -80 c14 -96 29 -127 96 -201 114 -124 282 -156
        436 -84 187 88 265 321 171 512 -29 57 -113 136 -176 166 -51 24 -70 27 -159
        27 -98 0 -103 -1 -178 -39 l-78 -40 -211 108 c-117 59 -219 111 -227 116 -8 5
        -67 34 -130 65 -63 30 -122 60 -130 65 -64 40 -161 74 -220 77 -58 3 -75 -1
        -150 -34z"/>
        <path d="M1598 3829 c-72 -10 -128 -39 -190 -97 -117 -110 -150 -289 -78 -436
        30 -62 109 -139 177 -173 52 -25 68 -28 158 -28 111 1 162 17 236 76 37 29 41
        30 58 15 10 -9 20 -16 24 -16 3 0 104 -58 224 -128 120 -71 246 -144 280 -163
        35 -19 63 -39 63 -45 0 -19 -336 -209 -625 -354 -220 -110 -278 -144 -316
        -182 -114 -115 -110 -313 9 -420 21 -19 94 -65 162 -104 69 -38 134 -74 145
        -81 11 -7 29 -16 41 -22 11 -5 55 -30 98 -55 43 -25 80 -46 82 -46 2 0 70 -38
        152 -83 81 -46 174 -99 207 -117 50 -28 149 -83 300 -170 86 -49 189 -107 213
        -120 123 -68 435 -243 512 -289 l95 -56 7 -65 c18 -166 103 -279 251 -334 69
        -26 213 -19 279 13 165 80 251 262 204 436 -37 139 -134 231 -286 270 -79 20
        -152 10 -247 -36 l-62 -30 -43 22 c-24 12 -88 47 -143 78 -55 32 -145 82 -200
        113 -252 140 -388 216 -480 268 -55 31 -122 69 -150 84 -27 16 -83 48 -123 73
        -40 24 -133 77 -205 117 -352 193 -607 341 -607 350 0 6 147 85 328 175 180
        90 336 171 347 181 11 10 35 26 54 36 18 11 41 24 50 29 9 6 50 30 91 54 41
        24 92 54 112 67 21 13 43 24 49 24 6 0 58 -28 115 -62 57 -35 119 -71 137 -80
        17 -9 149 -86 292 -170 l259 -153 11 -56 c25 -123 94 -216 202 -270 64 -32 74
        -34 168 -34 93 0 105 2 167 33 139 68 218 210 205 366 -13 160 -115 283 -276
        332 -101 30 -216 8 -318 -62 -55 -38 -56 -38 -123 6 -21 14 -411 240 -455 264
        -23 13 -257 151 -295 175 -14 8 -38 22 -55 31 -16 9 -97 56 -180 104 -82 49
        -226 133 -320 188 -93 55 -201 119 -240 141 -95 55 -103 63 -110 110 -19 111
        -77 195 -181 263 -35 22 -69 35 -105 39 -30 3 -63 8 -74 9 -11 2 -46 -1 -77
        -5z"/>
      </g>
    </svg>
    InfoLink
  </span>
</div>
<div style="font-size: 8px; margin-left: auto; margin-right: 0.5cm;">#DevNote</div>
 
```

## Markdown pdf footer custom 
```html
<div style='margin-left: 0.5cm;font-size:8px; text-align:left; width:25%;'>⬇️ Save post</div>
<div style='font-size:8px; text-align:center; width:50%;'>
  <span class='pageNumber'></span> of <span class='totalPages'></span>
</div>
<div style='margin-right: 0.5cm;font-size:8px; text-align:right; width:25%;'>Swipe ⟫</div>
```