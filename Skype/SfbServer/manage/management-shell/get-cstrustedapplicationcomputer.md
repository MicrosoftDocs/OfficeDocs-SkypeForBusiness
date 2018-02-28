---
title: "Get-CsTrustedApplicationComputer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 360796d8-48c7-4ce2-9bb4-1f8967562f24
description: "Retrieves information about one or more computers that host trusted applications. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsTrustedApplicationComputer
[]
Retrieves information about one or more computers that host trusted applications. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsTrustedApplicationComputer [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 retrieves all computers that have been assigned to any trusted application pool within the Skype for Business Server 2015 deployment.
  
```
Get-CsTrustedApplicationComputer
```

### EXAMPLE 2

Example 2 retrieves information about the computer with the FQDN Trust1.litwareinc.com.
  
```
Get-CsTrustedApplicationComputer -Identity Trust1.litwareinc.com
```

### EXAMPLE 3

This example uses the Filter parameter to do a wildcard search for all computers that have an FQDN beginning with the string Trust that have been assigned to trusted application pools. The Filter parameter searches the Identity property of all trusted application computers. The wildcard character (\*) at the end of the string means that the Filter should look for identities that begin with the string Trust followed by any other characters.
  
```
Get-CsTrustedApplicationComputer -Filter Trust*
```

### EXAMPLE 4

Example 4 retrieves a list of all computers that have been assigned to the trusted application pool TrustPool.litwareinc.com.
  
```
Get-CsTrustedApplicationComputer -Pool TrustPool.litwareinc.com
```

### EXAMPLE 5

In Example 3 we used the Filter parameter to do a wildcard search based on Identity (the FQDN of the computer). In this example, we're again doing a wildcard search, but this time on the pool rather than the identity. We first call the **Get-CsTrustedApplicationComputer** cmdlet to retrieve a collection of all the trusted application computers. We then pipe that collection to the **Where-Object** cmdlet. The **Where-Object** cmdlet enables us to narrow down the collection that has been piped to it. In this case we want to keep only the trusted application computers that are in any pool on the litwareinc.com domain. To do this we check the Pool property of each item in the collection ($_.Pool) and see if it matches (-like) the wildcard string *.litwareinc.com. A value will match that string if it begins with any set of characters and ends with the string .litwareinc.com.
  
```
Get-CsTrustedApplicationComputer | Where-Object {$_.Pool -like "*.litwareinc.com"}
```

## Detailed Description

We recommend that the computers that are running trusted applications within a Skype for Business Server 2015 deployment be added to a separate pool that is only for trusted applications. However, you can add trusted application computers to an existing pool that is also used for other purposes. Use this cmdlet to retrieve the Identity (FQDN) and the pool on which it is located of one of more computers that contain trusted applications.
  
You can use this cmdlet to retrieve computers based on the computer FQDN or to retrieve all the computers that are part of a specified pool.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |A string that includes wildcards that enables you to retrieve trusted computers based on Identity values that match the given wildcard string.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The fully qualified domain name (FQDN) of the computer you want to retrieve.  <br/> |
| _Local_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, returns information only for the local computer.  <br/> |
| _Pool_ <br/> |Optional  <br/> |System.String  <br/> |The FQDN of the trusted application pool for which you want to retrieve computer information.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Retrieves one or more objects of type Microsoft.Rtc.Management.Xds.DisplayComputer.
  
## See also

#### 

[New-CsTrustedApplicationComputer](new-cstrustedapplicationcomputer.md)
  
[Remove-CsTrustedApplicationComputer](remove-cstrustedapplicationcomputer.md)

