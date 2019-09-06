---
layout: post
title: Activate Power Query and PowerPivot add-in through VBA
category: VBA
tags: [VBA, Power Query, PowerPivot]
--- 

The Power Query and PowerPivot add-in in Excel disappear randomly sometimes. Below VBA script can check their status when a workbook is opened and activate the PowerPovit add-in automatically if it is not activated. For some reason, the Power Query add-in can only be connected by an administrator via VBA script, so the script pops up a message box to remind the user to activate it manually.

'''vba
Option Explicit

Private Sub Workbook_Open()
    ' activate PowerPivot add-in
    Application.COMAddIns("PowerPivotExcelClientAddIn.NativeEntry.1").Connect = True
    
    ' activate Power Query add-in
    On Error GoTo errorHandler ' Cannot be found in Excel 2016 because it is built in
    If Application.COMAddIns("Microsoft.Mashup.Client.Excel").Connect = False Then
        MsgBox "Please activate the Power Query add-in!"
    End If

errorHandler:
    Exit Sub
    
End Sub
'''
