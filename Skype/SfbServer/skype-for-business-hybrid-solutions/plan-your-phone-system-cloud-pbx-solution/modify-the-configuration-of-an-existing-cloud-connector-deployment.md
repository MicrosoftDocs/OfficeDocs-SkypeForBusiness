---
title: "Modify the configuration of an existing Cloud Connector deployment"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 2/15/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Hybrid
ms.custom:
ms.assetid: 90490c65-0e40-4e85-96e1-751f27897e25
description: "Follow the steps in this topic to modify the configuration of an existing Skype for Business Cloud Connector Edition 1.4.1 or later deployment."
---

# Modify the configuration of an existing Cloud Connector deployment
 
Follow the steps in this topic to modify the configuration of an existing Skype for Business Cloud Connector Edition 1.4.1 or later deployment. 
  
## Modify the configuration of a single site
<a name="BKMK_SIngleSite"> </a>

If there is only one appliance in the site, when you want to change the configuration settings after the appliance is deployed, you can modify the CloudConnector.ini file and start the deployment again.
  
1. Run the following cmdlet to uninstall all existing virtual machines on the host server: 
    
   ```
   Uninstall-CcAppliance
   ```

2. Run the following cmdlet to unregister the appliance:
    
   ```
   Unregister-CcAppliance
   ```

3. Update the CloudConnector.ini file in the Appliance Directory.
    
4. Run the following cmdlet to update the configuration: (This step is only applicable for version 2; for previous versions, skip to the next step.)
    
   ```
   Import-CcConfiguration 
   ```

5. Run the following cmdlet to register the appliance again:
    
   ```
   Register-CcAppliance
   ```

6. Run the following cmdlet to install Skype for Business Cloud Connector Edition:
    
   ```
   Install-CcAppliance
   ```

If there is more than one appliance in the site, you'll need to follow these steps, modify the CloudConnector.ini file, and redeploy the appliances one by one.
  
1. Run the following cmdlet to uninstall all existing virtual machines on the current appliance: 
    
   ```
   Uninstall-CcAppliance
   ```

2. Run the following cmdlet to unregister the appliance:
    
   ```
   Unregister-CcAppliance
   ```

3. Update the CloudConnector.ini file in the Appliance Directory.
    
4. Run the following cmdlet to update the configuration: (This step is only applicable for version 2; for previous versions, skip to the next step.)
    
   ```
   Import-CcConfiguration 
   ```

5. Run the following cmdlet to register the appliance again:
    
   ```
   Register-CcAppliance
   ```

6. Run the following cmdlet on all other appliances in the site to pick up the latest configuration:
    
   ```
   Publish-CcAppliance
   ```

7. Run the following cmdlet to redeploy Cloud Connector on the current appliance:
    
   ```
   Install-CcAppliance
   ```

## Modify the configuration of multiple sites
<a name="BKMK_MultipleSites"> </a>

To modify the configuration for multiple sites in a deployment, follow the steps for a single site, updating one site at a time.
  
## Modify the configuration of your Office 365 tenant to enable automatic updates
<a name="BKMK_MultipleSites"> </a>

To enable operating system automatic updates and Bits automatic updates, you must use the Skype for Business tenant admin account for online management and use tenant remote PowerShell as follows.
  
If you disabled operating system automatic updates or Bits automatic updates, your host and virtual machine may miss important Windows updates, and Cloud Connector will not upgrade to the new version automatically. It is highly recommended that you enable automatic updates.
  
1. The EnableAutoUpdate property of the site needs to be set to true (the default value). Run the following cmdlet to make sure EnableAutoUpdate is set to true:
    
   ```
   Get-CsHybridPSTNSite -Identity <SiteName>
   ```

2. Create auto update time window for the tenant.
    
    The time window can be daily, weekly and monthly. All the time windows need a start time and a duration.
    
   - For a daily time window, only start time and duration are needed. 
    
   - For a weekly time window, days of week are needed, which can be a single day or multiple days.
    
   - For a monthly time window, there can be two types. The first type is to specify the day of the month, which can be a single day. The second type is to specify the weeks of the month, along with days of the week, which both can be a single item or multiple items.
    
   - Each tenant can have 20 time windows defined. The default time window will be created for a new tenant as the default time window for operating system update and Bits update. Run the following cmdlet(s) to set the daily, weekly or monthly time window:
    
   ```
   New-CsTenantUpdateTimeWindow -Identity Night -Daily -StartTime 22:00 -Duration 6:00
   ```

   ```
   New-CsTenantUpdateTimeWindow -Identity WeekdayNight -Weekly -DaysOfWeek Monday,Tuesday,Wednesday,Thursday,Friday -StartTime 22:00 -Duration 4:00
   ```

   ```
   New-CsTenantUpdateTimeWindow -Identity FirstAndLastWeekend -Monthly -WeeksOfMonth First,Last -DaysOfWeek Sunday,Saturday -StartTime 0:00 -Duration 10:00
   ```

   ```
   New-CsTenantUpdateTimeWindow -Identity MidDayOfMonth -Monthly -DayOfMonth 15 -StartTime 0:00 -Duration 1.00:00
   ```

   - Assign update time windows to the site. 
    
     The Bits update time and OS update time windows are configured separately. Both of them can be assigned single or multiple time windows. Each time window can be assigned to different sites and different purpose (Bits update and OS update). Run the following cmdlet to set the time window for the site: 
    
   ```
   Set-CsHybridPSTNSite -Identity <SiteName> -BitsUpdateTimeWindow @{add="MidDayOfMonth","WeekdayNight"} -OsUpdateTimeWindow @{replace="Night"}
   ```

