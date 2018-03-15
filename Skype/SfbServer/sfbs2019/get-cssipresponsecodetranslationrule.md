---
title: "Get-CsSipResponseCodeTranslationRule"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 075e9e85-8f85-402c-9256-4e73ec93f96b
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsSipResponseCodeTranslationRule
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about SIP response code translation rules. These rules enable administrators to map SIP response codes with values between 400 and 699 to the values used by Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsSipResponseCodeTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 returns a collection of all the response code translation rules configured for use in your organization. This is done by calling the **Get-CsSipResponseCodeTranslationRule** cmdlet without any parameters. 
  
```
Get-CsSipResponseCodeTranslationRule
```

### EXAMPLE 2

Example 2 returns a single response code translation rule: the rule with the Identity PstnGateway:192.168.0.240/Rule404.
  
```
Get-CsSipResponseCodeTranslationRule -Identity "PstnGateway:192.168.0.240/Rule404"
```

### EXAMPLE 3

In Example 3, the Filter parameter is used to limit the returned data to all the response code translation rules configured at the site scope. The filter value "site:\*" limits the returned data to rules that have an Identity that begins with the string value "site:".
  
```
Get-CsSipResponseCodeTranslationRule -Filter "site:*"
```

### EXAMPLE 4

The command shown in Example 4 returns a collection of all the response code translation rules where no value has been configured for the ReceivedISUPCauseValue property. To do this, the command first calls the **Get-CsSipResponseCodeTranslationRule** cmdlet without any parameters in order to return a collection of all the response code translation rules currently in use. That collection is then piped to the **Where-Object** cmdlet, which picks out only those rules where the ReceivedISUPCauseValue property is equal to -1. 
  
```
Get-CsSipResponseCodeTranslationRule | Where-Object {$_.ReceivedISUPCauseValue -eq -1}
```

## Detailed Description
<a name="sectionSection1"> </a>

SIP trunking provides a way to connect a Voice over Internet Protocol (VoIP) network (such as Enterprise Voice) with the public switched telephone network (PSTN). In Lync Server, the Mediation Server uses trunking peers to interact with the PSTN network. When an outgoing call fails on the PSTN network, an ISDN User Part (ISUP) cause code is automatically generated. For example, a PSTN gateway might send cause code 34 to indicate that no circuit or channel was available for completing the call. When a Mediation Server trunking peer receives that ISUP cause code, it converts the code to a SIP response code, which is then sent to the Mediation Server itself. In turn, Lync Server uses these response codes to make its outbound routing decisions. For example, a malfunctioning gateway might automatically be assigned a "less-preferred" status; this minimizes the use of the malfunctioning gateway, and thus maximizes the chance of a call being successfully completed.
  
However, not all gateways use the recommended ISUP cause code to SIP response code mapping used by Lync Server. For these gateways, administrators can use the **CsSipResponseCodeTranslationRule** cmdlets to map the gateway SIP response code (in combination with the ISUP cause code, if that code is available) to a SIP response code used by Lync Server. For example, a gateway might map ISUP cause code 34 ("No circuit/channel is available") to SIP response code 486 ("Busy here"). Based on a response code of 486, the outbound routing logic of Lync Server will not attempt to find a new gateway in order to complete the call. 
  
For Lync Server, however, that SIP response code of 486 should instead be mapped to SIP response code 503. A response code of 503 triggers the retry mechanism in the outbound routing logic of Lync Server; that means that the system will try to find another gateway in order to complete the call. To handle this situation, you can create a translation rule that maps the combination of ISUP cause code 34 and SIP response code 486 to a SIP response code of 503.
  
The **Get-CsSipResponseCodeTranslationRule** cmdlet enables you to retrieve information about all the translation rules configured for use in your organization. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsSipResponseCodeTranslationRule** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsSipResponseCodeTranslationRule"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the translation rule (or rules) to be returned. For example, this syntax returns all the translation rules that have the string value "404" in their Identity:  <br/> -Filter "\*404\*"  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the translation rule. The identity for a translation rule consists of two parts: the scope where the rule was configured, and the name given to the rule when it was created. For example, a translation rule named Rule404 that was created at the global scope would have an Identity that looked like this: global/Rule404.  <br/> In addition to the global scope, translation rules can also be created at the site scope or the service scope (albeit for the PstnGateway service only).  <br/> To return all the translation rules created for a particular site or service, you can simply specify the site or service Identity. For example:  <br/> -Identity "site:Redmond"  <br/> If this parameter is omitted, the **Get-CsSipResponseCodeTranslationRule** cmdlet returns a collection of all your SIP response code translation rules.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the SIP response code translation rule data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsSipResponseCodeTranslationRule** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsSipResponseCodeTranslationRule** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.SipResponseCodeTRanslationRule#Decorated object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsSipResponseCodeTranslationRule](new-cssipresponsecodetranslationrule.md)
  
[Remove-CsSipResponseCodeTranslationRule](remove-cssipresponsecodetranslationrule.md)
  
[Set-CsSipResponseCodeTranslationRule](set-cssipresponsecodetranslationrule.md)

