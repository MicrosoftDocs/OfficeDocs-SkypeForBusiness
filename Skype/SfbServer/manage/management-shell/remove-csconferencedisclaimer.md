---
title: "Remove-CsConferenceDisclaimer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 196252a1-2526-4944-9064-01d1846f3266
description: "Clears the text from the header and body of the conference disclaimer used in your organization. The conference disclaimer is a message that is displayed to users who join the conference by using a hyperlink (for example, users who paste a link to the conference into a browser such as Windows Internet Explorer). This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsConferenceDisclaimer
 
Clears the text from the header and body of the conference disclaimer used in your organization. The conference disclaimer is a message that is displayed to users who join the conference by using a hyperlink (for example, users who paste a link to the conference into a browser such as Windows Internet Explorer). This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsConferenceDisclaimer -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 resets the property values of the global disclaimer. That means that both the disclaimer Header and Body will be set to null values, giving you a blank disclaimer.
  
```
Remove-CsConferenceDisclaimer -Identity global
```

## Detailed Description

When configuring conferencing settings, administrators can include a legal disclaimer to display to participants when these people join conferences hosted by Skype for Business Server 2015. This disclaimer is typically used to explain legal and intellectual property laws regarding the conference. Users cannot join the conference without agreeing to the stipulations set forth in the disclaimer. Note that this disclaimer is only shown to users who join a conference by using a hyperlink.
  
Skype for Business Server 2015 allows for a single, global instance of the conference disclaimer. The **Remove-CsConferenceDisclaimer** cmdlet enables you to reset your conference disclaimer: when you run this cmdlet, both the disclaimer header and the disclaimer body are set to null values.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the conference disclaimer to be removed. Although you can only have a single, global instance of the conference disclaimer, you must still use the Identity parameter when calling the **Remove-CsConferenceDisclaimer** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object. The **Remove-CsConferenceDisclaimer** cmdlet accepts pipelined input of conference disclaimer objects.
  
## Return Types

None. Instead, the **Remove-CsConferenceDisclaimer** cmdlet resets existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object to their default property values.
  
## See also

#### 

[Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md)
  
[Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)

