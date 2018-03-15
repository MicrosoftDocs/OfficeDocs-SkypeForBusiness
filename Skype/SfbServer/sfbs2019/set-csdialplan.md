---
title: "Set-CsDialPlan"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 80277dc6-8853-4cbd-87cb-e64f9e135d5f
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsDialPlan
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies an existing dial plan. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsDialPlan [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In Example 1, the **Set-CsDialPlan** cmdlet is used to modify the dial plan with the Identity RedmondDialPlan. In this case, the only property being modified is the Description; this modification is performed by specifying the Description parameter followed by the text for the new description. 
  
```
Set-CsDialPlan -Identity RedmondDialPlan -Description "This plan is for Redmond-based users only."
```

### EXAMPLE 2

In this example, the **Set-CsDialPlan** cmdlet is used to change the value of the ExternalAccessPrefix property for all the dial plans configured for use in the organization. To do this, the command first uses the **Get-CsDialPlan** cmdlet to return a collection of all the dial plans in the organization. That collection is then piped to the **Set-CsDialPlan** cmdlet, which assigns the value 8 to the ExternalAccessPrefix property for each profile in the collection. 
  
```
Get-CsDialPlan | Set-CsDialPlan -ExternalAccessPrefix 8
```

## Detailed Description
<a name="sectionSection1"> </a>

This cmdlet modifies an existing dial plan (also known as a location profile). Dial plans provide information required to enable Enterprise Voice users to make telephone calls. Dial plans are also used by the Conferencing Attendant application for dial-in conferencing. A dial plan determines such things as which normalization rules are applied and whether a prefix must be dialed for external calls.
  
Note: While normalization rules of a dial plan can be modified with this cmdlet, it is recommended that the **New-CsVoiceNormalizationRule** cmdlet, the **Set-CsVoiceNormalizationRule** cmdlet, or the **Remove-CsVoiceNormalizationRule** cmdlet be used instead. The changes made with those cmdlets will be reflected in the corresponding dial plan. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsDialPlan** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsDialPlan"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _City_ <br/> |Optional  <br/> |System.String  <br/> |This parameter is not used with this cmdlet.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _CountryCode_ <br/> |Optional  <br/> |System.String  <br/> |This parameter is not used with this cmdlet.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A description of this dial plan--what it's for, what type of user it applies to, or any other information that will be helpful in identifying the purpose of the dial plan.  <br/> Maximum characters: 512  <br/> |
| _DialinConferencingRegion_ <br/> |Optional  <br/> |System.String  <br/> |The name of the region associated with this dial plan. Specify a value for this parameter if the dial plan will be used for dial-in conferencing. This allows the correct access number to be assigned when the conference organizer sets up the conference. Available regions can be retrieved by calling the **Get-CsNetworkRegion** cmdlet.  <br/> Maximum characters: 512  <br/> |
| _ExternalAccessPrefix_ <br/> |Optional  <br/> |System.String  <br/> |A number (or set of numbers) that designates the call as external to the organization. (For example, to dial an outside line, first press 9.) This prefix will be ignored by the normalization rules, although these rules will be applied to the rest of the number.  <br/> The OptimizeDeviceDialing parameter must be set to True for this value to take effect.  <br/> The value of this parameter must match the regular expression [0-9]{1,4}. This means it must be a value one to four digits in length, each digit being a number 0 through 9.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier designating the scope, or, for per-user plans, a name, to identify the dial plan you want to modify. For example, a site Identity will be in the format site:\<sitename\>, where sitename is the name of the site. A dial plan at the service scope will be a Registrar or PSTN gateway service, where the Identity value is formatted like this: Registrar:Redmond.litwareinc.com. A per-user Identity will be a unique string value.  <br/> |
| _Instance_ <br/> |Optional  <br/> |LocationProfile  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values. You can retrieve this object reference by calling the **Get-CsDialPlan** cmdlet.  <br/> |
| _NormalizationRules_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |A list of normalization rules that are applied to this dial plan.  <br/> While this list and these rules can be modified directly with this cmdlet, it is recommended that you create normalization rules with the **New-CsVoiceNormalizationRule** cmdlet, which creates the rule and assigns it to the specified dial plan, and modify them with the **Set-CsVoiceNormalizationRule** cmdlet.  <br/> |
| _OptimizeDeviceDialing_ <br/> |Optional  <br/> |System.Boolean  <br/> |Setting this parameter to True will apply the prefix in the ExternalAccessPrefix parameter to calls made outside the organization. This value can be set to True only if a value has been specified for the ExternalAccessPrefix parameter.  <br/> |
| _SimpleName_ <br/> |Optional  <br/> |System.String  <br/> |A friendly name for the dial plan. Dial plan names must be unique among all dial plans within a Lync Server deployment.  <br/> This string can be up to 256 characters long. Valid characters are alphabetic or numeric characters, hyphen (-), dot (.), plus (+), underscore (_), and parentheses (()).  <br/> |
| _State_ <br/> |Optional  <br/> |System.String  <br/> |This parameter is not used with this cmdlet.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile object. Accepts pipelined input of dial plan objects.
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsDialPlan** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsDialPlan](new-csdialplan.md)
  
[Remove-CsDialPlan](remove-csdialplan.md)
  
[Get-CsDialPlan](get-csdialplan.md)
  
[Grant-CsDialPlan](grant-csdialplan.md)
  
[Test-CsDialPlan](test-csdialplan.md)
  
[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)
  
[Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)
  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)
  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)

