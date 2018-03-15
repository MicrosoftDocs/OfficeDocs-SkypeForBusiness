---
title: "Set-CsTenantPublicProvider"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8341d801-bfa1-4c5b-9b80-5d503deebaf7

description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsTenantPublicProvider
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Enables and disables communication with the third-party IM and presence providers Windows Live, AOL, and Yahoo. When enabled, Skype for Business Online users will be able to exchange IM and presence information with users who have accounts on the specified public provider.
  
The **Set-CsTenantPublicProvider** cmdlet can only be used with Skype for Business Online. 
  
```
Set-CsTenantPublicProvider -Tenant <String> [-Provider <String[]>] [-Verbose] [-WhatIf] [-Confirm]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 enables federation with Windows Live for the tenant with the tenant ID bf19b7db-6960-41e5-a139-2aa373474354. Because Windows Live is the only provider specified, both the AOL and Yahoo providers will be disabled after the command executes.
  
```
Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"
```

### Example 2

In Example 2, two public providers are enabled: Windows Live and AOL. That means that only the Yahoo public provider will be disabled for the specified tenant.
  
```
Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive","AOL"
```

### Example 3

Example 3 shows how you can disable all the public providers for a given tenant. This is done by setting the Provider property to an empty string ("").
  
```
Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider ""
```

### Example 4

The command shown in Example 4 disables all the public providers for all of your Skype for Business Online tenants. To accomplish this task, the command first uses the **Get-CsTenant** cmdlet to return a collection of all of your tenants. This collection is then piped to the **ForEach-Object** cmdlet, which takes each tenant in the collection, calls the **Set-CsTenantPublicProvider** cmdlet against each of those tenants, and disables all the public providers. That last task is carried out by setting the Provider property to an empty string (""). 
  
```
Get-CsTenant | ForEach-Object {Set-CsTenantPublicProvider -Tenant $_.TenantId -Provider ""}
```

## Detailed Description
<a name="DetailedDescription"> </a>

Public providers are organizations that provide SIP communication services for the general public. When you establish a federation relationship with a public provider, you effectively establish federation with any user who has an account hosted by that provider. For example, if you federate with Windows Live, then your users will be able to exchange instant messages and presence information with anyone who has a Windows Live instant messaging account.
  
Skype for Business Online gives administrators the option of configuring federation with one or more of the following public IM and presence providers:
  
> Windows Live
    
> AOL
    
> Yahoo!
    
The **Set-CsTenantPublicProvider** cmdlet can be used to enable or disable federation with any of these public providers. When using this cmdlet, keep in mind that each time you run the **Set-CsTenantPublicProvider** cmdlet you must specify all of the providers that should be enabled. For example, suppose all three providers are disabled and you run this command: 
  
```
Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"
```

As you might expect, that will enable Windows Live, and will leave AOL and Yahoo disabled.
  
Now, suppose you next run this command:
  
```
Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "AOL"
```

That command will enable AOL. However, it will also disable Windows Live: that's because Windows Live was not specified as part of the parameter value supplied to the Provider parameter. If you want to enable AOL and keep Windows Live enabled as well, then you must specify both AOL and Windows Live when calling Set-CsTenantPublicProvider:
  
```
Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "AOL","WindowsLive"
```

To disable federation for all three providers, set the Provider property to an empty string (""):
  
```
Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider ""
```

Note that simply enabling the status of a public provider does not mean that users can exchange instant messages and presence information with users who have accounts on that provider. In addition to enabling federation with the provider itself, administrators must also set the AllowPublicUsers property of the federation configuration settings to True. If this property is set to False then communication will not be allowed with any of the public providers, regardless of the public provider configuration settings.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Tenant_ <br/> |Required  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the tenant account whose public provider settings are being modified. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> ```Get-CsTenant | Select-Object DisplayName, TenantID```Get-CsTenant | Select-Object DisplayName, TenantID  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Provider_ <br/> |Optional  <br/> |System.String[]  <br/> |Indicates the public provider (or providers) that users will be allowed to communicate with. Valid values are:  <br/> \* AOL  <br/> \* WindowsLive  <br/> \* Yahoo  <br/> Note that, when configuring public providers, any provider included in the Provider parameter value will be enabled for use, while any provider not included in the parameter value will be disabled. For example, this syntax enables only Yahoo, while disabling Windows Live and AOL:  <br/> -Provider "AOL"  <br/> You can enable multiple providers by separating the provider names by using commas:  <br/> -Provider "AOL","WindowsLive"  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsTenantPublicProvider** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.Hosted.TenantPICStatus object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsTenantPublicProvider** cmdlet modifies existing instances of the Microsoft.Rtc.Management.Hosted.TenantPICStatus object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsTenantPublicProvider](get-cstenantpublicprovider.md)

