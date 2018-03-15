---
title: "New-CsAutodiscoverConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 4/4/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6b878b0e-f0c0-46a2-99b8-fd2105250600
description: "Creates a new collection of Autodiscover configuration settings at the site scope. The Autodiscover service provides a way for client applications such as Microsoft Lync Mobile to locate key resources such as a user's home pool or the URL for joining a dial-in conference. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011."
---

# New-CsAutodiscoverConfiguration
 
Creates a new collection of Autodiscover configuration settings at the site scope. The Autodiscover service provides a way for client applications such as Microsoft Lync Mobile to locate key resources such as a user's home pool or the URL for joining a dial-in conference. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
New-CsAutodiscoverConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableCertificateProvisioningServiceUrl <$true | $false>] [-EnableCORS <$true | $false>] [-ExternalSipClientAccessFqdn <String>] [-ExternalSipClientAccessPort <UInt32>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WebLinks <PSListModifier>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 creates a new collection of Autodiscover configuration settings for the Redmond site. Because the WebLinks parameter was not included, these settings will not contain any Autodiscover URLs.
  
```
New-CsAutoDiscoverConfiguration -Identity "site:Redmond"
```

### EXAMPLE 2

The commands shown in Example 2 create a new collection of Autodiscover configuration settings for the Redmond site and assign those new settings a pair of Autodiscover URLs: http://LyncDiscover.fabrikam.com and http://LyncDiscoverInternal.fabrikam.com. In order to carry out this task, the first two commands use the **New-CsWebLink** cmdlet to create the two Autodiscover URLs; the newly-created URLs are then stored in variables named $Link1 and $Link2. After the two URLs are created, the third command uses the **New-CsAutoDiscoverConfiguration** cmdlet to create the new Autodiscover configuration settings. In order to assign the two URLs to these settings, the WebLinks parameter is included along with the parameter value @{Add=$Link1,$Link2}. That syntax causes the values stored in the variables $Link1 and $Link2 to be added to the WebLinks property.
  
```
$Link1 = New-CsWebLink -Token "Fabrikam" -Href "http://LyncDiscover.fabrikam.com"
$Link2 = New-CsWebLink -Token "Fabrikam" -Href "http://LyncDiscoverInternal.fabrikam.com"

New-CsAutoDiscoverConfiguration -Identity "site:Redmond" -WebLinks @{Add=$Link1,$Link2}
```

## Detailed Description

For client applications to make the most effective use of Skype for Business Server 2015 those applications need to know the location of key Skype for Business Server 2015 components. For example, authenticated users must be able to locate their home pool; after all, they can only be authenticated by that home pool. Likewise, unauthenticated users must be able to do such things as locate the URL used for joining a conference.
  
If all your users logged on from behind the organization's firewall discovering these locations would be a relatively simple task. However, this relatively simple task gets more and more complicated as users access the system from external locations using applications like Microsoft Lync Mobile.
  
This is especially true in split-domain scenarios, scenarios in which some of an organization's users have accounts on the on-premises version of Skype for Business Server 2015 while other users have accounts on Skype for Business Online. In cases such as this, user accounts might be located in different Active Directory forests. That can pose a problem: for example, if a US-based user logs on from Europe the system must be able to recognize his or her forest and then refer the logon request to the proper pool.
  
The Autodiscover service was introduced in the cumulative update for Lync Server: November 2011 in order to address these issues. When a client application attempts to access Skype for Business Server 2015, the Autodiscover service parses the client SIP address and then redirects that request to the appropriate pool. Client applications connect to the Autodiscover service by sending an HTTP request to an Autodiscover URL; these URLs must be configured by administrators in order for the Autodiscover service to work. (Note that, in addition to configuring URLs, administrators must also create DNS records that correspond to these URLs.)
  
Autodiscover URLs are assigned to Autodiscover configuration settings; in turn, these settings can be applied to the global scope or to the site scope. When you install Skype for Business Server 2015 a global collection of settings will be created for you. (However, no Autodiscover URLs will be assigned to that collection.) If a single collection of Autodiscover settings will not fill your needs, then you can use the **New-CsAutoDiscoverConfiguration** cmdlet to create additional configuration settings at the site scope.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of Autodiscover configuration settings to be modified. To create a collection configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableCertificateProvisioningServiceUrl_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), the Certificate Provisioning Service URL is included in Autodiscover Service responses.  <br/> |
| _EnableCORS_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _ExternalSipClientAccessFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name of the server used for external client access.  <br/> |
| _ExternalSipClientAccessPort_ <br/> |Optional  <br/> |System.UInt32  <br/> |Port used for eternal client access.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of a command called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling the **Set-CsAutoDiscoverConfiguration** cmdlet. <br/> |
| _WebLinks_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of Autodiscover URLs. These URLs must be created by using the **New-CsWebLink** cmdlet. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

The **New-CsAutoDiscoverConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

Creates new instances of the Microsoft.Rtc.Management.WriteableConfig.Settings.AutoDiscoverConfiguration.AutoDiscoverConfiguration object.
  

