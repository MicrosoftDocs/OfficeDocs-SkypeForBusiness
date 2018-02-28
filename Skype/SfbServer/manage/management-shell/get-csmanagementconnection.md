---
title: "Get-CsManagementConnection"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b0e2377c-6aab-45d8-b71d-0d37c6f6dae3
description: "Returns information about the management connection to the Central Management store. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsManagementConnection
[]
Returns information about the management connection to the Central Management store. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsManagementConnection

```

## Examples

### EXAMPLE 1

The command in Example 1 returns information about the management connection to the Central Management store.
  
```
Get-CsManagementConnection
```

## Detailed Description

Configuration data for Skype for Business Server 2015 is stored in the Central Management store; it is crucial that both Windows PowerShell and the management replica services be able to locate this database. When you install Skype for Business Server 2015, a service control point is created in Active Directory Domain Services that provides location information for this database. Typically, computers rely on this service control point in order to connect to the Central Management store. To see the details behind this connection (that is, if you want to know which computer the Central Management store is running on, as well information about the SQL Server connection to that Central Management store) you can run the **Get-CsManagementConnection** cmdlet.
  
If you have used the **Set-CsManagementConnection** cmdlet to set up a temporary management connection for your current instance of Windows PowerShell (for example, in order to work from the local replica), the **Get-CsManagementConnection** cmdlet will report back information for that temporary connection. By comparison, the **Get-CsConfigurationStoreLocation** cmdlet always returns information for the service control point in Active Directory, regardless of where the local management connection is pointed.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|||||
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
|This cmdlet provides only common Windows PowerShell parameters.  <br/> ||||
   
## Input Types

None. The **Get-CsManagementConnection** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsManagementConnection** cmdlet returns instances of the Microsoft.Rtc.Management.Xds.ManagementConnection object.
  
## See also

#### 

[Remove-CsManagementConnection](remove-csmanagementconnection.md)
  
[Set-CsManagementConnection](set-csmanagementconnection.md)

