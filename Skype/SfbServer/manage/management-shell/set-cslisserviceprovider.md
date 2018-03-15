---
title: "Set-CsLisServiceProvider"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 3fe2878c-6ad2-4b7f-a844-e978c263163f
description: "Creates or modifies information about the web service provided by the Enhanced 9-1-1 (E9-1-1) Network Routing Provider to verify locations. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsLisServiceProvider
 
Creates or modifies information about the web service provided by the Enhanced 9-1-1 (E9-1-1) Network Routing Provider to verify locations. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsLisServiceProvider -CertFileName <String> -Password <SecureString> -ServiceProviderName <String> -ValidationServiceUrl <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

One of the required parameters for creating an entry for an E9-1-1 Network Routing Provider web service is a secure string containing the password to access the certificate file. Because of that, the first line in this example is a call to the **Read-Host** cmdlet. The **Read-Host** cmdlet will prompt for user input. We specify the parameter AsSecureString, which will display that input as asterisks (*) as it is entered. We've assigned the result of this command to the variable $p. The result will be a secure string, which is an encrypted version of the user input. In other words, running this command will prompt for the password to the web service and will store that password in the variable $p.
  
Now that we have the password, we can create an object that will access the web service. We do this by calling the **Set-CsLisServiceProvider** cmdlet. We pass several parameters to this cmdlet. The first is the name of the provider, in this case E911Provider. Next we provide a value for the ValidationServiceUrl, https://www.911contoso.com/validation/. Note that this must be a "secure site," with the prefix https rather than http. Next we enter the name of the file containing the certificate used to access this web service, C:\MS-Contoso-Cert.pfx. Finally, we pass the variable $p (which contains the secure string with the web service password) to the Password parameter.
  
```
$p = Read-Host -AsSecureString
Set-CsLisServiceProvider -ServiceProviderName E911Provider -ValidationServiceUrl https://www.911contoso.com/validation/ -CertFileName C:\MS-Contoso-Cert.pfx -Password $p
```

## Detailed Description

In an Enterprise Voice implementation with E9-1-1, emergency calls must first be routed through an E9-1-1 Network Routing Provider to ensure that the calls are routed to the appropriate Public Safety Answering Point (PSAP). (A PSAP is the agency in the United States that directs the calls to the nearest emergency services, such as police, fire, and ambulance services.) In order to do this, the provider must have a list of locations from the organization that it can then match against the Master Street Address Guide to ensure all locations are valid. This cmdlet creates or modifies information about a provider, including the name of the provider, a URL for the web service that the organization will use to send the locations, and a certificate and password for the secure web service.
  
You cannot define more than one service provider for a given E9-1-1 implementation. This cmdlet will not succeed unless it can resolve the URL and security information for the web service.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CertFileName_ <br/> |Required  <br/> |System.String  <br/> |The name (and full path) of the certificate file. This file must have a PFX file extension.  <br/> |
| _Password_ <br/> |Required  <br/> |System.Security.SecureString  <br/> |A secure string containing the password needed to access the certificate in the password protected file. Secure strings can be created by using the **ConvertTo-SecureString** cmdlet or the **Read-Host** cmdlet with the AsSecureString parameter. <br/> |
| _ServiceProviderName_ <br/> |Required  <br/> |System.String  <br/> |The name of the E9-1-1 Network Routing Provider.  <br/> |
| _ValidationServiceUrl_ <br/> |Required  <br/> |System.String  <br/> |The URL of the web service. This must be a secure URL, beginning with the prefix https://.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Accepts pipelined input of Location Information Server (LIS) service provider objects.
  
## Return Types

This cmdlet creates or modifies an object of type System.Management.Automation.PSCustomObject.
  
## See also

#### 

[Remove-CsLisServiceProvider](remove-cslisserviceprovider.md)
  
[Get-CsLisServiceProvider](get-cslisserviceprovider.md)

