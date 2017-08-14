---
title: Get-CsStorageServiceConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: b3a1e270-bab1-4233-a5f6-d97b03b03c48
---


# Get-CsStorageServiceConfiguration
[]
Returns information about existing instances of the Skype for Business Server 2015 Storage Service. The storage service provides a common infrastructure that enables Skype for Business Server 2015 components to use Exchange as a back-end data store.
  
    
    

This cmdlet was introduced in Skype for Business Server 2015.
```

Get-CsStorageServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 returns information about all the storage service configuration settings in use in your organization.
  
    
    

```

Get-CsStorageServiceConfiguration
```


### Example 2

In Example 2, information is returned for a single collection of storage service configuration settings: the collection of settings applied to the Redmond site.
  
    
    

```
Get-CsStorageServiceConfiguration -Identity "site:Redmond"
```


### Example 3

Example 3 returns information for all the storage service configuration settings applied at the service scope. To do this, the command uses the Filter parameter and the filter value "service:*". That filter value limits returned data to collections that have an Identity that begins with the string value "service:".
  
    
    

```
Get-CsStorageServiceConfiguration -Filter "service:*"
```


## Detailed Description
<a name="Examples"> </a>

The Skype for Business Server 2015 Storage Service enables Skype for Business Server 2015 components (such as archiving) to use Exchange as a back-end data store. This helps to reduce operating costs; for example, you do not need to have separate storage solutions for Exchange archiving and for Skype for Business Server 2015 archiving. The Storage Service also enables Skype for Business Server 2015 to leverage the heavy investment that has been made in Exchange archiving and storage, and prevents administrators from having to use multiple tools to retrieve archived data.
  
    
    
Separate instances of the Skype for Business Server 2015 Storage Service can be configured at the global, site, and service scope (for the Registrar service only). By default, Skype for Business Server 2015 provides you with a single, global collection of Storage Service configuration settings. However, administrators have the option of creating custom setting collections by using the **New-CsStorageServiceConfiguration** cmdlet. Information about all of these Storage Service settings can be returned by using the **Get-CsStorageServiceConfiguration** cmdlet.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsStorageServiceConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="Examples"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcards when retrieving one or more collections of storage service configuration settings. For example, to return all the settings configured at the site scope, use this syntax:  <br/>  `-Filter "site:*"` <br/> To return all the settings configured at the service scope, use this syntax:  <br/>  `-Filter "service:*"` <br/> Note that you cannot use both the Filter parameter and the Identity parameter in the same command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the storage service configuration settings to be returned. Storage service configuration settings can be applied to the global, site, or service scope (for the Registrar service only). To return a complete collection of storage service configuration settings, omit the Identity parameter altogether:  <br/>  `Get-CsStorageServiceConfiguration` <br/> Alternatively, you can use the Identity parameter to retrieve information for a specific collection of storage service configuration settings. To return just the global settings, use this syntax:  <br/>  `-Identity "global"` <br/> To return settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To return settings at the service level, use syntax similar to this:  <br/>  `-Identity "service:Registrr:atl-cs-001.litwareinc.com"` <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the storage service configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="Examples"> </a>

None. The **Get-CsStorageServiceConfiguration** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="Examples"> </a>

The **Get-CsStorageServiceConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.StorageService.StorageServiceSettings object.
  
    
    

## See also
<a name="Examples"> </a>


#### 


  
    
    
 [New-CsStorageServiceConfiguration](new-csstorageserviceconfiguration.md)
  
    
    
 [Remove-CsStorageServiceConfiguration](remove-csstorageserviceconfiguration.md)
  
    
    
 [Set-CsStorageServiceConfiguration](set-csstorageserviceconfiguration.md)
