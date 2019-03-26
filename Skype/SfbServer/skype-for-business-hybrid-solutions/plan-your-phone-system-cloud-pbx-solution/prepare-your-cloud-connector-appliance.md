---
title: "Prepare your Cloud Connector appliance"
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
ms.assetid: 6eacfa99-9759-4c13-aca3-8992c2ff2710
description: "Learn about how to prepare your Cloud Connector appliance for deployment and use with Phone System in Office 365 (Cloud PBX)."
---

# Prepare your Cloud Connector appliance

Learn about how to prepare your Cloud Connector appliance for deployment and use with Phone System in Office 365 (Cloud PBX).

This section describes how to get the Skype for Business Cloud Connector Edition installation files, install Cloud Connector software, and prepare your Cloud Connector appliance for deployment. After you have completed all steps in this section, you will be ready to deploy Cloud Connector for a single site or multiple sites. If you have an existing Cloud Connector deployment, and you have not yet upgraded to Cloud Connector version 2.1, see [Upgrade to a new version of Cloud Connector](upgrade-to-a-new-version-of-cloud-connector.md).

> [!NOTE]
> Microsoft supports the current version of Cloud Connector Edition, version 2.1. If you configured automatic update, Cloud Connector will update automatically. If you configured manual update, you will need to upgrade to version 2.1 within 60 days of its release. Microsoft will support the previous version for 60 days after the release of 2.1 to allow you time to upgrade. 

> [!NOTE]
> For Cloud Connector version 2.1 and later, the host appliance must have .NET Framework 4.6.1 or later installed. 

> [!IMPORTANT]
> For successful deployment, when you run the cmdlets to configure Skype for Business Cloud Connector Edition, always use the same console session as the one you started in. Avoid switching to different sessions during the deployment and configuration. 

> [!NOTE]
> There are some steps that you perform only for the first appliance in your deployment: creating a share for the site directory, downloading the bits, and preparing a virtual hard disk (VHDX) file from the Windows Server ISO image. 

## Download the Skype for Business Cloud Connector Edition installer

