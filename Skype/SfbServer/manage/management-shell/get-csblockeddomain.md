---
title: "Get-CsBlockedDomain"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5fa2c2a3-b5e4-430c-970a-0c506a6924b5
description: "Returns information about the domains that are included on the list of domains blocked for federation. By definition, your users are not allowed to use Skype for Business Server 2015 applications to communicate with people from the blocked domain; for example, users cannot use Skype for Business to exchange instant messages with anyone with a Session Initiation Protocol (SIP) account in a domain on the blocked list. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsBlockedDomain
[]
Returns information about the domains that are included on the list of domains blocked for federation. By definition, your users are not allowed to use Skype for Business Server 2015 applications to communicate with people from the blocked domain; for example, users cannot use Skype for Business to exchange instant messages with anyone with a Session Initiation Protocol (SIP) account in a domain on the blocked list. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsBlockedDomain [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns a collection of all the domains included on the blocked domain list. This is done by calling the **Get-CsBlockedDomain** cmdlet without any additional parameters.
  
```
Get-CsBlockedDomain
```

### EXAMPLE 2

In Example 2, the only blocked domain returned is the one with the Identity "fabrikam.com". Because domains on the blocked list must have unique identities, this command will return, at most, a single item.
  
```
Get-CsBlockedDomain -Identity fabrikam.com
```

### EXAMPLE 3

Example 3 uses the Filter parameter to return a collection of all the blocked domains that have an identity that ends in the string value ".net". This sample command returns such domains as northwindtraders.net, contoso.net, and fabrikam.net.
  
```
Get-CsBlockedDomain -Filter *.net
```

### EXAMPLE 4

Example 4 returns a collection of all the domains where the Comment property has no value. To do this, the command first uses the **Get-CsBlockedDomain** cmdlet to return a collection of all the domains on the blocked list. This collection is then piped to the **Where-Object** cmdlet, which selects only those domains where the Comment property is equal to a null value.
  
```
Get-CsBlockedDomain | Where-Object {$_.Comment -eq $Null}
```

### EXAMPLE 5

In Example 5, all the blocked domains that include the string value "Ken Myer" somewhere in the Comment property are returned. To carry out this task, the **Get-CsBlockedDomain** cmdlet is first called in order to return a collection of all the domains on the blocked domains list. This collection is then piped to the **Where-Object** cmdlet, which picks out those domains where the Comment property contains the string value "Ken Myer".
  
```
Get-CsBlockedDomain | Where-Object {$_.Comment -match "Ken Myer"}
```

## Detailed Description

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another by using SIP applications such as Skype for Business. Skype for Business Server 2015 allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
Setting up direct federation with another organization involves several tasks. To begin with, you must configure the Lync Server Access Edge service to allow federation. In addition, the other organization must enable federation with you; federation cannot be established unless both parties agree to the relationship.
  
To set up a federated relationship you might also need to manage two federation-related lists: the allowed list and the blocked list. The allowed list represents the organizations you have chosen to federate with; if a domain appears on the allowed list then (depending on your configuration settings) your users will be able to exchange instant messages and presence information with users who have accounts in that federated domain. Conversely, the blocked list represents domains that users are expressly forbidden from federating with; for example, messages sent from a blocked domain will automatically be rejected by Skype for Business Server 2015.
  
The **Get-CsBlockedDomain** cmdlet enables you to return information about the domains that appear on the blocked domain list.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return one or more domains from the list of blocked domains. To return all the domains that have an Identity that begins with the letter "r" use this syntax:  `-Filter r*`. To return all the domains that have an Identity that ends with ".net" use this syntax:  `-Filter "*.net"`. To return all the domains that have an Identity that begins with the letter "f" or with the letter "g" use this syntax:  `-Filter [fg]*`.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Name of the domain to be returned. Domains are listed on the blocked list by their fully qualified domain name (FQDN); thus the Identity for a given domain will be similar to fabrikam.com or contoso.net. Note that you cannot use wildcards when specifying a domain Identity. To use wildcards to return a given domain (or set of domains), use the Filter parameter instead.  <br/> If this parameter is not specified, then all the domains on the blocked domain list will be returned.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the blocked domain data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsBlockedDomain** cmdlet does not accept pipelined input.
  
## Return Types

Returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.BlockedDomain object.
  
## See also

#### 

[New-CsBlockedDomain](new-csblockeddomain.md)
  
[Remove-CsBlockedDomain](remove-csblockeddomain.md)
  
[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)
  
[Set-CsBlockedDomain](set-csblockeddomain.md)

