---
title: "Get-CsManagementConnection"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b0e2377c-6aab-45d8-b71d-0d37c6f6dae3
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsManagementConnection
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the management connection to the Central Management store. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsManagementConnection
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command in Example 1 returns information about the management connection to the Central Management store.
  
```
Get-CsManagementConnection
```

## Detailed Description
<a name="sectionSection1"> </a>

Configuration data for Lync Server is stored in the Central Management store; it is crucial that both Windows PowerShell and the management replica services be able to locate this database. When you install Lync Server, a service control point is created in Active Directory Domain Services that provides location information for this database. Typically, computers rely on this service control point in order to connect to the Central Management store. To see the details behind this connection (that is, if you want to know which computer the Central Management store is running on, as well information about the SQL Server connection to that Central Management store) you can run the **Get-CsManagementConnection** cmdlet. 
  
If you have used the **Set-CsManagementConnection** cmdlet to set up a temporary management connection for your current instance of Windows PowerShell (for example, in order to work from the local replica), the **Get-CsManagementConnection** cmdlet will report back information for that temporary connection. By comparison, the **Get-CsConfigurationStoreLocation** cmdlet always returns information for the service control point in Active Directory, regardless of where the local management connection is pointed. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsManagementConnection** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsManagementConnection"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|||||
|This cmdlet provides only common Windows PowerShell parameters.  <br/> ||||
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsManagementConnection** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsManagementConnection** cmdlet returns instances of the Microsoft.Rtc.Management.Xds.ManagementConnection object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsManagementConnection](remove-csmanagementconnection.md)
  
[Set-CsManagementConnection](set-csmanagementconnection.md)

