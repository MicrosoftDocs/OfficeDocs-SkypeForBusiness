---
title: "New-CsSipProxyUseDefault"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1e8bedca-8bd5-4559-b530-0f18ae23d6d3
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsSipProxyUseDefault
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Used to assign the default realm (SIP Communications Service) to a collection of proxy configuration settings. Realms (also known as protection domains) are used to authenticate user credentials during logon. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsSipProxyUseDefault
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 assigns the default realm (SIP Communications Service) to a variable named $x. 
  
```
$x = New-CsSipProxyUseDefault

```

## Detailed Description
<a name="sectionSection1"> </a>

Proxy servers provide a way for users outside your internal network to access resources on your internal network. Each proxy server must be associated with a realm; realms (also known as protection domains) indicate where a user's logon credentials should be processed. By default, Lync Server uses SIP Communications Service as its default realm; however, it is possible to change the realm employed by a proxy server. If you change the realm and then want to revert back to using the default realm, you can do so by creating a SipProxy.UseDefault object, and then assigning that object to the Realm property of the appropriate proxy server (or servers). 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsSipProxyUseDefault** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsSipProxyUseDefault"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|||||
|This cmdlet provides only common Windows PowerShell parameters.  <br/> ||||
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsSipProxyUseDefault** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **New-CsSipProxyUseDefault** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.UseDefault object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsSipProxyCustom](new-cssipproxycustom.md)
  
[New-CsSipProxyRealm](new-cssipproxyrealm.md)

