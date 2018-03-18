---
title: "Set-CsOAuthConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 43193254-acb1-47c8-8e21-143b610c2edc
description: "Modifies the Open Authorization (OAuth) configuration settings currently in use in the organization. OAuth is a standard protocol used for server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013."
---

# Set-CsOAuthConfiguration
 
Modifies the Open Authorization (OAuth) configuration settings currently in use in the organization. OAuth is a standard protocol used for server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsOAuthConfiguration [-ClientAuthorizationOAuthServerIdentity <String>] [-ExchangeAutodiscoverAllowedDomains <String>] [-ExchangeAutodiscoverUrl <String>] [-Identity <XdsIdentity>] [-Realm <String>] [-ServiceName <String>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 modifies the global collection of OAuth configuration settings. In this example, the Realm property is set to "contoso.com".
  
```
Set-CsOAuthConfiguration -Identity global -Realm "contoso.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, server-to-server authentication (for example, the authentication that enables Skype for Business Server 2015 and Exchange to share information) is carried out using the OAuth security protocol. OAuth is always on in Skype for Business Server 2015; there is no need (or even any way) to enable or disable the protocol. However, if Skype for Business Server 2015 needs to communicate with other server products you might need to modify your OAuth configuration settings; for example, you might need to specify the autodiscover URL for the Office 365 version of Exchange, and you might need to specify your Realm name. These settings can only be managed by using the **CsOAuthConfiguration** cmdlets; options for managing OAuth settings are not available in the Skype for Business Server Control Panel.
  
Note that, for the on-premises version of Skype for Business Server 2015, you can have only a single, global collection of OAuth settings: you cannot not create additional collections of OAuth settings nor can you delete the global collection. Each Skype for Business Online tenant is also limited to a single collection of OAuth configuration settings.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Set-CsOAuthConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ClientAuthorizationOAuthServerIdentity_ <br/> |Optional  <br/> |System.String  <br/> |URI of the OAuth server used for client authentication.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _ExchangeAutodiscoverAllowedDomains_ <br/> |Optional  <br/> |System.String  <br/> |Collection of domains that autodiscover requests can be redirected to. For example:  <br/>  `-ExchangeAutodiscoverAllowedDomains "*.contoso.com; *.fabrikam.com"` <br/> |
| _ExchangeAutodiscoverUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for the autodiscovery service used by the Office 365 version of Microsoft Exchange Server.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the OAuth configuration settings. Because you can only have a single, global instance of these settings, you do not need to specify an Identity when calling the **Set-CsOAuthConfiguration** cmdlet. You can, however, use the following syntax to reference the global settings: <br/>  `-Identity global` <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Realm_ <br/> |Optional  <br/> |System.String  <br/> |Server-to-server security container. By default, Skype for Business Server 2015 uses your default SIP domain as its OAuth realm.  <br/> |
| _ServiceName_ <br/> |Optional  <br/> |System.String  <br/> |Globally unique identifier (GUID) assigned to the OAuth service.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account for which the OAuth configuration settings are being modified. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsOAuthConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthSettings object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsOAuthConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthSettings object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsOAuthConfiguration](get-csoauthconfiguration.md)

