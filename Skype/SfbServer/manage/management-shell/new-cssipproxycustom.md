---
title: "New-CsSipProxyCustom"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3dc75cb0-c3d2-48bd-af32-2b2034b655dd
description: "Used to assign a custom realm (SIP Communications Service) to a collection of proxy configuration settings. Realms (also known as protection domains) are used to authenticate user credentials during logon. This cmdlet was introduced in Lync Server 2010."
---

# New-CsSipProxyCustom
 
Used to assign a custom realm (SIP Communications Service) to a collection of proxy configuration settings. Realms (also known as protection domains) are used to authenticate user credentials during logon. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsSipProxyCustom -CustomValue <String>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 assigns a custom realm (Litwareinc Communications Service) to a variable named $x.
  
```
$x = New-CsSipProxyCustom -CustomValue "Litwareinc Communications Service"
```

## Detailed Description

Each proxy server must be associated with a realm; realms (also known as protection domains) indicate where a user's logon credentials should be processed. By default, Skype for Business Server 2015 uses SIP Communications Service as its default realm; however, it is possible to change the realm used by a proxy server. This is done by creating a SipProxy.Custom object and then assigning that object to the Realm property of the appropriate proxy server (or servers). You can create a custom realm by using the **New-CsSipProxyCustom** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CustomValue_ <br/> |Required  <br/> |System.String  <br/> |Name of the realm to be used for authentication purposes.  <br/> |
   
## Input Types

None. The **New-CsSipProxyCustom** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsSipProxyCustom** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.Custom object.
  
## See also

#### 

[New-CsSipProxyRealm](new-cssipproxyrealm.md)
  
[New-CsSipProxyUseDefault](new-cssipproxyusedefault.md)

