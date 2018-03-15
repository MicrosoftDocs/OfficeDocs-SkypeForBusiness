---
title: "Set-CsOAuthServer"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 52825ca3-d287-4e09-9aec-b8b2d7bafc06
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsOAuthServer
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Modifies an existing Open Authorization (OAuth) server. OAuth servers, also known as security token servers, issue security tokens used in server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsOAuthServer <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 updates the metadata URL for the OAuth Server Office 365.
  
```
Set-CsOAuthServer -Identity "Office 365" -MetadataUrl "https://sts.office365.microsoft.com/metadata/json/1"
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Lync Server 2013, server-to-server authentication (for example, the authentication that enables Lync Server 2013 and Microsoft Exchange Server 2013 to share information) is carried out using the OAuth security protocol. This type of authentication typically requires three servers: the two servers that need to communicate with one another (Server A and B) and a third-party security token server. If Servers A and B need to communicate with one another, the two servers contact the token server (also known as an OAuth server) and obtain mutually-trusted security tokens that the two servers can exchange in order to prove their identities.
  
If you are using an on-premises version of Lync Server 2013 and you need to communicate with another server product that fully supports the OAuth protocol (for example, Exchange 2013 or Microsoft SharePoint 2013) then you typically do not need to use a token server; that's because these server products are able to issue their own security tokens. However, if you need to communicate with another server product (including server products found on Office 365) then you will need to use a token servers. These token servers can be managed by using the CsOAuthServer cmdlets.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsOAuthServer"}
  
 **Lync Server Control Panel:** The functions carried out by the **Set-CsOAuthServer** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Friendly (and unique) name used to identify the OAuth server.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _MetadataUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL where the WS-FederationMetadata for the server is published. Servers use the metadata to agree on the types of tokens that will be exchanged as well the keys that will be used to sign these tokens.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the OAuth server being modified. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsOAuthServer** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthServer#Decorated object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsOAuthServer** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthServer#Decorated object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsOAuthServer](get-csoauthserver.md)
  
[New-CsOAuthServer](new-csoauthserver.md)
  
[Remove-CsOAuthServer](remove-csoauthserver.md)

