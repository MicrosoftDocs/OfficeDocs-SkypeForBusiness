---
title: "Set-CsTenantHybridConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 805ac9ee-df40-40e1-baaa-adffb6bd8cf6
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsTenantHybridConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Used in a hybrid scenario to give users homed on Skype for Business Online access to on-premises Enterprise Voice features such as media bypass, Enhanced 9-1-1, and call parking. A hybrid scenario (also known as a split-domain scenario) is a Lync Server deployment in which some users have accounts homed on-premises while other users have accounts homed on Skype for Business Online.
  
This cmdlet can only be used with Skype for Business Online.
  
```
Set-CsTenantHybridConfiguration [[-Identity] <XdsIdentity>] [-Tenant <guid>] [-PeerDestination <string>] [-HybridConfigServiceInternalUrl <string>] [-HybridConfigServiceExternalUrl <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]Set-CsTenantHybridConfiguration [-Tenant <guid>] [-PeerDestination <string>][-HybridConfigServiceInternalUrl <string>] [-HybridConfigServiceExternalUrl <string>] [-Instance <psobject>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 sets the internal service URL for the global collection of tenant hybrid configuration settings. To configure a global setting, include the Identity parameter along with the parameter value "global".
  
```
Set-CsTenantHybridConfiguration -Identity "global" - HybridConfigServiceInternalUrl "https://internal.litwareinc.com"
```

### Example 2

In Example 2, the internal service URL is configured for a specific tenant; in this example, the tenant that has the TenantID "bf19b7db-6960-41e5-a139-2aa373474354". When a property value is explicitly assigned to an individual tenant, the tenant will be governed by their individual tenant hybrid configuration settings instead of the global settings.
  
```
Set-CsTenantHybridConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" HybridConfigServiceInternalUrl "https://internal.litwareinc.com"
```

### Example 3

The command shown in Example 3 configures the internal service URL for all of your organization's tenants. To do this, the command first uses the **Get-CsTenant** cmdlet to return a collection of all the available tenants; that collection is then piped to the **ForEach-Object** cmdlet. In turn, the **ForEach-Object** cmdlet runs the **Set-CsTenantHybridConfiguration** cmdlet against each tenant in the collection, setting the internal service URL for each of those tenants to "https://internal.litwareinc.com". 
  
```
Get-CsTenant | ForEach-Object {Set-CsTenantHybridConfiguration -Tenant $_.TenantID -HybridConfigServiceInternalUrl "https://internal.litwareinc.com"}
```

## Detailed Description
<a name="DetailedDescription"> </a>

In a hybrid or "split domain" deployment, an organization has some users who have accounts homed on Skype for Business Online while simultaneously having other users who have accounts homed on Lync Server. By default, users homed on Skype for Business Online do not have access to the complete range of capabilities offered by Enterprise Voice; that's because the Skype for Business Online servers do not have direct access to on-premises Lync Server deployment and network configuration information. Among other things, Skype for Business Online users do not have default access to such things as:
  
- Enhanced 9-1-1, the Lync Server service used for making emergency phone calls.
    
- Call parking, the Lync Server service which enables users to place a call on hold phone A, then retrieve that call from phone B.
    
- Media bypass, which enables calls to and from the public switched telephone network (PSTN) to bypass the Mediation server, helping to minimize transcoding and network latency.
    
- PSTN conferencing dial-in and dial-out, which enables users to participate in the audio portion of an online conference by using any PSTN telephone or mobile device.
    
- The Response Group application, which provides a way for you to automatically route phone calls to entities such as a help desk or customer support line. By default, Skype for Business Online users cannot function as Response Group agents.
    
In order to provide Skype for Business Online users with access to these Enterprise Voice capabilities, administrators need to assign the appropriate values to hybrid configuration settings such as the internal and external Web service URLs and the fully qualified domain name of the organization's Access Edge server. These values, which can only be configured by using the **Set-CsTenantHybridConfiguration** cmdlet, provide the Skype for Business Online servers with the information needed to make use of these advanced Enterprise Voice features. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> ||System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _HybridConfigServiceExternalUrl_ <br/> |Optional  <br/> |System.String  <br/> |External Web service URL.  <br/> |
| _HybridConfigServiceInternalUrl_ <br/> |Optional  <br/> |System.String  <br/> |Internal Web service URL.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the tenant hybrid configuration settings to be modified. Because you are limited to a single, global collection of hybrid configuration settings, the only collection that can be modified by using the Identity parameter is the global collection:  <br/> -Identity global  <br/> To modify the settings for an individual tenant, use the Tenant parameter instead of the Identity parameter.  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _PeerDestination_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name of your on-premises Access Edge server.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the tenant account whose hybrid configuration settings are being modified. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> If you are using a remote session of Windows PowerShell and are connected only to Skype for Business Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Set-CsTenantHybridConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsTenantHybridConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.HybridConfiguration.TenantHybridConfiguration object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsTenantHybridConfiguration](get-cstenanthybridconfiguration.md)

