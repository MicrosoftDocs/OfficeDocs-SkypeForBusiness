---
title: "Get-CsPublicProvider"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c122505d-7209-4dcb-a888-5c73f58fa68a
description: "Returns information about the public providers configured for use in your organization. A public provider is an organization that provides instant messaging, presence, and related services to the general public. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsPublicProvider
 
Returns information about the public providers configured for use in your organization. A public provider is an organization that provides instant messaging, presence, and related services to the general public. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns a collection of all the public providers that are configured for use in the organization. Calling the **Get-CsPublicProvider** cmdlet without any additional parameters always returns the complete collection of public providers.
  
```
Get-CsPublicProvider
```

### EXAMPLE 2

In Example 2, all the public providers that have the Identity Skype are returned. Because Identities must be unique among public providers (and among hosting providers), this command will always return, at most, a single item.
  
```
Get-CsPublicProvider -Identity "Skype"
```

### EXAMPLE 3

Example 3 returns all the public providers that have an Identity that begins with the letter W. This is done by including the Filter parameter and the filter value "W\*".
  
```
Get-CsPublicProvider -Filter W*
```

### EXAMPLE 4

The command shown in Example 4 returns a collection of all the public providers that are currently disabled. To do this, the command first calls the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those providers where the Enabled property is equal to False.
  
```
Get-CsPublicProvider | Where-Object {$_.Enabled -eq $False}
```

### EXAMPLE 5

Example 5 returns all the public providers where the VerificationLevel property is set to either AlwaysUnverifiable or UseSourceVerification. (Verification levels can be set to AlwaysUnverifiable; UseSourceVerification; or AlwaysVerifiable.) To perform this task, the command first calls the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those providers where the VerificationLevel property is not equal to AlwaysVerifiable. The net effect: only providers where the VerificationLevel property is set to either AlwaysUnverifiable or UseSourceVerification will be selected.
  
```
Get-CsPublicProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable"}
```

## Detailed Description

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another using SIP applications such as Skype for Business. Skype for Business Server 2015 allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.
  
A public provider is an organization which provides SIP communication services for the general public. When you establish a federation relationship with a public provider, you effectively establish federation with any user who has an account hosted by that provider. For example, if you federate with Skype then your users will be able to exchange instant messages and presence information with anyone who has a Skype instant messaging account.
  
In order to federate with a public provider you need to create and enable a new public provider. (In addition, the public provider will need to create a federation relationship with you.) The **Get-CsPublicProvider** cmdlet enables you to return information about the public providers that have been configured for use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard values in order to return one or more public providers. For example, to return a collection of all the public providers that have an Identity that begins with the letter Y, use this syntax:  <br/>  `-Filter "Y*"` <br/> To return a collection of all the public providers that include the string value "Windows" anywhere in their Identity, use this syntax:  <br/>  `-Filter "*Windows*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Unique identifier for the public provider to be returned. The Identity is typically the name of the web site providing the services.  <br/> You cannot use wildcards when specifying the Identity. To use wildcards to return one or more public providers, use the Filter parameter instead.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the public provider data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsPublicProvider** cmdlet does not accept pipelined input.
  
## Return Types

Returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider object.
  
## See also

#### 

[Disable-CsPublicProvider](disable-cspublicprovider.md)
  
[Enable-CsPublicProvider](enable-cspublicprovider.md)
  
[New-CsPublicProvider](new-cspublicprovider.md)
  
[Remove-CsPublicProvider](remove-cspublicprovider.md)
  
[Set-CsPublicProvider](set-cspublicprovider.md)

