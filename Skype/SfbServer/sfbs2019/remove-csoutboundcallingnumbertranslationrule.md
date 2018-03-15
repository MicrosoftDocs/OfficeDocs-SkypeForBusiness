---
title: "Remove-CsOutboundCallingNumberTranslationRule"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 41ca92c9-7c2e-44e0-8ec8-9f39843b73e7
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsOutboundCallingNumberTranslationRule
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Removes an existing outbound calling number translation rule. An outbound calling number translation rule converts the E.164 phone numbers used by Lync Server 2013 to a format that can be used by trunking peers that do not support E.164 numbers. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsOutboundCallingNumberTranslationRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 removes the outbound calling number translation rule that has the Identity site:Redmond/SevenDigit.
  
```
Remove-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond/SevenDigit"
```

### Example 2

In Example 2, all the outbound calling number translation rules configured for the Redmond site are removed. To do this, the command calls the **Remove-CsOutboundCallingNumberTranslationRule** cmdlet along with the Identity parameter; the parameter value "site:Redmond" ensures that all the translation rules configured for the Redmond site will be removed. 
  
```
Remove-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond"
```

### Example 3

Example 3 deletes all the outbound calling number translation rules that use the Pattern "^\+1425(\d{7})$". To do this, the command first uses the **Get-CsOutboundCallingNumberTranslationRule** cmdlet to return a collection of all the translation rules used in the organization. This collection is then piped to the Where-Object cmdlet, which picks out only those rules where the Pattern property is equal to "^\+1425(\d{7})$". That filtered collection is then piped to the **Remove-CsOutboundCallingNumberTranslationRule** cmdlet, which deletes each rule in the collection. 
  
```
Get-CsOutboundCallingNumberTranslationRule | Where-Object {$_.Pattern -eq '^\+1425(\d{7})$'} | Remove-CsOutboundCallingNumberTranslationRule
```

## Detailed Description
<a name="DetailedDescription"> </a>

Outbound calling number translation rules convert the E.164 phone numbers used by Lync 2013 to a format that can be used by trunking peers that do not support E.164 numbers; when you create a translation rule you supply a regular expression representing the outbound E.164 number (the Pattern) as well as a regular expression representing the converted number (the Translation).
  
Outbound calling number translation rules must be bound to a collection of trunk configuration settings; when you create a new translation rule you must specify both the Identity of the trunking configuration settings and a name for the new rule (for example, site:Redmond/RedmondTranslationRule). Note that the trunking configuration settings do not necessarily have to exist at the time you create a new rule. For example, suppose you create the rule site:Redmond/RedmondTranslationRule but no trunk configuration settings have been created for the Redmond site. If the Redmond site is a valid site, trunk configuration settings will automatically be created for the site and the new translation rule will be assigned to that collection of settings. However, your command will fail if the Redmond site does not exist.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsOutboundCallingNumberTranslationRule"}
  
 **Lync Server Control Panel:** To remove an outbound calling number translation rule using the Lync Server Control Panel, click Voice Routing and then click Trunk Configuration. Double-click the appropriate item in the Name column and then, in the Edit Trunk Configuration dialog box, scroll down to the section labeled Calling number translation roles. Select the rule to be deleted, and then click Remove. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the outbound translation rule you want to remove. The Identity consists of the scope followed by a unique name within each scope. For example:  <br/> -Identity "site:Redmond/OutboundRule1"  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsOutboundCallingNumberTranslationRule** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule#Decorated object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsOutboundCallingNumberTranslationRule** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule#Decorated object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsOutboundCallingNumberTranslationRule](get-csoutboundcallingnumbertranslationrule.md)
  
[New-CsOutboundCallingNumberTranslationRule](new-csoutboundcallingnumbertranslationrule.md)
  
[Set-CsOutboundCallingNumberTranslationRule](set-csoutboundcallingnumbertranslationrule.md)

