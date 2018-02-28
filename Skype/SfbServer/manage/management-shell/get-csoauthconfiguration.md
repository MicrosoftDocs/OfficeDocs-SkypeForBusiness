---
title: "Get-CsOAuthConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a3fda8bf-84e3-4d14-a1c5-093e6eb36ffe
description: "Returns information about the Open Authorization (OAuth) configuration settings currently in use in the organization. OAuth is a standard protocol used for server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsOAuthConfiguration
[]
Returns information about the Open Authorization (OAuth) configuration settings currently in use in the organization. OAuth is a standard protocol used for server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsOAuthConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information for the OAuth configuration settings in use in the organization.
  
```
Get-CsOAuthConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, server-to-server authentication (for example, the authentication that enables Skype for Business Server 2015 and Exchange to share information) is carried out using the OAuth security protocol. OAuth is always on in Skype for Business Server 2015; there is no need (or even any way) to enable or disable the protocol. However, if Skype for Business Server 2015 needs to communicate with other server products you might need to modify your OAuth configuration settings; for example, you might need to specify the autodiscover URL for the Office 365 version of Exchange, and you might need to specify your Realm name. These settings can only be managed by using the **CsOAuthConfiguration** cmdlets; options for managing OAuth settings are not available in the Skype for Business Server Control Panel.
  
Note that, for the on-premises version of Skype for Business Server 2015, you can have only a single, global collection of OAuth settings: you cannot not create additional collections of OAuth settings nor can you delete the global collection. Each Skype for Business Online tenant is also limited to a single collection of OAuth configuration settings.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsOAuthConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard values when referencing a collection of OAuth configuration settings. Because you can only have a single, global instance of these settings there is no reason to use the Filter parameter. However, if you prefer you can use the following syntax to reference the global settings:  <br/>  `-Filter "g*"` <br/> That syntax brings back all the OAuth configuration settings that have an Identity that begins with the letter "g".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the OAuth configuration settings. Because you can only have a single, global instance of these settings, you do not need to specify an Identity when calling the **Get-CsOAuthConfiguration** cmdlet. If you prefer, however, you can use the following syntax to reference the global settings: <br/>  `-Identity global` <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the OAuth configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose OAuth configuration settings are to be retrieved.  <br/> For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsOAuthConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsOAuthConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthSettings object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsOAuthConfiguration](set-csoauthconfiguration.md)

