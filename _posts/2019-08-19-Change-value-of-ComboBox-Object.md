---
layout: post
title: Change value of ComboBox Object
category:
tags: [VBA, ComboBox]
---

A individual ComboBox object can be referenced through `ws.DropDowns(1).Value`. However, when it is grouped with other objects, the script should be `ws.Shapes(1).GroupItems(3).ControlFormat.Value`.
