---
layout: post
title: Like operator and Instr
category:
tags: [VBScript, VBA]
---


There is no `Like` operator in VBScript. You could use `Instr`.

`if Instr( 1, strPrinter, "printer_USA", vbTextCompare ) > 0 then`

The vbTextCompare constant (value=1) is used to Perform a textual comparison

https://stackoverflow.com/questions/30301118/vbs-using-like-to-compare-strings-sub-or-function-not-defined

'Like' operator is case-sensitive, but 'Instr' is not.

Pattens can be used with `Like` operator. See https://docs.microsoft.com/en-us/office/vba/language/reference/user-interface-help/like-operator
