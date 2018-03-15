---
title: "Merge-CsLegacyTopology"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 396d6c84-7b38-41ae-9273-665f76cdd9ea
description: "This cmdlet is reserved for Microsoft internal use only."
---

# Merge-CsLegacyTopology
 
This cmdlet is reserved for Microsoft internal use only. 
  
The **Merge-CsLegacyTopology** cmdlet enables you to migrate topology information from Microsoft Office Communications Server 2007 R2 or Microsoft Office Communications Server 2007 to Skype for Business Server 2015. This helps provide interoperability between Skype for Business Server 2015 and earlier versions of the software. This cmdlet was introduced in Lync Server 2010.
  
```
Merge-CsLegacyTopology -TopologyXmlFileName <String> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 merges topology information and trusted service entries from Communications Server 2007 R2 or Communications Server 2007 with a new installation of Skype for Business Server 2015. The required parameter TopologyXmlFileName is used to indicate the path to the output file generated when you run the **Merge-CsLegacyTopology** cmdlet.
  
```
Merge-CsLegacyTopology -TopologyXmlFileName C:\New_Topology.xml
```

### EXAMPLE 2

Example 2 is a variation of the command used in Example 1. In Example 2, however, the UserInputFileName parameter is included in order to merge Edge Server information into the topology. The parameter value C:\EdgeServers.xml points to a custom XML file containing Edge Server information for Office Communications Server.
  
```
Merge-CsLegacyTopology -TopologyXmlFileName C:\New_Topology.xml -UserInputFileName C:\EdgeServers.xml
```

## Detailed Description

The **Merge-CsLegacyTopology** cmdlet is the first tool to use when migrating from an earlier version of Office Communications Server (either Office Communications Server 2007 R2 or Office Communications Server 2007) to Skype for Business Server 2015. The **Merge-CsLegacyTopology** cmdlet is used to migrate trusted service entries and topology information for the following components: domains, user services, Registrar, Mediation Server, and Edge Server. In addition, the cmdlet migrates trusted service entries for the Conferencing Attendant application; Communicator Web Access; and conferencing directories. (A trusted service entry is an Active Directory record that represents a server trusted by Skype for Business Server 2015.) Merging the topology information enables users homed on Skype for Business Server 2015 to communicate with users homed on Communications Server 2007 or Communications Server 2007 R2.
  
Before you can run the **Merge-CsLegacyTopology** cmdlet you must first install the Windows Management Instrumentation (WMI) Backward Compatibility interfaces package; this application is installed by running OCSWMIBC.msi. (OCSWMIBC.msi can be found on the installation DVD in the Setup.) After installing the Compatibility interfaces package, the **Merge-CsLegacyTopology** cmdlet can then be called. The **Merge-CsLegacyTopology** cmdlet will use WMI to read legacy data from the earlier version of Office Communications Server; it will then take the retrieved data and create corresponding objects in Skype for Business Server 2015. For example, for each SIP domain found in your installation of Office Communications Server, a corresponding SIP domain will be created in your new installation of Skype for Business Server 2015.
  
After running the **Merge-CsLegacyTopology** cmdlet, you should then run the **Import-CsLegacyConfiguration** cmdlet and the **Import-CsLegacyConferenceDirectory** cmdlet.
  
The **Merge-CsLegacyTopology** cmdlet needs to be run at least twice: once at the start of a migration (in order to introduce the Communications Server 2007 or Communications Server 2007 R2 topology), and once at the end of migration, when the previous Office Communications Server environment has been decommissioned. You will also need to run the cmdlet any time you make a change to your legacy Office Communications Server environment. For example, if you add a Mediation Server to or decommission a pool from your Office Communications Server topology, you will need to re-run the **Merge-CsLegacyTopology** cmdlet in order to import the modified topology.
  
The **Import-CsLegacyConfiguration** cmdlet and the **Import-CsLegacyConferenceDirectory** cmdlet depend on values configured by the **Merge-CsLegacyTopology** cmdlet. That means that you might receive error messages from either the **Import-CsLegacyConfiguration** cmdlet or the **Import-CsLegacyConferenceDirectory** cmdlet that instruct you to run the **Merge-CsLegacyTopology** cmdlet as a possible solution to the problem that just occurred. If you do not re-run the **Merge-CsLegacyTopology** cmdlet, then additional errors can occur, especially if an item is removed from the Office Communications Server environment while it is still in use by Skype for Business Server 2015.
  
If you need to merge Edge Servers from a previous installation of Office Communications Server you must first create a custom XML file that contains your Edge Server; you must create the file yourself because Edge Server settings are not stored in Active Directory, and, as a result, cannot be retrieved by the **Merge-CsLegacyTopology** cmdlet. After you have created this XML file (see the Skype for Business Server 2015 Deployment Guide for information on how to create this file) you must include the path to that file and the UserInputFileName parameter when running the **Merge-CsLegacyTopology** cmdlet. If you do not do this no Edge Servers will be included in your merged topology.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Reserved_ <br/> |Required  <br/> |PS topology object  <br/> |Enables you to merge the topology using a topology object instead of a topology XML file.  <br/> |
| _TopologyXmlFileName_ <br/> |Required  <br/> |System.String  <br/> |Path to the output file to be created when the **Merge-CsLegacyTopology** cmdlet is run. Note that this file differs from the file specified using the Report parameter; the latter file is used for recording error information while the Topology XML file contains your newly created Skype for Business Server 2015 topology. This file will later be used to publish the new topology. <br/> If the specified file already exists, it will be overwritten when you run the **Merge-CsLegacyTopology** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\MergeTopology.html"` <br/> |
| _UserInputFileName_ <br/> |Optional  <br/> |System.String  <br/> |Path to the XML file used to import Edge Server data from an earlier version of Skype for Business Server 2015. This XML file (which you must create following the guidelines detailed in the Skype for Business Server 2015 Deployment Guide) is required because Edge Server settings are not stored in Active Directory Domain Services. If you do not need to import Edge Server information, then this parameter can be omitted.  <br/> If this parameter is not used, remote and external access features (including federation) might not function as expected in an environment running both Communications Server 2007 R2 or Communications Server 2007 R2and .  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Merge-CsLegacyTopology** cmdlet does not accept pipelined input.
  
## Return Types

The **Merge-CsLegacyTopology** cmdlet does not return any objects or values.
  
## See also

#### 

[Import-CsLegacyConfiguration](import-cslegacyconfiguration.md)
  
[Import-CsLegacyConferenceDirectory](import-cslegacyconferencedirectory.md)
  
[Move-CsLegacyUser](move-cslegacyuser.md)

