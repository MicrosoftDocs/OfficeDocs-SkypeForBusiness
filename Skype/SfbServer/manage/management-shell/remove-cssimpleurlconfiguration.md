---
title: "Remove-CsSimpleUrlConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6cf483ed-7a53-47b0-b87a-6ef70493ba32
description: "Removes one or more of the simple URL configuration collections currently in use in your organization. Simple URLs make it easier for users to join meetings and conferences, as well as making it easier for Administrators to log on to the Skype for Business Server Control Panel. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsSimpleUrlConfiguration
 
Removes one or more of the simple URL configuration collections currently in use in your organization. Simple URLs make it easier for users to join meetings and conferences, as well as making it easier for Administrators to log on to the Skype for Business Server Control Panel. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsSimpleUrlConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 deletes the simple URL configuration collection applied to the Redmond site. This command deletes all the simple URLs assigned to the specified site.
  
```
Remove-CsSimpleUrlConfiguration -Identity "site:Redmond"
```

### EXAMPLE 2

In Example 2, all the simple URL configuration collections applied at the site scope are deleted. To do this, the command first uses the **Get-CsSimpleUrlConfiguration** cmdlet and the Filter parameter to return all the simple URL collections configured at the site scope; the filter value "site:*" limits the returned data to those collections that have an Identity that begins with the string value "site:". The filtered collection is then piped to the **Remove-CsSimpleUrlConfiguration** cmdlet, which deletes each item in that collection.
  
```
Get-CsSimpleUrlConfiguration -Filter "site:*" | Remove-CsSimpleUrlConfiguration 
```

## Detailed Description

In Microsoft Office Communications Server 2007 R2, meetings had URLs similar to this: 
  
https://imdf.litwareinc.com/Join?uri=sip%3Akenmyer%40litwareinc.com%3Bgruu%3Bopaque%3Dapp%3Aconf%3Afocus%3Aid%3A125f95a0b0184dcea706f1a0191202a8&amp;key=EcznhLh5K5t
  
However, such URLs are not especially intuitive, and not easy to convey to someone else. The simple URLs introduced in Lync Server 2010 help overcome those problems by providing users with URLs that look more like this:
  
https://meet.litwareinc.com/kenmyer/071200
  
Simple URLs are an improvement over the URLs used in Office Communications Server. However, simple URLs are not automatically created for you; instead, you must configure the URLs yourself. In addition, you must also do such things as create Domain Name System (DNS) records for each URL; configure reverse proxy rules for external access; add the simple URLs to the your Front End Server certificates; and so on.
  
Skype for Business Server 2015 enables you to create three different simple URLs:
  
Meet - Used for meetings. You must have at least one Meet URL for each of your SIP domains.
  
Admin - Used to point administrators to the Skype for Business Server Control Panel.
  
Dialin - Used for the dial-in conferencing webpage.
  
Simple URLs are stored in simple URL configuration collections. When you install Skype for Business Server 2015, a global collection is created for you; you can also create custom collections at the site scope. This gives you the ability to use different simple URLs at each of your sites.
  
Simple URL configuration collections are created by using the **New-CsSimpleUrlConfiguration** cmdlet; you can then use additional cmdlets (such as the **New-CsSimpleUrlEntry** cmdlet and the **Set-CsSimpleUrlConfiguration** cmdlet) to populate these collections with simple URLs. If you later decide to delete one or more of the site-scoped collections, you can do so by using the **Remove-CsSimpleUrlConfiguration** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of simple URLs to be removed. To remove a collection from the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> Note that you cannot use wildcards when specifying an Identity.  <br/> You can also run this cmdlet against the global collection by using this syntax:  <br/>  `-Identity global` <br/> In that case, however, the global collection will not be deleted. Instead, all the Simple URLs within that collection will be deleted.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for the Simple URL configuration settings being deleted. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.SimpleUrl.SimpleUrlConfiguration object. The **Remove-CsSimpleUrlConfiguration** cmdlet accepts pipelined instances of the simple URL configuration object.
  
## Return Types

None.
  
## See also

#### 

[Get-CsSimpleUrlConfiguration](get-cssimpleurlconfiguration.md)
  
[New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)
  
[Set-CsSimpleUrlConfiguration](set-cssimpleurlconfiguration.md)

