---
layout: post
title: Add favicon to Jekyll site
category: Jekyll
tags: [Jekyll, Favicon]
---

Save icon file (preferably `.png`) in `\images` and rename it as `favicon.png`, then add below declaration to `_layouts\default.html`.

```html
<link rel="shortcut icon" type="image/png" href="/images/favicon.png">
``` 
  
<https://stackoverflow.com/a/30552322/8403973>