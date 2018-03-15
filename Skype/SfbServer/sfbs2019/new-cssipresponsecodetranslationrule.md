---
title: "New-CsSipResponseCodeTranslationRule"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f7667ffd-3d11-40ec-87d4-7f9b1a861aae
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsSipResponseCodeTranslationRule
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new SIP response code translation rule. These rules enable administrators to map SIP response codes with values between 400 and 699 to the values used by Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsSipResponseCodeTranslationRule -Name <String> -Parent <String> <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 creates a new SIP response code translation rule with the Identity PstnGateway:192.168.0.240/Rule404. This rule translates a received response code of 434 to the standard SIP response code 404 (Not Found).
  
```
New-CsSipResponseCodeTranslationRule -Identity "PstnGateway:192.168.0.240/Rule404" -ReceivedResponseCode 434 -TranslatedResponseCode 404
```

### EXAMPLE 2

The command shown in Example 2 performs the same task as the command shown in Example 1. In Example 2, however, the Parent and Name parameters are used instead of the Identity parameter. This simply shows an alternate way of creating a new SIP response code translation rule that has the Identity PstnGateway:192.168.0.240/Rule404.
  
```
New-CsSipResponseCodeTranslationRule -Parent "PstnGateway:192.168.0.240" -Name "Rule404" -ReceivedResponseCode 434 -TranslatedResponseCode 404
```

## Detailed Description
<a name="sectionSection1"> </a>

SIP trunking provides a way to connect a Voice over Internet Protocol (VoIP) network (such as Enterprise Voice) with the public switched telephone network (PSTN). In Lync Server, the Mediation Server uses trunking peers to interact with the PSTN network. When an outgoing call fails on the PSTN network, an ISDN User Part (ISUP) cause code is automatically generated. For example, a PSTN gateway might send cause code 34 to indicate that no circuit or channel was available for completing the call. When a Mediation Server trunking peer receives that ISUP cause code, it converts that code to a SIP response code, which is then sent to the Mediation Server itself. In turn, Lync Server uses these response codes to make its outbound routing decisions. For example, a malfunctioning gateway might automatically be assigned a "less-preferred" status; this minimizes the use of the malfunctioning gateway, and thus maximizes the chance of a call being successfully completed.
  
However, not all gateways use the recommended ISUP cause code to SIP response code mapping used by Lync Server. For these gateways, administrators can use the **CsSipResponseCodeTranslationRule** cmdlets to map the gateway SIP response code (in combination with the ISUP cause code, if that cause code is available) to a SIP response code used by Lync Server. For example, a gateway might map ISUP cause code 34 ("No circuit/channel is available") to SIP response code 486 ("Busy here"). Based on a response code of 486, the outbound routing logic of Lync Server will not attempt to find a new gateway in order to complete the call. 
  
For Lync Server, however, that SIP response code of 486 should instead be mapped to SIP response code 503. A response code of 503 triggers the retry mechanism in the outbound routing logic of Lync Server; that means that the system will try to find another gateway in order to complete the call. To handle this situation, you can create a translation rule that maps the combination of ISUP cause code 34 and SIP response code 486 to a SIP response code of 503. These new translation rules are created by using the **New-CsSipResponseCodeTranslationRule** cmdlet. Translation rules can be assigned to the global scope, the site scope, or to the service scope (for the PSTN Gateway service only). 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsSipResponseCodeTranslationRule** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsSipResponseCodeTranslationRule"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the translation rule to be created. The identity for a translation rule consists of two parts: the scope where the rule is to be assigned and the name to be given to the rule. For example, a translation rule named Rule404 to be created at the global scope would have an Identity that looks like this: global/Rule404.  <br/> Instead of using the Identity parameter, you can use the Parent and Name parameters when creating a new translation rule.  <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |Name used to differentiate one translation rule from another. Names must be unique within a given scope; for example, the Redmond site can only have one translation rule named Rule404. However, you can have a translation rule named Rule404 at the Redmond site and another rule named Rule404 at the Dublin site.  <br/> The Name parameter must always be used in conjunction with the Parent parameter.  <br/> |
| _Parent_ <br/> |Required  <br/> |System.String  <br/> |Scope where the new translation rule is to be assigned. To assign a rule to the global scope, use this syntax: -Parent global. To assign a rule to the site scope, use syntax like this: -Parent site:Redmond. To assign a rule to the service scope, use syntax similar to this: -Parent PstnGateway:192.168.0.242.  <br/> The Parent parameter must always be used in conjunction with the Name parameter.  <br/> |
| _TranslatedResponseCode_ <br/> |Required  <br/> |System.Int32  <br/> |Value of the Lync Server SIP response code that the ReceivedResponseCode and/or the ReceivedISUPCauseCode should be translated to. Translated response codes can be any integer value between 400 and 699, inclusive.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _Priority_ <br/> |Optional  <br/> |System.Int32  <br/> |Relative priority of the translation rule. Rules are processed in order of their assigned priority; the first rule to be processed has a priority of 0; the second rule to be processed has a priority of 1; and so on. If not specified the new rule will be given the lowest priority in its scope.  <br/> |
| _ReceivedISUPCauseValue_ <br/> |Optional  <br/> |System.Int32  <br/> |Value of the ISDN User Part (ISUP) code that must be present in the SIP response message used by a gateway when responding to an INVITE message. A value of -1 indicates that only the SIP response code will be used when executing the translation rule; the ISUP cause code will be ignored.  <br/> |
| _ReceivedResponseCode_ <br/> |Optional  <br/> |System.Int32  <br/> |Value of the SIP response code used by a gateway when responding to an INVITE message. A response code can be any integer value between 400 and 699, inclusive. Although the cmdlet will accept integer values less than 400, these are not recognized as final responses. As a result, the translation rule will never be used. A value of 0 means that only the ISUP cause code will be used when executing the translation rule; the SIP response code will be ignored.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **New-CsSipResponseCodeTranslationRule** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **New-CsSipResponseCodeTranslationRule** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.SipResponseCodeTRanslationRule#Decorated object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsSipResponseCodeTranslationRule](get-cssipresponsecodetranslationrule.md)
  
[Remove-CsSipResponseCodeTranslationRule](remove-cssipresponsecodetranslationrule.md)
  
[Set-CsSipResponseCodeTranslationRule](set-cssipresponsecodetranslationrule.md)

