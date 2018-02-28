---
title: "New-CsNetworkBWAlternatePath"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9017378e-4583-42bc-9572-aa8e9571cfe3
description: "Creates new settings that define whether media can be routed to alternate paths through the Internet for bandwidth-constrained connections. This cmdlet was introduced in Lync Server 2010."
---

# New-CsNetworkBWAlternatePath
[]
Creates new settings that define whether media can be routed to alternate paths through the Internet for bandwidth-constrained connections. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsNetworkBWAlternatePath -AlternatePath <$true | $false> -BWPolicyModality <Audio | Video>

```

## Examples

### EXAMPLE 1

This example creates a new network bandwidth alternate path and assigns those settings to a newly created region. The first line in the example calls the **New-CsNetworkBWAlternatePath** cmdlet to create a new alternate path. An alternate path has only two properties: BWPolicyModality, which must be set to either audio or video (in this example, audio is used); and AlternatePath, which must be either True or False (in this example, True is used). We assign the output from this cmdlet, which is a reference to the alternate path object just created, to the variable $a.
  
In line 2 of this example we use this newly created alternate path in the creation of a new network region. To do this we call the **New-CsNetworkRegion** cmdlet, passing an Identity of NorthAmerica. We assign a value for the required parameter CentralSite (in this example the name of the central site for this region is Redmond-NA-MLS), and then we specify the BWAlternatePaths parameter, passing it the variable ($a) containing the alternate path object we just create.
  
```
$a = New-CsNetworkBWAlternatePath -BWPolicyModality "audio" -AlternatePath $true
New-CsNetworkRegion -Identity NorthAmerica -CentralSite Redmond-NA-MLS -BWAlternatePaths $a
```

## Detailed Description

Within a call admission control (CAC) configuration in Skype for Business Server 2015, there are two possible modalities: audio and video. Bandwidth limitations can be set on each of these modalities. When bandwidth limitations will prevent a call from completing, it may be possible for the call to take an alternate path through the Internet that will enable the call to be established. This cmdlet allows you to create the settings that define whether a call can be routed to an alternate path through the Internet based on modality. The settings apply per region within the CAC configuration.
  
This cmdlet does not immediately save the newly created settings. Instead, it creates the settings in memory. To apply these settings to a region within the network, you need to assign the output of the cmdlet to a variable, and then use that variable as a value to the BWAlternatePaths parameter of the **New-CsNetworkRegion** cmdlet or the **Set-CsNetworkRegion** cmdlet. Note that you can apply these settings directly by using the AudioAlternatePath and VideoAlternatePath parameters of the **New-CsNetworkRegion** cmdlet and the **Set-CsNetworkRegion** cmdlet, without having to call the **New-CsNetworkBWAlternatePath** cmdlet to create a new object.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AlternatePath_ <br/> |Required  <br/> |Boolean  <br/> |Set the parameter to True to allow calls made in the media of the modality specified in the BWPolicyModality parameter (either audio or video) to be routed through an alternate path if adequate bandwidth does not exist in the primary path.  <br/> |
| _BWPolicyModality_ <br/> |Required  <br/> |BWPolicyModality  <br/> |The modality to which the alternate path setting applies.  <br/> Valid values: audio, video  <br/> Full data type: Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyModality  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWAlternatePathType.
  
## See also

#### 

[New-CsNetworkRegion](new-csnetworkregion.md)
  
[Set-CsNetworkRegion](set-csnetworkregion.md)

