---
title: "Set-CsCertificate"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6da0be05-b257-4258-9d6d-7ddf283f1038
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsCertificate
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Enables you to assign a certificate to a Lync Server server or server role. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsCertificate -Reference <CertificateReference> -Type <CertType[]> [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 assigns the certificate with the Thumbprint B142918E463981A76503828BB1278391B716280987B to the WebServicesExternal role on the local computer.
  
```
Set-CsCertificate -Type WebServicesExternal -Thumbprint "B142918E463981A76503828BB1278391B716280987B"
```

### EXAMPLE 2

Example 2 assigns the assigns the certificate with the Thumbprint B142918E463981A76503828BB1278391B716280987B to three different roles on the local computer: Default, WebServicesInternal, and WebServicesExternal.
  
```
Set-CsCertificate -Type Default, WebServicesInternal, WebServicesExternal -Thumbprint "B142918E463981A76503828BB1278391B716280987B"
```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Server uses certificates as a way for servers and server roles to verify their identities; for example, an Edge Server uses certificates to verify that the computer it is communicating with really is a Front End Server and vice versa. In order to fully implement Lync Server, you will need to have the appropriate certificates assigned to the appropriate server roles.
  
The **Set-CsCertificate** cmdlet enables administrators to assign a certificate to a server or server role. Note that you can only assign certificates that have already been configured for use with Lync Server. To identify certificates available for assignment, use the **Get-CsCertificate** cmdlet. 
  
Who can run this cmdlet: You must be a local administrator in order to run the **Set-CsCertificate** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsCertificate"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |When set to Global, enables the certificate to function at the global scope. Global certificates will automatically be copied and distributed to the appropriate computers.  <br/> |
| _Path_ <br/> |Required  <br/> |System.String  <br/> |Full path to the .PFX certificate file.  <br/> |
| _Reference_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.CertificateReference  <br/> |Object reference to a certificate configured for use with Lync Server. The following command returns an object reference (the variable $x) representing a certificate with the thumbprint B142918E463981A76503828BB1278391B716280987B:  <br/> $x = Get-CsCertificate | Where-Object {$_.Thumbprint -eq "B142918E463981A76503828BB1278391B716280987B".  <br/> |
| _Thumbprint_ <br/> |Required  <br/> |System.String  <br/> |Unique identifier for the certificate. A certificate thumbprint looks similar to this: B142918E463981A76503828BB1278391B716280987B.  <br/> |
| _Type_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.CertType[]  <br/> |Type of certificate being assigned. Certificate types include, but are not limited to, the following:  <br/> AccessEdgeExternal  <br/> AudioVideoAuthentication  <br/> DataEdgeExternal  <br/> Default  <br/> External  <br/> Internal  <br/> iPhoneAPNService  <br/> iPadAPNService  <br/> MPNService  <br/> PICWebService (Microsoft Lync Online 2010 only)  <br/> ProvisionService (Microsoft Lync Online 2010 only)  <br/> WebServicesExternal  <br/> WebServicesInternal  <br/> WsFedTokenTransfer  <br/> For example, this syntax assigns the Default certificate: -Type Default.  <br/> You can specify multiple types in a single command by separating the certificate types with commas:  <br/> -Type Internal,External,Default  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EffectiveDate_ <br/> |Optional  <br/> |System.DateTime  <br/> |Date and time when the certificate can first be used. For example, to configure a certificate for first use at 8:00 AM on July 31, 2012 use this syntax on a server running under the US English Region and Language settings:  <br/> -EffectiveTime "7/31/2012 8:00 AM"  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Password_ <br/> |Optional  <br/> |System.String  <br/> |Password for the certificate.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to record detailed information about the procedures carried out by the **Set-CsCertificate** cmdlet. The parameter value should be the full path to the HTML file to be generated; for example: -Report C:\Logs\Certificates.html. If the specified file already exists it will automatically be overwritten with the new information.  <br/> |
| _Roll_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to update the specified certificate at the date and time specified by the EffectiveDate parameter; this enables you to specify a date and time when the new certificate will become the primary certificate. Note that your command will fail if you specify the Roll parameter without including the EffectiveDate parameter.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.Deployment.CertificateReference. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsCertificate** cmdlet does not return any values or objects. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsCertificate](get-cscertificate.md)
  
[Import-CsCertificate](import-cscertificate.md)
  
[Remove-CsCertificate](remove-cscertificate.md)
  
[Request-CsCertificate](request-cscertificate.md)

