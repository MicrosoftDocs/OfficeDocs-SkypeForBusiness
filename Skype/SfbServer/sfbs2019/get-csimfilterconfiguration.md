---
title: "Get-CsImFilterConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: de9b24a1-8d17-4da1-89c2-db5b532674eb
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsImFilterConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns the instant messaging (IM) link filters configured in your organization. These filters are used to prevent users from sending instant messages that contain hyperlinks with specific prefixes (for example, links with an http or telnet prefix). Depending on your settings, this means that any Uniform Resource Identifier (URI) prefaced with one of these schemes will be converted to a non-clickable hyperlink or removed altogether. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsImFilterConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 returns a collection of all the IM hyperlink filters configured for use in your organization. This is the behavior any time you call the **Get-CsImFilterConfiguration** cmdlet without any additional parameters. 
  
```
Get-CsImFilterConfiguration
```

### EXAMPLE 2

Example 2 returns settings for one IM filter: the settings that have the Identity site:Redmond. Because identities must be unique, this command can never return more than one configuration.
  
```
Get-CsImFilterConfiguration -Identity site:Redmond
```

### EXAMPLE 3

Example 3 uses the Filter parameter to return a collection of all the IM filters that have been configured at the site level. The wildcard string site:* instructs the **Get-CsImFilterConfiguration** cmdlet to return only those IM filter configurations that have an Identity that begins with the string value site:. 
  
```
Get-CsImFilterConfiguration -Filter site:*
```

### EXAMPLE 4

In Example 4 the value of the global IM filter configuration's Prefixes property is "expanded" when displayed on the screen; this simply means that the property and its values are shown in a more user-friendly and readable format. To perform this task, the **Get-CsImFilterConfiguration** cmdlet is first used to retrieve the global IM filter configuration. (Note that the call to the **Get-CsImFilterConfiguration** cmdlet is enclosed in parentheses. That tells Windows PowerShell to first carry out the command enclosed in parentheses, and then continue on from there.) After the configuration has been retrieved, the value of the Prefixes property is displayed with one prefix on each line. 
  
```
(Get-CsImFilterConfiguration -Identity Global).Prefixes
```

## Detailed Description
<a name="sectionSection1"> </a>

When sending instant messages, users can embed a URI within the text of that message to refer other participants in the conversation to a particular web site or share. Lync Server can be configured so that hyperlinks with certain prefixes are blocked or are not active. (In other words, the participants can't simply click the link and go to the site the URI refers to; they must copy and paste the link manually into a browser.) 
  
The **Get-CsImFilterConfiguration** cmdlet retrieves all the settings for filtering URIs from instant messages. Called by itself (with no parameters), the **Get-CsImFilterConfiguration** cmdlet returns all URI IM filter settings, globally and for all sites. You can also specify an Identity to show the settings for a specific site (or the global settings). 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsImFilterConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsImFilterConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Performs a wildcard search for configurations matching a given Identity pattern. For example, returns all settings with identities beginning with site\* (all site-specific settings).  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the settings you want to retrieve. This will be either global or site:\<site name\>, where \<site name\> is the name of the site to which these settings apply, such as site:Redmond.  <br/> Full Data Type: Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the IM filter configuration from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsImFilterConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsImFilterConfiguration](new-csimfilterconfiguration.md)
  
[Remove-CsImFilterConfiguration](remove-csimfilterconfiguration.md)
  
[Set-CsImFilterConfiguration](set-csimfilterconfiguration.md)