## Update the dedicated tenant admin credentials
<a name="BKMK_MultipleSites"> </a>

Administrative changes in the Office 365 tenant for Cloud Connector are made from an account with the needed permissions. In Cloud Connector versions before 2.0, that account is a dedicated global tenant admin account. In Cloud Connector versions 2.0 and later, that account can be an Office 365 account with Skype for Business Administrator rights.
  
If your admin account credentials change in Office 365, you also need to update the locally cached credentials in Cloud Connector by running the following Administrator PowerShell command on each Cloud Connector appliance you have deployed:
  
```
Set-CcCredential -AccountType TenantAdmin
```

## Update the password for the host server
<a name="BKMK_UpdatePassword"> </a>

> [!NOTE]
> This section is applicable to Cloud Connector version 2.0 and later. 
  
All Cloud Connector credentials are stored in the following file: "%SystemDrive%\Programdata\Cloudconnector\credentials.\<CurrentUser\>.xml". When the password on the host server changes, you will need to update the locally stored credentials.
  
To update the locally stored credentials on the Cloud Connector appliance, use the [Get-CcCredential](get-cccredential.md) and [Set-CcCredential](set-cccredential.md) cmdlets and follow these steps:
  
1. Run the following commands to retrieve the passwords you will need later: 
    
   - Get-CcCredential -AccountType DomainAdmin -DisplayPassword
    
   - Get-CcCredential -AccountType VMAdmin -DisplayPassword
    
   - Get-CcCredential -AccountType CceService -DisplayPassword
    
2. Change the password of your account on the host server.
    
3. Restart the host server.
    
4. Delete the following file: "%SystemDrive%\Programdata\Cloudconnector\credentials.\<CurrentUser\>.xml".
    
5. Launch a PowerShell console as administrator, and then run "Register-CcAppliance -Local" to re-enter the passwords following the description. Be sure you enter the same password you entered before for the Cloud Connector deployment.
    
By default, VmAdmin and DomainAdmin use the same password as CceService. If the DomainAdmin, VMAdmin, and CceService passwords returned in step 1 are different, you must perform the following steps:
  
1. Run Set-CcCredential -AccountType DomainAdmin as follows:
    
1. When prompted for the old account credential, enter the credential you used for the CceService password.
    
2. When prompted for the new account credential, enter the password for the DomainAdmin password returned in step 1.
    
2. Run Set-CcCredential -AccountType VmAdmin as follows:
    
1. When prompted for the old account credential, enter the credential you used for the CceService password.
    
2. When prompted for the new account credential, enter the password for the VmAdmin password returned in step 1. 
    
## Update the password for the CceService account
<a name="BKMK_UpdatePassword"> </a>

> [!NOTE]
> This section is applicable to Cloud Connector version 2.0.1 and later. 
  
The Cloud Connector service runs the Cloud Connector Management service. The CceService account is created during the Cloud Connector Edition deployment and stored in the following files: "%SystemDrive%\Programdata\Cloudconnector\credentials.\<CurrentUser\>.xml" and "%SystemDrive%\Programdata\Cloudconnector\credentials..CceService.xml".
  
To ensure that all appliances can access the site directory share, the password for the CceService account must be the same on all appliances deployed within the site. Keep the following in mind:
  
- By default, the CceService account is configured as "Password never expires". When you update the password, Microsoft recommends keeping this configuration.
    
- You should update the password during non-peak usage periods and outside of automatic update time windows for bits or Windows updates. When you update the password, the appliance needs to be drained and restarted, which takes some time. Restarting the appliance will interrupt automatic update operations. 
    
- When you change the CceService account password, you will need to specify all the credentials and update them in the locally stored file. 
    
For each appliance that belongs to the same PSTN site, you will need to specify the following: 
  
1. Run the following commands to retrieve the account names and passwords that you will use later:
    
   ```
   Get-CcCredential -AccountType TenantAdmin -DisplayPassword
   Get-CcCredential -AccountType TenantAdmin
   Get-CcCredential -AccountType OMSWorkspace -DisplayPassword
   Get-CcCredential -AccountType OMSWorkspace 
   Get-CcCredential -AccountType ExternalCert -DisplayPassword
   Get-CcCredential -AccountType CABackupFile -DisplayPassword
   Get-CcCredential -AccountType CceService -DisplayPassword
   Get-CcCredential -AccountType VMAdmin -DisplayPassword
   Get-CcCredential -AccountType DomainAdmin -DisplayPassword
   ```

2. Run the Enter-CcUpdate cmdlet to drain the appliance and move it into manual maintenance mode.
    
