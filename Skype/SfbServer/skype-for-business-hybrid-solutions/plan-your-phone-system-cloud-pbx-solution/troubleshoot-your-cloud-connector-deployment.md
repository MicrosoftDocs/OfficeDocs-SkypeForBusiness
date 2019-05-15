---
title: "Troubleshoot your Cloud Connector deployment"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 12/5/2017
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Hybrid
ms.custom:
ms.assetid: e6cf58cc-dbd9-4f35-a51a-3e2fea71b5a5
description: "Troubleshoot your Cloud Connector Edition deployment."
---

# Troubleshoot your Cloud Connector deployment
 
Troubleshoot your Cloud Connector Edition deployment.
  
This topic describes solutions to common issues with Cloud Connector Edition deployments. If you are experiencing issues with calls to and from the Public Switched Telephone Network (PSTN), you can investigate by following the solutions described in this topic.
  
Cloud Connector provides built-in mechanisms for automatically resolving some issues. An automatic detection process looks for potential issues with the Cloud Connector appliances, and, if possible, takes corrective action to resolve those issues without the need for administrator intervention. The detection process works as follows:
  
- **Detection sequence:** The Cloud Connector Management service runs a process every 60 seconds for detecting whether an appliance is down. In Cloud Connector version 2.0 and later, the detection process uses the Skype for Business Corpnet switch for making PowerShell connections to the Cloud Connector machines; for versions previous to 2.0, the detection process uses the Cloud Connector management switch.
    
    > [!NOTE]
    > For automatic recovery to succeed, there must be network connectivity between the host and virtual machines over the host network switch. Be sure to check network connectivity to ensure that automatic detection and recovery can succeed. 
  
- **Monitoring:** The following services are monitored in Cloud Connector version 2.0 and later:
    
  - Virtual Machines are not connected to the Cloud Connector Corporate or Internet virtual switches
    
  - Virtual Machines are in a saved or stopped status
    
  - Central Management Server services: REPLICA, MASTER
    
  - Mediation Server services: REPLICA, RTCSRV and MEDSVC
    
  - Edge Server services: REPLICA, RTCSRV, RTCDATAPROXY, RTCMRAUTH, RTCMEDIARELAY
    
  - Inbound firewall rules are disabled for CS RTCSRV on Edge server, CS RTCMEDSRV on Mediation server
    
    In Cloud Connector version 1.4.2, only the following services are monitored:
    
  - Mediation Server services: RTCSRV and MEDSVC
    
  - Edge Server service: RTCSRV
    
- **Recovery process:** If any monitored services are down, an appliance is marked down, and services are stopped and marked manual until all issues can be resolved. This will prevent calls from routing to an appliance that may cause call failures.
    
    The Cloud Connector Management service will retry automatic recovery as follows
    
  - The initial retry interval is every ten seconds with a maximum interval time of one hour.
    
  - For the first three recovery attempts, the interval time is 10 seconds. Starting from the fourth retry, the interval time increases by two times the previous interval time. For example, the fourth retry will occur in 20 seconds, the fifth in 40 seconds, and so on. 
    
  - When the maximum interval time of one hour is reached, retries will continue once per hour.
    
  - When recovery is successful, the interval and retry counts are set to their initial values.
    
  - If the Management service is restarted, the interval and retry counts are reset to their initial values.
    
## Troubleshooting

Following are solutions to commonly encountered issues:
  
- **Issue: Deployment fails or stops responding when running the deployment scripts. After logging on to each VM, the IP address is missing or incorrect for the Management/Internal/External NIC.**
    
    **Resolution:** This issue cannot be resolved automatically. NICs cannot be added to VMs while they are running. Please shut down and remove these VMs in hyper-v manager, then run the following cmdlets:
    
  ```
  Uninstall-CcAppliance
  ```

  ```
  Install-CcAppliance
  ```

- 
    
    **Issue: After the Active Directory Server and forest are installed, the CMS Server and/or Mediation Server did not join the domain correctly.**
    
    **Resolution:** To resolve this issue, take the following steps:
    
  - Log on to the Active Directory Server and verify that the domain was created correctly.
    
  - Log on to the CMS/Mediation Server and verify that on the corpnet NIC a valid IP address is assigned, and that valid static IP and DNS is configured as the AD server's IP address.
    
  - Log on to the CMS/Mediation Server, and open a command prompt. Make sure you can ping the FQDN and IP address of the Active Directory Server. If you cannot, there may be an IP address conflict. Please try to assign a new IP for Active Directory and update DNS on the CMS/Mediation server accordingly.
    
