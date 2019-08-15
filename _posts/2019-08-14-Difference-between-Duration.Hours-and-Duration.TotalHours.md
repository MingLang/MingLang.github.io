---
layout: post
title: Difference between Duration.Hours and Duration.TotalHours
category: Power Query
tags: [Power Query]
---

`Duration.TotalSeconds` returns the duration in seconds.
`Duration.Seconds` returns the seconds part of the duration.

For example, if time A is 00:01:03 and time B is 00:00:00, then `Duration.TotalSeconds(time A - time B)` returns 63, and `Duration.Seconds(time A - time B)` returns 3. 

<https://docs.microsoft.com/en-us/powerquery-m/duration-seconds>
<https://docs.microsoft.com/en-us/powerquery-m/duration-totalseconds>