3. Update the password of the CceService account on the host server.
    
4. Restart the host server.
    
5. Run the Restore-CcCredentials cmdlet to re-enter the passwords following the description. 
    
    Be sure you enter the same password you entered before for the Cloud Connector deployment except for the CceService account. For the CceService account, enter your new password. Be sure the new password for the CceService account is the same for all appliances in the PSTN site.
    
6. By default, VmAdmin and DomainAdmin use the same password as CceService. If the DomainAdmin, VMAdmin, and CceService passwords returned in step 1 are different, you must perform the following steps:
    
7. Run Set-CcCredential -AccountType DomainAdmin as follows:
    
   - When prompted for the old account credential, enter the credential you used for the CceService password.
    
   - When prompted for the new account credential, enter the password for the DomainAdmin password returned in step 1.
    
8. Run Set-CcCredential -AccountType VmAdmin as follows:
    
   - When prompted for the old account credential, enter the credential you used for the CceService password.
    
   - When prompted for the new account credential, enter the password for the VmAdmin password returned in step 1. 
    
9. Run the Exit-CcUpdate cmdlet to move the appliance out of manual maintenance mode.
    
10. After you complete these steps on all appliances in the same PSTN site, delete the following files in the site root directory:
    
    - CcLockFile
    
    - Site_\<Edge External Sip Pool fqdn\>
    
    - Tenant_\<Edge External Sip Pool fqdn\>
    
    - TenantConfigLock_\<Edge External Sip Pool fqdn\>
    
## Add a new SIP domain
<a name="BKMK_UpdatePassword"> </a>

To add a new SIP domain (or multiple SIP domains) to your existing Cloud Connector deployment, do the following:
  
1. Make sure you've completed the steps to update your domain in Office 365 and have the ability to add DNS records. For more information about how to set up your domain in Office 365, see [Add a domain to Office 365](https://support.office.com/en-us/article/Add-a-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).
    
2. Update the Cloud Connector configuration file with the new SIP domain or domains.
    
3. Request a new Edge external certificate with additional SAN names for sip.domain for each SIP domain defined in your Cloud Connector configuration. 
    
4. Set the path for the new Edge external certificate as follows:
    
   ```
   Set-CcExternalCertificateFilePath -Path <Full path to External certificate>
   ```

5. 
    
    Follow the instructions to [Modify the configuration of a single site](modify-the-configuration-of-an-existing-cloud-connector-deployment.md#BKMK_SIngleSite) or [Modify the configuration of multiple sites](modify-the-configuration-of-an-existing-cloud-connector-deployment.md#BKMK_MultipleSites).
    
## Modify the primary SIP domain
<a name="BKMK_UpdatePassword"> </a>

If you need to change the primary SIP domain in your Cloud Connector deployment, do the following:
  
1. Make sure you've completed the steps to update your domain in Office 365 and have the ability to add DNS records. For more information about how to set up your domain in Office 365, see [Add a domain to Office 365](https://support.office.com/en-us/article/Add-a-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).
    
2. Update the Cloud Connector configuration file with the new SIP domain.
    
3. Request a new Edge external certificate with additional SAN names for sip.domain for each SIP domain defined in your Cloud Connector configuration. 
    
4. Set the path for the new Edge external certificate as follows:
    
   ```
   Set-CcExternalCertificateFilePath -Path <Full path to External certificate>
   ```

5. 
    
    Remove the tenant registration for each appliance in a site by running the following cmdlet in administrator PowerShell on Cloud Connector:
    
   ```
   Unregister-CcAppliance
   ```

6. 
    
    Remove the site registration for each site by running the following cmdlet in Skype for Business Online PowerShell:
    
   ```
   Remove-CsHybridPSTNSite
   ```

7. 
    
    Uninstall each appliance by running the following cmdlet in administrator PowerShell on Cloud Connector:
    
   ```
   Uninstall-CcAppliance
   ```

8. 
    
     Register each appliance by running the following cmdlet in administrator PowerShell on Cloud Connector:
    
   ```
   Register-ccAppliance
   ```

9. 
    
     Install each appliance, one by one, by running the following cmdlet in administrator PowerShell on Cloud Connector:
    
   ```
   Install-CcAppliance
   ```

## Replace the external Edge certificate with a new certificate
<a name="BKMK_UpdatePassword"> </a>

When you need to replace the external Edge certificate on your Cloud Connector appliances, you will need to obtain a new Edge certificate, prepare the PFX file containing the Private Key and full certificate chain, and then do the following on each appliance:
  
1. Put the appliance in maintenance mode by using the Enter-CcUpdate cmdlet.
    
2. Run the following command: 
    
   ```
   Set-CcExternalCertificateFilePath -Target EdgeServer -Path <Full file path of new certificate including filename> -Import
   ```

3. 
    
    If the password of the new certificate is the same as the old, the import will be successful. If the password is different, you will receive an error that the password is wrong, and you will need to reset the password by running the Register-CcAppliance cmdlet with the -Local parameter, and then repeating step 2. 
    
4. Take the appliance out of maintenance mode by using the Exit -CcUpdate cmdlet.
    

