---
title: "New-CsSipProxyUseDefault"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1e8bedca-8bd5-4559-b530-0f18ae23d6d3
description: "Used to assign the default realm (SIP Communications Service) to a collection of proxy configuration settings. Realms (also known as protection domains) are used to authenticate user credentials during logon. This cmdlet was introduced in Lync Server 2010."
---

# New-CsSipProxyUseDefault
[]
Used to assign the default realm (SIP Communications Service) to a collection of proxy configuration settings. Realms (also known as protection domains) are used to authenticate user credentials during logon. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsSipProxyUseDefault

```

## Examples

### EXAMPLE 1

The command shown in Example 1 assigns the default realm (SIP Communications Service) to a variable named $x. 
  
```
$x = New-CsSipProxyUseDefault

```

## Detailed Description

Proxy servers provide a way for users outside your internal network to access resources on your internal network. Each proxy server must be associated with a realm; realms (also known as protection domains) indicate where a user's logon credentials should be processed. By default, Skype for Business Server 2015 uses SIP Communications Service as its default realm; however, it is possible to change the realm employed by a proxy server. If you change the realm and then want to revert back to using the default realm, you can do so by creating a SipProxy.UseDefault object, and then assigning that object to the Realm property of the appropriate proxy server (or servers). 
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|||||
|This cmdlet provides only common Windows PowerShell parameters.  <br/> ||||
   
## Input Types

None. The **New-CsSipProxyUseDefault** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsSipProxyUseDefault** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.UseDefault object.
  
## See also

#### 

[New-CsSipProxyCustom](new-cssipproxycustom.md)
  
[New-CsSipProxyRealm](new-cssipproxyrealm.md)

