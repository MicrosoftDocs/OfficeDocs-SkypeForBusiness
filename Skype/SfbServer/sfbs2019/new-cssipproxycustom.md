---
title: "New-CsSipProxyCustom"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3dc75cb0-c3d2-48bd-af32-2b2034b655dd
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsSipProxyCustom
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Used to assign a custom realm (SIP Communications Service) to a collection of proxy configuration settings. Realms (also known as protection domains) are used to authenticate user credentials during logon. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsSipProxyCustom -CustomValue <String>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 assigns a custom realm (Litwareinc Communications Service) to a variable named $x.
  
```
$x = New-CsSipProxyCustom -CustomValue "Litwareinc Communications Service"
```

## Detailed Description
<a name="sectionSection1"> </a>

Each proxy server must be associated with a realm; realms (also known as protection domains) indicate where a user's logon credentials should be processed. By default, Lync Server uses SIP Communications Service as its default realm; however, it is possible to change the realm used by a proxy server. This is done by creating a SipProxy.Custom object and then assigning that object to the Realm property of the appropriate proxy server (or servers). You can create a custom realm by using the **New-CsSipProxyCustom** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsSipProxyCustom** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsSipProxyCustom"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CustomValue_ <br/> |Required  <br/> |System.String  <br/> |Name of the realm to be used for authentication purposes.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsSipProxyCustom** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **New-CsSipProxyCustom** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.Custom object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsSipProxyRealm](new-cssipproxyrealm.md)
  
[New-CsSipProxyUseDefault](new-cssipproxyusedefault.md)

