---
title: "Set-SPServiceApplicationSecurity"
ms.author: laurawi
author: LauraWi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8d769193-f126-43f7-8c1e-4bec75c8446d

description: "Updates the SPObjectSecurity object for a service application."
---

# Set-SPServiceApplicationSecurity

Updates the **SPObjectSecurity** object for a service application. 
  
```
Set-SPServiceApplicationSecurity [-Identity] <SPServiceApplicationPipeBind> [-ObjectSecurity] <SPObjectSecurity> [-Admin <SwitchParameter>] [-AssignmentCollection <SPAssignmentCollection>]
```

## Detailed Description

The **Set-SPServiceApplicationSecurity** cmdlet updates a security object for the specified service application. Use this cmdlet with the **Grant-SPObjectSecurity** and **Get-SPServiceApplicationSecurity** cmdlets to manage security for a service application. 
  
For permissions and the most current information about Windows PowerShell for SharePoint Products, see the online documentation at [Windows PowerShell for SharePoint Server 2016 reference](https://go.microsoft.com/fwlink/p/?LinkId=671715).
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Identity** <br/> |Required  <br/> |Microsoft.SharePoint.PowerShell.SPServiceApplicationPipeBind  <br/> |Specifies the service application that contains the **SPObjectSecurity** object to update.  <br/> The type must be a valid GUID, in the form 12345678-90ab-cdef-1234-567890bcdefgh; a valid name of a service application (for example, ServiceApp1); or an instance of a valid **SPServiceApplication** object.  <br/> |
|**ObjectSecurity** <br/> |Required  <br/> |Microsoft.SharePoint.Administration.AccessControl.SPObjectSecurity  <br/> |Specifies the **SPObjectSecurity** object to update.  <br/> |
|**Admin** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Updates the access control list (ACL) that contains the administrators list of the service application.  <br/> |
|**AssignmentCollection** <br/> |Optional  <br/> |Microsoft.SharePoint.PowerShell.SPAssignmentCollection  <br/> |Manages objects for the purpose of proper disposal. Use of objects, such as **SPWeb** or **SPSite**, can use large amounts of memory and use of these objects in Windows PowerShell scripts requires proper memory management. Using the **SPAssignment** object, you can assign objects to a variable and dispose of the objects after they are needed to free up memory. When **SPWeb**, **SPSite**, or **SPSiteAdministration** objects are used, the objects are automatically disposed of if an assignment collection or the **Global** parameter is not used.  <br/> > [!NOTE]> When the **Global** parameter is used, all objects are contained in the global store. If objects are not immediately used, or disposed of by using the **Stop-SPAssignment** command, an out-of-memory scenario can occur.           |
   
## AutoGenParams

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Identity** <br/> |Required  <br/> |Microsoft.SharePoint.PowerShell.SPServiceApplicationPipeBind  <br/> ||
|**ObjectSecurity** <br/> |Required  <br/> |Microsoft.SharePoint.Administration.AccessControl.SPObjectSecurity  <br/> ||
|**Admin** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**AssignmentCollection** <br/> |Optional  <br/> |Microsoft.SharePoint.PowerShell.SPAssignmentCollection  <br/> ||
   
## Example

------------------EXAMPLE------------------
  
```
$security = Get-SPServiceApplicationSecurity $serviceApp -AdminGrant-SPObjectSecurity $security $principal "Full Control"Set-SPServiceApplicationSecurity $serviceApp -Admin $security
```

This example retrieves the **SPObjectSecurity** object corresponding to the administrator ACL on a service application, and adds a new user principal to that ACL. The new user is an administrator for the service application  `$serviceApp`.
  
## See also

#### 

[Get-SPServiceApplicationSecurity](get-spserviceapplicationsecurity.md)
  
[Grant-SPObjectSecurity](grant-spobjectsecurity.md)
  
[Revoke-SPObjectSecurity](revoke-spobjectsecurity.md)
