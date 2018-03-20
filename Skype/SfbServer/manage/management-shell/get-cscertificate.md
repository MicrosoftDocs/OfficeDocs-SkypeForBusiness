---
title: "Get-CsCertificate"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 15b8f019-1d00-4389-9abe-18deb8cbf2ea
description: "Returns information about certificates on the local computers that have been configured for use with Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsCertificate
 
Returns information about certificates on the local computers that have been configured for use with Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsCertificate [-Identity <XdsIdentity>] [-Report <String>] [-Type <CertType >]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns information about the certificates currently assigned to Skype for Business Server 2015 components. This is done by calling the **Get-CsCertificate** cmdlet without any additional parameters.
  
```
Get-CsCertificate
```

### EXAMPLE 2

Example 2 retrieves all the Skype for Business Server 2015 certificates used for internal Web services. To do this, the Type parameter is included, along with the parameter value WebServicesInternal. 
  
```
Get-CsCertificate -Type WebServicesInternal

```

### EXAMPLE 3

Example 3 returns all the Skype for Business Server 2015 certificates that expire before September 1, 2012. To carry out this task, the command first uses the **Get-CsCertificate** cmdlet to return a collection of all the Skype for Business Server 2015 certificates currently in use. This collection is then piped to the **Where-Object** cmdlet, which selects only those certificates that expire before September 1, 2012. The date specified in this example (9/1/2012) uses the U.S. English format for date-time values. Dates should be specified using a format compatible with your Regional and Language Options.
  
```
Get-CsCertificate | Where-Object {$_.NotAfter -lt "9/1/2012"}

```

### EXAMPLE 4

Example 4 returns information about all the Skype for Business Server 2015 certificates issued by the certification authority (CA) MyCa. To do this, the command first calls the **Get-CsCertificate** cmdlet without any parameters in order to return a collection of all the certificates currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out all the certificates where the Issuer property is equal to (-eq) "Cn=MyCa".
  
```
Get-CsCertificate | Where-Object {$_.Issuer -eq "Cn=MyCa"}

```

### EXAMPLE 5

The command shown in Example 5 returns all the Skype for Business Server 2015 certificates where the Subject property has been set to CN=atl-cs-001.litwareinc.com. This is done by using the **Get-CsCertificate** cmdlet to return a collection of all the Skype for Business Server 2015 certificates, then piping that collection to the **Where-Object** cmdlet. In turn, the **Where-Object** cmdlet selects only those certificates where the Subject property is equal to "CN=atl-cs-001.litwareinc.com".
  
```
Get-CsCertificate | Where-Object {$_.Subject -eq "CN=atl-cs-001.litwareinc.com"}
```

## Detailed Description

Skype for Business Server 2015 uses certificates as a way for servers and server roles to verify their identities; for example, an Edge Server uses certificates to verify that the computer it is communicating with really is a Front End Server, and vice versa. In order to fully implement Skype for Business Server 2015 you will need to have the appropriate certificates assigned to the appropriate server roles. 
  
The **Get-CsCertificate** cmdlet provides a way for you to retrieve detailed information about the certificates that have been configured for use with Skype for Business Server 2015. Note that the cmdlet only returns information about Skype for Business Server 2015 certificates. If a certificate has not been configured for use with Skype for Business Server 2015 (by using the **Set-CsCertificate** cmdlet) then that certificate will not be returned when you run the **Get-CsCertificate** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Enables you to retrieve certificates configured at the global scope (global certificates are copied and distributed to the appropriate computers). Use this syntax to return information about the global certificates:  <br/>  `Get-CsCertificate -Identity "global"` <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to record detailed information about the procedures carried out by the **Get-CsCertificate** cmdlet. The parameter value should be the full path to the HTML file that will be generated; for example: `-Report C:\Logs\Certificates.html`. If the specified file already exists, it will automatically be overwritten with the new information.  <br/> |
| _Type_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deployment.CertType   <br/> |Type of certificate being requested. Certificate types include, but are not limited to, the following:  <br/> AccessEdgeExternal  <br/> AudioVideoAuthentication  <br/> DataEdgeExternal  <br/> Default  <br/> External  <br/> Internal  <br/> iPhoneAPNService  <br/> iPadAPNService  <br/> MPNService  <br/> PICWebService (Skype for Business Online only)  <br/> ProvisionService (Skype for Business Online only)  <br/> WebServicesExternal  <br/> WebServicesInternal  <br/> WsFedTokenTransfer  <br/> For example, this syntax returns information about the Default certificate: -Type Default.  <br/> You can specify multiple types in a single command by separating the certificate types with commas:  <br/>  `-Type Internal,External,Default` <br/> |
   
## Input Types

None. The **Get-CsCertificate** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsCertificate** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment.CertificateReference object.
  
## See also

#### 

[Import-CsCertificate](import-cscertificate.md)
  
[Remove-CsCertificate](remove-cscertificate.md)
  
[Request-CsCertificate](request-cscertificate.md)
  
[Set-CsCertificate](set-cscertificate.md)

