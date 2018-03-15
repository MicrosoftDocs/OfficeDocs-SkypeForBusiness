---
title: "Remove-CsOAuthServer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fac7be48-06bb-4572-86a2-b872fe96d199
description: "Removes an existing Open Authorization (OAuth) server. OAuth servers, also known as security token servers, issue security tokens used in server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013."
---

# Remove-CsOAuthServer
 
Removes an existing Open Authorization (OAuth) server. OAuth servers, also known as security token servers, issue security tokens used in server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsOAuthServer -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 deletes a single OAuth server: the server with the identity "Office 365".
  
```
Remove-CsOAuthServer -Identity "Office365"
```

### Example 2

Example 2 deletes all the OAuth servers configured for use in the organization. To carry out this task, the command first calls the **Get-CsOAuthServer** cmdlet without any parameters in order to return all the OAuth servers. These servers are then piped to, and removed by, the **Remove-CsOAuthServer** cmdlet.
  
```
Get-CsOAuthServer | Remove-CsOAuthServer
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, server-to-server authentication (for example, the authentication that enables Skype for Business Server 2015 and Exchange to share information) is carried out using the OAuth security protocol. This type of authentication typically requires three servers: the two servers that need to communicate with one another (Server A and B) and a third-party security token server. If Servers A and B need to communicate with one another, the two servers contact the token server (also known as an OAuth server) and obtain mutually-trusted security tokens that the two servers can exchange in order to prove their identities.
  
If you are using an on-premises version of Skype for Business Server 2015 and you need to communicate with another server product that fully supports the OAuth protocol then you typically do not need to use a token server; that's because these server products are able to issue their own security tokens. However, if you need to communicate with another server product (including server products found on Office 365) then you will need to use a token servers. These token servers can be managed by using the **CsOAuthServer** cmdlets.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Remove-CsOAuthServer** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the OAuth server to be deleted. For example:  <br/>  `-Identity "Office 365"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the OAuth server being deleted. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsOAuthServer** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthServer#Decorated object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsOAuthServer** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthServer#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsOAuthServer](get-csoauthserver.md)
  
[New-CsOAuthServer](new-csoauthserver.md)
  
[Set-CsOAuthServer](set-csoauthserver.md)

