---
title: Set-CsOutboundCallingNumberTranslationRule
ms.prod: SKYPEFORBUSINESS
ms.assetid: e9a7190a-a50d-4d01-8f33-66ed88a52b9e
---


# Set-CsOutboundCallingNumberTranslationRule
[]
Modifies an existing outbound calling number translation rule. An outbound calling number translation rule converts the E.164 phone numbers used by Skype for Business Server 2015 to a format that can be used by trunking peers that do not support E.164 numbers. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Set-CsOutboundCallingNumberTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 changes the Priority of the outbound calling number translation rule with the Identity site:Redmond/SevenDigit. In this example, the Priority is set to 0.
  
    
    

```

Set-CsOutboundCallingNumberTranslationRule -Identity "site:Redmond/SevenDigit" -Priority 0
```


## Detailed Description
<a name="DetailedDescription"> </a>

Outbound calling number translation rules convert the E.164 phone numbers used by Skype for Business to a format that can be used by trunking peers that do not support E.164 numbers; when you create a translation rule you supply a regular expression representing the outbound E.164 number (the Pattern) as well as a regular expression representing the converted number (the Translation).
  
    
    
Outbound calling number translation rules must be bound to a collection of trunk configuration settings; when you create a new translation rule you must specify both the Identity of the trunking configuration settings and a name for the new rule (for example, site:Redmond/RedmondTranslationRule). Note that the trunking configuration settings do not necessarily have to exist at the time you create a new rule. For example, suppose you create the rule site:Redmond/RedmondTranslationRule but no trunk configuration settings have been created for the Redmond site. If the Redmond site is a valid site, trunk configuration settings will automatically be created for the site and the new translation rule will be assigned to that collection of settings. However, your command will fail if the Redmond site does not exist.
  
    
    
 **Skype for Business Server Control Panel:** To edit an existing outbound calling number translation rule using the Skype for Business Server Control Panel, click **Voice Routing**, click **Trunk Configuration**, and then double-click the configuration settings containing the rule to be modified. In the **Edit Trunk Configuration** dialog box, scroll down to the section labeled **Calling number translation rules** and then double-click the rule to be modified.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide additional text to accompany a translation rule. This description can be used to help administrators clearly identify the purpose of the rule.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the translation rule to be modified. The Identity consists of the scope followed by a unique name within each scope. For example:  <br/>  `-Identity "site:Redmond/OutboundRule1"` <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Pattern_ <br/> |Optional  <br/> |System.String  <br/> |A regular expression representing the number pattern to which the Translation will be applied.  <br/> |
| _Priority_ <br/> |Optional  <br/> |System.Int32  <br/> |Priority assigned to the rule. If a number matches the Pattern of more than one outbound translation rule, rules are applied in priority order. Rules are processed in order of their assigned priority; the first rule to be processed has a priority of 0; the second rule to be processed has a priority of 1; and so on.  <br/> |
| _Translation_ <br/> |Optional  <br/> |System.String  <br/> |A regular expression that will be applied to the number matching the Pattern to prepare that number for outbound calling.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The **Set-CsOutboundCallingNumberTranslationRule** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule#Decorated object.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsOutboundCallingNumberTranslationRule** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.CallingNumberTranslationRule#Decorated object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsOutboundCallingNumberTranslationRule](get-csoutboundcallingnumbertranslationrule.md)
  
    
    
 [New-CsOutboundCallingNumberTranslationRule](new-csoutboundcallingnumbertranslationrule.md)
  
    
    
 [Remove-CsOutboundCallingNumberTranslationRule](remove-csoutboundcallingnumbertranslationrule.md)
