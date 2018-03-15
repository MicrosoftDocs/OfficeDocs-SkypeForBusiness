---
title: "Set-CsConferenceDisclaimer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 97afce6d-b031-466d-a170-3ca50d6df245
description: "Modifies the property values of the conference disclaimer used in your organization. The conference disclaimer is a message displayed to users who join a conference by using a hyperlink (for example, by pasting a link to the conference into a browser such as Windows Internet Explorer). This cmdlet was introduced in Lync Server 2010."
---

# Set-CsConferenceDisclaimer
 
Modifies the property values of the conference disclaimer used in your organization. The conference disclaimer is a message displayed to users who join a conference by using a hyperlink (for example, by pasting a link to the conference into a browser such as Windows Internet Explorer). This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsConferenceDisclaimer [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 modifies both the Header and Body properties for your organization's conference disclaimer. Because you can have only one such disclaimer, you do not need to specify the Identity when running the **Set-CsConferenceDisclaimer** cmdlet.
  
```
Set-CsConferenceDisclaimer -Header "Litwareinc.com Online Conference" -Body "Important note: Conferencing proceedings are recorded and archived."
```

## Detailed Description

When configuring conferencing settings, administrators can include a legal disclaimer to display to participants when they join conferences hosted by Skype for Business Server 2015. This disclaimer is typically used to explain legal and intellectual property laws regarding the conference. Users cannot join the conference without agreeing to the stipulations set forth in the disclaimer. Note, however, that this disclaimer is only shown to users who join a conference by using a hyperlink.
  
Skype for Business Server 2015 allows for a single, global instance of the conference disclaimer. The **Set-CsConferenceDisclaimer** cmdlet enables you to modify the conference disclaimer used in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Body_ <br/> |Optional  <br/> |System.String  <br/> |Contents of the conference disclaimer.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Header_ <br/> |Optional  <br/> |System.String  <br/> |Title given the conference disclaimer.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the conference disclaimer. Because you can only have a single, global instance of the conference disclaimer, you do not need to specify an Identity when calling the **Set-CsConferenceDisclaimer** cmdlet. However, you can use the following syntax to reference the global disclaimer: `-Identity global`.  <br/> |
| _Instance_ <br/> |Optional  <br/> |ConferenceDisclaimer object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object. The **Set-CsConferenceDisclaimer** cmdlet accepts pipelined input of conference disclaimer objects.
  
## Return Types

The **Set-CsConferenceDisclaimer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object.
  
## See also

#### 

[Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md)
  
[Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)

