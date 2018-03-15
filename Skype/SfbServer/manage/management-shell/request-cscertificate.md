---
title: "Request-CsCertificate"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 24e8ba6f-6023-4c03-a594-5b40784fd16a
description: "Provides a way to request certificates for use with servers running Skype for Business Server 2015 and server roles. Also provides a way to check the status of existing certificate requests and, if needed, to cancel any (or all) of those requests. This cmdlet was introduced in Lync Server 2010."
---

# Request-CsCertificate
 
Provides a way to request certificates for use with servers running Skype for Business Server 2015 and server roles. Also provides a way to check the status of existing certificate requests and, if needed, to cancel any (or all) of those requests. This cmdlet was introduced in Lync Server 2010.
  
```
Request-CsCertificate -New <SwitchParameter> -Type <CertType > [-AllSipDomain <SwitchParameter>] [-CA <String>] [-CaAccount <String>] [-CaPassword <String>] [-City <String>] [-ClientEKU <$true | $false>] [-ComputerFqdn <Fqdn>] [-Country <String>] [-DomainName <String>] [-FriendlyName <String>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-KeyAlg <RSA | ECDH_P256 | ECDH_P384 | ECDH_P521>] [-KeySize <Int32>] [-Organization <String>] [-OU <String>] [-Output <String>] [-PrivateKeyExportable <$true | $false>] [-State <String>] [-Template <String>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 creates a new certificate request: it contacts the CA atl-ca-001.litwareinc.com\myca and requests a new WebServicesExternal certificate.
  
```
Request-CsCertificate -New -Type WebServicesExternal -CA "atl-ca-001.litwareinc.com\myca"
```

### EXAMPLE 2

Example 2 lists all the pending certificate requests made by using the **Request-CsCertificate** cmdlet.
  
```
Request-CsCertificate -List
```

### EXAMPLE 3

Example 3 uses the Output parameter to create an offline certificate request.
  
```
Request-CsCertificate -New -Type WebServicesExternal -Output C:\Certificates\WebServicesExternal.cer
```

### EXAMPLE 4

Example 4 is a more detailed (and more realistic) example of how to use the Request-CsCertificate cmdlet. This example requests a certificate for use with the Standard Edition of Skype for Business Server 2015.
  
```
Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -ComputerFqdn "atl-cs-001.litwareinc.com" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Standard Edition Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-cs-001.litwareinc.com,atl-ext.litwareinc.com"
```

### EXAMPLE 5

In Example 5, a pool certificate is requested for use with the Enterprise Edition of Skype for Business Server 2015.
  
```
Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -ComputerFqdn "atl-cs-001.litwareinc.com" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Enterprise Edition Pool Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "pool1.litwareinc.com,pool1int.litwareinc.com,pool1ext.litwareinc.com"
```

### EXAMPLE 6

Example 6 shows how you can request a certificate for the internal Edge Server.
  
```
Request-CsCertificate -New -Type Internal -ComputerFqdn "atl-edge-001" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Internal Edge Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-edge-001.litwareinc.com, ap.litwareinc.com"
```

### EXAMPLE 7

Example 7 is a variation of the command shown in Example 6, In this case, however, the request is for the external Edge Server.
  
```
Request-CsCertificate -New -Type AccessEdgeExternal,DataEdgeExternal,AudioVideoAuthentication -ComputerFqdn "atl-edge-001" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "External Edge Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-edge-001.litwareinc.com,ap.litwareinc.com,dp.litwareinc.com,atl-edge-001"
```

## Detailed Description

Skype for Business Server 2015 uses certificates as a way for servers and server roles to verify their identities; for example, an Edge Server uses certificates to verify that the computer it is communicating with really is a Front End Server and vice versa. In order to fully implement Skype for Business Server 2015, you will need to have the appropriate certificates assigned to the appropriate server roles.
  
One way to request certificates for use with Skype for Business Server 2015 is to call the **Request-CsCertificate** cmdlet. Although it is possible to use other standard Windows tools in order to request certificates for use with Skype for Business Server 2015, one major advantage to using the **Request-CsCertificate** cmdlet is the fact that the cmdlet will analyze your topology before contacting the certification authority (CA). Based on that analysis, the **Request-CsCertificate** cmdlet will automatically request a certificate with the proper subject name and subject alternative name fields.
  
The **Request-CsCertificate** cmdlet is designed to request certificates specifically for use with Skype for Business Server 2015. It is not designed to be an all-purpose certificate management tool.
  
In addition to requesting new certificates, this cmdlet can also be used to review any pending certificate requests, provided those requests were made using the **Request-CsCertificate** cmdlet. The **Request-CsCertificate** cmdlet can also be used to delete pending certificate requests, as long as those requests were made using the cmdlet.
  
When attempting to retrieve certificate requests you might receive an error message if you have any revoked requests; currently the **Request-CsCertificate** cmdlet only supports these request types: Issued, Denied, and Pending. If you encounter problems due to a revoked certificate use a command similar to this to clear the revoked request (where 224 is the RequestID of the revoked certificate request):
  
```
Request-CsCertificate -Clear -RequestID 224

