---
title: "Test-CsCertificateConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8086bdf7-d283-4666-9f6c-0d5a3a31b3a6
description: "Returns information about the Skype for Business Server 2015 certificates being used on the local computer. This cmdlet was introduced in Lync Server 2010."
---

# Test-CsCertificateConfiguration
 
Returns information about the Skype for Business Server 2015 certificates being used on the local computer. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsCertificateConfiguration [-Report <String>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns information about the certificates that are currently being used (on the local computer) by Skype for Business Server 2015. 
  
```
Test-CsCertificateConfiguration
```

### EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In this case, however, the Report parameter is used to specify a file path (C:\Logs\Certificates.xml) for the output file generated when you run the **Test-CsCertificateConfiguration** cmdlet.
  
```
Test-CsCertificateConfiguration -Report "C:\Logs\Certificates.xml"
```

## Detailed Description

The **Test-CsCertificateConfiguration** cmdlet is an example of a "synthetic transaction." Synthetic transactions are used in Skype for Business Server 2015 to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).
  
The **Test-CsCertificateConfiguration** cmdlet returns information about the certificates being used by Skype for Business Server 2015. The **Test-CsCertificateConfiguration** cmdlet is primarily intended for use by the Certificate wizard. It is recommended that administrators use the **Get-CsCertificate** cmdlet to retrieve certificate information.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\Certificates.html"`. If this file already exists, it will be overwritten when you run the cmdlet.  <br/> |
   
## Input Types

None. The **Test-CsCertificateConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **Test-CsCertificateConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment,CertificateExists object.
  
## See also

#### 

[Get-CsCertificate](get-cscertificate.md)

