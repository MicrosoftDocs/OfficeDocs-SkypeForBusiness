---
title: "Remove-CsTrustedApplication"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0d441b74-324b-4dab-8bd6-7d0a7eb18d28
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsTrustedApplication
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes a trusted application from the associated trusted service. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsTrustedApplication -Identity <ExternalApplicationIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example removes the trusted application with the Identity TrustPool.litwareinc.com/tapp2 from the associated trusted service.
  
```
Remove-CsTrustedApplication -Identity TrustPool.litwareinc.com/tapp2
```

### EXAMPLE 2

Example 2 removes all trusted applications that have identities that include the string "trust". The command begins with a call to the **Get-CsTrustedApplication** cmdlet, passing a Filter value of *trust*. This command will retrieve all trusted applications with the string trust anywhere within the Identity. The collection of trusted applications that is retrieved is then piped to the **Remove-CsTrustedApplication** cmdlet, which removes each one as a trusted application. (Note that the application itself is not deleted; only the association with the trusted application pool and the trusted service is removed.) 
  
```
Get-CsTrustedApplication -Filter *trust* | Remove-CsTrustedApplication
```

## Detailed Description
<a name="sectionSection1"> </a>

A trusted application is an application developed by a third party that is given trusted status to run as part of Lync Server but that is not a built-in part of the product. This cmdlet removes a trusted application from a trusted application pool. Note that the application itself is not deleted, only the association with the trusted application pool and the trusted service is removed.
  
When you use this cmdlet to remove a trusted application, you must supply a value for the Identity parameter. The Identity is the fully qualified domain name (FQDN) of the pool on which the application is homed followed by a slash (/) followed by the application ID. For example, TrustPool.litwareinc.com/tapp2, where TrustPool.litwareinc.com is the pool FQDN and tapp2 is the application ID. Note that if you view an existing application by calling the **Get-CsTrustedApplication** cmdlet you'll see an ID that looks more like this: TrustPool.litwareinc.com/urn:application:tapp2. Notice the prefix urn:application: before the application name (tapp2). While this prefix is part of the Identity, it's not required when you specify the value for the Identity parameter. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsTrustedApplication** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsTrustedApplication\b"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.ExternalApplicationIdentity  <br/> |The unique identifier of the trusted application to be removed from the trusted application pool. Identity values must be entered in the format \<pool FQDN\>/\<application ID\>, where pool FQDN is the FQDN of the pool on which the application resides, and application ID is the name of the application.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.Xds.DisplayTrustedApplication object. Accepts pipelined input of trusted application objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.Xds.DisplayTrustedApplication.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsTrustedApplication](new-cstrustedapplication.md)
  
[Set-CsTrustedApplication](set-cstrustedapplication.md)
  
[Get-CsTrustedApplication](get-cstrustedapplication.md)

