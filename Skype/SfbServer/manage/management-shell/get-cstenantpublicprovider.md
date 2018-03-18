---
title: "Get-CsTenantPublicProvider"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0d949ec2-206d-4979-a3be-a5578ae93ed3
description: "Returns information indicating whether Microsoft Lync Online users are allowed to communicate with people who have accounts on the third-party IM and presence providers Windows Live, AOL, and Yahoo."
---

# Get-CsTenantPublicProvider
 
Returns information indicating whether Microsoft Lync Online users are allowed to communicate with people who have accounts on the third-party IM and presence providers Windows Live, AOL, and Yahoo.
  
This cmdlet can only be used with Lync Online.
  
```
Get-CsTenantPublicProvider -Tenant <String> [-Verbose]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns public provider information for the tenant with the tenant ID "bf19b7db-6960-41e5-a139-2aa373474354".
  
```
Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"
```

Note that the Tenant parameter is optional. You can also call Get-CsTenantPublicProvider by using this syntax:
  
```
Get-CsTenantPublicProvider
```

### Example 2

The preceding command returns detailed information about the status of all the public providers assigned to the tenant bf19b7db-6960-41e5-a139-2aa373474354. To do this, the command first uses the **Get-CsTenantPublicProvider** cmdlet to return public provider information for the specified tenant. That information is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty parameter to "expand" the value of the DomainPICStatus property. Expanding a property simply means displaying all the values stored in that property onscreen, and in an easy-to-read format.
  
```
Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty DomainPICStatus
```

A command like this would be used in a hybrid deployment of Lync Server 2013.
  
### Example 3

The command shown in Example 3 is a variation of the command shown in Example 2. In Example 3, however, the public provider information returned by "expanding" the value of the DomainPICStatus property is, in turn, piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet then picks out only those providers where the Status property is set to Enabled. The net effect is to display only those public providers that are enabled for use.
  
```
Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty DomainPICStatus | Where-Object {$_.Status -eq "Enabled"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

Public providers are organizations that provide SIP communication services for the general public. When you establish a federation relationship with a public provider, you effectively establish federation with any user who has an account hosted by that provider. For example, if you federate with Windows Live, then your users will be able to exchange instant messages and presence information with anyone who has a Windows Live instant messaging account.
  
Lync Online gives administrators the option of configuring federation with one or more of the following public IM and presence providers:
  
- Windows Live
    
- AOL
    
- Yahoo!
    
Administrators can use the **Get-CsTenantPublicProvider** cmdlet to determine which of those providers (if any) have been enabled for federation. When you call the **Get-CsTenantPublicProvider** cmdlet you will get back information similar to this:
  
```
PublicProviderSet     DomainPicStatus
------------------    ------------------------
True                  {Microsoft.Rtc.Management.Hosted.DomainPICStatus}
```

The PublicProviderSet property indicates whether or not federation has been enabled for one or more public provider. If PublicProviderSet is equal to True then that means federation has been enabled with at least one provider; if PublicProviderSet is equal to False then that means that federation is disabled for all three public providers (Windows Live, AOL, and Yahoo). To determine the actual status of each provider use this command:
  
```
Get-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty DomainPICStatus
```

Note that simply enabling the status of a public provider does not mean that users can exchange instant messages and presence information with users who have accounts on that provider. In addition to enabling federation with the provider itself, administrators must also set the AllowPublicUsers property of the federation configuration settings to True. If this property is set to False then communication will not be allowed with any of the public providers, regardless of the public provider configuration settings.
  
For more information, see the help topic for the **Set-CsTenantFederationConfiguration** cmdlet.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Tenant_ <br/> |Required  <br/> |System.String  <br/> |Globally unique identifier (GUID) of the tenant account whose public provider settings are being returned. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> If you are using a remote session of Windows PowerShell and are connected only to Lync Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsTenantPublicProvider** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsTenantPublicProvider** cmdlet returns instances of the Microsoft.Rtc.Management.Hosted.TenantPICStatus object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsTenantPublicProvider](set-cstenantpublicprovider.md)

