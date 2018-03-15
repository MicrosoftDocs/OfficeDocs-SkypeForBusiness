---
title: "Test-CsCertificateConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8086bdf7-d283-4666-9f6c-0d5a3a31b3a6
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsCertificateConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information about the Lync Server certificates being used on the local computer. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsCertificateConfiguration [-Report <String>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 returns information about the certificates that are currently being used (on the local computer) by Lync Server. 
  
```
Test-CsCertificateConfiguration
```

### EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In this case, however, the Report parameter is used to specify a file path (C:\Logs\Certificates.xml) for the output file generated when you run the **Test-CsCertificateConfiguration** cmdlet. 
  
```
Test-CsCertificateConfiguration -Report "C:\Logs\Certificates.xml"
```

## Detailed Description
<a name="sectionSection1"> </a>

The **Test-CsCertificateConfiguration** cmdlet is an example of a "synthetic transaction." Synthetic transactions are used in Lync Server to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager). 
  
The **Test-CsCertificateConfiguration** cmdlet returns information about the certificates being used by Lync Server. The **Test-CsCertificateConfiguration** cmdlet is primarily intended for use by the Certificate wizard. It is recommended that administrators use the **Get-CsCertificate** cmdlet to retrieve certificate information. 
  
Who can run this cmdlet: To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsCertificateConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\Certificates.html". If this file already exists, it will be overwritten when you run the cmdlet.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Test-CsCertificateConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Test-CsCertificateConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment,CertificateExists object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsCertificate](get-cscertificate.md)

