---
title: "Set-SPLogLevel"
ms.author: laurawi
author: LauraWi
manager: laurawi
ms.date: 11/24/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c8ede92a-f685-4140-8587-96700d1a45de

description: "Sets the trace and event level for a set of categories."
---

# Set-SPLogLevel

Sets the trace and event level for a set of categories.
  
```
Set-SPLogLevel [-AssignmentCollection <SPAssignmentCollection>] [-EventSeverity <String>] [-Identity <String[]>] [-InputObject <PSObject>] [-TraceSeverity <String>]
```

## Detailed Description

The **Set-SPLogLevel** cmdlet sets the Windows event logging and trace logging levels for one or more diagnostic logging categories registered in the farm. If an event or trace associated with a category occurs, but is less severe than that category's logging level, the event or trace is not written to the event log or the trace log. If an event or trace associated with a category occurs and is equally severe or more severe than that category's logging level, the event or trace is written to the event log or the trace log. 
  
For permissions and the most current information about Windows PowerShell for SharePoint Products, see the online documentation at [Windows PowerShell for SharePoint Server 2016 reference](https://go.microsoft.com/fwlink/p/?LinkId=671715).
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**AssignmentCollection** <br/> |Optional  <br/> |Microsoft.SharePoint.PowerShell.SPAssignmentCollection  <br/> |Manages objects for the purpose of proper disposal. Use of objects, such as **SPWeb** or **SPSite**, can use large amounts of memory and use of these objects in Windows PowerShell scripts requires proper memory management. Using the **SPAssignment** object, you can assign objects to a variable and dispose of the objects after they are needed to free up memory. When **SPWeb**, **SPSite**, or **SPSiteAdministration** objects are used, the objects are automatically disposed of if an assignment collection or the **Global** parameter is not used.  <br/> > [!NOTE]> When the **Global** parameter is used, all objects are contained in the global store. If objects are not immediately used, or disposed of by using the **Stop-SPAssignment** command, an out-of-memory scenario can occur.           |
|**EventSeverity** <br/> |Optional  <br/> |System.String  <br/> |Specifies the category level to be set. The category level is any one of the following values:  <br/> - **None** <br/> - **ErrorCritical** <br/> - **Error** <br/> - **Warning** <br/> - **Information** <br/> - **Verbose** <br/> |
|**Identity** <br/> |Optional  <br/> |System.String[]  <br/> |Specifies the name(s) of the category or set of categories to set the throttle for; for example, "Unified Logging Service". If the **Identity** parameter is not specified, the event-throttling setting is applied to all categories in the farm.  <br/> |
|**InputObject** <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |The InputObject is pipelined to the cmdlet and can be a string in a format identical to the **Identity** parameter, or can be an **SPDiagnosticsCategory** object. The user can retrieve one or more categories from the **Get-SPLogLevel** cmdlet, modify the category values, and then pipeline them into the **Set-SPLogLevel** cmdlet.  <br/> |
|**TraceSeverity** <br/> |Optional  <br/> |System.String  <br/> |Specifies trace throttle to set the specified categor(ies) to. The trace log files are text files that are written to the trace log path that is defined on the Diagnostic Logging Settings page on the SharePoint Central Administration site. The type must be any one of the following values:  <br/> - **None** (no traces are written to the trace log)  <br/> - **Unexpected** <br/> - **Monitorable** <br/> - **High** <br/> - **Medium** <br/> - **Verbose** <br/> - **VerboseEx** <br/> |
   
## Example

------------------EXAMPLE 1-----------------------
  
```
set-sploglevel -TraceSeverity Monitorable
```

This example sets the  `TraceSeverity` values for all categories to  `Monitorable`.
  
------------------EXAMPLE 2-----------------------
  
```
Set-SPLogLevel -TraceSeverity High -EventSeverity Warning -Identity "Cat1"
```

This example sets the  `EventSeverity` and  `TraceSeverity` values for a single category. 
  
------------------EXAMPLE 3-----------------------
  
```
"Cat1", "Cat2", "Cat3" | Set-SPLogLevel -EventSeverity Error
```

This example sets the  `EventSeverity` values for multiple categories. 
  
------------------EXAMPLE 4-----------------------
  
```
Set-SPLogLevel -EventSeverity Warning -Identity "AreaName:*"
```

This example sets the  `EventSeverity` values for all categories in the same area. 
  
## See also

#### 

[Get-SPLogLevel](get-sploglevel.md)
  
[Clear-SPLogLevel](clear-sploglevel.md)
