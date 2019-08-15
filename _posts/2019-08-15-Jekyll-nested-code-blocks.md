---
layout: post
Title: Jekyll highlighted code blocks nested by default
Category:
tags: [Jekyll, CSS]
---

When use ```` ``` ```` to highlight code blocks, Jeykll shows code blocks with an extra frame. 

The issue can be solved by replacing all `.highlight` with `pre.highlight` in `_sass/_highlights.scss`.

<https://stackoverflow.com/questions/55305080/jekyll-rouge-highlighted-code-blocks-nested>
<https://meta.stackexchange.com/questions/125148/implement-style-fenced-markdown-code-blocks>
<https://meta.stackexchange.com/revisions/d29ee470-c239-4d38-8ab1-5583517d1f9c/view-source>