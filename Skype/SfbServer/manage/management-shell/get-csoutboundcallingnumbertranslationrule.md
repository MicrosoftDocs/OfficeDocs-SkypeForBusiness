---
title: "Get-CsOutboundCallingNumberTranslationRule"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 65589388-f935-4d25-ae74-362be97c8597
description: "Returns information about the outbound calling number translation rules created for use in your organization. An outbound calling number translation rule converts the E.164 phone numbers used by Skype for Business Server 2015 to a format that can be used by trunking peers that do not support E.164 numbers. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsOutboundCallingNumberTranslationRule
 
Returns information about the outbound calling number translation rules created for use in your organization. An outbound calling number translation rule converts the E.164 phone numbers used by Skype for Business Server 2015 to a format that can be used by trunking peers that do not support E.164 numbers. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsOutboundCallingNumberTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about all the outbound calling number translation rules currently configured for use in the organization.
  
```
Get-CsOutboundCallingNumberTranslationRule
```

### Example 2

In Example 2, information is returned only for the outbound calling number translation rule that has the Identity "site:Redmond/SevenDigit."
  
```
Get-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond/SevenDigit"
```

### Example 3

Example 3 returns information for all the outbound calling number translation rules configured for the Redmond site. This is done by setting the value of the Identity parameter to the Identity of the Redmond site (site:Redmond).
  
```
Get-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond"
```

### Example 4

The command shown in Example 4 returns information only for outbound calling number translation rules that are on the Redmond site and have a Priority equal to 0. To do this, the command first uses the **Get-CsOutboundCallingNumberTranslationRule** cmdlet and the Identity parameter to return a collection of all the translation rules assigned to the Redmond site. This collection is then piped to the **Where-Object** cmdlet, which picks out only those rules that have a Priority equal to 0.
  
```
Get-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond" | Where-Object {$_.Priority -eq 0}
```

## Detailed Description
<a name="DetailedDescription"> </a>

Outbound calling number translation rules convert the E.164 phone numbers used by Skype for Business to a format that can be used by trunking peers that do not support E.164 numbers; when you create a translation rule you supply a regular expression representing the outbound E.164 number (the Pattern) as well as a regular expression representing the converted number (the Translation).
  
Outbound calling number translation rules must be bound to a collection of trunk configuration settings; when you create a new translation rule you must specify both the Identity of the trunking configuration settings and a name for the new rule (for example, site:Redmond/RedmondTranslationRule). Note that the trunking configuration settings do not necessarily have to exist at the time you create a new rule. For example, suppose you create the rule site:Redmond/RedmondTranslationRule but no trunk configuration settings have been created for the Redmond site. If the Redmond site is a valid site, trunk configuration settings will automatically be created for the site and the new translation rule will be assigned to that collection of settings. However, your command will fail if the Redmond site does not exist.
  
 **Skype for Business Server Control Panel:** To view outbound calling number translation roles in the Skype for Business Server Control Panel, click **Voice Routing** and then click **Trunk Configuration**. Double-click appropriate entry in the **Name** column and then, in the **Edit Trunk Configuration** dialog box, scroll down to the section labeled **Calling number translation rules**.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Performs a wildcard search that allows you to return only those outbound translation rules that have Identities that match the wildcard string. For example, this syntax returns all the translation rules that include the string value "Redmond":  <br/>  `-Filter "*Redmond*"` <br/> To return all the translation rules configured at the site scope use this syntax:  <br/>  `-Filter "site:*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the outbound calling number translation rule you want to retrieve. The Identity consists of the scope followed by a unique name within each scope; for example:  <br/>  `-Identity "site:Redmond/OutboundRule1"` <br/> To return all the translation rules configured for a specific scope (such as the Redmond site) simply set the Identity to the scope itself:  <br/>  `-Identity "site:Redmond"` <br/> If neither the Identity parameter nor the Filter parameter is specified the **Get-CsOutboundCallingNumberTranslationRule** cmdlet returns information about all your outbound calling number translation rules. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the outbound calling number translation rule data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsOutboundCallingNumberTranslationRule** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsOutboundCallingNumberTranslationRule** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsOutboundCallingNumberTranslationRule](new-csoutboundcallingnumbertranslationrule.md)
  
[Remove-CsOutboundCallingNumberTranslationRule](remove-csoutboundcallingnumbertranslationrule.md)
  
[Set-CsOutboundCallingNumberTranslationRule](set-csoutboundcallingnumbertranslationrule.md)