1. On the host server where the Cloud Connector VMs will run, download the installation files: [https://aka.ms/CloudConnectorInstaller](https://aka.ms/CloudConnectorInstaller). 

    > [!IMPORTANT]
    > The host server must be able to access the Internet during the installation of Cloud Connector because additional files are downloaded during the installation. 

2. Run the installer and accept the default values during the installation.

3. Confirm that the installation completed successfully.

## Verify the installation and configure the environment

1. Open a PowerShell console as administrator and confirm that the Skype for Business Cloud Connector Edition cmdlets are available using the following cmdlet:

   ```
   Get-Command *-Cc*
   ```

    The command should return a list of cmdlets for Skype for Business Cloud Connector Edition.

2. The VHDs, SfBBits, and VersionInfo files will be stored in the **Site Directory**.

    You can find the location of the **Site Directory** with the following cmdlet:

   ```
   Get-CcSiteDirectory
   ```

    The command should return a location in your file system. The location can be a local folder or a file share. The default location for the **Site Directory** is: %USERPROFILE%\CloudConnector\SiteRoot. The default location should be changed to a file share on the first appliance created in each site.

    The location you select must be:

   - Created on the first appliance created in each site.

   - A shared folder that is accessible by the other host servers (appliances) in the same site.

     To set the **Site Directory** to a location other than the default, run the following cmdlet:

   ```
   Set-CcSiteDirectory <UNC File path>
   ```

    If you are deploying High Availability (HA) for the site, make sure you run the cmdlet to set the **Site Directory** to the same location on each host server within the site.

    When you log on and deploy each appliance in the site, make sure your current logon account has the right access to the **Site Directory**.

3. The **Appliance Directory** is the local working root directory for Skype for Business Cloud Connector Edition, and the location where external certificates, instances, and logs are saved. The default location is: %USERPROFILE%\CloudConnector\ApplianceRoot.

    To find the location of the **Appliance Directory**, run the following cmdlet:

   ```
   Get-CcApplianceDirectory
   ```

    To set the **Appliance Directory** to a location other than the default, run the following cmdlet:

   ```
   Set-CcApplianceDirectory <File path>
   ```

    The Appliance Directory should be set to a local folder on the appliance. You should only set the **Appliance Directory** before you start the Skype for Business Cloud Connector Edition deployment. If you change it after deployment, you'll need to redeploy the host server.

    > [!IMPORTANT]
    > The path to the **Appliance Directory** must not contain any spaces.

## Set the path for the external Edge certificate

- Run the following cmdlet to set the path, including the file name, to the external Edge certificate. For example: C:\certs\cce\ap.contoso.com.pfx. The certificate must contain private keys.

  ```
  Set-CcExternalCertificateFilePath -Path <Full path to External certificate, including file name> -Target EdgeServer
  ```

    > [!NOTE]
    > Note that the -Target parameter is specific to versions 1.4.2 and later. 

    Specify the full path to the external certificate, including the file name. The certificate can be stored locally or on a file share. If the certificate is stored in a shared folder, the shared folder must be created on the first appliance of each site and must be accessible by other appliances belonging to the same site. This cmdlet copies the external certificate to the **Appliance Directory**.

    > [!IMPORTANT]
    > **If you have updated to Cloud Connector version 1.4.2 or later**, make sure your prepared external certificate contains private keys and the full certificate chain including the root CA certificate and the intermediate CA certificates. **If you have NOT yet updated to Cloud Connector version 1.4.2**, make sure your prepared external certificate contains private keys. This external certificate must be issued by a Certificate Authority that is trusted by Windows by default.

## Set the path for the external PSTN gateway/SBC certificate

If you are using TLS between the Mediation Server and the PSTN gateway/SBC, run the following cmdlet to set the path, including the file name, to the gateway certificate. For example: C:\certs\cce\sbc.contoso.com.cer. The certificate must contain the root CA and the intermediate chain for the certificate assigned to the gateway:

```
Set-CcExternalCertificateFilePath -Path <Full path to gateway certificate, including file name> -Target MediationServer 
```

> [!NOTE]
> Note that the -Target parameter is specific to versions 1.4.2 and later. 

## Create virtual switches in Hyper-V Manager

1. Open **Hyper-V Manager** > **Virtual Switch Manager**, and select **New Virtual Switch Manager**.

2. Create an External virtual switch and bind it to the physical network adapter that is connected to your internal network domain:

    Select **Allow management operating system to share this network adapter** for this virtual switch.

3. Create an External virtual switch and bind it to the physical network adapter that is routed to the Internet:

    De-select **Allow management operating system to share this network adapter** for this virtual switch.

4. Set the name of the switch that connects your perimeter network to your internal network domain **SfB CCE Corpnet Switch**.

    Set the name of the switch that connects your perimeter network to the Internet **SfB CCE Internet Switch**.

## Update the CloudConnector.ini configuration file

Prepare the CloudConnector.ini file using the information you gathered in [Determine deployment parameters](plan-skype-for-business-cloud-connector-edition.md#BKMK_SiteParams) in the [Plan for Skype for Business Cloud Connector Edition](plan-skype-for-business-cloud-connector-edition.md) topic.

To update the file, first run the following cmdlet to get the sample template (CloudConnector.Sample.ini):

```
Export-CcConfigurationSampleFile
```

The sample template is stored in the **Appliance Directory**.

After you update it with the values for your environment, save the file as CloudConnector.ini in the **Appliance Directory**. You can run **Get-CcApplianceDirectory** to determine the path to the **Appliance Directory**.

When updating the .ini file, consider the following:

> [!NOTE]
> Not all values for the .ini file are discussed in this section, only those with a special consideration are covered here. For a full list, see the [Determine deployment parameters](plan-skype-for-business-cloud-connector-edition.md#BKMK_SiteParams) section of the [Plan for Skype for Business Cloud Connector Edition](plan-skype-for-business-cloud-connector-edition.md) topic. For more information about what values need to be changed for additional appliances or new sites, see [Single site with High Availability (HA) compared to multi-site deployments](deploy-multiple-sites-in-cloud-connector.md#BKMK_SingleSitecomparedtomulti-site) in the topic [Deploy multiple sites in Cloud Connector](deploy-multiple-sites-in-cloud-connector.md). 

- **SiteName:** The default value is **Site1**. You must update it before you deploy Cloud Connector, because when you run **Register-CcAppliance** to register an appliance to an existing or new site, the cmdlet will use **SiteName** to determine which site to register.

     If you want to register the appliance to a new site, the value of **SiteName** must be unique and different from existing sites. If you want to register the appliance to an existing site, the value for **SiteName** in .ini file must match the name defined in your Office 365 tenant configuration. If you are copying a configuration file from one site to another, make sure you update the value for **SiteName** for each site accordingly.

- **ServerName:** The server name should not contain the domain name and should be limited to 15 characters.

- **HardwareType:** If you don't set or leave the value to null, the default value of **Normal** will be used. Use **Normal** if you plan to deploy the larger version of Cloud Connector to support 500 simultaneous calls per host machine as described in [Plan for Skype for Business Cloud Connector Edition](plan-skype-for-business-cloud-connector-edition.md). Use **Minimum** for a smaller deployment that supports 50 simultaneous calls.

- **Internet/Corpnet/Management virtual switches:**: Add the name of the virtual switches you have created. For the management virtual switch, leave the default value. The deployment script will create the management virtual switch at the beginning of deployment and delete it when the deployment finishes.

- **ManagementIPPrefix:** ManagementIPPrefix in the Network section must be a different subnet from other internal IPs. For example, as the default value shows, ManagementIPPrefix is 192.168.213.0, while AD IPAddress is 192.168.0.238.

    The deployment scripts create a management network adapter on each virtual machine, assign a management IP, and connect it to a management virtual switch. This enables the host server to connect to and manage each virtual machine via this management network. The management virtual switch is deleted when the deployment is finished.

- **Base VM specific configurations:** Settings in this section must be configured for the **Convert-CcIsoToVhdx** cmdlet.

    During base VM image preparation, the base VM will be connected to the internal network switch. The following settings are critical for the VM to be able to access the Internet:

  - [Common]BaseVMIP: the corpnet IP address to be assigned to the base VM.

  - [Network]CorpnetDefaultGateway: the default gateway to be assigned to the base VM.

  - [Network]CorpnetDNSIPAddress: the DNS IP address to be assigned to the base VM.

  - [Network]WSUSServer: the IP address of Windows Server Update Service.

  - [Network]WSUSStatusServer: the IP address of Windows Server Update Service status server.

  - [Network]EnableReferSupport: this will define whether SIP REFER support is enabled or disabled on the Trunk Configuration to your IP/PBX.

- **Internal IPs:**

  - Make sure subnet mask CorpnetIPPrefixLength is correct.

  - Make sure there are no IP conflicts for these internal IPs.

- **External IPs:**

  - For MR public IP: specify either ExternalMRIPs for non-NAT or ExternalMRPublicIPs for NAT.

  - ExternalSIPIPs and ExternalMRIPs can be the same.

  - Make sure subnet mask InternetIPPrefixLength is correct.

  - Make sure there are no IP conflicts for these external IPs.

- **Gateways:**

  - If you have only one gateway, remove the section for the secondary gateway. If you have more than two gateways, create additional sections by copying and pasting the existing one and then updating it.

  - Make sure that the IP address and port of the gateway(s) are correct.

  - To support PSTN gateway level HA, leave the secondary gateway, and add any additional gateways you will use. You can copy and paste an existing entry and then update it.

- Optionally, you can update the LocalRoute value to restrict outbound call numbers.

## Download the bits to the Site Directory

Run the following cmdlet to download the bits and version information files to the **Site Directory**:

```
Start-CcDownload
```

> [!NOTE]
> You need to perform this step for the first appliance only. 

## Prepare base virtual disk (VHDX) from the downloaded ISO file

This step prepares a virtual hard disk (VHDX) file from the Windows Server 2012 ISO image. The VHDX will be used to create virtual machines during deployment. A temporary virtual machine (base VM) will be created and Windows Server 2012 will be installed from the ISO file. After the VM is created, some necessary components will be installed and the latest Windows update will be applied. At the end, the base VM will be generalized (sysprep) and cleaned up, leaving only the generated virtual disk file.

> [!NOTE]
> You need to perform this step for the first appliance only. 

Before proceeding with this step, make sure that the corpnet switch is created. Also, confirm that the following settings are correctly configured in the CloudConnector.ini file:

- [Network]CorpnetSwitchName

- [Common]BaseVMIP

- [Network]CorpnetIPPrefixLength

- [Network]CorpnetDefaultGateway

- [Network]CorpnetDNSIPAddress

Start a PowerShell console as administrator and run the following cmdlet to convert the ISO image to a virtual hard disk (VHD):

```
Convert-CcIsoToVhdx -IsoFilePath <Windows ISO File Path, including file name>
```

Specify the full path, including file name, to the ISO image. For example: C:\ISO\WindowsServer2012R2.iso.

The created VHD file is stored in the **Site Directory** \Bits\VHD folder. You can get the path to the **Site Directory** by running the **Get-CcSiteDirectory**.

> [!IMPORTANT]
> By default, proxy settings are not configured on the base VM. If a proxy is required in your network environment to update the VM via Windows Update, you should add the -PauseBeforeUpdate switch when you run "Convert-CcIsoToVhdx". The script will pause before Windows Update and you'll have a chance to manually set up proxy on the VM. After the proxy is setup and the VM can access Internet, you can resume the script to complete the remaining steps. 

### Create VHDs for a multi-site deployment

This is an optional step that applies only to multi-site deployments.

If you are deploying a multi-site deployment, you do not need to convert the ISO to a VHD for each site. You can copy the VHDX created for the first site to the host server for a second site.

 Copy the file to the same file location ( **Site Directory** \Bits\VHD folder), and with the same file name, on the host server for an additional site.

## Set the PowerShell Execution policy to RemoteSigned

The PowerShell scripts provided require that the execution policy be set to RemoteSigned. To see the current setting, open a PowerShell console as administrator and then run the following cmdlet:

```
Get-ExecutionPolicy
```

If it is not set to "RemoteSigned," run the following cmdlet to change it:

```
Set-ExecutionPolicy RemoteSigned
```

## Change local Group Policy on the host machine (versions 1.4.1 and earlier)

> [!NOTE]
> This task is not required for Cloud Connector versions 1.4.2 and later. 

The CceService account is created during the Skype for Business Cloud Connector Edition deployment. It runs the Cloud Connector Management Service and requires permission to uninstall the cloudconnector.msi. You must change the group policy setting on the Cloud Connector host machine to specify that the user registry should not be unloaded when the user logs off. Follow the steps below:

### To change the Group Policy setting

1. Open the **Group Policy Editor** by running gpedit.msc.

2. In the **Group Policy Editor**, navigate to Administrative Templates > System > UserProfile > Do not forcefully unload the user registry at user logoff. 

3. Set its value to **Enabled**.

## Set up your Office 365 tenant

An Office 365 tenant with Skype for Business Online and Phone System in Office 365 is required. Make sure your tenant is set up and configured before attempting to use Cloud Connector.

Some Office 365 setup steps require you to use Tenant Remote PowerShell (TRPS) to configure your Office 365 tenant. **This should be installed on the host server.** You can download the Skype for Business Online module for PowerShell from: [Skype for Business Online, Windows PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).

Create a dedicated Skype for Business administrator account for Cloud Connector online management, for example CceOnlineManagmentAdministrator. This account will be used by appliance to add or remove appliance, enable or disable automatic OS update, enable or disable automatic binary update. Set the password for this account to never expire so that you do not need to change it for the service each time it expires.


