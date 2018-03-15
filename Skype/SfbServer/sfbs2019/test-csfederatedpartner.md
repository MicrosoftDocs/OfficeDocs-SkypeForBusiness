---
title: "Test-CsFederatedPartner"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1f56bf80-37b4-4520-b8a5-da0740a894a2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsFederatedPartner
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Verifies the ability to connect to a federated domain. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsFederatedPartner -Domain <String> -TargetFqdn <String> [-Certificate <X509Certificate2>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-ProxyFqdn <String>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 verifies the connection between the local access proxy server (accessproxy.litwareinc.com) and the federated domain Fabrikam.com. Note that TargetFqdn must point to the internal edge of the proxy server to which federated SIP traffic is directed.
  
```
Test-CsFederatedPartner -TargetFqdn accessproxy.litwareinc.com -Domain fabrikam.com
```

### EXAMPLE 2

Example 2 shows how you can test the connection between your domain and the Lync Server Push Notification Service. You must have configured this service as a hosting provider and must have added push.lync.com to your list of allowed domains for this test to succeed. For more information, see [Configuring for push notifications in Lync Server 2013](configuring-for-push-notifications.md).
  
```
Test-CsFederatedPartner -TargetFqdn accessproxy.litwareinco.com -Domain push.lync.com -ProxyFqdn sipfed.online.lync.com
```

### EXAMPLE 3

In Example 3, connectivity is verified for all the domains on your allowed domains list. To do this, the command first uses the Get-CsAllowedDomain cmdlet to retrieve a collection of all your allowed domains. That collection is then piped to the ForEach-Object cmdlet. In turn, ForEach-Object runs the Test-CsFederatedPartner cmdlet against each domain in the collection.
  
```
Get-CsAllowedDomain | ForEach-Object {Test-CsFederatedPartner -TargetFqdn accessproxy.litwareinc.com -Domain $_.Identity}
```

## Detailed Description
<a name="sectionSection1"> </a>

 **Test-CsFederatedPartner** verifies your ability to connect to the domain of a federated partner. In order to verify the connectivity to a domain, that domain must be listed in the collection of allowed (federated) domains. Domains can be added to the allowed list by using the **New-CsAllowedDomain** cmdlet. When using the Test-CsFederatedPartner cmdlet, make sure that the TargetFqdn parameter points to the internal edge of the proxy server to which federated SIP traffic is directed. 
  
Who can run this cmdlet: To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsFederatedPartner"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Domain_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the federated domain. For example: -Domain "fabrikam.com".  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |FQDN of the access proxy server used by your organization for federated SIP traffic. The TargetFqdn must point to the internal edge of the proxy server to which federated SIP traffic is directed.  <br/> |
| _Certificate_ <br/> |Optional  <br/> |System.Security.Cryptography.X509Certificates.X509Certificate2  <br/> |Enables you to provide an X509 certificate for authentication purposes when connecting to the federated domain.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/> -OutLoggerVariable TestOutput  <br/> Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/> $TestOutput.ToHTML() \> C:\Logs\TestOutput.html  <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/> $TestOutput.ToXML() \> C:\Logs\TestOutput.xml  <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/> -OutVerboseVariable TestOutput  <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _ProxyFqdn_ <br/> |Optional  <br/> |System.String  <br/> |FQDN of the access proxy server used by the federated organization.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. **Test-CsFederatedPartner** does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

 **Test-CsFederatedPartner** returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsAllowedDomain](get-csalloweddomain.md)

