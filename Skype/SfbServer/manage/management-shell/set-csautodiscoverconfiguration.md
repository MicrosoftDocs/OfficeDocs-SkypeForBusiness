---
title: "Set-CsAutodiscoverConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 4/4/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 06f59d62-b4dd-4b50-9cf3-40d6d41d74af
description: "Modifies an existing collection of Autodiscover Service configuration settings. The Autodiscover Service provides a way for client applications such as Lync Web App or Lync Mobile to locate key resources such as a user's home pool or the URL for joining a dial-in conference. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011."
---

# Set-CsAutodiscoverConfiguration
[]
Modifies an existing collection of Autodiscover Service configuration settings. The Autodiscover Service provides a way for client applications such as Lync Web App or Lync Mobile to locate key resources such as a user's home pool or the URL for joining a dial-in conference. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
Set-CsAutodiscoverConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The commands shown in Example 1 add a new Autodiscover URL (http://LyncDiscover.fabrikam.com) to the Autodiscover configuration settings assigned to the Redmond site. To do this, the first command in the example uses the **New-CsWebLink** cmdlet to create a new Autodiscover URL; that URL is stored in a variable named $Link1. In the second command, the **Set-CsAutoDiscoverConfiguration** cmdlet is used to add the new URL to any URLs already assigned to these settings. This is done by using the WebLinks parameter and the parameter value @{Add=$Link1}.
  
```
$Link1 = New-CsWebLink -Token "Fabrikam" -Href "http://LyncDiscover.fabrikam.com"

Set-CsAutoDiscoverConfiguration -Identity "site:Redmond" -WebLinks @{Add=$Link1}
```

### EXAMPLE 2

The commands shown in Example 2 demonstrate how you can remove a URL from a collection of Autodiscover Service configuration settings. In order to do this, the first command in the collection retrieves an object reference to the URL to be deleted (a URL that has a Token equal to "Fabrikam"). This is done by first calling the **Get-CsAutoDiscoverConfiguration** cmdlet in order to retrieve the Autodiscover Service settings for the Redmond site. That collection in then piped to the **Select-Object** cmdlet, which uses the ExpandProperty parameter to "expand" the WebLinks property. (When a property is expanded, that provides the **Get-CsAutoDiscoverConfiguration** cmdlet access to the individual objects stored in that property.) These WebLinks objects are then piped to the **Where-Object** cmdlet, which selects the one object where the Token property is equal to "Fabrikam". That WebLinks object is then stored in a variable named $Link1.
  
After that the second command in the example uses the **Set-CsAutoDiscoverConfiguration** cmdlet to remove the object stored in $Link1. To do this, the command uses the WebLinks parameter and the parameter value @{Remove=$Link1}.
  
```
$Link1 = Get-CsAutoDiscoverConfiguration  -Identity "site:Redmond" | Select-Object -ExpandProperty WebLinks | Where-Object {$_.Token -eq "Fabrikam"}

Set-CsAutoDiscoverConfiguration -Identity "site:Redmond" -WebLinks @{Remove=$Link1}
```

### EXAMPLE 3

Example 3 shows how you can replace an existing collection of Autodiscover URLs with, in this case, a single URL. To carry out this task, the first command in the example uses the **New-CsWebLink** cmdlet to create a new Autodiscover URL for http://LyncDiscover.contoso.com; the resulting URL is stored in a variable named $Link2. The second command then uses the **Set-CsAutoDiscoverConfiguration** cmdlet and the WebLinks parameter to remove any URLs previously assigned to the Redmond site and replace them with the URL for http://LyncDiscover.contoso.com. To do this, the command uses the Replace method instead of the Add or Remove method.
  
```
$Link2 = New-CsWebLink -Token "Contoso" -Href "http://LyncDiscover.contoso.com"

Set-CsAutoDiscoverConfiguration -Identity "site:Redmond" -WebLinks @{Replace=$Link2}
```

### EXAMPLE 4

The command shown in Example 4 removes all the Autodiscover URLs that have been assigned to the Redmond site. To do this, the command sets the WebLinks property to a null value. In turn, that deletes any URLs previously assigned to that property.
  
```
Set-CsAutoDiscoverConfiguration -Identity "site:Redmond" -WebLinks $Null
```

## Detailed Description

For client applications to make the most effective use of Skype for Business Server 2015 those applications need to know the location of key Skype for Business Server 2015 components. For example, authenticated users must be able to locate their home pool; after all, they can only be authenticated by that home pool. Likewise, unauthenticated users must be able to do such things as locate the URL used for joining a conference.
  
If all your users logged on from behind the organization's firewall discovering these locations would be a relatively simple task. However, this relatively simple task gets more and more complicated as users access the system from external locations using Lync Mobile.
  
This is especially true in split-domain scenarios, scenarios in which some of an organization's users have accounts on the on-premises version of Skype for Business Server 2015 while other users have accounts on Skype for Business Online. In cases such as this, user accounts might be located in different Active Directory forests. That can pose a problem: for example, if a US-based user logs on from Europe the system must be able to recognize his or her forest and then refer the logon request to the proper pool.
  
The Autodiscover Service was introduced in the cumulative update for Lync Server: November 2011 in order to address these issues. When a client application attempts to access Skype for Business Server 2015, the Autodiscover service parses the client SIP address and then redirects that request to the appropriate pool. Client applications connect to the Autodiscover service by sending an HTTP request to an Autodiscover URL; these URLs must be configured by administrators in order for the Autodiscover service to work. (Note that, in addition to configuring URLs, administrators must also create DNS records that correspond to these URLs.)
  
Autodiscover URLs are assigned to Autodiscover Service configuration settings. In turn, these settings can be applied to the global scope or to the site scope. When you install Skype for Business Server 2015 a global collection of settings will be created for you. (However, no Autodiscover URLs will be assigned to that collection.) If a single collection of Autodiscover settings will not fill your needs, then you can use the **New-CsAutoDiscoverConfiguration** cmdlet to create additional configuration settings at the site scope. From there, you can use the **Set-CsAutoDiscoverConfiguration** cmdlet to add or remove Autodiscover URLs from the global collection or from any site-scoped collection.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableCertificateProvisioningServiceUrl_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), the Certificate Provisioning Service URL is included in Autodiscover Service responses.  <br/> |
| _EnableCORS_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _ExternalSipClientAccessFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the server that is used for external client access.  <br/> |
| _ExternalSipClientAccessPort_ <br/> |Optional  <br/> |System.UInt32  <br/> |Port used for eternal client access.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of Autodiscover configuration settings to be modified. To modify to the global collection, use this syntax:  <br/>  `-Identity "global"` <br/> To modify a collection configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> If this parameter is not specified, then the **Set-CsAutoDiscoverConfiguration** cmdlet will automatically modify the global settings. <br/> |
| _Instance_ <br/> |Optional  <br/> |AutoDiscoverConfiguration object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WebLinks_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of Autodiscover URLs. These URLs must be created by using the **New-CsWebLink** cmdlet. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

The **Set-CsAutoDiscoverConfiguration** cmdlet accepts pipelined input of the Microsoft.Rtc.Management.WriteableConfig.Settings.AutoDiscoverConfiguration.AutoDiscoverConfiguration object.
  
## Return Types

None. The **Set-CsAutoDiscoverConfiguration** cmdlet modifies instances of the Microsoft.Rtc.Management.WriteableConfig.Settings.AutoDiscoverConfiguration.AutoDiscoverConfiguration object.
  

