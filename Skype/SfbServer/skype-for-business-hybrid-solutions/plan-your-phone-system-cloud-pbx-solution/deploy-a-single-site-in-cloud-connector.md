---
title: "Deploy a single site in Cloud Connector"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 9/25/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Hybrid
ms.custom:
ms.assetid: fa8aa499-1188-447e-bc30-89d1f5b198a7
description: "Learn about deploying a single PSTN site in Cloud Connector Edition."
---

# Deploy a single site in Cloud Connector
 
Learn about deploying a single PSTN site in Cloud Connector Edition.
  
You can deploy Skype for Business Cloud Connector Edition with or without High Availability (HA) support. If you want to enable HA, you'll need to deploy two or more appliances within a site. You can also convert an existing appliance to support HA after it is deployed.
  
## Deploy the first Skype for Business Cloud Connector Edition appliance

To deploy the first appliance in a site, open a PowerShell console as administrator and run the following cmdlet to register the appliance:
  
```
Register-CcAppliance
```

Follow the instructions to provide the tenant admin account name and password. Use the account you have created for Cloud Connector online management. Also, follow the instructions to provide the external certificate password, safe mode admin password, domain admin password, and VM admin password. 
  
In release 1.4.2 and earlier, also follow the instructions to provide the external certificate password, safe mode admin password, domain admin password, and VM admin password. 
  
In release 2.0 and later, also follow the instructions to provide the external certificate password, CceService password and CABackupFile password.
  
To start the installation, open a PowerShell console as administrator and run the following cmdlet:
  
```
Install-CcAppliance
```

## Add an appliance to an existing site

You can extend an existing Cloud Connector site to support HA by adding additional appliances to the site. 
  
1. Follow the steps to prepare your Cloud Connector appliance as described in [Prepare your Cloud Connector appliance](prepare-your-cloud-connector-appliance.md). Note that some steps are required only for the first appliance in your deployment. Confirm that the site directory exists and is correctly configured for HA support.
    
2. Run the following cmdlet only on the newly added host server to update topology information in your Office 365 tenant configuration. If you want to add multiple appliances at the same time, run the cmdlet on each newly added host server one by one:
    
   ```
   Register-CcAppliance
   ```

3. Update the topology on existing appliances by running the following cmdlet on each host server. Only run the cmdlet on the existing appliances.
    
   ```
   Publish-CcAppliance
   ```

4. Run the following cmdlet only on newly added host servers. Do not run this cmdlet on the existing appliance. If you want to add multiple appliances at the same time, run the cmdlet on each newly added host server one by one.
    
   ```
   Install-CcAppliance
   ```

> [!NOTE]
> If the site directory was set to a local folder path, you need to define a file share for this folder and use a UNC path for the site directory on the new appliance. You may leave the first appliance site directory with the local path or modify it to use the UNC path for the share to the same folder. If the location for the shared site directory changes, any previously-installed appliances need to be uninstalled and then reinstalled. > Important: The password for both the CceService account and the CABackupFile account must be the same on all appliances deployed within the site, so that the appliances can access the site directory share and the encrypted CA backup file in the site directory. 
  
## Remove an appliance from an existing site

If you want to remove an appliance from an existing site:
  
1. Run the following cmdlet only on the host servers you want to remove from the site to update the topology information in your Office 365 tenant configuration.
    
   ```
   Unregister-CcAppliance
   ```

2. Run the following cmdlet only on the host servers from which you want to remove all the virtual machines of the appliance.
    
   ```
   Uninstall-CcAppliance
   ```


