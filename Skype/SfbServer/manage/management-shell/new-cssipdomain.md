---
title: "New-CsSipDomain"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 385f0f23-397b-4d8d-b9b7-ec942cda4a99
description: "Creates a new SIP domain for use in your organization. SIP domains are domains authorized to send and receive SIP traffic, and are used when assigning SIP addresses to users. This cmdlet was introduced in Lync Server 2010."
---

# New-CsSipDomain
[]
Creates a new SIP domain for use in your organization. SIP domains are domains authorized to send and receive SIP traffic, and are used when assigning SIP addresses to users. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsSipDomain -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-IsDefault <$true | $false>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 creates a new SIP domain, one that has the Identity fabrikam.com.
  
```
New-CsSipDomain -Identity fabrikam.com
```

### EXAMPLE 2

Example 2 creates a new SIP domain named fabrikam.com and makes this new domain the default SIP domain. By making fabrikam.com the default domain, this command also "demotes" the domain that previously served as the default SIP domain. That's because you can have only one default SIP domain.
  
```
New-CsSipDomain -Identity fabrikam.com -IsDefault $True
```

## Detailed Description

In order to configure SIP addresses for your users (and thus enable them to use SIP-related software such as Skype for Business), you need two pieces of information: a user ID (for example, Ken.Myer) and a SIP domain (for example, litwareinc.com). The SIP domain used to construct a SIP address must be a domain, located within your Active Directory forest, that is authorized to send and receive SIP traffic. For example, suppose you have domains named litwareinc.com, fabrikam.com, and contoso.com, but only litwareinc.com has been identified as being a SIP domain. In that case, you cannot use a SIP address like sip:Ken.Myer@fabrikam.com or sip:Ken.Myer@contoso.com, at least not until fabrikam.com and contoso.com have been configured as valid SIP domains. That is something you can do by running the **New-CsSipDomain** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Fully qualified domain name (FQDN) for the new SIP domain. For example:  <br/>  `-Identity fabrikam.com` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _IsDefault_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether the domain is the default SIP domain, the domain used by Skype for Business Server 2015 any time a domain name is not explicitly stated. If set to True, the new domain will also become the new default domain  <br/> The default value for IsDefault is False. If you do not want to make the new domain the default domain you can simply leave out the parameter.  <br/> If you change the default SIP domain you will need to restart the RTCCAA and RTCCAS services.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsSipDomain** cmdlet does not accept pipelined data.
  
## Return Types

The **New-CsSipDomain** cmdlet creates new instances of the Microsoft.Rtc.Management.Xds.SipDomain object.
  
## See also

#### 

[Get-CsSipDomain](get-cssipdomain.md)
  
[Remove-CsSipDomain](remove-cssipdomain.md)
  
[Set-CsSipDomain](set-cssipdomain.md)

