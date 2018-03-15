---
title: "Export-CsLisConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 714bd67e-4cd6-4066-a065-59f7e079b6ad
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Export-CsLisConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Exports an Enterprise Voice Enhanced 9-1-1 (E9-1-1) configuration to a file in compressed format for backup purposes. This cmdlet was introduced in Lync Server 2010.
  
```
Export-CsLisConfiguration -FileName <String> <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example exports the entire E9-1-1 configuration from the Location Information Server (LIS) to the backup file named E911Config.bak.
  
```
Export-CsLisConfiguration -FileName C:\E911Config.bak
```

### EXAMPLE 2

In this example, the LIS configuration is stored as an array of bytes in a variable, $lisconfig.
  
```
$lisconfig = Export-CsLisConfiguration -AsBytes
```

### EXAMPLE 3

Example 3 is a more complete version of Example 2. The first line is the same, we call the **Export-CsLisConfiguration** cmdlet with the AsBytes parameter to store the LIS configuration as an array of bytes in the variable $lisconfig. The rest of this example shows how to save that configuration to a file and then import it back into the location configuration database. 
  
In line 2 we pipe the contents of $lisconfig, which is the byte array representing the LIS configuration, to the Windows PowerShell **Set-Content** cmdlet. We assign values to two parameters of the **Set-Content** cmdet: Path and Encoding. We assign the full path and file name of the file to which we want to save the configuration to the Path parameter. We use the Encoding parameter with a value of byte to ensure the configuration is stored as an array of bytes. 
  
Finally, in line 3 we import the configuration back into the location configuration database. First we call the **Get-Content** cmdlet to retrieve the contents from the file. We pass a value of 0 to the ReadCount property, which tells the **Get-Content** cmdlet to read all the contents of the file at once rather than one line at a time. We again use the Encoding parameter with a value of byte to specify what type of data we're reading from the file. Finally we pass the file name to the Path parameter. The contents of the file that we read with the **Get-Content** cmdlet are piped to the **Import-CsLisConfiguration** cmdlet, which imports the saved configuration into the location database. 
  
```
$lisconfig = Export-CsLisConfiguration -AsBytes
$lisconfig | Set-Content -Path C:\E911Config.bak -Encoding byte
Get-Content -ReadCount 0 -Encoding byte -Path C:\E911Config.bak  | Import-CsLisConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

Implementing E9-1-1 in an organization can, depending on the size of the organization, involve mapping thousands of subnets, ports, switches, and wireless access points (WAPs) to locations. An E9-1-1 configuration also includes information about web services provided by the E9-1-1 Network Routing Provider, and about locations and civic addresses and whether or not they've been validated. Given the volume of information and settings required to implement E9-1-1, it's recommended that you regularly back up the entire configuration. You can use this cmdlet to back up the E9-1-1 configuration to a file, which will save the entire configuration in compressed format. To recover the configuration, call the **Import-CsLisConfiguration** cmdlet. 
  
This cmdlet creates a new backup file; it will not overwrite an existing file. That means the file name that is specified in the call to this cmdlet cannot be the name of an existing file.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Export-CsLisConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Export-CsLisConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FileName_ <br/> |Required  <br/> |System.String  <br/> |The path and file name of the file to which you want to save the configuration. This cannot be the name of an existing file.  <br/> If you supply a value to the AsBytes parameter, you cannot supply a value to the FileName parameter. If you're accessing this cmdlet remotely, you must use AsBytes rather than FileName.  <br/> |
| _AsBytes_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Returns the configuration as a byte array. The output of the command should be assigned to a variable for later import. (If you don't assign the output to a variable, the byte array representing the configuration will scroll down your Lync Server Management Shell window.) You cannot specify both the AsBytes parameter and the FileName parameter; you can use only one or the other for each call to this cmdlet.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Returns a byte array (Byte[]) when the AsBytes parameter is used.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Import-CsLisConfiguration](import-cslisconfiguration.md)
  
[Debug-CsLisConfiguration](debug-cslisconfiguration.md)
  
[Publish-CsLisConfiguration](publish-cslisconfiguration.md)
  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)
  
[Test-CsLisConfiguration](test-cslisconfiguration.md)

