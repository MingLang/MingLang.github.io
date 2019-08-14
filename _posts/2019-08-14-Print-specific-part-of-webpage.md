---
layout: post
Title: Print specific part of webpage
Category:
tags: javascript
---

```javascript
var prtContent = document.getElementsByTagName("article")[0];
var WinPrint = window.open('', '', 'left=0,top=0,width=800,height=900,toolbar=0,scrollbars=0,status=0');
WinPrint.document.write(prtContent.innerHTML);
WinPrint.document.close();
WinPrint.focus();
WinPrint.print();
WinPrint.close();
```

https://stackoverflow.com/questions/12997123/print-specific-part-of-webpage
