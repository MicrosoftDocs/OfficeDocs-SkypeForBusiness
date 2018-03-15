---
title: "Get-CsPresenceManagementState"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6b7bc986-b655-4adf-87c5-b13b622ce333
description: "Use the Get-CsPresenceManagementState to return the notification settings of a computer or pool. The management state settings determine the batching and timing of Skype for Business Server 2015 notifications."
---

# Get-CsPresenceManagementState
 
Use the **Get-CsPresenceManagementState** to return the notification settings of a computer or pool. The management state settings determine the batching and timing of Skype for Business Server 2015 notifications.
  
```
Get-CsPresenceManagementState [-Force <SwitchParameter>] [-Fqdn <Fqdn>]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example returns the management state of a pool specified by its fully qualified domain name (FQDN).
  
```
Get-CsPresenceManagementState -Fqdn "atl-mcs-001.litwareinc.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |The  _Force_ parameter is not implemented for this cmdlet. <br/> |
| _Fqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Specifies the computer or pool to report. The computer or pool should be referenced by using its fully qualified domain name (FQDN). For example,  `-ComputerName "atl-mcs-001.litwareinc.com"`. If a pool is specified, the output contains the management state of all the computers in the pool. If  _FQDN_ is not specified, the settings for the local machine will be modified. <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsPresenceManagementState** cmdlet returns instances of the **[Microsoft.Rtc.Management.PresenceMaintain.Cmdlet.PresenceManagementState]** object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsPresenceManagementState](set-cspresencemanagementstate.md)