```

After that you should be able to retrieve certificate requests.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Clear_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, deletes any pending certificate requests made by using the **Request-CsCertificate** cmdlet. <br/> |
| _List_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, lists any pending certificate requests made by using the **Request-CsCertificate** cmdlet. <br/> |
| _New_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, indicates that you want to request a new certificate.  <br/> |
| _Retrieve_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, retrieves any pending certificate requests made by using the **Request-CsCertificate** cmdlet and attempts to complete the operation and import the requested certificate. <br/> |
| _Type_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.CertType   <br/> |Type of certificate being requested. Certificate types include (but are not limited to):  <br/> AccessEdgeExternal  <br/> AudioVideoAuthentication  <br/> DataEdgeExternal  <br/> Default  <br/> External  <br/> Internal  <br/> iPhoneAPNService  <br/> iPadAPNService  <br/> MPNService  <br/> PICWebService (Skype for Business Online only)  <br/> ProvisionService (Skype for Business Online only)  <br/> WebServicesExternal  <br/> WebServicesInternal  <br/> WsFedTokenTransfer  <br/> For example, this syntax requests a new Default certificate:  `-Type Default`.  <br/> You can specify multiple types in a single command by separating the certificate types with commas:  <br/>  `-Type Internal,External,Default` <br/> |
| _AllSipDomain_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, all your SIP domains are automatically added to the certificates Subject Alternative Name field. If not present, only the primary SIP domain is added by default. However, additional domains can be specified by using the DomainName parameter.  <br/> |
| _CA_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) that points to the CA. For example:  `-CA "atl-ca-001.litwareinc.com\myca"`. To obtain a list of known CAs, type the following at the Windows PowerShell prompt, and then press ENTER:  <br/>  `certutil` <br/> The Config property returned by Certutil indicates the location of a CA.  <br/> |
| _CaAccount_ <br/> |Optional  <br/> |System.String  <br/> |Account name of the user requesting the new certificate, using the format domain_name\user_name. For example:  `-CaAccount "litwareinc\kenmyer"`. If not specified, the **Request-CsCertificate** cmdlet will use the credentials of the logged-on user when requesting the new certificate. <br/> |
| _CaPassword_ <br/> |Optional  <br/> |System.String  <br/> |Password for the user requesting the new certificate (as specified using the CaAccount parameter).  <br/> |
| _City_ <br/> |Optional  <br/> |System.String  <br/> |City where the certificate will be deployed.  <br/> |
| _ClientEKU_ <br/> |Optional  <br/> |System.Boolean  <br/> |Set this parameter to True if the certificate is to be used for client authentication. This type of authentication is required if you want your users to be able to exchange instant messages with people who have accounts with AOL. The EKU portion of the parameter name is short for extended key usage; the extended key usage field lists the valid uses for the certificate.  <br/> |
| _ComputerFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of the computer for which the certificate is being requested. When present, this parameter forces the **Request-CsCertificate** cmdlet to connect to the Central Management store in order to locate the specified computer. You should always use the computer name when requesting a certificate, even when requesting a pool certificate. The **Request-CsCertificate** cmdlet will automatically add the pool name to the Subject Name of any certificate obtained using this cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Country_ <br/> |Optional  <br/> |System.String  <br/> |Country/region where the certificate will be deployed.  <br/> |
| _DomainName_ <br/> |Optional  <br/> |System.String  <br/> |Comma-separated list of fully-qualified domain names that should be added to the certificate's Subject Alternative Name field. For example:  <br/>  `-DomainName "atl-cs-001.litwareinc.com, atl-cs-002.litwareinc.com,atl-cs-003.litwareinc.com"` <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _FriendlyName_ <br/> |Optional  <br/> |System.String  <br/> |User-assigned name that makes it easier to identify the certificate.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a global catalog server in your domain. This parameter is not required if you are running the **Request-CsCertificate** cmdlet on a computer with an account in your domain. <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services then this parameter must point to the root domain controller. If global settings are stored in the Configuration container then any domain controller can be used and this parameter can be omitted.  <br/> |
| _KeyAlg_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deployment.X509Certificates.KeyAlgorithmIdentifier  <br/> |Indicates the type of cryptographic algorithm to be used in generating the public and private keys for the new certificate. Valid key algorithms include:  <br/> RSA  <br/> ECDH_P256  <br/> ECDH_P384  <br/> ECDH_P521  <br/> |
| _KeySize_ <br/> |Optional  <br/> |System.Int32  <br/> |Indicates the size (in bits) of the private key used by the certificate. Larger key sizes are more secure, but require more processing overhead in order to be decrypted.  <br/>  Valid key sizes are 1024; 2048; and 4096. For example: `-KeySize 2048`.  <br/> |
| _Organization_ <br/> |Optional  <br/> |System.String  <br/> |Name of the organization requesting the new certificate. For example: -Organization "Litwareinc".  <br/> |
| _OU_ <br/> |Optional  <br/> |System.String  <br/> |Active Directory organizational unit for the computer that will be assigned the new certificate.  <br/> |
| _Output_ <br/> |Optional  <br/> |System.String  <br/> |Path to the certificate file. If you want to create an offline certificate request use the Output parameter and specify a file path for the certificate request; for example:  `-Output C:\Certificates\NewCertificate.pfx`. That will create a certificate request file that can then be emailed to a certification authority for processing.  <br/> |
| _PrivateKeyExportable_ <br/> |Optional  <br/> |System.Boolean  <br/> |Set this parameter to True if you want to make the certificate's private key exportable. When a private key is exportable, the certificate can be copied and used on multiple computers.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\Certificates.html"` <br/> |
| _RequestId_ <br/> |Optional  <br/> |System.Int32  <br/> |Identification number associated with a certificate request. The RequestID parameter provides a way for you to list, retrieve, or clear an individual certificate.  <br/> |
| _State_ <br/> |Optional  <br/> |System.String  <br/> |State where the certificate will be deployed. For example:  `-State WA`.  <br/> |
| _Template_ <br/> |Optional  <br/> |System.String  <br/> |Indicates the certificate template to be used when generating the new certificate; for example:  `-Template "WebServer"`. The requested template must be installed on the CA. Note that the value entered must be the template name, not the template display name.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

None. The **Request-CsCertificate** cmdlet does not accept pipelined input.
  
## Return Types

None. Instead, the **Request-CsCertificate** cmdlet helps manage instances of the Microsoft.Rtc.Management.Deployment.CertificateReference object.
  
## See also

#### 

[Get-CsCertificate](get-cscertificate.md)
  
[Import-CsCertificate](import-cscertificate.md)
  
[Remove-CsCertificate](remove-cscertificate.md)
  
[Set-CsCertificate](set-cscertificate.md)

