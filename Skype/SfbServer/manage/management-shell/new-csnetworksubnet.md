---
title: "New-CsNetworkSubnet"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 15af44bd-d798-435c-9c27-df47ab475023
description: "Creates a new network subnet. This cmdlet was introduced in Lync Server 2010."
---

# New-CsNetworkSubnet
 
Creates a new network subnet. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsNetworkSubnet -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example demonstrates how to create a new subnet object that represents the subnet 172.11.15.0/24. The Identity of the subnet is set to 172.11.15.0. This value will automatically be assigned as the SubnetID. A subnet must have mask bits defined. That is done by supplying a value--in this case 24--to the MaskBits parameter. Finally, the site ID Vancouver is passed to the NetworkSiteID parameter to associate this subnet with that site.
  
```
New-CsNetworkSubnet -Identity 172.11.15.0 -MaskBits 24 -NetworkSiteID Vancouver
```

### EXAMPLE 2

Example 2 reads from a CSV file to create a series of subnets. The CSV file in this example looks something like this:
  
Identity, Mask, SiteID
  
172.11.12.0, 24, Redmond
  
172.11.13.0, 24, Chicago
  
172.11.14.0, 25, Vancouver
  
172.11.15.0, 31, Paris
  
...
  
The example starts by calling the **Import-CSV** cmdlet, passing it the path to a CSV file. This cmdlet will read the contents of that file into memory. Those file contents are then piped to the foreach function. The foreach function iterates through the contents one line at a time. As you can see from the example file, the first line is a list of headings that define the rest of the contents; the foreach function will use these headings to access the comma-separated values by name.
  
Inside the foreach statement, the **New-CsNetworkSubnet** cmdlet is called. As foreach iterates through each line of the file contents, that line is passed as the values for the **New-CsNetworkSubnet** cmdlet parameters. For example, the first time through the foreach statement, the **New-CsNetworkSubnet** cmdlet will create a subnet with the Identity 172.11.12.0: this is the value in the Identity position in the first comma-separated line of values. (The $_ indicates the current value in the foreach loop.) The Mask value (24) is then passed to the MaskBits parameter, and the SiteID value (Redmond) from the file is passed to the NetworkSiteID parameter.
  
This process continues until all lines in the file have been read, and their values used to create new subnets.
  
```
Import-CSV C:\subnet.csv | foreach {New-CsNetworkSubnet -Identity $_.Identity -MaskBits $_.Mask -NetworkSiteID $_.SiteID}
```

## Detailed Description

Each subnet must be associated with a network site for the purposes of determining the geographic location of the host belonging to this subnet. Use this cmdlet to create a new subnet, and at the same time (optionally) assign it to a network site.
  
In most deployments of Skype for Business Server 2015 where call admission control (CAC) is implemented, there will typically be a large number of subnets. Because of this, it's often best to call the **New-CsNetworkSubnet** cmdlet in conjunction with the **Import-CSV** cmdlet. By using these cmdlets together, you can read in subnet settings from a comma-separated values (CSV) file and create multiple subnets at once. For more details, see the Examples section for this cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique subnet ID of the subnet being created. This must be an IP address (such as 174.11.12.0), and it must be the first address in the IP address range defined by the subnet.  <br/> |
| _MaskBits_ <br/> |Required  <br/> |System.Int32  <br/> |The bitmask to be applied to the subnet being created.  <br/> Valid values: 1 through 32  <br/> |
| _SubnetID_ <br/> |Required  <br/> |System.String  <br/> |This is the same value as the Identity. You must specify either an Identity or a SubnetID, but you cannot specify both. Whatever value you supply to one will automatically be applied to the other.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A description of the subnet being created.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _NetworkSiteID_ <br/> |Optional  <br/> |System.String  <br/> |The site ID of the site to which this subnet belongs. You can retrieve site IDs for your deployment by calling the **Get-CsNetworkSite** cmdlet. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType.
  
## See also

#### 

[Remove-CsNetworkSubnet](remove-csnetworksubnet.md)
  
[Set-CsNetworkSubnet](set-csnetworksubnet.md)
  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)
  
[Get-CsNetworkSite](get-csnetworksite.md)

