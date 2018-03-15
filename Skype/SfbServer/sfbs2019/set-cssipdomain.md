---
title: "Set-CsSipDomain"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c19aaa3f-04d3-467e-b9d5-d574674eb4a4
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsSipDomain
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Enables you to modify property values for the SIP domains in your organization. SIP domains are domains authorized to send and receive SIP traffic, and are used when assigning SIP addresses to users. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsSipDomain [-Identity <XdsGlobalRelativeIdentity>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-IsDefault <$true | $false>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 makes the SIP domain fabrikam.com the default SIP domain; this is done by using the IsDefault parameter and the parameter value $True. When this command is run, Fabrikam.com will become the default domain, and the domain which previously served as the default will be "demoted." That's because you can have only one default domain.
  
```
Set-CsSipDomain -Identity fabrikam.com -IsDefault $True
```

## Detailed Description
<a name="sectionSection1"> </a>

In order to configure SIP addresses for your users (and thus enable them to use SIP-related software such as Lync 2013), you need two pieces of information: a user ID (for example, Ken.Myer) and a SIP domain (for example, litwareinc.com). The SIP domain used to construct a SIP address must be a domain located within your Active Directory forest that is authorized to send and receive SIP traffic. For example, suppose you have domains named litwareinc.com, fabrikam.com, and contoso.com, but only litwareinc.com has been identified as being a SIP domain. In that case, you cannot use a SIP address like sip:Ken.Myer@fabrikam.com or sip:Ken.Myer@contoso.com, at least not until fabrikam.com and contoso.com have been configured as valid SIP domains. That is something you can do by running the **New-CsSipDomain** cmdlet. 
  
You must always have one SIP domain configured as the default domain. The **Set-CsSipDomain** cmdlet provides a way for you to change your default SIP domain. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsSipDomain** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsSipDomain"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name (FQDN) of the SIP domain to be configured as the default domain. For example: -Identity fabrikam.com.  <br/> |
| _IsDefault_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether the domain is the default SIP domain, the domain used by Lync Server any time a domain name is not explicitly stated. If set to True, the new domain will become the new default domain. You cannot set this value to False because that would leave you without a default SIP domain.  <br/> If you change the default SIP domain you will need to restart the RTCCAA and RTCCAS services.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Set-CsSipDomain** cmdlet does not accept pipelined data. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsSipDomain** cmdlet does not return any objects or values. Instead, the cmdlet is used to modify existing instances of the Microsoft.Rtc.Management.Xds.SipDomain object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsSipDomain](get-cssipdomain.md)
  
[New-CsSipDomain](new-cssipdomain.md)
  
[Remove-CsSipDomain](remove-cssipdomain.md)

