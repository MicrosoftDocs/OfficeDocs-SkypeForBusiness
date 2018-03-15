---
title: "Set-CsSlaConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 4/12/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e701759e-14e1-4017-b46c-3976eba3e561
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsSlaConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
 Use the **Set-CsSlaConfiguration** cmdlet to create or modify a shared number in Shared Line Appearance (SLA). A shared number in SLA is an Enterprise Voice user that is capable of receiving multiple calls at a time and forwarding them to its delegates, who answer the call. 
  
```
Set-CsSlaConfiguration -Identity <UserIdParameter> [-BusyOption <Forward | BusyOnBusy | Voicemail>] [-Confirm [<SwitchParameter>]] [-MaxNumberOfCalls <UInt32>] [-MissedCallForwardTarget <Uri>] [-MissedCallOption <Disconnect | Forward | BusySignal>] [-PassThru <SwitchParameter>] [-Target <Uri>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example configures SLA for a user identified as "emergency" that can accept at max 3 calls at a time. Note that "emergency" is a valid enterprise voice enabled Skype for Business (SfB) user. BusyOption is required if SLA is being setup for the first time.
  
```
Set-CsSlaConfiguration -Identity emergency -MaxNumberOfCalls 3 -BusyOption BusyOnBusy
```

### Example 2

This example configures SLA for a user identified as "emergency" to forward calls to "sla_forward_number" when all lines are busy.
  
```
Set-CsSlaConfiguration -Identity emergency -MaxNumberOfCalls 3 -BusyOption Forward -Target sip:sla_forward_number@contosohealth.com  
```

### Example 3

This example configures SLA for a user identified as "emergency" to transfer to voice mail when all lines are busy.
  
```
Set-CsSlaConfiguration -Identity emergency -MaxNumberOfCalls 3 -BusyOption Voicemail
```

## Detailed Description
<a name="DetailedDescription"> </a>

 SLA is a feature in Skype for Business (SfB) for handling multiple calls on a specific number called a shared number. SLA can configure any enterprise voice enabled SfB user as a shared number with multiple lines to respond to multiple calls. The calls are not actually received on the shared number, instead they are forwarded to users that act as delegates for the shared number. Any one of the delegates can pick up the call while the rest of the delegates get a notification on their phone about who picked up the call and which line has become busy as a result. Both the number of lines and the delegates are configurable for a shared number in SLA. In addition, advanced options such as BusyOption (what happens in a situation when all lines are busy) and MissedCallOption (the case in which none of the delegates pick up a call) etc. can also be configured for a shared number. 
  
The Set-CsSlaConfiguration cmdlet provides a way to configure a shared number.
  
> [!NOTE]
> Logging in with the account created for the SLA number is not supported. Using the SLA number account with any device or Desktop Client can result in unpredictable behavior. It is not necessary to use that account for the Shared Line Appearance feature to function. 
  
By default, members of the RTCUniversalServerAdmins group are authorized to run the **Set-CsSlaConfiguration** cmdlet. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsSlaConfiguration"}
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Indicates the identity of the Enterprise Voice user whose shared number information will be created or modified.  <br/> UNRESOLVED_TOKENBLOCK_VAL(PS_PD_User_Updated_Specification)  <br/> |
| _BusyOption_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SlaBusyOption  <br/> |Specifies the action to take when all lines are busy. The valid values for the option are "Forward", "BusyOnBusy", or "Voicemail". The default is "BusyOnBusy".  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _MaxNumberOfCalls_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the maximum number of calls the shared number can receive.  <br/> |
| _MissedCallForwardTarget_ <br/> |Optional  <br/> |System.Uri  <br/> | Specifies the forwarding target if  _MissedCallOption_ is set to "Forward".  _MissedCallForwardTarget_ should be set to a valid SIP Uri. If the PSTN number needs to be specified, it should be prefixed with "tel:". For example, "tel:+2504395".  <br/> |
| _MissedCallOption_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SlaUserMissedCallOption  <br/> |Specifies the action to take when none of the delegates picks up the call. The valid values for the option are "Disconnect", "Forward", or "BusySignal". The default is "Disconnect".  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |UNRESOLVED_TOKEN_VAL(PS_PD_Passthru_Generic_CurrentObjects)  <br/> |
| _Target_ <br/> |Optional  <br/> |System.Uri  <br/> | Specifies the forwarding target if  _BusyOption_ is set to "Forward".  _Target_ should be set to a valid SIP Uri. If the PSTN number needs to be specified, it should be prefixed with "tel:", "tel:+2504395".  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsSlaConfiguration** cmdlet accepts a pipelined object representing a user account that has been enabled for Skype for Business Server 2015. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Set-CsSlaConfiguration** cmdlet returns an instance of the **[Microsoft.Rtc.Management.SlaConfiguration]** object. 
  

