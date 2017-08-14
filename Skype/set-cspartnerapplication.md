---
title: Set-CsPartnerApplication
ms.prod: SKYPEFORBUSINESS
ms.assetid: 29c8c511-157b-478e-814f-b911955a8251
---


# Set-CsPartnerApplication
[]
Modifies an existing partner application. A partner application is any application that Skype for Business Server 2015 can directly exchange security tokens with, without having to go through a third-party security token server. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Set-CsPartnerApplication -Identity <XdsGlobalRelativeIdentity> [-AcceptSecurityIdentifierInformation <$true | $false>] [-ApplicationTrustLevel <User | Application | Full>] [-Enabled <$true | $false>] [-Tenant <Guid>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 disables the partner application MicrosoftExchange. This is done by setting the Enabled property to False ($False).
  
    
    

```

Set-CsPartnerApplication -Identity "MicrosoftExchange" -Enabled $False
```


### Example 2

In Example 2, all the partner applications currently in use in the organization are disabled. To do this, the command first uses the **Get-CsPartnerApplication** cmdlet to return a collection of all the partner applications. This collection is then piped to the **ForEach-Object** cmdlet. In turn, the **ForEach-Object** cmdlet runs the **Set-CsPartnerApplication** cmdlet against each application in the collection. Doing so disables each of those partner applications.
  
    
    

```
Get-CsPartnerApplication | ForEach-Object {Set-CsPartnerApplication -Identity $_.Identity -Enabled $False}
```


### Example 3

Example 3 disables all partner applications where the ApplicationTrustLevel property is set to User. To carry out this task, the command first calls the **Get-CsPartnerApplication** cmdlet without any parameters; that returns a collection of all the partner applications configured for use in the organization. This collection is then piped to the Where-Object cmdlet, which picks out only those applications where the ApplicationTrustLevel property is equal to "User". That filtered collection is then piped to the **ForEach-Object** cmdlet, which uses the **Set-CsPartnerApplication** cmdlet to take each item in the collection and set the Enabled property to $False.
  
    
    

```
Get-CsPartnerApplication | Where-Object {$_.ApplicationTrustLevel -eq "User"} | ForEach-Object {Set-CsPartnerApplication -Identity $_.Identity -Enabled $False}
```


## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, server-to-server authentication (for example, the authentication that enables Skype for Business Server 2015 and Exchange to share information) is carried out using the OAuth security protocol. This type of authentication typically requires three servers: the two servers that need to communicate with one another (Server A and B) and a third-party security token server. If Servers A and B need to communicate with one another, the two servers contact the token server (also known as an OAuth server) and obtain mutually-trusted security tokens that the two servers can exchange in order to prove their identities.
  
    
    
If you are using an on-premises version of Skype for Business Server 2015 and you need to communicate with another server product that fully supports the OAuth protocol (for example, Exchange or SharePoint) then you typically do not need to use a token server; that's because these server products are able to issue their own security tokens. However, you will need to configure the other server product (e.g., Exchange) as a partner application. (You will also need to configure Skype for Business Server 2015 as a partner application for the other server product.) In Skype for Business Server 2015, partner applications are managed by using the **CsPartnerApplication** cmdlets.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Set-CsPartnerApplication** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CertificateFileData_ <br/> |Required  <br/> |String  <br/> |Path to a certificate file that can be assigned to the partner application. For example:  <br/>  `-CertificateFileData "C:\\Certificates\\PartnerApplication.cer"` <br/> |
| _CertificateRawData_ <br/> |Required  <br/> |String  <br/> |Certificate (in Base64 encoded format) that can be assigned to the partner application. To read raw data from a certificate and then convert that data to the required format, use commands similar to these:  <br/>  `$x = Get-Content "C:\\Certificates\\PartnerApplication.cer" -Encoding Byte` <br/>  `$y = [Convert]::ToBase64String($x)` <br/> You can then use this syntax to assign the certificate data stored in the variable $y:  <br/>  `-CertificateRawData $y` <br/> |
| _Identity_ <br/> |Required  <br/> |XdsGlobalRelativeIdentity  <br/> |Unique identifier of the partner application. For example:  <br/>  `-Identity "MicrosoftExchange"` <br/> |
| _MetadataUrl_ <br/> |Required  <br/> |String  <br/> |URL of the security token servicer federation metadata that carries the signing keys, the issuer identifier, and the issuer endpoint URL.  <br/> |
| _UseOAuthServer_ <br/> |Required  <br/> |SwitchParameter  <br/> |When present, the partner application will use the configured OAuth Server for server-to-server authentication. When not present, the partner application will use its built-in security token service for server-to-server authentication.  <br/> |
| _AcceptSecurityIdentifierInformation_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True ($True), security identifiers (SIDs) can be used for authentication purposes. The default value is False.  <br/> |
| _ApplicationTrustLevel_ <br/> |Optional  <br/> |ApplicationTrustLevel  <br/> |Specifies the level of trust between Skype for Business Server 2015 and the partner application. Allowed values are:  <br/> * Full -- The partner application is trusted to represent itself and to impersonate any user in the realm. This is the default value.  <br/> * Application -- The partner application is trusted to represent itself within the realm. In order to impersonate a user, it must obtain consent through from a security token server.  <br/> * User -- The partner application must obtain consent from a security token server in order to represent a user, and cannot represent itself.  <br/> The default value is Full.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, the partner application is available for use with Skype for Business Server 2015. When set to False the partner application will continue to run, but will not be able to communicate with Skype for Business Server 2015 until the Enabled property has been set to True.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Instance_ <br/> |Optional  <br/> |PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the partner application being modified. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Set-CsPartnerApplication** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsPartnerApplication** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.PartnerApplication#Decorated object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsPartnerApplication](get-cspartnerapplication.md)
  
    
    
 [New-CsPartnerApplication](new-cspartnerapplication.md)
  
    
    
 [Remove-CsPartnerApplication](remove-cspartnerapplication.md)