- **Issue: You receive the following error message, "Remove-VMSwitch : Failed while removing virtual Ethernet switch. The virtual switch 'Cloud Connector Management Switch' cannot be deleted because it is being used by running virtual machines or assigned to child pools."**
    
    **Resolution:** The "Cloud Connector Management Switch" was not deleted after the deployment. If you hit this error, please go to Hyper-v manager and verify that there is not still a virtual machine still connected to it. If there are virtual machines still connected, disconnect them and delete the management switch. If the management switch still cannot be deleted, restart the host server and try again.
    
- **Issue: You receive the following error message, "Service RTCMRAUTH failed to start. Check to make sure the service is not disabled."**
    
    > [!NOTE]
    > This issue only applies to Cloud Connector versions earlier than 1.4.2. 
  
    The failure to start could also be because this Front End server was previously failed over (using computer fail over). If that's the case, please invoke fail back (using computer fail back).
    
    **Resolution:** This issue happens on an Edge Server when the root CA certificate or intermediate CA certificate is not trusted by the Edge Server. Even if the external certificate can be imported but the certificate chain is broken. Under this condition, the RTCMRAUTH and/or RTCSRV service can not start.
    
    Please import the root CA certificate and all intermediate CA certificates of your external certificate manually into the Edge Server and then restart the Edge Server. After you see the RTCMRAUTH and RTCSRV services started on the Edge Server, go back to your host server, launch a PowerShell console as administrator, and run following cmdlet to switch to the new deployment:
    
  ```
  Switch-CcVersion
  ```

- 
    
    **Issue: The host server was restarted when Windows updates were applied, and calls serviced by the server are failing.**
    
    **Resolution:** If you deployed a high availability environment, Microsoft provides a cmdlet to help move one host machine (deployment instance) into or out of the current topology when you check and install Windows update manually. Use the following steps to accomplish this:
    
1. On the host server, start a PowerShell console as administrator, then run:
    
   ```
   Enter-CcUpdate
   ```

2. Check for updates and install any that are available.
    
3. In the PowerShell console, run the following cmdlet:
    
   ```
   Exit-CcUpdate
   ```

