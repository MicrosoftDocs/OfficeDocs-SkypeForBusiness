---
title: Get-CsNetworkRegionLink
ms.prod: SKYPEFORBUSINESS
ms.assetid: dc5cb988-13e2-4af4-8b36-0aaa58ebf1c5
---


# Get-CsNetworkRegionLink
[]
Retrieves one or more links between network regions configured for call admission control (CAC). This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Get-CsNetworkRegionLink [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

Example 1 retrieves all network region links defined within a Skype for Business Server 2015 deployment.
  
    
    

```

Get-CsNetworkRegionLink
```


### EXAMPLE 2

Example 2 retrieves information about (at most) one network region link, the link with the Identity NA_EMEA.
  
    
    

```
Get-CsNetworkRegionLink -Identity NA_EMEA
```


### EXAMPLE 3

In this example we use the Filter parameter to retrieve all network region links with the string EMEA in the name (Identity) of the link. Notice the * characters, one before the string EMEA and one after. This means any character or characters can precede or follow the string; the string EMEA simply must be included in the Identity somewhere. This will retrieve links with names such as NA_EMEA, EMEA_APAC, and EMEA2_SA.
  
    
    

```
Get-CsNetworkRegionLink -Filter *EMEA*
```


### EXAMPLE 4

This example retrieves all network region links that include EMEA as one of the two regions being linked. The example begins by calling the **Get-CsNetworkRegionLink** cmdlet with no parameters, which will retrieve all region links. This collection of links is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet looks through each member of the collection one-by-one, checking the values of the NetworkRegionID1 and NetworkRegionID2 properties. If either of these properties is equal to EMEA--in other words if either NetworkRegionID1 is equal to (-eq) EMEA or (-or) NetworkRegionID2 is equal to (-eq) EMEA--then we want to keep that item in the collection and display it.
  
    
    

```
Get-CsNetworkRegionLink | Where-Object {$_.NetworkRegionID1 -eq "EMEA" -or $_.NetworkRegionID2 -eq "EMEA"}
```


## Detailed Description

Regions within a network are linked through physical WAN connectivity. This cmdlet retrieves one or more region links that are defined within the network configuration settings for a Skype for Business Server 2015 deployment.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Accepts a wildcard string that is used to retrieve network links based on matching the value of the Identity to the wildcard string.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique identifier of the network region link you want to retrieve. Network region links are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that link. (Note that this value is the same as the NetworkRegionLinkID.)  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the network region link information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

Retrieves one or more objects of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.
  
    
    

## See also


#### 


  
    
    
 [New-CsNetworkRegionLink](new-csnetworkregionlink.md)
  
    
    
 [Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)
  
    
    
 [Set-CsNetworkRegionLink](set-csnetworkregionlink.md)
