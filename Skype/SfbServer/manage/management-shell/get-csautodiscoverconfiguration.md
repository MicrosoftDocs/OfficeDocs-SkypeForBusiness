---
title: "Get-CsAutodiscoverConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 221d26d6-0f77-4873-8872-d600913eb98b
description: "Returns information about the Autodiscover configuration settings currently in use in an organization. The Autodiscover service provides a way for client applications to locate key resources such as a user's home pool or the URL for joining a dial-in conference. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011."
---

# Get-CsAutodiscoverConfiguration
[]
Returns information about the Autodiscover configuration settings currently in use in an organization. The Autodiscover service provides a way for client applications to locate key resources such as a user's home pool or the URL for joining a dial-in conference. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
Get-CsAutodiscoverConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns all the Autodiscover configuration settings currently in use in the organization.
  
```
Get-CsAutoDiscoverConfiguration
```

### EXAMPLE 2

In Example 2, only one collection of Autodiscover configuration settings are returned: the global collection.
  
```
Get-CsAutoDiscoverConfiguration -Identity "global"
```

### EXAMPLE 3

The command shown in Example 3 returns all the Autodiscover configuration settings assigned to the site scope. To do this, the Filter parameter is included, along with the filter value "site:\*"; that filter value ensures that the only settings returned are those that have an Identity that begins with the string value "site:". By definition, any settings with an Identity beginning with "site:" are settings configured at the site scope.
  
```
Get-CsAutoDiscoverConfiguration -Filter "site:*"
```

### EXAMPLE 4

The command shown in Example 4 returns all the Autodiscover configuration settings that include an Autodiscover URL for fabrikam.com. To carry out this task, the command first uses the **Get-CsAutoDiscoverConfiguration** cmdlet to return a collection of all the Autodiscover settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the WebLinks property includes the string value "fabrikam.com"
  
```
Get-CsAutoDiscoverConfiguration | Where-Object {$_.WebLinks -like "*fabrikam.com"}
```

## Detailed Description

For client applications to make the most effective use of Skype for Business Server 2015 those applications need to know the location of key Skype for Business Server 2015 components. For example, authenticated users must be able to locate their home pool; after all, they can only be authenticated by that home pool. Likewise, unauthenticated users must be able to do such things as locate the URL used for joining a conference.
  
If all your users logged on from behind the organization's firewall discovering these locations would be a relatively simple task. However, this relatively simple task gets more and more complicated as users access the system from external.
  
This is especially true in split-domain scenarios, scenarios in which some of an organization's users have accounts on the on-premises version of Skype for Business Server 2015 while other users have accounts on Skype for Business Online. In cases such as this, user accounts might be located in different Active Directory forests. That can pose a problem: for example, if a US-based user logs on from Europe the system must be able to recognize his or her forest and then refer the logon request to the proper pool.
  
The Autodiscover service was introduced in the cumulative update for Lync Server: November 2011 in order to address these issues. When a client application attempts to access Skype for Business Server 2015, the Autodiscover service parses the client SIP address and then redirects that request to the appropriate pool. Client applications connect to the Autodiscover service by sending an HTTP request to an Autodiscover URL; these URLs must be configured by administrators in order for the Autodiscover service to work. (Note that, in addition to configuring URLs, administrators must also create DNS records that correspond to these URLs.)
  
Autodiscover URLs are assigned to Autodiscover configuration settings; in turn, these settings can be applied to the global scope or to the site scope. The **Get-CsAutoDiscoverConfiguration** cmdlet provides a way to return information about the Autodiscover settings (and Autodiscover URLs) currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when specifying the Identity of the Autodiscover configuration settings to be returned. For example, this syntax returns all the settings configured at the site scope:  <br/>  `-Filter "site:*"` <br/> Note that you cannot use both the Identity and the Filter parameters in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of Autodiscover configuration settings to be retrieved. To retrieve the global settings, use this syntax:  <br/>  `-Identity "global"` <br/> To retrieve settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> If this parameter is not included, then the **Get-CsAutoDiscoverConfiguration** cmdlet will return all the Autodiscover configuration settings currently in use in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the Autodiscover configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

The **Get-CsAutoDiscoverConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsAutoDiscoverConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WriteableConfig.Settings.AutoDiscoverConfiguration.AutoDiscoverConfiguration object.
  

