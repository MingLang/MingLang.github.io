---
layout: post
title: Jekyll tables not render properly
category: Jekyll
tags: [Jekyll, CSS]
--- 

Create `_sass\_table.scss` and put this in:

```css
table {
  padding: 0; }
  table tr {
    border-top: 1px solid #cccccc;
    background-color: white;
    margin: 0;
    padding: 0; }
    table tr:nth-child(2n) {
      background-color: #f8f8f8; }
    table tr th {
      font-weight: bold;
      border: 1px solid #cccccc;
      text-align: left;
      margin: 0;
      padding: 6px 13px; }
    table tr td {
      border: 1px solid #cccccc;
      text-align: left;
      margin: 0;
      padding: 6px 13px; }
    table tr th :first-child, table tr td :first-child {
      margin-top: 0; }
    table tr th :last-child, table tr td :last-child {
      margin-bottom: 0; }
```

Then add this in `/style.scss`:

```css

// Import the github style to fix the tables.
@import "table";

```

<https://github.com/barryclark/jekyll-now/issues/561#issuecomment-340239560>
<https://github.com/misaka-10032/misaka-10032.github.io/commit/a779676201ebaa54fbe07c7803a71e88851470e5>