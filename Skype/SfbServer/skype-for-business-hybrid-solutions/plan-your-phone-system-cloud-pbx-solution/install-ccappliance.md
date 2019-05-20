---
title: "Install-CcAppliance"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 385453cd-3a96-4837-8bb4-513aa97a256b
description: "The Install-CcAppliance cmdlet installs the Skype for Business Cloud Connector Edition appliance—including the AD, Central Management Store, Mediation Server, and Edge Server virtual machines—on the host server."
---

# Install-CcAppliance
 
The Install-CcAppliance cmdlet installs the Skype for Business Cloud Connector Edition appliance—including the AD, Central Management Store, Mediation Server, and Edge Server virtual machines—on the host server. 
  
```
Install-CcAppliance [-Steps <array>] [-SkipExistingObjects] [-Upgrade] [-UpdateAllCredentials] [<CommonParameters>]
Install-CcAppliance [-Steps <array>] [-PrepareOnly]  [<CommonParameters>]
Install-CcAppliance [-ShowStepsOnly]  [<CommonParameters>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example installs a new Cloud Connector appliance on the host server:
  
```
Install-CcAppliance
```

### Example 2

The following example upgrades Cloud Connector to the latest version:
  
```
Install-CcAppliance -Upgrade
```

### Example 3

The following example removes all Cloud Connector credentials cached on the host server, prompts the user to specify all credential information again, and then installs Cloud Connector:
  
```
Install-CcAppliance -UpdateAllCredentials
```

### Example 4

The following example displays all deployment steps in the PowerShell console:
  
```
Install-CcAppliance -ShowStepsOnly
```

The -ShowStepsOnly parameter is for troubleshooting only.
  
### Example 5

The following example generates configuration files for each deployment step on the host server. Configuration files are saved to the \<ApplianceRoot\>\Instances\\<Version\>-default\ExportedConfig folder on the host server:
  
```
Install-CcAppliance -PrepareOnly
```

To determine the appliance root, run the Get-CcApplianceDirectory cmdlet. 
  
### Example 6

In the following example, Cloud Connector runs deployment steps 1, 2, and 3 to create virtual switches, create an AD virtual machine, and install the domain service on the AD server. It skips the step if the step has already been executed:
  
```
Install-CcAppliance -Steps @(1,2,3) -SkipExistingObjects
```

The SkipExistingObjects parameter must be used in conjunction with the Steps parameter.
  
> [!NOTE]
> The Steps parameter is for troubleshooting purposes only. Do not use this parameter to deploy an appliance or to upgrade an appliance that is in service. 
  
To determine the steps of the deployment, run the following command:
  
Install-CcAppliance -ShowStepsOnly
  
## Detailed Description
<a name="DetailedDescription"> </a>

The Install-CcAppliance cmdlet is used to deploy Cloud Connector to a new appliance or to upgrade an existing appliance to the latest version.
  
If you have a new appliance, be sure to read Prepare your environment for Cloud Connector first, run the Register-CcAppliance cmdlet to register the appliance, and then run the Install-CcAppliance cmdlet. For more information, see [Deploy a single site in Cloud Connector](deploy-a-single-site-in-cloud-connector.md) and [Deploy multiple sites in Cloud Connector](deploy-multiple-sites-in-cloud-connector.md). 
  
If you have an existing deployment of Cloud Connector and you want to upgrade, please follow the instructions in [Upgrade to a new version of Cloud Connector](upgrade-to-a-new-version-of-cloud-connector.md).
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|PrepareOnly  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> | Generate configuration files for each deployment step. This parameter is for troubleshooting only. <br/> |
|ShowStepsOnly  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Display deployment step names only. This parameter is for troubleshooting only.  <br/> |
|SkipExistingObjects  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |This parameter must be used in conjunction with the Steps parameter. This parameter is for troubleshooting only.  <br/> |
|Steps  <br/> |Optional  <br/> |System.Array  <br/> |Run the deployment steps. This parameter is for troubleshooting only.  <br/> |
|Upgrade  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Upgrade existing Cloud Connector to the latest version.  <br/> |
|UpdateAllCredentials  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Remove all Cloud Connector credentials in the cache. Prompt the user to specify new credential information for the installation.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Install-CcAppliance cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Publish-CcAppliance](publish-ccappliance.md)
  
[Register-CcAppliance](register-ccappliance.md)
  
[Unregister-CcAppliance](unregister-ccappliance.md)
  
[Uninstall-CcAppliance](uninstall-ccappliance.md)
  

