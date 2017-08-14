---
title: Get-CsVideoInteropServerSyntheticTransactionConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 306a33ee-9d18-4f34-b804-815d7ab357f4
---


# Get-CsVideoInteropServerSyntheticTransactionConfiguration
[]
Use the **Get-CsVideoInteropServerSyntheticTransactionConfiguration** cmdlet to retrieve Video Interop Server (VIS) synthetic transaction configurations.
  
    
    


```

Get-CsVideoInteropServerSyntheticTransactionConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

This example returns the Video Interop Server synthetic transaction configuration for the Redmond site.
  
    
    

```

Get-CsVideoInteropServerSyntheticTransactionConfiguration -Identity "site:Redmond"
```


## Detailed Description
<a name="DetailedDescription"> </a>

To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
    
    

```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```


## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return one or more collections of VIS configuration settings. For example, to return all the settings that have been configured at the site scope use the following syntax:  <br/>  `-Filter "site:*"` <br/> The  _Filter_ and the _Identity_ parameters are mutually exclusive. <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The Video Interop Server (VIS) synthetic transaction configuration to be retrieved.  <br/> Wildcard characters such as the asterisk (*) cannot be used with the  _Identity_ parameter. To do a wildcard search for policies, use the _Filter_ parameter instead. <br/> If neither the  _Identity_ nor the _Filter_ parameter is specified, then the **Get-CsVideoInteropServerConfiguration** cmdlet returns all the VIS synthetic transaction configurations in your organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the VIS configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

Returns an object array, or single instance (if used with the  _Identity_ parameter) of the `VideoInteropServerSyntheticTransactionConfiguration` object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Set-CsVideoInteropServerSyntheticTransactionConfiguration](set-csvideointeropserversynthetictransactionconfiguration.md)
  
    
    
 [New-CsVideoInteropServerSyntheticTransactionConfiguration](new-csvideointeropserversynthetictransactionconfiguration.md)
  
    
    
 [Remove-CsVideoInteropServerSyntheticTransactionConfiguration](remove-csvideointeropserversynthetictransactionconfiguration.md)
  
    
    
 [Test-CsP2PVideoInteropServerSipTrunkAV](test-csp2pvideointeropserversiptrunkav.md)
