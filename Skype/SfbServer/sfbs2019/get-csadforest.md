---
title: "Get-CsAdForest"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f063df2f-fdb2-4599-bfb0-fb4ba3584e3b
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsAdForest
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Returns information indicating whether your Active Directory forest has been correctly configured to allow for the installation of Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsAdForest [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-RootDomainController <Fqdn>] [-SkipPrepareCheck <$true | $false>]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 returns information indicating whether your Active Directory forest has been correctly configured to allow for the installation of Lync Server.
  
```
Get-CsAdForest
```

### EXAMPLE 2

In Example 2, forest state information is returned and the forest readiness is displayed on the screen. In addition, detailed information about the steps taken to determine the forest state is written to a file named C:\Logs\ForestState.html. This file includes a detailed list of all the Active Directory groups and Active Directory containers where permissions were verified.
  
```
Get-CsAdForest -Report C:\Logs\ForestState.html
```

## Detailed Description
<a name="sectionSection1"> </a>

Before you can install Lync Server, you must make a number of forest-level changes to Active Directory Domain Services. This includes creating display specifiers and objects specific to Lync Server, creating the universal security groups that are needed to manage Lync Server, and granting global settings object access permissions to these groups. The **Get-CsAdForest** cmdlet returns a single value that tells you whether or not Lync Server can be installed in a forest. If the **Get-CsAdForest** cmdlet returns the value LC_FORESTSETTINGS_STATE_READY then you can install Lync Server in the forest. If the cmdlet returns LC_FORESTSETTINGS_STATE_NOT_READY then you will need to correctly prepare the forest before trying to install Lync Server. 
  
The **Get-CsAdForest** cmdlet runs as part of the Setup Wizard; if the Wizard determines that the forest is not correctly prepared, then you will receive an error message and Setup will stop. However, you can also run the **Get-CsAdForest** cmdlet independently of the Setup Wizard in order to verify the forest status before you try to install Lync Server. 
  
The **Get-CsAdForest** cmdlet performs the same function as the following Microsoft Office Communications Server 2007 R2 command: 
  
Lcscmd.exe /forest /action:CheckForestPrepState
  
Who can run this cmdlet: By default, anyone who has read permissions to Active Directory can run the **Get-CsAdForest** cmdlet locally. Typically all domain members have this permission. 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsAdForest"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the **Get-CsAdForest** cmdlet on a computer with an account in your domain.  <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in AD DS, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\ForestPrep.html"  <br/> |
| _RootDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of the root domain controller, used to create trust paths for clients that need to access resources in domains other than their own.  <br/> |
| _SkipPrepareCheck_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True), causes Get-CsAdForest to run without first doing its initial preparation checks.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

The **Get-CsAdForest** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment.LcForestSettingsState object. 
  

