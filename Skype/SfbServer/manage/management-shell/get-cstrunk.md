---
title: "Get-CsTrunk"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c49407f2-2e03-4b8b-b51b-75b12ef87fd1
description: "Returns information about the SIP trunks employed by your organization. SIP trunks connect the Skype for Business Server 2015 Voice over IP phone network with the Public Switched Telephone Network. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsTrunk
 
Returns information about the SIP trunks employed by your organization. SIP trunks connect the Skype for Business Server 2015 Voice over IP phone network with the Public Switched Telephone Network. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsTrunk [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information for all the SIP trunks configured for use in your organization.
  
```
Get-CsTrunk
```

### Example 2

In Example 2, information is returned for a single SIP trunk: the trunk with the Identity PstnGateway:192.168.0.240.
  
```
Get-CsTrunk -Identity "PstnGateway:192.168.0.240"
```

### Example 3

The command shown in Example 3 returns information for all the SIP trunks found on the pool atl-cs-001.litwareinc.com.
  
```
Get-CsTrunk -PoolFqdn "atl-cs-001.litwareinc.com"
```

### Example 4

Example 4 returns information for all the routable SIP trunks. To do this, the command first calls the **Get-CsTrunk** cmdlet without any parameters in order to return a collection of all the available SIP trunks. This collection is then piped to the **Where-Object** cmdlet, which picks out only those trunks where the Routable property is equal to (-eq) True ($True).
  
```
Get-CsTrunk | Where-Object {$_.Routable -eq $True}
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, trunks were used to route outbound calls from a Mediation Server to a PSTN gateway. Each gateway was limited to a single trunk; among other things this made it difficult for administrators to provide resiliency for outbound calls. However, because trunks and PSTN gateways were essentially identical, you could retrieve information about all your trunks by running this command:
  
 `Get-CsService -PstnGateway`
  
In Skype for Business Server 2015, multiple trunks can be assigned to a single PSTN gateway; this means that gateways and trunks are no longer essentially identical. In turn, that means that, in Skype for Business Server 2015, you cannot retrieve detailed information about individual trunks by using the **Get-CsService** cmdlet. Instead, detailed information about individual trunks is returned by using the new **Get-CsTrunk** cmdlet.
  
Note that, as far as the Windows PowerShell command-line interface is concerned, trunk information is read-only: you cannot create, delete or modify trunks by using PowerShell. Those operations can only be carried out by using Skype for Business Server 2015 Topology Builder.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsTrunk** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a SIP trunk (or collection of SIP trunks). For example, to return a collection of all the SIP trunks configured as part of the PSTN gateway service use this syntax:  <br/>  `-Filter "PstnGateway:*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the SIP trunk to be returned. For example:  <br/>  `-Identity "PstnGateway:192.168.0.240"` <br/> Note that you cannot use wildcards when specifying an Identity. If you need to use wildcards, then include the Filter parameter instead.  <br/> If this parameter is not specified, then the **Get-CsTrunk** cmdlet returns a collection of all the SIP trunks in use in the organization. <br/> |
| _PoolFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name for the trunk or PSTN gateway as defined in the topology. For example:  <br/>  `-PoolFqdn "atl-trunk-001.litwareinc.com"` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsTrunk** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsTrunk** cmdlet returns instances of the Microsoft.Rtc.Management.Xds.DisplayPstnGateway#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)

