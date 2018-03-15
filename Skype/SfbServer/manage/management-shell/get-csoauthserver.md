---
title: "Get-CsOAuthServer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c2a61eb0-cdff-4069-99e4-2bdf42812f47
description: "Returns information about the Open Authorization (OAuth) servers configured for use by the organization. OAuth servers, also known as security token servers, issue security tokens used in server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsOAuthServer
 
Returns information about the Open Authorization (OAuth) servers configured for use by the organization. OAuth servers, also known as security token servers, issue security tokens used in server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsOAuthServer [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

Example 1 returns information about all the OAuth servers configured for use in the organization.
  
```
Get-CsOAuthServer
```

### Example 2

In Example 2, information is returned for the OAuth server that has the Identity "Office 365".
  
```
Get-CsOAuthServer -Identity "Office 365"
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, server-to-server authentication (for example, the authentication that enables Skype for Business Server 2015 and Exchange to share information) is carried out using the OAuth security protocol. This type of authentication typically requires three servers: the two servers that need to communicate with one another (Server A and B) and a third-party security token server. If Servers A and B need to communicate with one another, the two servers contact the token server (also known as an OAuth server) and obtain mutually-trusted security tokens that the two servers can exchange in order to prove their identities.
  
If you are using an on-premises version of Skype for Business Server 2015 and you need to communicate with another server product that fully supports the OAuth protocol then you typically do not need to use a token server; that's because these server products are able to issue their own security tokens. However, if you need to communicate with another server product then you will need to use a token servers. These token servers can be managed by using the **CsOAuthServer** cmdlets.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsOAuthServer** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return one or more OAuth servers. For example, to return all of the OAuth servers that have an Identity that includes the string value "Microsoft" use this syntax:  <br/>  `-Filter "*Microsoft*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the OAuth server to be returned. For example:  <br/>  `-Identity "Office 365"` <br/> If neither the Identity parameter nor the Filter parameter is included in the command then the **Get-CsOAuthServer** cmdlet will return information about all your OAuth servers. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the OAuth service data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose OAuth server settings are to be retrieved.  <br/> For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsOAuthServer** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsOAuthServer** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthServer#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsOAuthServer](new-csoauthserver.md)
  
[Remove-CsOAuthServer](remove-csoauthserver.md)
  
[Set-CsOAuthServer](set-csoauthserver.md)

