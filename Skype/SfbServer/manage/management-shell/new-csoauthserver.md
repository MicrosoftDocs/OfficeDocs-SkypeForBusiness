---
title: "New-CsOAuthServer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b9d10216-a743-4e62-9cf0-6d5fb55dd64e
description: "Creates a new Open Authorization (OAuth) server for use by the organization. OAuth servers, also known as security token servers, issue security tokens used in server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013."
---

# New-CsOAuthServer
 
Creates a new Open Authorization (OAuth) server for use by the organization. OAuth servers, also known as security token servers, issue security tokens used in server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsOAuthServer -MetadataUrl <String> [-AcceptSecurityIdentifierInformation <$true | $false>] [-AuthorizationUriOverride <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Identity <XdsGlobalRelativeIdentity>] [-InMemory <SwitchParameter>] [-Realm <String>] [-Tenant <Guid>] [-Type <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

Example 1 creates a new OAuth Server named "Office 365". The new server uses the metadata URL https://sts.office365.microsoft.com/metadata/json/1.
  
```
New-CsOAuthServer -Identity "Office 365" -MetadataUrl "https://sts.office365.microsoft.com/metadata/json/1"
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, server-to-server authentication (for example, the authentication that enables Skype for Business Server 2015 and Exchange to share information) is carried out using the OAuth security protocol. This type of authentication typically requires three servers: the two servers that need to communicate with one another (Server A and B) and a third-party security token server. If Servers A and B need to communicate with one another, the two servers contact the token server (also known as an OAuth server) and obtain mutually-trusted security tokens that the two servers can exchange in order to prove their identities.
  
If you are using an on-premises version of Skype for Business Server 2015 and you need to communicate with another server product that fully supports the OAuth then you typically do not need to use a token server; that's because these server products are able to issue their own security tokens. However, if you need to communicate with another server product then you will need to use a token servers. These token servers can be managed by using the **CsOAuthServer** cmdlets.
  
 **Skype for Business Server Control Panel:** The functions carried out by the New-CsOAuthServer cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _MetadataUrl_ <br/> |Required  <br/> |System.String  <br/> |URL where the WS-FederationMetadata for the server is published. Servers use the metadata to agree on the types of tokens that will be exchanged as well the keys that will be used to sign these tokens. Note that the specified URL must be available when you run the **New-CsOAuthServer** cmdlet or else the command will fail. <br/> |
| _AcceptSecurityIdentifierInformation_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _AuthorizationUriOverride_ <br/> |Optional  <br/> |System.String  <br/> |URI used for OAuth authorization override. The override prevents authenticated users from being reprompted for their credentials after they have logged on.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Friendly (and unique) name used to identify the OAuth server.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _Realm_ <br/> |Optional  <br/> |System.String  <br/> |Server-to-server security container. By default, Skype for Business Server 2015 uses your default SIP domain as its OAuth realm.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which the new OAuth server is being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _Type_ <br/> |Optional  <br/> |System.String  <br/> |Type of authentication used by the server. For example, this syntax configures the server to use Active Directory Federation Services authentication:  <br/>  `-Type "ADFS"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsOAuthServer** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsOAuthServer** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthServer#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsOAuthServer](get-csoauthserver.md)
  
[Remove-CsOAuthServer](remove-csoauthserver.md)
  
[Set-CsOAuthServer](set-csoauthserver.md)

