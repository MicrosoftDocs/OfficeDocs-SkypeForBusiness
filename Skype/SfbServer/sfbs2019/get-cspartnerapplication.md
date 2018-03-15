---
title: "Get-CsPartnerApplication"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a20738b5-d9e7-4da4-bcac-e967f73c4bdc
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsPartnerApplication
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Returns information about all the partner applications configured for use in the organization. A partner application is any application that Lync Server 2013 can directly exchange security tokens with, without having to exchange those tokens by using a third-party security token server. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsPartnerApplication [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about all the partner applications configured for use in the organization
  
```
Get-CsPartnerApplication
```

### Example 2

Example 2 returns information for the partner application that has the Identity MicrosoftExchange. 
  
```
Get-CsPartnerApplication -Identity "MicrosoftExchange"
```

### Example 3

In Example 3, information is returned for all the partner applications that have an application identifier equal to "microsoft.exchange." In order to do this, the command first calls the **Get-CsPartnerApplication** cmdlet without any parameters; that returns a collection of all the configured partner applications. That collection is then piped to the Where-Object cmdlet, which picks out only those partner applications where the ApplicationIdentifier property is equal to "microsoft.exchange." 
  
```
Get-CsPartnerApplication | Where-Object {$_.ApplicationIdentifier -eq "microsoft.exchange"}
```

### Example 4

In Example 4, information is returned for all the partner applications that are currently disabled. To do this, the command first calls the **Get-CsPartnerApplication** cmdlet in order to return a collection of all the partner applications, both enabled and disabled. That collection is then piped to the **Where-Object** cmdlet, which selects only those applications where the Enabled property is equal to False. 
  
```
Get-CsPartnerApplication | Where-Object {$_.Enabled -eq $False}
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Lync Server 2013, server-to-server authentication (for example, the authentication that enables Lync Server 2013 and Exchange 2013 to share information) is carried out using the OAuth security protocol. This type of authentication typically requires three servers: the two servers that need to communicate with one another (Server A and B) and a third-party security token server. If Servers A and B need to communicate with one another, the two servers contact the token server (also known as an OAuth server) and obtain mutually-trusted security tokens that the two servers can exchange in order to prove their identities.
  
If you are using an on-premises version of Lync Server 2013 and you need to communicate with another server product that fully supports the OAuth protocol (for example, Exchange 2013 or Microsoft SharePoint 2013) then you typically do not need to use a token server; that's because these server products are able to issue their own security tokens. However, you will need to configure the other server product (e.g., Exchange 2013) as a partner application. (You will also need to configure Lync Server 2013 as a partner application for the other server product.) In Lync Server 2013, partner applications are managed by using the **CsPartnerApplication** cmdlets. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsPartnerApplication"}
  
 **Lync Server Control Panel:** The functions carried out by the **Get-CsPartnerApplication** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard values to return one or more partner applications. For example, to return all the partner applications that have an Identity that includes the string value "Microsoft" use this syntax:  <br/> -Filter "\*Microsoft\*"  <br/>  You cannot use both the Filter parameter and the Identity parameter in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the partner application. For example:  <br/> -Identity "MicrosoftExchange"  <br/> If neither the identity parameter nor the Filter parameter are included in the command then the **Get-CsPartnerApplication** cmdlet will return information for all your partner applications.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the partner application data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account where whose partner application settings are to be retrieved.  <br/> For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsPartnerApplication** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsPartnerApplication** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.PartnerApplication#Decorated object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsPartnerApplication](new-cspartnerapplication.md)
  
[Remove-CsPartnerApplication](remove-cspartnerapplication.md)
  
[Set-CsPartnerApplication](set-cspartnerapplication.md)

