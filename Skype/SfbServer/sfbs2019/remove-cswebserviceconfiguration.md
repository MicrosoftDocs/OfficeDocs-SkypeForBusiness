---
title: "Remove-CsWebServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1df2f881-6594-4de7-9762-8d64b2243355
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsWebServiceConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes one or more collections of Web Services configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsWebServiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 removes the Web Services configuration settings for the Redmond site. 
  
```
Remove-CsWebServiceConfiguration -Identity site:Redmond
```

### EXAMPLE 2

In Example 2, all the Web Services settings configured at the site scope are removed. To carry out this task, the command first calls the **Get-CsWebServiceConfiguration** cmdlet and the Filter parameter; the filter value "site:*" ensures that only those settings that have an Identity that begins with the characters "site:" are returned. This filtered collection is then piped to the **Remove-CsWebServiceConfiguration** cmdlet, which deletes each item in the collection. 
  
```
Get-CsWebServiceConfiguration -Filter "site:*" | Remove-CsWebServiceConfiguration
```

### EXAMPLE 3

The command shown in Example 3 deletes all the Web Services configuration settings where group expansion has been disabled. To do this, the command first calls the **Get-CsWebServiceConfiguration** cmdlet without any parameters in order to return a collection of all the Web Services configuration settings used in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the EnableGroupExpansion property is equal to False. The filtered collection is then piped to the **Remove-CsWebServiceConfiguration** cmdlet, which deletes each item in the collection. 
  
```
Get-CsWebServiceConfiguration | Where-Object {$_.EnableGroupExpansion -eq $False} | Remove-CsWebServiceConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

Many Lync Server components are web-based: these components either use web services or webpages to carry out their tasks. For example, users employ a web service when searching for new contacts in the Address Book or when using group expansion to view the individual members of a distribution group. Likewise, components ranging from dial-in conferencing to Lync Server Control Panel use webpages as the interface between Lync Server and users.
  
The **CsWebServiceConfiguration** cmdlets enable administrators to manage Web Services configuration settings throughout the organization. This includes managing group expansion, certificate settings, and allowed authentication methods. Because you can configure different settings at the global, site, and service scope (for the Web Services service only), you can customize Web Services capabilities for different users and different locations. 
  
If you create custom Web Services configuration settings at the site or service scope these settings can later be removed by using the **Remove-CsWebServiceConfiguration** cmdlet. Note that you can also run the **Remove-CsWebServiceConfiguration** cmdlet against the global collection of Web Services settings. In that case, however, the global collection will not be removed; that's because Lync Server does not allow you to remove global settings. Instead, all the properties in the global collection will revert to their default values. For example, suppose you have changed the MaxGroupSizeToExpand value to 500. Because the default value for this property is 100, "removing" the global collection will reset the value of the MaxGroupSizeToExpand property to 100. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsWebServiceConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsWebServiceConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the Web Services configuration settings to be removed. To remove settings configured at the site scope, use syntax similar to this: -Identity "site:Redmond". To remove settings configured at the service scope, use syntax similar to this: -Identity "service:WebServer:atl-cs-001.litwareinc.com".  <br/> The **Remove-CsWebServiceConfiguration** cmdlet can also be run against the global collection. In that case, however, the global collection will not be removed; instead, all the properties in that collection will be reset to their default values. To reset the global collection, use this syntax: -Identity global.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.Web.WebServiceSettings object. The **Remove-CsWebServiceConfiguration** cmdlet accepts pipelined input of the Web Services settings object, 
  
## Return Types
<a name="sectionSection3"> </a>

None. Instead, the **Remove-CsWebServiceConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Web.WebServiceSettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)
  
[New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)
  
[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

