---
title: "Get-CsTrustedApplicationEndpoint"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f66ac464-31ef-4aa3-9b79-f9e67ebc1475
description: "Retrieves information about one or more trusted application endpoints. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsTrustedApplicationEndpoint
 
Retrieves information about one or more trusted application endpoints. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsTrustedApplicationEndpoint [-Identity <UserIdParameter>] [-ApplicationId <String>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>] [-TrustedApplicationPoolFqdn <Fqdn>]

```

## Examples

### EXAMPLE 1

This example retrieves information about all trusted application endpoints defined within the Skype for Business Server 2015 deployment.
  
```
Get-CsTrustedApplicationEndpoint
```

### EXAMPLE 2

Example 2 retrieves information about the application endpoint contact with the SIP address endpoint1@litwareinc.com. Note that the sip: prefix is required when using a SIP address as the Identity.
  
```
Get-CsTrustedApplicationEndpoint -Identity "sip:endpoint1@litwareinc.com"
```

### EXAMPLE 3

Example 3 retrieves all trusted application endpoints that have the string "endpoint" anywhere within their display name. To do this, the command uses the Filter parameter. The value of the parameter filters to find endpoint objects that have a display name (DisplayName) that contains (-like) the string endpoint (\*endpoint\* - the wildcard characters indicate that any characters can come before or after the string endpoint, meaning endpoint can be anywhere within the display name).
  
```
Get-CsTrustedApplicationEndpoint -Filter {DisplayName -like "*endpoint*"}
```

### EXAMPLE 4

Example 4 will return all trusted application endpoints associated with the application tapp2. This is accomplished by passing the ID tapp2 to the ApplicationId parameter. Notice that we didn't supply a pool FQDN; this means that if an application with the ID tapp2 exists on more than one pool, endpoints for all those applications will be retrieved. The next part of this command pipes the returned object or objects to the **Select-Object** cmdlet, which displays only the SipAddress, DisplayName, and OwnerUrn properties of those objects.
  
```
Get-CsTrustedApplicationEndpoint -ApplicationId tapp2 | Select-Object SipAddress, DisplayName, OwnerUrn
```

## Detailed Description

A trusted application endpoint is an Active Directory contact object that enables routing of calls to a trusted application. This cmdlet retrieves one or more existing endpoint contact objects in Active Directory Domain Services.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ApplicationId_ <br/> |Optional  <br/> |System.String  <br/> |The application ID of the trusted application for the endpoint you want to retrieve.  <br/> |
| _Credential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |Alternate credentials to be used to retrieve the endpoint. You can retrieve a PSCredential object by calling the **Get-Credential** cmdlet. <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.  <br/> |
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering on specific attributes for Skype for Business Server 2015. For example, you can limit returned data to contacts whose display names or SIP addresses match a certain wildcard pattern.  <br/> The Filter parameter uses the same Windows PowerShell filtering syntax that is used by the **Where-Object** cmdlet. For example, a filter that returns only contacts that have been enabled for Enterprise Voice would look like this: {EnterpriseVoiceEnabled -eq $True}, with EnterpriseVoiceEnabled representing the Active Directory attribute, -eq representing the comparison operator (equal to), and $True (a built-in Windows PowerShell variable) representing the filter value. <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |The Identity (distinguished name), SIP address, or display name of the application endpoint to be modified.  <br/> |
| _OU_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |The OU in which the endpoint resides.  <br/> |
| _ResultSize_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.Unlimited  <br/> |The maximum number of endpoint records to retrieve.  <br/> |
| _TrustedApplicationPoolFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |The fully qualified domain name (FQDN) of the trusted application pool associated with the application for the endpoint you want to retrieve.  <br/> |
   
## Input Types

String. Accepts a pipelined string value representing the Identity of a user account.
  
## Return Types

Retrieves an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact.
  
## See also

#### 

[New-CsTrustedApplicationEndpoint](new-cstrustedapplicationendpoint.md)
  
[Remove-CsTrustedApplicationEndpoint](remove-cstrustedapplicationendpoint.md)
  
[Set-CsTrustedApplicationEndpoint](set-cstrustedapplicationendpoint.md)

