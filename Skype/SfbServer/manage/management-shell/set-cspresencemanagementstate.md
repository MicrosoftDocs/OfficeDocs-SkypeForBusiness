---
title: "Set-CsPresenceManagementState"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dbb6a81d-ebff-486e-b83f-4e73365a193c
description: "Use the Set-CsPresenceManagementState cmdlet to modify the settings of the Skype for Business Server 2015 management state. The management state settings determine the batching and timing of Skype for Business Server 2015 notifications."
---

# Set-CsPresenceManagementState
 
Use the **Set-CsPresenceManagementState** cmdlet to modify the settings of the Skype for Business Server 2015 management state. The management state settings determine the batching and timing of Skype for Business Server 2015 notifications.
  
> [!NOTE]
> Generally the **Set-CsPresenceManagementState** cmdlet should only be used under the direction of Microsoft support. Setting the presence management parameters incorrectly can result in unwanted network behavior, or cause presence not to update.
  
```
Set-CsPresenceManagementState [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Fqdn <Fqdn>] [-LimitedNotificationMode <$true | $false>] [-ManualOverride <$true | $false>] [-MaxHttpMessageSizeKb <UInt32>] [-MaxPublishersPerBatch <UInt32>] [-MaxRemotePublishersPerBatch <UInt32>] [-MaxRemoteQueueThreadCount <UInt32>] [-NotificationBatchInterval <UInt32>] [-NotificationBatchSize <UInt32>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example set the  _NotificationBatchSize_ to 50 on the pool or computer named "atl-mcs-001.litwareinc.com".
  
```
Set-CsPresenceManagementState -Fqdn "atl-mcs-001.litwareinc.com" -NotificationBatchSize 50
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
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |The  _Force_ parameter is not implemented for this cmdlet. <br/> |
| _Fqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Specifies the computer or pool to modify. The computer or pool should be referenced by using its fully qualified domain name (FQDN). For example:  `-Fqdn "atl-mcs-001.litwareinc.com"`. If  _FQDN_ is not specified, the settings for the local machine will be modified. <br/> |
| _LimitedNotificationMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _ManualOverride_ <br/> |Optional  <br/> |System.Boolean  <br/> |This parameter is reserved for internal Microsoft use.  <br/> |
| _MaxHttpMessageSizeKb_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _MaxPublishersPerBatch_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies a general guideline for the number of publishers that are collected before notifications are sent. Reducing the  _MaxPublishersPerBatch_ value reduces database pressure at the expense of longer notification wait time after publishing. Increasing this value reduces notification wait times during periods of high volume, but increases database and network traffic. <br/> |
| _MaxRemotePublishersPerBatch_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _MaxRemoteQueueThreadCount_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _NotificationBatchInterval_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the time in seconds between notification batches. Reducing the  _NotificationBatchInterval_ value increases database and network traffic but improves notification wait times. Increasing the value increases notification wait times. <br/> |
| _NotificationBatchSize_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the maximum number of messages to send in one batch notification. This parameters should only be changed if messages are exceeding a maximum message size parameter in your organization.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableOutgoingNotificationQueue_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnablePublishRequestThrottleEndpoint_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _MaxNumOfEndpointPublishRequestAllowed_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _ResetEndpointThrottlingPeriodInMin_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPresenceManagementState](get-cspresencemanagementstate.md)

