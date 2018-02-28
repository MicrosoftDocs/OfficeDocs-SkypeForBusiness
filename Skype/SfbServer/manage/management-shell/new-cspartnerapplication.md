---
title: "New-CsPartnerApplication"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0248acde-626d-42b4-a071-c96171364a18
description: "Creates a new partner application. A partner application is any application that Skype for Business Server 2015 can directly exchange security tokens with, without having to go through a third-party security token server. This cmdlet was introduced in Lync Server 2013."
---

# New-CsPartnerApplication
[]
Creates a new partner application. A partner application is any application that Skype for Business Server 2015 can directly exchange security tokens with, without having to go through a third-party security token server. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsPartnerApplication -ApplicationIdentifier <String> -ApplicationTrustLevel <User | Application | Full> -UseOAuthServer <SwitchParameter> [-AcceptSecurityIdentifierInformation <$true | $false>] [-Enabled <$true | $false>] [-Identity <XdsGlobalRelativeIdentity>] [-Realm <String>] [-Tenant <Guid>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new partner application with the Identity "MicrosoftExchange". In this example, the new partner application uses the metadata URL https://autodiscover.litwareinc.com/metadata/json/1.
  
```
New-CsPartnerApplication -Identity "MicrosoftExchange" -ApplicationTrustLevel "Full" -MetadataUrl"https://autodiscover.litwareinc.com/metadata/json/1"
```

### Example 2

The command shown in Example 2 also creates a new partner application with the Identity "MicrosoftExchange". In this case, however, the new partner application does not use a metadata URL but, instead, is configured to use a predefined OAuth Server. To do this, the command uses the UseOAuthServer parameter instead of the MetadataUrl parameter.
  
```
New-CsPartnerApplication -Identity "MicrosoftExchange" -ApplicationIdentifier "microsoft.exchange" -ApplicationTrustLevel "Full" -UseOAuthServer
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, server-to-server authentication (for example, the authentication that enables Skype for Business Server 2015 and Exchange to share information) is carried out by using the OAuth security protocol. This type of authentication typically requires three servers: the two servers that need to communicate with one another (Server A and B) and a third-party security token server. If Servers A and B need to communicate with one another, the two servers contact the token server (also known as an OAuth server) and obtain mutually-trusted security tokens that the two servers can exchange in order to prove their identities.
  
If you are using an on-premises version of Skype for Business Server 2015 and you need to communicate with another server product that fully supports the OAuth protocol (for example, Exchange or SharePoint) then you typically do not need to use a token server; that's because these server products are able to issue their own security tokens. However, you will need to configure the other server product (e.g., Exchange) as a partner application. (You will also need to configure Skype for Business Server 2015 as a partner application for the other server product.) In Skype for Business Server 2015, partner applications are managed by using the **CsPartnerApplication** cmdlets.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **New-CsPartnerApplication** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ApplicationIdentifier_ <br/> |Required  <br/> |String  <br/> |Unique identifier for the partner application. The ApplicationIdentifier is provided by the server application. You cannot use the ApplicationIdentifier parameter and the MetadataUrl parameter in the same command.  <br/> |
| _ApplicationTrustLevel_ <br/> |Required  <br/> |ApplicationTrustLevel  <br/> |Specifies the level of trust between Skype for Business Server 2015 and the partner application. Allowed values are:  <br/> \* Full -- The partner application is trusted to represent itself and to impersonate any user in the realm. This is the default value.  <br/> \* Application -- The partner application is trusted to represent itself within the realm. In order to impersonate a user, it must obtain consent through from a security token server.  <br/> \* User -- The partner application must obtain consent from a security token server in order to represent a user, and cannot represent itself.  <br/> The default value is Full.  <br/> |
| _CertificateFileData_ <br/> |Required  <br/> |String  <br/> |Path to a certificate file that can be assigned to the partner application. For example:  <br/>  `-CertificateFileData "C:\Certificates\PartnerApplication.cer"` <br/> |
| _CertificateRawData_ <br/> |Required  <br/> |String  <br/> |Certificate (in Base64 encoded format) that can be assigned to the partner application. To read raw data from a certificate and then convert that data to the required format, use commands similar to these:  <br/>  `$x = Get-Content "C:\Certificates\PartnerApplication.cer" -Encoding Byte` <br/>  `$y = [Convert]::ToBase64String($x)` <br/> You can then use this syntax to assign the certificate data stored in the variable $y:  <br/>  `-CertificateRawData $y` <br/> |
| _MetadataUrl_ <br/> |Required  <br/> |String  <br/> |URL where the WS-FederationMetadata for the partner application is published. Partner applications use the metadata to agree on the types of tokens that will be exchanged as well the keys that will be used to sign these tokens.  <br/> |
| _UseOAuthServer_ <br/> |Required  <br/> |SwitchParameter  <br/> |When present, indicates that the partner application will use one of the pre-authorized OAuth servers instead of a security token server built into the application itself.  <br/> |
| _AcceptSecurityIdentifierInformation_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True ($True), security identifiers (SIDs) can be used for authentication purposes. The default value is False.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True the partner application will be enabled and available for immediate use. The default value is True.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsGlobalRelativeIdentity  <br/> |Unique identifier for the new partner application.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _Realm_ <br/> |Optional  <br/> |String  <br/> |Server-to-server security container. By default, Skype for Business Server 2015 uses your default SIP domain as its OAuth realm.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which the new partner application is being created. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsPartnerApplication** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsPartnerApplication** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.PartnerApplication#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPartnerApplication](get-cspartnerapplication.md)
  
[Remove-CsPartnerApplication](remove-cspartnerapplication.md)
  
[Set-CsPartnerApplication](set-cspartnerapplication.md)

