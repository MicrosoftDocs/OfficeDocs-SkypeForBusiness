---
title: "Get-CsTenantHybridConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4b2e6781-8f46-4ba3-be76-3a95460e3132
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsTenantHybridConfiguration
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Returns values for the hybrid configuration settings that enable users homed on Skype for Business Online to have access to Enterprise Voice features such as media bypass, Enhanced 9-1-1, and call parking. A hybrid scenario (also known as a split-domain scenario) is a Lync Server deployment in which some users have accounts homed on-premises while other users have accounts homed on Skype for Business Online.
  
The Get-CsTenantHybridConfiguration cmdlet can only be used with Skype for Business Online.
  
```
Get-CsTenantHybridConfiguration [[-Identity] <XdsIdentity>] [-Tenant <guid>] [-LocalStore] [<CommonParameters>]Get-CsTenantHybridConfiguration [-Tenant <guid>] [-Filter <string>] [-LocalStore] [<CommonParameters>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns the property values for the global collection of tenant hybrid configuration settings.
  
```
Get-CsTenantHybridConfiguration -Identity "Global"
```

### Example 2

In Example 2, property values are returned for the custom tenant hybrid configuration settings applied to the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354".
  
```
Get-CsTenantHybridConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"
```

### Example 3

Example 3 returns tenant hybrid configuration information for all of your available tenants. To do this, the command first calls the **Get-CsTenant** cmdlet to return a collection of all of these tenants. This collection is then piped to the **ForEach-Object** cmdlet, which takes each tenant in the collection and, one-by-one, performs two tasks. First, the cmdlet prints out the Active Directory display name for the tenant; this ensures that each collection of settings can be readily identified. After that, the **ForEach-Object** cmdlet runs the **Get-CsTenantHybridConfiguration** cmdlet to return the tenant hybrid configuration settings for the tenant in question. 
  
```
Get-CsTenant | ForEach-Object {$_.DisplayName; Get-CsTenantHybridConfiguration -Tenant $_.TenantId}
```

## Detailed Description
<a name="DetailedDescription"> </a>

In a hybrid or "split domain" deployment, an organization has some users who have accounts homed on Skype for Business Online while simultaneously having other users who have accounts homed on the on-premises version of Lync Server. By default, users homed on Skype for Business Online do not have access to the complete range of capabilities offered by Enterprise Voice; that's because the Skype for Business Online servers do not have direct access to Lync Server deployment and network configuration information. Among other things, Skype for Business Online users do not have default access to such things as:
  
- Enhanced 9-1-1, the Lync Server service used for making emergency phone calls.
    
- Call parking, the Lync Server service which enables users to place a call on hold phone A, then retrieve that call from phone B.
    
- Media bypass, which enables calls to and from the public switched telephone network (PSTN) to bypass the Mediation server, helping to minimize transcoding and network latency.
    
- PSTN conferencing dial-in and dial-out, which enables users to participate in the audio portion of an online conference by using any PSTN telephone or mobile device.
    
- The Response Group application, which provides a way for you to automatically route phone calls to entities such as a help desk or customer support line. By default, Lync Server users cannot function as Response Group agents.
    
In order to provide Skype for Business Online users with access to these Enterprise Voice capabilities, administrators need to assign the appropriate values to hybrid configuration settings such as the internal and external Web service URLs and the fully qualified domain name of the organization's Access Edge server. These values, which can only be configured by using the **Set-CsTenantHybridConfiguration** cmdlet, provide the Skype for Business Online servers with the information needed to make use of these advanced Enterprise Voice features. 
  
You can return information about the tenant hybrid configuration settings currently in use in your organization by using the **Get-CsTenantHybridConfiguration** cmdlet. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a collection of tenant hybrid configuration settings. Because you are limited to a single, global collection of hybrid configuration settings there is no need to use the Filter parameter. However, this is valid syntax for the **Get-CsTenantHybridConfiguration** cmdlet:  <br/> Get-CsTenantHybridConfiguration -Filter "g\*"  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique Identity of the tenant hybrid configuration settings to be returned. Because you are limited to a single, global collection of hybrid configuration settings, the only collection that can be returned by using the Identity parameter is the global collection:  <br/> -Identity global  <br/> To modify the settings for an individual tenant, use the Tenant parameter instead of the Identity parameter.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the tenant hybrid configuration data from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the tenant account whose hybrid configuration settings are being returned. For example:  <br/> -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"  <br/> You can return the tenant ID for each of your tenants by running this command:  <br/> Get-CsTenant | Select-Object DisplayName, TenantID  <br/> If you are using a remote session of Windows PowerShell and are connected only to Skype for Business Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsTenantHybridConfiguration** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsTenantHybridConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.HybridConfiguration.TenantHybridConfiguration object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsTenantHybridConfiguration](set-cstenanthybridconfiguration.md)

