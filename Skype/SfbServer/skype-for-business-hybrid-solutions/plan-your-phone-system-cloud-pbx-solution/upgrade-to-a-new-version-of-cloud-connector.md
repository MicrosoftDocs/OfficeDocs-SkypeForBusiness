---
title: "Upgrade to a new version of Cloud Connector"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 11/15/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Hybrid
ms.custom:
ms.assetid: efbe25f2-faf5-41c7-8c95-dbc4a835a4a8
description: "Learn about how to upgrade your Cloud Connector Edition deployment."
---

# Upgrade to a new version of Cloud Connector
 
Learn about how to upgrade your Cloud Connector Edition deployment.
  
If you have set up an online management tenant account and enabled automatic updates, your existing deployment of Skype for Business Cloud Connector Edition will be upgraded to the newer version automatically—according to your automatic update time window configuration. You can also perform a manual upgrade. 
  
Cloud Connector Edition versions 1.4.1 and later perform automatic updates by default. If you want to upgrade to the latest version (2.1) manually, see [Upgrade a single site to a new version](upgrade-to-a-new-version-of-cloud-connector.md#BKMK_Upgrade) later in this topic.
  
Automatic update requires that the Cloud Connector service is running. The following steps describe the process for automatic updates:
  
- The automatic update process will run according to the schedule you have configured for automatic updates.
    
- Operating system update tasks
    
  - Check and download operating system updates to all Cloud Connector VMs. 
    
  - Install and update all Cloud Connector VMs one by one and restart.
    
  - After the Cloud Connector VMs restart, check to see if another restart is needed.
    
  - After the Cloud Connector VMs have been successfully patched, repeat the process for the Cloud Connector host machine.
    
  - After the Cloud Connector host machine successfully boots up, any outstanding operating system update tasks are completed.
    
- Cloud Connector update tasks
    
  - Download and check the version file from the download site.
    
  - Download the new version .msi file. 
    
  - Uninstall the old msi file; install the new msi file.
    
  - Download the new version of Skype for Business bits.
    
  - Register the appliance by calling Register-CcAppliance.
    
  - Install the new Cloud Connector version.
    
  - Drain the old appliance and switch the network connection to the new appliance.
    
> [!NOTE]
>  When Cloud Connector updates to a new build, Cloud Connector cmdlets might not be updated. This can happen, for example, if a PowerShell window is left open while automatic update occurs. To load the updated cmdlets, you can do either of the following steps:>  Close PowerShell on the Cloud Connector appliance, and then reopen PowerShell.>  Or, you can run Import-Module CloudConnector -Force.
  
## Upgrade a single site to a new version
<a name="BKMK_Upgrade"> </a>

If there is only one appliance in the site you want to upgrade, do the following:
  
1. Uninstall the existing Cloud Connector version in **Control Panel \> Programs \> Programs and Features**.
    
2. Install the new version of CloudConnector.msi from [https://aka.ms/CloudConnectorInstaller](https://aka.ms/CloudConnectorInstaller).
    
3. Confirm that you have the CloudConnector.ini file for the version you are installing, and that you have updated all of the required values for your environment. You cannot use the .ini file from a previous release. If you are upgrading Cloud Connector, please refer to the topic [Prepare your Cloud Connector appliance](prepare-your-cloud-connector-appliance.md) and make sure SiteName and EnableReferSupport are set to the correct value in the CloudConnector.ini file.
    
4. Start a PowerShell console as administrator and run the following cmdlet to register the current appliance:
    
   ```
   Register-CcAppliance
   ```

5. Run the following cmdlet to download the latest version:
    
   ```
   Start-CcDownload
   ```

6. Run the following cmdlet to start the installation: 
    
   ```
   Install-CcAppliance -Upgrade
   ```

7. Run the following cmdlet to activate the new deployment and turn off the previous version:
    
   ```
   Switch-CcVersion
   ```

If there is more than one appliance in the site, please follow the preceding steps to upgrade each appliance one by one.
  
If you want to update Domain administrator, Virtual machine administrator, Safe Mode administrator and Tenant administrator credentials, you can run the cmdlet with the  _UpdateAllCredentials_ parameter to reset all credentials:
  
```
Install-CcAppliance -UpdateAllCredentials
```

Then, when you start to upgrade to a new version, you will be promoted to input the new credentials. 
  
If you only want to reset your Tenant administrator credentials, run the following cmdlet:
  
```
Set-CcCredential -AccountType TenantAdmin
```

## Upgrade multiple sites to a new version
<a name="BKMK_Upgrade"> </a>

Follow the steps for upgrading a single site, upgrading one site at a time for each site in your deployment. Make sure and [Validate your Cloud Connector deployment](validate-your-cloud-connector-deployment.md) after upgrading each site.
  

