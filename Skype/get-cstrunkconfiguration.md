---
title: Get-CsTrunkConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 15951113-5f96-4f44-8cad-9ff97fb5dfd6
---


# Get-CsTrunkConfiguration
[]
Retrieves one or more trunk configurations, which describe the settings for a trunking peer entity such as a public switched telephone network (PSTN) gateway, IP-private branch exchange (PBX), or Session Border Controller (SBC) at the service provider. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Get-CsTrunkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

This example retrieves all trunk configurations for the Skype for Business Server 2015 deployment.
  
    
    

```

Get-CsTrunkConfiguration
```


### EXAMPLE 2

This example retrieves the trunk configuration with the Identity site:Redmond. Because identities are unique, this command will return at most one object.
  
    
    

```
Get-CsTrunkConfiguration -Identity site:Redmond
```


### EXAMPLE 3

Example 3 retrieves all trunk configurations defined at the site level. The **Get-CsTrunkConfiguration** cmdlet uses the Filter parameter to retrieve all trunk configurations with an Identity beginning with site:, meaning all trunk configurations defined at the site level.
  
    
    

```
Get-CsTrunkConfiguration -Filter site:*
```


## Detailed Description

Use this cmdlet to retrieve one or more trunking configurations applicable to PSTN gateway entities. Each configuration contains specific settings for a trunking peer entity such as a PSTN gateway, IP-PBX, or SBC at the service provider. These settings configure such things as whether media bypass is enabled on this trunk, whether real-time transport control protocol (RTCP) packets are sent under certain conditions, and whether to require secure real-time protocol (SRTP) encryption.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |This parameter accepts a wildcard string and returns all trunk configurations with identities matching that string. For example, a Filter value of site:* will return all trunk configurations defined at the site level.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the trunk configuration you want to retrieve. Trunk configurations can be defined at the Global scope, the Site scope, or at the Service scope for a PSTN Gateway service. For example, site:Redmond (for site) or PstnGateway:Redmond.litwareinc.com (for service).  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

This cmdlet returns an object of type Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration.
  
    
    

## See also


#### 


  
    
    
 [New-CsTrunkConfiguration](new-cstrunkconfiguration.md)
  
    
    
 [Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md)
  
    
    
 [Set-CsTrunkConfiguration](set-cstrunkconfiguration.md)
  
    
    
 [Test-CsTrunkConfiguration](test-cstrunkconfiguration.md)
