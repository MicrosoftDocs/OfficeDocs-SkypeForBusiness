---
title: "Get-CsDialPlan"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f77df510-ea43-4352-84c1-13f69eda252e
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsDialPlan
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the dial plans used in your organization. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsDialPlan [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 returns a collection of all the dial plans configured for use in your organization; this is done by calling the **Get-CsDialPlan** cmdlet without any additional parameters. 
  
```
Get-CsDialPlan
```

### EXAMPLE 2

In Example 2, the Identity parameter is used to limit the retrieved data to dial plans that have a per-user dial plan with the Identity RedmondDialPlan. Because identities must be unique, this command will return only the specified dial plan.
  
```
Get-CsDialPlan -Identity RedmondDialPlan
```

### EXAMPLE 3

Example 3 is identical to Example 2 except that instead of retrieving a per-user dial plan, we're retrieving a dial plan assigned to a site. We do that by specifying the value site: followed by the site name (in this case Redmond) of the site we want to retrieve.
  
```
Get-CsDialPlan -Identity site:Redmond
```

### EXAMPLE 4

This example uses the Filter parameter to return a collection of all the dial plans that have been configured at the per-user scope. (Settings configured at the per-user, or tag, scope can be directly assigned to users and groups.) The wildcard string tag:\* instructs the cmdlet to return only those dial plans that have an identity beginning with the string value tag:, which identifies a dial plan as a per-user dial plan.
  
```
Get-CsDialPlan -Filter tag:*
```

### EXAMPLE 5

This example displays the normalization rules used by the dial plans configured for use in your organization. Because the NormalizationRules property consists of an array of objects, the complete set of normalization rules is typically not displayed on screen. To see all of these rules, this sample command first uses the **Get-CsDialPlan** cmdlet to retrieve a collection of all the dial plans. That collection is then piped to the **Select-Object** cmdlet; in turn, the ExpandProperty parameter of the **Select-Object** cmdlet is used to "expand" the values found in the NormalizationRules property. Expanding the values simply means that all the normalization rules will be listed out individually on the screen, the same output that would be seen if the **Get-CsVoiceNormalizationRule** cmdlet had been called. 
  
```
Get-CsDialPlan | Select-Object -ExpandProperty NormalizationRules
```

### EXAMPLE 6

In Example 6, the **Get-CsDialPlan** cmdlet and the **Where-Object** cmdlet are used to retrieve a collection of all the dial plans that include the word Redmond in their description. To do this, the command first uses the **Get-CsDialPlan** cmdlet to retrieve all the dial plans. That collection is then piped to the **Where-Object** cmdlet, which applies a filter that limits the returned data to profiles that have the word Redmond somewhere in their Description. 
  
```
Get-CsDialPlan | Where-Object {$_.Description -match "Redmond"}
```

## Detailed Description
<a name="sectionSection1"> </a>

This cmdlet returns information about one or more dial plans (also known as a location profiles) in an organization. Dial plans provide information required to enable Enterprise Voice users to make telephone calls. Dial plans are also used by the Conferencing Attendant application for dial-in conferencing. A dial plan determines such things as which normalization rules are applied and whether a prefix must be dialed for external calls.
  
Note: You can use the **Get-CsDialPlan** cmdlet to retrieve specific information about the normalization rules of a dial plan, but if that's the only dial plan information you need, you can also use the **Get-CsVoiceNormalizationRule** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsDialPlan** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsDialPlan"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Performs a wildcard search that allows you to narrow down your results to only dial plans with identities that match the given wildcard string.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier designating the scope, and for per-user scope a name, to identify the dial plan you want to retrieve.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the dial plan information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsDialPlan](new-csdialplan.md)
  
[Remove-CsDialPlan](remove-csdialplan.md)
  
[Set-CsDialPlan](set-csdialplan.md)
  
[Grant-CsDialPlan](grant-csdialplan.md)
  
[Test-CsDialPlan](test-csdialplan.md)
  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)

