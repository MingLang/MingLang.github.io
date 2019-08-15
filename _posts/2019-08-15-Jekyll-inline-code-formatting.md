---
layout: post
title: Jekyll inline code formatting
category:
tags: [Jekyll]
---

According to the page source, the class of inline code is `highlighter-ruge`. Therefore, add this to `_sass\_highlights.scss`: 

```CSS
.highlighter-rouge {
    background-color: #efefef;
    padding-left: 7px;
    padding-right: 7px;
}
```
  
<https://talk.jekyllrb.com/t/changing-the-coloring-of-inline-code-span/151/8>