---
title: "Get-CsCertificate"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 15b8f019-1d00-4389-9abe-18deb8cbf2ea
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsCertificate
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about certificates on the local computers that have been configured for use with Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsCertificate [-Identity <XdsIdentity>] [-Report <String>] [-Type <CertType[]>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 returns information about the certificates currently assigned to Lync Server components. This is done by calling the **Get-CsCertificate** cmdlet without any additional parameters. 
  
```
Get-CsCertificate
```

### EXAMPLE 2

Example 2 retrieves all the Lync Server certificates used for internal Web services. To do this, the Type parameter is included, along with the parameter value WebServicesInternal. 
  
```
Get-CsCertificate -Type WebServicesInternal

```

### EXAMPLE 3

Example 3 returns all the Lync Server certificates that expire before September 1, 2012. To carry out this task, the command first uses the **Get-CsCertificate** cmdlet to return a collection of all the Lync Server certificates currently in use. This collection is then piped to the **Where-Object** cmdlet, which selects only those certificates that expire before September 1, 2012. The date specified in this example (9/1/2012) uses the U.S. English format for date-time values. Dates should be specified using a format compatible with your Regional and Language Options. 
  
```
Get-CsCertificate | Where-Object {$_.NotAfter -lt "9/1/2012"}

```

### EXAMPLE 4

Example 4 returns information about all the Lync Server certificates issued by the certification authority (CA) MyCa. To do this, the command first calls the **Get-CsCertificate** cmdlet without any parameters in order to return a collection of all the certificates currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out all the certificates where the Issuer property is equal to (-eq) "Cn=MyCa". 
  
```
Get-CsCertificate | Where-Object {$_.Issuer -eq "Cn=MyCa"}

```

### EXAMPLE 5

The command shown in Example 5 returns all the Lync Server certificates where the Subject property has been set to CN=atl-cs-001.litwareinc.com. This is done by using the **Get-CsCertificate** cmdlet to return a collection of all the Lync Server certificates, then piping that collection to the **Where-Object** cmdlet. In turn, the **Where-Object** cmdlet selects only those certificates where the Subject property is equal to "CN=atl-cs-001.litwareinc.com". 
  
```
Get-CsCertificate | Where-Object {$_.Subject -eq "CN=atl-cs-001.litwareinc.com"}
```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Server uses certificates as a way for servers and server roles to verify their identities; for example, an Edge Server uses certificates to verify that the computer it is communicating with really is a Front End Server, and vice versa. In order to fully implement Lync Server you will need to have the appropriate certificates assigned to the appropriate server roles. 
  
The **Get-CsCertificate** cmdlet provides a way for you to retrieve detailed information about the certificates that have been configured for use with Lync Server. Note that the cmdlet only returns information about Lync Server certificates. If a certificate has not been configured for use with Lync Server (by using the **Set-CsCertificate** cmdlet) then that certificate will not be returned when you run the **Get-CsCertificate** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsCertificate** cmdlet locally: RTCUniversalServerAdmins. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Enables you to retrieve certificates configured at the global scope (global certificates are copied and distributed to the appropriate computers). Use this syntax to return information about the global certificates:  <br/> Get-CsCertificate -Identity "global"  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to record detailed information about the procedures carried out by the **Get-CsCertificate** cmdlet. The parameter value should be the full path to the HTML file that will be generated; for example: -Report C:\Logs\Certificates.html. If the specified file already exists, it will automatically be overwritten with the new information.  <br/> |
| _Type_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deployment.CertType[]  <br/> |Type of certificate being requested. Certificate types include, but are not limited to, the following:  <br/> AccessEdgeExternal  <br/> AudioVideoAuthentication  <br/> DataEdgeExternal  <br/> Default  <br/> External  <br/> Internal  <br/> iPhoneAPNService  <br/> iPadAPNService  <br/> MPNService  <br/> PICWebService (Microsoft Lync Online 2010 only)  <br/> ProvisionService (Microsoft Lync Online 2010 only)  <br/> WebServicesExternal  <br/> WebServicesInternal  <br/> WsFedTokenTransfer  <br/> For example, this syntax returns information about the Default certificate: -Type Default.  <br/> You can specify multiple types in a single command by separating the certificate types with commas:  <br/> -Type Internal,External,Default  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Get-CsCertificate** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsCertificate** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment.CertificateReference object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Import-CsCertificate](import-cscertificate.md)
  
[Remove-CsCertificate](remove-cscertificate.md)
  
[Request-CsCertificate](request-cscertificate.md)
  
[Set-CsCertificate](set-cscertificate.md)

