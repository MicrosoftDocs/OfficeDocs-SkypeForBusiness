---
title: "Get-CsComputer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 493931a9-1670-4a76-abba-7d3c7723d2e1
description: "Returns information about the computers that perform service roles within your Skype for Business Server 2015 infrastructure. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsComputer
 
Returns information about the computers that perform service roles within your Skype for Business Server 2015 infrastructure. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsComputer [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

In Example 1 the **Get-CsComputer** cmdlet is used to return information about all the computers that perform service roles within your Skype for Business Server 2015 infrastructure.
  
```
Get-CsComputer
```

### EXAMPLE 2

The command shown in Example 2 uses the Filter parameter to return only those service role computers that are part of the litwareinc.com domain. The wildcard string \*.litwareinc.com restricts the returned information to computers that have an FQDN that ends with the string value ".litwareinc.com". 
  
```
Get-CsComputer -Filter "*.litwareinc.com"
```

### EXAMPLE 3

In Example 3, the Identity parameter is used to limit the returned data to the one computer that has the FQDN atl-cs-001.litwareinc.com.
  
```
Get-CsComputer -Identity "atl-cs-001.litwareinc.com"
```

### EXAMPLE 4

In Example 4, the Pool parameter is used to return information about all the computers found in the pool atl-cs-001.litwareinc.com.
  
```
Get-CsComputer -Pool "atl-cs-001.litwareinc.com"
```

## Detailed Description

The **Get-CsComputer** cmdlet provides a way to quickly identify computers that are running Skype for Business Server 2015 services or server roles. Called without any parameters, the **Get-CsComputer** cmdlet returns a collection of all the computers that are running Skype for Business Server 2015 services or server roles; this collection includes the Identity, pool name, and fully qualified domain name (FQDN) for each computer. Alternatively, you can use optional parameters such as Identity, Filter, or Pool to limit the returned data to a single computer or set of computers.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters when specifying the Identity of the computer (or computers) to be returned. For example, this command returns information about all the computers that have an Identity that begins with the string value "atl-":  `-Filter "atl-*"`.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |FQDN of the computer to be returned. For example:  `-Identity "atl-cs-001.litwareinc.com"`.  <br/> If this parameter is not specified, all of the computers running Skype for Business Server 2015 will be returned.  <br/> |
| _Local_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, returns information only for the local computer.  <br/> |
| _Pool_ <br/> |Optional  <br/> |System.String  <br/> |FQDN of a Skype for Business Server 2015 pool. When you use this parameter, information about all the computers in the specified pool will be returned.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsComputer** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsComputer** cmdlet returns instances of the Microsoft.Rtc.Management.Deploy.Internal.Machine object.
  
## See also

#### 

[Disable-CsComputer](disable-cscomputer.md)
  
[Enable-CsComputer](enable-cscomputer.md)
  
[Test-CsComputer](test-cscomputer.md)

