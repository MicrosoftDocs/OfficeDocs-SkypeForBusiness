---
title: Modify the configuration of an existing Cloud Connector deployment
ms.prod: SKYPEFORBUSINESS
ms.assetid: 90490c65-0e40-4e85-96e1-751f27897e25
---


# Modify the configuration of an existing Cloud Connector deployment
[]
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
    
  
4. Run the following cmdlet to update the configuration: (only applicable for v2, skip to the next step for previous versions)
    
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
  
    
    

1. Run the following cmdlet to uninstall all existing virtual machines on current appliance: 
    
  ```
  Uninstall-CcAppliance
  ```

2. Run the following cmdlet to unregister the appliance:
    
  ```
  Unregister-CcAppliance
  ```

3. Update the CloudConnector.ini file in the Appliance Directory.
    
  
4. Run the following cmdlet to update the configuration: (only applicable for v2, skip to the next step for previous versions)
    
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

To modify the configuration for multiple sites in a deployment, just follow the steps for a single site for each site, updating one site at a time.
  
    
    

## Modify the configuration of your O365 tenant to enable automatic updates
<a name="BKMK_MultipleSites"> </a>

To enable operating system automatic updates and Bits automatic updates, your Skype for Business tenant admin account for online management needs to set the EnableAutoUpdate flag to true and configure the Windows update time using tenant remote PowerShell.
  
    
    

1. The EnableAutoUpdate property of the site needs to be set to true. The default value is true. Run the following cmdlet to make sure EnableAutoUpdate is set to true:
    
  ```
  Get-CsHybridPSTNSite -Identity <SiteName>
  ```


    If you disabled operating system automatic updates or Bits automatic updates, your host and virtual machine may miss important Windows updates; and Cloud Connector will not upgrade to the new version automatically. It is highly recommended that you enable automatic updates.
    
  
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

  - Assign update time windows to site. 
    
    The Bits update time and OS update time windows are configured separately. Both of them can be assigned single or multiple time windows. Each time window can be assigned to different sites and different purpose (Bits update and OS update). Run the following below cmdlet to set time window for site: 
    


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

This section is applicable to Cloud Connector version 2.0 and later.
  
    
    
All Cloud Connector credentials are stored in the following file: "%SystemDrive%\\Programdata\\Cloudconnector\\credentials.<CurrentUser>.xml". When the password on the host server changes, you will need to update the locally stored credentials.
  
    
    
To update the locally stored credentials on the Cloud Connector appliance, use the  [Get-CcCredential](get-cccredential.md) and [Set-CcCredential](set-cccredential.md) cmdlets and follow these steps:
  
    
    

1. Run the following commands to retrieve the passwords you will need later: 
    
  - Get-CcCredential -AccountType DomainAdmin -DisplayPassword
    
  
  - Get-CcCredential -AccountType VMAdmin -DisplayPassword
    
  
  - Get-CcCredential -AccountType CceService -DisplayPassword
    
  
2. Change the password of your account on the host server.
    
  
3. Restart the host server.
    
  
4. Delete the following file: "%SystemDrive%\\Programdata\\Cloudconnector\\credentials.<CurrentUser>.xml".
    
  
5. Launch a PowerShell console as administrator, and then run "Register-CcAppliance -Local" to re-enter the passwords following the description. Be sure you enter the same password you entered before for the Cloud Connector deployment.
    
  
By default, VmAdmin and DomainAdmin use the same password as CceService. If the DomainAdmin, VMAdmin, and CceService passwords returned in step 1 are different, you must perform the following steps:
  
    
    

1. Run Set-CcCredential -AccountType DomainAdmin as follows:
    
1. When prompted for the old account credential, enter the credential you used for the CceService password.
    
  
2. When prompted for the new account credential, enter the password for the DomainAdmin password returned in step 1.
    
  
2. Run Set-CcCredential -AccountType VmAdmin as follows:
    
1. When prompted for the old account credential, enter the credential you used for the CceService password.
    
  
2. When prompted for the new account credential, enter the password for the VmAdmin password returned in step 1. 
    
  

## Add a new SIP domain
<a name="BKMK_UpdatePassword"> </a>

To add a new SIP domain (or multiple SIP domains) to your existing Cloud Connector deployment, do the following:
  
    
    

1. Make sure you've completed the steps to update your domain in Office 365 and have the ability to add DNS records. For more information about how to set up your domain in Office 365, see the video  [Set up your domain in Office 365](https://support.office.com/en-us/article/Video-Set-up-your-domain-in-Office-365-703dfec1-882d-4e33-b647-937f731887b7?ui=en-US&amp;rs=en-US&amp;ad=US).
    
  
2. Update the Cloud Connector configuration file with the new SIP domain or domains.
    
  
3. Request a new Edge external certificate with additional SAN names for sip.domain for each SIP domain defined in your Cloud Connector configuration. 
    
  
4. Set the path for the new Edge external certificate as follows:
    
  ```
  Set-CcExternalCertificateFilePath -Path <Full path to External certificate>
  ```

5. 
    
    Follow the instructions to  [Modify the configuration of a single site](modify-the-configuration-of-an-existing-cloud-connector-deployment.md#BKMK_SIngleSite) or [Modify the configuration of multiple sites](modify-the-configuration-of-an-existing-cloud-connector-deployment.md#BKMK_MultipleSites).
    
  

## Modify the primary SIP domain
<a name="BKMK_UpdatePassword"> </a>

If you need to change the primary SIP domain in your Cloud Connector deployment, do the following:
  
    
    

1. Make sure you've completed the steps to update your domain in Office 365 and have the ability to add DNS records. For more information about how to set up your domain in Office 365, see the video  [Set up your domain in Office 365](https://support.office.com/en-us/article/Video-Set-up-your-domain-in-Office-365-703dfec1-882d-4e33-b647-937f731887b7?ui=en-US&amp;rs=en-US&amp;ad=US).
    
  
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


