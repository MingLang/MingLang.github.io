---
layout: post
title: Power Query combine multiple columns into one
category: Power Query
tags: [Power Query]
--- 

When combining multiple columns into one column, one way is using `&`, i.e. `[c1]&[c2]&[c3]`. However, when one of the columns is null, the formula will return null. Text.Combine is needed in this case. It can be used like `Text.Combine({[c1], [c2], [c3]})`, or `Text.Combine({[c1], [c2], [c3]}, "-")` when a seperator is needed.

