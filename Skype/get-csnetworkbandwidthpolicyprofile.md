---
title: Get-CsNetworkBandwidthPolicyProfile
ms.prod: SKYPEFORBUSINESS
ms.assetid: 31784852-0cf4-4114-bf92-5eef6f346c47
---


# Get-CsNetworkBandwidthPolicyProfile
[]
Retrieves one or more network bandwidth policy profiles. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Get-CsNetworkBandwidthPolicyProfile [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

Calling the **Get-CsNetworkBandwidthPolicyProfile** cmdlet without any parameters will retrieve all bandwidth policy profiles defined within the Skype for Business Server 2015 deployment.
  
    
    

```

Get-CsNetworkBandwidthPolicyProfile
```


### EXAMPLE 2

This example retrieves the bandwidth policy profile with the Identity LowBWProfile. Because identities must be unique this will return, at most, one profile.
  
    
    

```
Get-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile
```


### EXAMPLE 3

In this example we use the Filter parameter to specify one or more profiles to retrieve based on a wildcard string. We've used the string *50MB*, which indicates that we want to retrieve all the bandwidth policy profiles with Identity values that contain the string 50MB anywhere within the value. For example, this would retrieve profiles with identities such as "BW profile for 50MB links", "50MB audio limit", and "video limits of 50MB".
  
    
    

```
Get-CsNetworkBandwidthPolicyProfile -Filter *50MB*
```


## Detailed Description

As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. (In Skype for Business Server 2015, only audio and video modalities can be assigned bandwidth limitations.) This cmdlet retrieves one or more container profiles for these policies.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |A string containing wildcards that is used to retrieve bandwidth policy profiles that have Identity values that match the wildcard pattern.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A string value that uniquely identifies the bandwidth policy profile you want to retrieve. Specifying an Identity will retrieve, at most, one profile.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the network bandwidth policy profile from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

Returns an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType.
  
    
    

## See also


#### 


  
    
    
 [New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)
  
    
    
 [Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)
  
    
    
 [Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)
