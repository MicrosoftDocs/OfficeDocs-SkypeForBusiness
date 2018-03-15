---
title: "New-CsSipProxyRealm"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fedf9c71-5a23-4818-9f98-db5008a2ba74
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsSipProxyRealm
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Used to assign the default realm (SIP Communications Service) to a collection of proxy configuration settings. Realms (also known as protection domains) are used to authenticate user credentials during logon. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsSipProxyRealm -RealmChoice <IRealmChoice>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The commands shown in Example 1 assign the default realm (SIP Communications Service) to a variable named $y. To do this, the first command calls the **New-CsSipProxyUseDefault** cmdlet in order to create a SipProxy.UseDefault object; this object is stored in a variable named $x. 
  
In the second command, $x is used as the parameter value for the **New-CsSipProxyRealm** cmdlet and the RealmChoice parameter. In turn, this creates a new proxy realm object that is stored in a variable named $y. 
  
```
$x = New-CsSipProxyUseDefault
$y = New-CsSipProxyRealm -RealmChoice $x

```

### EXAMPLE 2

The commands shown in Example 2 assign a custom realm (Litwareinc Communications Service) to a variable named $y. To do this, the first command calls the **New-CsSipProxyCustom** cmdlet in order to create a SipProxy.Custom object; this object (which uses the CustomValue Litwareinc Communications Service) is stored in a variable named $x. 
  
In the second command, $x is used, along with the **New-CsSipProxyRealm** cmdlet and the RealmChoice parameter, to create a new custom realm object. 
  
```
$x = New-CsSipProxyCustom -CustomValue "Litwareinc Communications Service"
$y = New-CsSipProxyRealm -RealmChoice $x
```

## Detailed Description
<a name="sectionSection1"> </a>

Proxy servers provide a way for users outside your internal network to access resources on your internal network. Each proxy server must be associated with a realm; realms (also known as protection domains) indicate where a user's logon credentials should be processed. By default, Lync Server uses SIP Communications Service as its default realm; however, it is possible to change the realm used by a proxy server. The **New-CsSipProxyUseDefault** cmdlet and the **New-CsSipProxyCustom** cmdlet provide a way for you to change the realm used by a proxy server. These changes can also be made by using the **New-CsSipProxyRealm** cmdlet. However, because this cmdlet requires an additional step you might want to use the other two cmdlets any time you need to change the realm used by a proxy server. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsSipProxyRealm** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsSipProxyRealm"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _RealmChoice_ <br/> |Required  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.IRealmChoice  <br/> |Object representing the realm to be used by a proxy server. The RealmChoice must be created by using either the **New-CsSipProxyUseDefault** or the **New-CsSipProxyCustom** cmdlet.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsSipProxyRealm** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **New-CsSipProxyRealm** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.Realm object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsSipProxyCustom](new-cssipproxycustom.md)
  
[New-CsSipProxyUseDefault](new-cssipproxyusedefault.md)

