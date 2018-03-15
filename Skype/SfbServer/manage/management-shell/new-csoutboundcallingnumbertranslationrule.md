---
title: "New-CsOutboundCallingNumberTranslationRule"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 959591bb-4a6b-4b7f-9666-da1fa0f9cd43
description: "Creates a new outbound calling number translation rule. An outbound calling number translation rule converts the E.164 phone numbers used by Skype for Business Server 2015 to a format that can be used by trunking peers that do not support E.164 numbers. This cmdlet was introduced in Lync Server 2013."
---

# New-CsOutboundCallingNumberTranslationRule
 
Creates a new outbound calling number translation rule. An outbound calling number translation rule converts the E.164 phone numbers used by Skype for Business Server 2015 to a format that can be used by trunking peers that do not support E.164 numbers. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsOutboundCallingNumberTranslationRule -Identity <XdsIdentity> <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new outbound calling number translation rule that converts an E.164 number that begins with the string value +1206 (for example, +12065551219) to a seven-digit value (for example, 5551219, stripping off the +1206).
  
```
New-CsOutboundCallingNumberTranslationRule -Parent "site:Redmond" -Name SevenDigit -Description "Converts a dialed number to seven digits" -Pattern '^\+1206(\d{7})$' -Translation '$1'
```

## Detailed Description
<a name="DetailedDescription"> </a>

Outbound calling number translation rules convert the E.164 phone numbers used by Skype for Business to a format that can be used by trunking peers that do not support E.164 numbers; when you create a translation rule you supply a regular expression representing the outbound E.164 number (the Pattern) as well as a regular expression representing the converted number (the Translation).
  
Outbound calling number translation rules must be bound to a collection of trunk configuration settings; when you create a new translation rule you must specify both the Identity of the trunking configuration settings and a name for the new rule (for example, site:Redmond/RedmondTranslationRule). Note that the trunking configuration settings do not necessarily have to exist at the time you create a new rule. For example, suppose you create the rule site:Redmond/RedmondTranslationRule but no trunk configuration settings have been created for the Redmond site. If the Redmond site is a valid site, trunk configuration settings will automatically be created for the site and the new translation rule will be assigned to that collection of settings. However, your command will fail if the Redmond site does not exist.
  
 **Skype for Business Server Control Panel:** To create a new outbound calling number translation rule using the Skype for Business Server Control Panel, click **Voice Routing** then click **Trunk Configuration**, and then double-click the appropriate item in the **Name** column. In the **Edit Trunk Configuration** dialog box scroll down to the section labeled **Calling number translation rules** and then click **New**.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the new translation rule. Names are composed of the scope (parent), a "/" character, and a unique name within that scope. For example, a rule named RedmondDialing created for the Redmond site would have an Identity that looked like this:  <br/>  `-Identity "site:Redmond/RedmondDialing"` <br/> If you use the Identity parameter then your command cannot contain either the Parent or the Name parameter.  <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |Name for the new translation rule; names must be unique for the given scope. For example:  <br/>  `-Name "RedmondDialing"` <br/> Any time you use the Name parameter you must also use the Parent parameter. The Name parameter cannot be used in the same command as the Identity parameter.  <br/> |
| _Parent_ <br/> |Required  <br/> |System.String  <br/> |Scope at which the new translation rule will be configured. To configure a rule at the global scope, use this syntax:  <br/>  `-Parent "global"` <br/> To configure a rule at the site scope, use syntax similar to this:  <br/>  `-Parent "site:Redmond"` <br/> To configure a rule at the service scope (for the PstnGateway service only) use syntax like this:  <br/>  `-Parent "service:PstnGateway:192.168.0.100"` <br/> Any time you use the Parent parameter you must also use the Name parameter. The Parent parameter cannot be used in the same command as the Identity parameter.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide additional text to accompany a translation rule. This description can be used to help administrators clearly identify the purpose of the rule.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _Pattern_ <br/> |Optional  <br/> |System.String  <br/> |A regular expression representing the number pattern to which the Translation will be applied.  <br/> |
| _Priority_ <br/> |Optional  <br/> |System.Int32  <br/> |Priority assigned to the rule. If a number matches the Pattern of more than one outbound translation rule, rules are applied in priority order. Rules are processed in order of their assigned priority; the first rule to be processed has a priority of 0; the second rule to be processed has a priority of 1; and so on.  <br/> |
| _Translation_ <br/> |Optional  <br/> |System.String  <br/> |A regular expression that will be applied to the number matching the Pattern to prepare that number for outbound calling.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsOutboundCallingNumberTranslationRule** cmdlet does not accept pipelined data.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsOutboundCallingNumberTranslationRule** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsOutboundCallingNumberTranslationRule](get-csoutboundcallingnumbertranslationrule.md)
  
[Remove-CsOutboundCallingNumberTranslationRule](remove-csoutboundcallingnumbertranslationrule.md)
  
[Set-CsOutboundCallingNumberTranslationRule](set-csoutboundcallingnumbertranslationrule.md)

