---
layout: post
title: Add back-to-top button to Jekyll pages
category: Jekyll
tags: [Jekyll, BackToTop]
---

Add this to `<body>` in `_layouts/default.html`.

```html
<script src="https://unpkg.com/vanilla-back-to-top@7.2.0/dist/vanilla-back-to-top.min.js"></script>
<script>addBackToTop({
  diameter: 56,
  backgroundColor: 'rgb(255, 82, 82)',
  textColor: '#fff'
})</script>
```

<https://github.com/vfeskov/vanilla-back-to-top>