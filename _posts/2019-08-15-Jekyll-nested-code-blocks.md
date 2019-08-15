---
layout: post
Title: Jekyll highlighted code blocks nested by default
Category:
tags: [Jekyll, CSS]
---

When use ```` to highlight code blocks, Jeykll shows code blocks with an extra frame. 

The issue can be solved by replacing all `.highlight` with `pre.highlight` in `_sass/_highlights.scss`.

<https://stackoverflow.com/questions/55305080/jekyll-rouge-highlighted-code-blocks-nested>