- 
    
    **Issue: When a call is made from a Skype for Business client using a PSTN number, the call cannot be escalated to a conference by inviting another PSTN number.**
    
    **Resolution:** To resolve this issue, see [Configure online hybrid Mediation Server Settings](configure-cloud-connector-integration-with-your-office-365-tenant.md#BKMK_ConfigureMediationServer).
    
- **Issue: A warning message is displayed about Windows Update when you are installing Active Directory server - "Windows automatic updating is not enabled. To ensure that your newly-installed role or feature is automatically updated, turn on Windows Update."**
    
    **Resolution:** Launch a Tenant Remote PowerShell session using Skype for Business tenant admin credentials, then run the following cmdlet to check the _EnableAutoUpdate_ configuration of your site:
    
  ```
  Get-CsHybridPSTNSite
  ```

    If  _EnableAutoUpdate_ is set to **True**, you can safely ignore this warning message because the CCEManagement service will handle downloading and installing Windows updates for both virtual machines and the host server. If  _EnableAutoUpdate_ is set to **False**, run following cmdlet to set it to **True**.
    
  ```
  Set-CsHybridPSTNSite -EnableAutoUpdate $true
  ```

    Alternatively, you can manually check for and install updates. See the next section.
    
- **Issue: You receive an error message: Cannot register appliance because your current input/configuration \<SiteName\> or \<ApplianceName\> or \<Mediation Server FQDN\> or \<Mediation Server IP Address\> conflicts with existing appliance(s). Remove conflict appliance or update your input/configuration information then register again. ' when run Register-CcAppliance to register current appliance to online.**
    
    **Resolution:** Values for the \<ApplianceName\>, \<Mediation Server FQDN\> and \<Mediation Server IP Address\> must be unique and only used for one appliance registration. By default, \<ApplianceName\> comes from the host name. \<Mediation Server FQDN\> and \<Mediation Server IP Address\> defined in configuration ini file.
    
    For example, using (ApplianceName= MyserverNew, Mediation Server FQDN=ms.contoso.com, Mediation Server IP Address=10.10.10.10) to register to SiteName=MySite, but if there is a registered appliance (ApplianceName= Myserver, Mediation Server FQDN=ms.contoso.com, Mediation Server IP Address=10.10.10.10), you will have the conflict.
    
    First, please check your CloudConnector.ini file in ApplianceRoot directory section. You will get \<SiteName\>, \<Mediation Server FQDN\> and \<Mediation Server IP Address\> values in the file. \<ApplianceName\> is your host server name.
    
    Second, Launch Tenant Remote PowerShell using your Skype for Business tenant admin credentials, then run the following cmdlet to check the registered appliance(s).
    
  ```
  Get-CsHybridPSTNAppliance
  ```

    After identifying any conflicts, you can either update your CloudConnector.ini file with information that matches the registered appliance, or unregister the existing appliance to resolve the conflicts.
    
  ```
  Unregister-CsHybridPSTNAppliance -Force
  ```

    
- **Issue: The Get-CcRunningVersion cmdlet returns an empty value if there is a deployed appliance running on the host.**
    
  **Resolution:** This can happen when you upgrade from 1.3.4 or 1.3.8 to 1.4.1. After you install version 1.4.1 with the .msi, you must run `Register-CcAppliance` before you run any other cmdlet. `Register-CcAppliance` will migrate the module.ini file from %UserProfile%\CloudConnector to %ProgramData%\CloudConnector. If you missed it, a new module.ini will be created in %ProgramData%\CloudConnector folder and replace the running/backup version information for 1.3.4 or 1.3.8.
    
  Compare module.ini files in %UserProfile%\CloudConnector and %ProgramData%\CloudConnector folder. If there are differences, delete the module.ini file in %ProgramData%\CloudConnector and rerun  `Register-CcAppliance`. You could also modify the file manually to the correct running and backup version.
    
- **Issue: After you run the Switch-CcVersion cmdlet to switch to an old version which is different from current script version, there is no High Availability support for this old version.**
    
    **Resolution:** For example, you have upgraded from 1.4.1 to 1.4.2. Your current script version, which can be determined by running `Get-CcVersion`, and your running version, which can be determined by running  `Get-CcRunningVersion` are both 1.4.2. At this time, if you run `Switch-CcVersion` to switch the running version back to 1.4.1, then there will be no High Availability support for this old version.
    
    To get full High Availability support, please switch back to 1.4.2, so the running version and script version are the same. If you are experiencing problems with your 1.4.2 deployment, please uninstall and reinstall it as soon as possible.
    
- **Issue: Certificate authority certificates or internal certificates issued to Central Management Store, Mediation Server, and Edge Server are near expiration or are compromised.**
    
    **Resolution:** Skype for Business certification authority certificates are valid for five years. Internal certificates issued to the Central Management Store, Mediation Server, and Edge Server are valid for two years.
    
    > [!NOTE]
    > In Cloud Connector version 2.0 and later, the Renew-CcServerCertificate cmdlet has changed to Update-CcServerCertificate and the Renew-CcCACertificate cmdlet has changed to Update-CcCACertificate. 
  
    If internal certificates issued to the Central Management Store, Mediation Server, and Edge Server are near expiration or compromised, run the Renew-CcServerCertificate or Update-CcServerCertificate cmdlet to renew your certificates.
    
    If certification authority certificates are near expiration, run the Renew-CcCACertificate or Update-CcCACertificate cmdlet to renew your certificates.
    
    **If certification authority certificates are compromised and there is only one appliance in the site,** perform the following steps:
    
1. Run the Enter-CcUpdate cmdlet to drain services and put the appliance in maintenance mode.
   
   ```
   Enter-CcUpdate
   ```
   
2. Run the following cmdlets to reset and create new certification authority certificates and all internal server certificates:
    
    For Cloud Connector releases before 2.0:
    
    ```
    Reset-CcCACertificate 
    Renew-CcServerCertificate 
    Remove-CcLegacyServerCertificate 
    ```

    Or for Cloud Connector release 2.0 and later:
    
    ```
    Reset-CcCACertificate 
    Update-CcServerCertificate 
    Remove-CcLegacyServerCertificate 
    ```
    
3. If TLS is used between the gateway and the Mediation Server, run the Export-CcRootCertificate cmdlet from the appliance, and then install the exported certificate to your PSTN gateways. You may also be required to re-issue the certificate on your gateway.

   ```
   Export-CcRootCertificate
   ```

4. Run the Exit-CcUpdate cmdlet to start services and exit maintenance mode.

   ```
   Exit-CcUpdate
   ```


    **If certification authority certificates are compromised and there are multiple appliances in the site,** perform the following sequential steps on each appliance in the site.
    
    Microsoft recommends that you perform these steps during non-peak usage times.
    
1. On the first appliance, run the Remove-CcCertificationAuthorityFile cmdlet to clean up the CA backup files in the \<SiteRoot\> directory.

     ```
     Remove-CcCertificationAuthorityFile
     ```
    
2. Run the Enter-CcUpdate cmdlet to drain services and put each appliance in maintenance mode.

     ```
     Enter-CcUpdate
     ```
    
3. On the first appliance, run the following cmdlets to reset and create new certification authority certificates and all internal server certificates:
    
     For Cloud Connector releases before 2.0:
    
     ```
     Reset-CcCACertificate
     Renew-CcServerCertificate
     Remove-CcLegacyServerCertificate 
     ```

     Or for Cloud Connector release 2.0 and later:
    
     ```
     Reset-CcCACertificate
     Update-CcServerCertificate
     Remove-CcLegacyServerCertificate 
     ```

4. On the first appliance, run the following cmdlet to back up the CA files to the \<SiteRoot\> folder.
    
     ```
     Backup-CcCertificationAuthority
     ```
   
5. On all other appliance's in the same site, run the following commands to consume the CA backup files, so that the appliances all use the same root certificate, and then request new certificates. 
   
     ```
     Reset-CcCACertificate
     Update-CcServerCertificate
     Remove-CcLegacyServerCertificate 
     ```
     
6. If TLS is used between the gateway and the Mediation Server, run the Export-CcRootCertificate cmdlet from any appliance in the site, and then install the exported certificate to your PSTN gateways. You may also be required to re-issue the certificate on your gateway.
  
     ```
     Export-CcRootCertificate
     ```
     
7. Run the Exit-CcUpdate cmdlet to start services and exit maintenance mode. 

     ```
     Exit-CcUpdate
     ```
    
    
- **Issue: You receive the following error message in the Cloud Connector Management Service Log, "C:\Program Files\Skype for Business Cloud Connector Edition\ManagementService\CceManagementService.log": CceService Error: 0 : Unexpected exception when reporting status to online: System.Management.Automation.CmdletInvocationException: Logon failed for the user \<Global Tenant Admin\>. Please create a new credential object, making sure that you have used the correct user name and password. ---\>**
    
    **Resolution:** The Office 365 global tenant admin credentials have been changed since the Cloud Connector appliance was registered. To update the locally stored credentials on the Cloud Connector appliance, run the following from Administrator PowerShell on the host appliance:
    
  ```
  Set-CcCredential -AccountType TenantAdmin
  ```

- **Issue: After you change the password for the host server account you used for the deployment, you receive the following error message: "ConvertTo-SecureString : Key not valid for use in specified state." in %ProgramFiles%\Skype for Business Cloud Connector Edition\ManagementService\CceManagementService.log or while running the Get-CcCredential cmdlet.**
    
    **Resolution:** All Cloud Connector credentials are stored in the following file: "%SystemDrive%\Programdata\Cloudconnector\credentials.\<CurrentUser\>.xml". When the password on the host server changes, you will need to update the locally stored credentials.
    
    **If you are running Cloud Connector version 1.4.2,** regenerate all Cloud Connector passwords by following these steps:
    
  1. Restart the host server.
    
  2. Delete the following file: "%SystemDrive%\Programdata\Cloudconnector\credentials.\<CurrentUser\>.xml".
    
  3. Launch a PowerShell console as administrator, and then run "Register-CcAppliance -Local" to re-enter the passwords following the description. Enter the same passwords you entered before for the Cloud Connector deployment.
    
     **If you are running Cloud Connector version 2.0 or later,** regenerate all Cloud Connector passwords by following these steps:
    
  4. Restart the host server.
    
  5. Delete the following file: "%SystemDrive%\Programdata\Cloudconnector\credentials.\<CurrentUser\>.xml" .
    
  6. Launch a PowerShell console as administrator, and then run "Register-CcAppliance -Local" to re-enter the passwords following the description. 
    
     If the cached password file was generated with Cloud Connector version 1.4.2, use the VMAdmin password for the CceService password when prompted. Enter the same password you entered before for the Cloud Connector deployment for all other accounts.
    
     If the cached password file was generated with Cloud Connector version 1.4.2 and the DomainAdmin and VMAdmin passwords are different, you must perform the following steps:
    
  7. Run Set-CcCredential -AccountType DomainAdmin as follows:
    
  8. When prompted for the old account credential, enter the credential you used for the CceService password.
    
  9. When prompted for the new account credential, enter the password for the DomainAdmin password you used before.
    
     If the cached password file was generated with Cloud Connector version 2.0 or later, by default, VmAdmin and DomainAdmin use the same password as CceService. If you changed the DomainAdmin and VMAdmin passwords, you must perform the following steps:
    
  10. Run Set-CcCredential -AccountType DomainAdmin as follows:
    
       1. When prompted for the old account credential, enter the credential you used for the CceService password
    
       2. When prompted for the new account credential, enter the password for the DomainAdmin password you used before.
    
  11. Run Set-CcCredential -AccountType VmAdmin as follows:
    
       1. When prompted for the old account credential, enter the credential you used for the CceService password
    
       2. When prompted for the new account credential, enter the password for the VmAdmin password you used before. 
    
- **Issue: With Cloud Connector version 2.1 and later, when running Register-CcAppliance or other cmdlets on the appliance, you receive an error message such as: "For Each-Object : The property 'Common' cannot be found on this object. Verify that the property exists. At C:\Program Files\WindowsPowerShell\Modules\CloudConnector\Internal\MtHostCommon.ps1:681 char:14"**
    
    **Resolution:** Cloud Connector 2.1 and later requires .NET Framework 4.6.1 or later. Please update .NET Framework on the appliance to version 4.6.1 or later and run the cmdlet(s) again.

- **Issue: With Cloud Connector Edition 2.1, when running Install-CcAppliance, you receive an error message such as: "Failed to install new instance with error: Cannot set "State" because only strings can be used as values to set XmlNode properties"**

   **Resolution:** In Cloudconnector.ini, under the [Common] section, please add the “State” config as below:
   CountryCode=US
   State=WA
   City=Redmond

   It is not mandatory for the "State" line to have value, however the "State" line cannot be removed from the Cloudconnector.ini file.

- **Issue: You receive the following error message "Dismount-WindowsImage : Dismount-WindowsImage failed. Error code = 0xc1550115" when installing or upgrading Cloud Connector Edition.**
    
    **Resolution:** Launch a PowerShell console as administrator, run "DISM -Cleanup-Wim'". This will clean up all troubled images. Run Install-CcAppliance again or wait for the bits to automatically upgrade.
    
- **Issue: Deployment of the first Cloud Connector appliance in an HA environment fails**
    
    **Resolution:** The steps you take depend on the reason the deployment failed:
    
  - If the first Cloud Connector appliance fails and you cannot determine the reason for the failure, you must install the appliance again until the deployment is successful, and then install the other appliances.
    
  - If the first Cloud Connector appliance fails with a minor issue, such as an external certificate issue, you might be able to fix the problem without re-installing the appliance. You can then use tenant remote PowerShell to mark the deployment as successful as follows. (You can also use the following steps if the first deployment was successful, but, for some reason, Cloud Connector fails to report the deployment as a success.)
    
  - To get the Identity (GUID) of the first Cloud Connector appliance, run the Get-CsHybridPSTNAppliance cmdlet.
    
  - To mark the appliance as successfully deployed, run the Set-CsCceApplianceDeploymentStatus as follows:
    
  ```
  Set-CsCceApplianceDeploymentStatus -Identity <Appliance Identity GUID> -Action Deploy -Status Finished
  ```

- **Issue: You need to check for and install Windows updates manually on the host server or virtual machines.**
    
   **Resolution:** We recommend that you take advantage of automated OS updates provided by Skype for Business Cloud Connector Edition. After an appliance is registered for online management and auto OS update is enabled, the host server and virtual machines will check and install Windows Updates automatically according to the OS update time window settings.
    
   If you need to check for and install Windows Updates manually, follow the steps in this section that apply to your type of deployment. You should plan on updating both the host server and the virtual machines running on it at the same time to minimize the amount of down time necessary for the updates.
    
   If you prefer, you can use a Windows Server Update Services (WSUS) server to provide updates to Cloud Connector servers. Just be sure to configure the Windows Update to **not** install automatically.
    
   For information about how to manually update your Cloud Connector deployment, see the following section.
    
- **Issue: When Cloud Connector updates to a new build, Cloud Connector cmdlets are not updated.** This sometimes happens if a PowerShell window is left open when automatic update occurs.
    
  **Resolution:** To load the updated cmdlets, you can do either of the following steps:
    
   - Close PowerShell on the Cloud Connector appliance, and then reopen PowerShell.
    
     - Or, you can run Import-Module CloudConnector -Force. 
 
-   **Issue: "The term 'Stop-CsWindowsService' is not recognized as the name of a cmdlet, function, script file, or operable program." error when attempting to run Enter-CcUpdate cmdlet.**

    **Resolution:** Delete the $HOME\AppData\Local\Microsoft\Windows\PowerShell\ModuleAnalysisCache file.
PowerShell creates this file as a cache of cmdlets from modules that it finds so that it doesn’t have to re-analyze all the modules each time as that would make things really slow. Most likely, there was some file corruption that provided misleading results to PowerShell when it was reading back from that cache.

-   **Issue: “Import-Module CloudConnector” generates error “Import-Module: The specified module “CloudConnector” was not loaded because no valid module file was found in any module directory”**

    **Resolution:**
    - Validate that indeed the CloudConnector module exists under c:\Program Files\WindowsPowerShell\Modules
    
    - After validating that CloudConnector module exists under this location, the PSModulePath environment variable storing the path to the locations of the modules can be changed:
    
     a. Temporary change:
        Start Powershell as an Administrator and run the following command:
        $env:PSModulePath = $env:PSModulePath + ";C:\Program Files\WindowsPowerShell\Modules\"
        
     b. For persistent change, Start PowerShell as an Administrator and run the following commands, one by one:
        $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
        SetEnvironmentVariable("PSModulePath", $CurrentValue + "; C:\Program Files\WindowsPowerShell\Modules", "Machine")

    
## Install Windows updates manually

If you do not want to use automatic updates in your environment, follow these steps to manually check for and apply Windows updates. Checking for and installing Windows updates may require a server restart. When a host server is restarting, users will not be able to use Cloud Connector to place or receive calls. You can manually check for and install updates to control when the updates take place, and then restart the machines as needed during times you choose to avoid disruption of services.
  
To manually check for updates, connect to each host server and open the **Control Panel**. Select **System and Security \>Windows Update**, and then manage the updates and server restarts as appropriate for your environment.
  
- If there is only one appliance in the site, connect to each virtual machine and open the **Control Panel**. Select **System and Security \>Windows Update**, and then configure the updates and server restarts as appropriate.
    
- If there are more than one appliance in the site, the instance being updated and restarted cannot be accessed by users during the updates. Users will connect to other instances in the deployment until all virtual machines and all Skype for Business services start on the virtual machines after the updates are completed. To avoid any potential disruption to service, you can remove the instance from HA while you apply the updates, and then restore it when complete. To do so:
    
1. On each host server, open a PowerShell console as administrator.
    
2. Remove the instance from HA with the following cmdlet:
    
   ```
   Enter-CcUpdate
   ```

3. 
    
    Follow the steps for a single instance to manually apply the updates and restart the virtual machine.
    
4. Set the instance back to HA with the following cmdlet:
    
   ```
   Exit-CcUpdate
   ```

For multi-site deployments, follow the steps for a single site for each site in the deployment, applying updates to one site at a time.
  
## Tips when installing anti-virus software on the Cloud Connector host machine

If you need to install anti-virus software on the Cloud Connector host machine, you need to add the following exclusions:
  
- Local Appliance Directory on each machine.
    
- Remote Site Directory on each machine.
    
- Local Site Directory on the machine hosts the shared site root folder.
    
- %ProgramFiles%\Skype for Business Cloud Connector Edition
    
- %ALLUSERSPROFILE%\CloudConnector
    
- %ProgramFiles%\WindowsPowerShell\Modules\CloudConnector
    
- The process Microsoft.Rtc.CCE.ManagementService.exe.
