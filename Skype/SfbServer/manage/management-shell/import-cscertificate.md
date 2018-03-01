---
title: "Import-CsCertificate"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 87bdafce-f4b9-4c44-ad8f-86c2deb680a4
description: "Imports a certificate for use with Skype for Business Server 2015. If a certificate is not acquired by using the Request-CsCertificate cmdlet, then that certificate must be imported before it can be assigned to a Skype for Business Server 2015 server role. This cmdlet was introduced in Lync Server 2010."
---

# Import-CsCertificate
 
Imports a certificate for use with Skype for Business Server 2015. If a certificate is not acquired by using the **Request-CsCertificate** cmdlet, then that certificate must be imported before it can be assigned to a Skype for Business Server 2015 server role. This cmdlet was introduced in Lync Server 2010.
  
```
Import-CsCertificate [-PrivateKeyExportable <$true | $false>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 imports the certificate C:\Certificates\WebServer.pfx. After the command completes, the certificate will be available to be assigned to a server role.
  
```
Import-CsCertificate -Path "C:\Certificates\WebServer.pfx" -PrivateKeyExportable $True
```

## Detailed Description

Skype for Business Server 2015 uses certificates as a way for servers and server roles to verify their identities; for example, an Edge Server uses certificates to verify that the computer it is communicating with really is a Front End Server and vice versa. In order to fully implement Skype for Business Server 2015 you will need to have the appropriate certificates assigned to the appropriate server roles.
  
In order for certificates to be assigned to a Skype for Business Server 2015 role those certificates must be made known to Skype for Business Server 2015. The **Request-CsCertificate** cmdlet enables you to make both online and offline requests for new certificates. If an online request is made, the certificate will automatically be downloaded and saved in the local certificate store; equally important, it will be immediately available for use by Skype for Business Server 2015. If an offline request is made, a certificate file will be sent to you. At that point, you can use the **Import-CsCertificate** cmdlet to import the certificate, a process that makes the certificate available for assignment to a Skype for Business Server 2015 server role.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |When set to Global, enables the certificate to function at the global scope. Global certificates will automatically be copied and distributed to the appropriate computers.  <br/> |
| _Path_ <br/> |Required  <br/> |System.String  <br/> |Full path to the certificate file to be imported. For example:  `-Path "C:\Certificates\WebServer.cer"`.  <br/> |
| _Type_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.CertType   <br/> |Type of certificate being requested. Certificate types include, but are not limited to, the following:  <br/> AccessEdgeExternal  <br/> AudioVideoAuthentication  <br/> DataEdgeExternal  <br/> Default  <br/> External  <br/> Internal  <br/> iPadAPNService  <br/> iPhoneAPNService  <br/> LogRetentionService  <br/> MPNService  <br/> OAuthTokenIssuer  <br/> PICWebService  <br/> ProvisionService  <br/> SMPDNSWebService  <br/> TenantAdmin  <br/> UpgradeEngineService  <br/> WebServicesExternal  <br/> WebServicesInternal  <br/> WsFedTokenTransfer  <br/> XMPPServer  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EffectiveDate_ <br/> |Optional  <br/> |System.DateTime  <br/> |Date and time when the certificate can first be used. For example, to configure a certificate for first use at 8:00 AM on July 31, 2012 use this syntax on a server running under the US English Region and Language settings:  <br/>  `-EffectiveTime "7/31/2012 8:00 AM"` <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Password_ <br/> |Optional  <br/> |System.String  <br/> |Password associated with the certificate file.  <br/> |
| _PrivateKeyExportable_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, ensures that the private key portion of the certificate can be read by the Network Service account.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\Certificates.html"` <br/> |
| _Roll_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to update the specified certificate at the date and time specified by the EffectiveDate parameter; this enables you to specify a date and time when the new certificate will become the primary certificate. Note that your command will fail if you specify the Roll parameter without including the EffectiveDate parameter.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

None. The **Import-CsCertificate** cmdlet does not accept pipelined input.
  
## Return Types

None.
  
## See also

#### 

[Get-CsCertificate](get-cscertificate.md)
  
[Remove-CsCertificate](remove-cscertificate.md)
  
[Request-CsCertificate](request-cscertificate.md)
  
[Set-CsCertificate](set-cscertificate.md)

