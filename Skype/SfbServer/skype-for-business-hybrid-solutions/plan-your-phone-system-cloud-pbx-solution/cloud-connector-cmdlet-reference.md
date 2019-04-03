---
title: "Cloud Connector cmdlet reference"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 11/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 072b4bdc-0f1e-4fce-a41e-5c60d24556d5
description: "The following table lists the Skype for Business Cloud Connector Edition cmdlets with a brief description and links to more information."
---

# Cloud Connector cmdlet reference
 
The following table lists the Skype for Business Cloud Connector Edition cmdlets with a brief description and links to more information.
  
> [!NOTE]
> You must run all the cmdlets on the Cloud Connector host machine, and you must run the PowerShell session as Administrator. 
  
|**Cmdlet name**|**Description**|
|:-----|:-----|
|[Backup-CcCertificationAuthority](backup-cccertificationauthority.md) <br/> Version 1.4.2 and later  <br/> |Backs up the certification authority service to a file and saves it to the CA folder under the site share directory.     <br/> |
|[Convert-CcIsoToVhdx](convert-ccisotovhdx.md) <br/> |Creates a base virtual hard disk file (VHDX) using a customer supplied Windows Server 2012 R2 ISO file. The VHDX file will be used during the deployment ofCloud Connector.  <br/> |
|[Enter-CcUpdate](enter-ccupdate.md) <br/> |Prepares the Cloud Connector host server for the update process by putting it in maintenance mode. The appliance is "drained"; that is, all existing calls will complete, but new calls are rejected.  <br/> |
|[Exit-CcUpdate](exit-ccupdate.md) <br/> |Exits update maintenance mode on the Cloud Connector host server.  <br/> |
|[Export-CcConfiguration](export-ccconfiguration.md) <br/> | Exports a Skype for Business Cloud Connector Edition configuration to a local file on the Skype for Business Cloud Connector Edition host server. <br/> |
|[Export-CcConfigurationSampleFile](export-ccconfigurationsamplefile.md) <br/> |Exports a Cloud Connector sample configuration file (.ini) to the appliance directory of a Cloud Connector appliance. You can modify and rename the file to use for your deployment.  <br/> |
|[Export-CcRootCertificate](export-ccrootcertificate.md) <br/> Version 1.4.2 and later  <br/> |Exports the root CA certificate to a local file on the Cloud Connector host server.  <br/> |
|[Get-CcApplianceDirectory](get-ccappliancedirectory.md) <br/> |Retrieves the working directory on the Cloud Connector host server. All deployment files are stored in this directory.  <br/> |
|[Get-CcApplianceLogDirectory](get-ccappliancelogdirectory.md) <br/> |Shows the current directory where logs for a Cloud Connector appliance are stored..  <br/> |
|[Get-CcApplianceStatus](get-ccappliancestatus.md) <br/> Version 2.1 and later  <br/> |Provides diagnostic information for the Cloud Connector appliance.  <br/> |
|[Get-CcCredential](get-cccredential.md) <br/> |Returns the credential of the current Cloud Connector deployment.  <br/> |
|[Get-CcExternalCertificateFilePath](get-ccexternalcertificatefilepath.md) <br/> |Returns the external certificate file path for the Cloud Connector deployment. The user prepares this certificate.  <br/> |
|[Get-CcSiteDirectory](get-ccsitedirectory.md) <br/> |Shows the current directory where site level configuration files are stored. The folder contains the base VHD and Cloud Connector installation files. This folder should be shared with all other appliances of a Cloud Connector site.  <br/> |
|[Get-CcSiteLogDirectory](get-ccsitelogdirectory.md) <br/> |Shows the current directory where the site level logs for Cloud Connector are stored.  <br/> |
|[Get-CcVersion](get-ccversion.md) <br/> Version 2.0 and later  <br/> |Returns the version on Cloud Connector instance. Get-CCVersion can only be used in the host machine of Cloud Connector.  <br/> |
|[Import-CcConfiguration](import-ccconfiguration.md) <br/> Version 2.0 and later  <br/> |Imports the Skype for Business Cloud Connector Edition configuration from a local file to the Cloud Connector host server.  <br/> |
|[Install-CcAppliance](install-ccappliance.md) <br/> |Installs the Cloud Connector appliance—including the AD, Central Management Store, Mediation Server, and Edge Server virtual machines—on the host server.  <br/> |
|[Publish-CcAppliance](publish-ccappliance.md) <br/> | Gets high availability information from the online tenant configuration and publishes it to the Cloud Connector appliance on the host server. <br/> |
|[Register-CcAppliance](register-ccappliance.md) <br/> | Registers appliance information to a PSTN site in an online tenant configuration. An appliance must be registered before it can be deployed and managed by the Cloud Connector management service. <br/> |
|[Remove-CcCertificationAuthorityFile](remove-cccertificationauthorityfile.md) <br/> Version 1.4.2 and later  <br/> |Removes the certification authority service backup file "\<SiteRootDirectory\>\CA\SfB CCE Root.p12" in the CA folder under the site share directory for Cloud Connector.  <br/> |
|[Remove-CcLegacyServerCertificate](remove-cclegacyservercertificate.md) <br/> Version 1.4.2 and later  <br/> |Removes legacy server certificates on the Central Management Store, Mediation Server, and Edge Server after you execute the Renew-CcCACertificate or Renew CcServerCertificate cmdlets.  <br/> |
|[Renew-CcCACertificate](renew-cccacertificate.md) <br/> Version 1.4.2 only  <br/> |Reinstalls the Certification Authority Service AD Server to create a new root CA certificate.  <br/> |
|[Renew-CcServerCertificate](renew-ccservercertificate.md) <br/> Version 1.4.2 only  <br/> |Renews the certificates for Cloud Connector when they are near expiration or already expired.  <br/> |
|[Reset-CcCACertificate](reset-cccacertificate.md) <br/> Version 1.4.2 and later  <br/> |Resets the certificate authority servers to install a new certificate authority certificate.  <br/> |
|[Restore-CcCredentials](restore-cccredentials.md) <br/> Version 2.1 and later  <br/> |Cleans up credentials and prompts you to re-enter all the credentials used for the current Cloud Connector deployment.  <br/> |
|[Search-CcLog](search-cclog.md) <br/> |Searches the incoming and outgoing call logs in the Cloud Connector appliance log directory  <br/> |
|[Set-CcApplianceDirectory](set-ccappliancedirectory.md) <br/> |Sets the working directory on the Cloud Connector host server. All deployment files are stored in this directory.  <br/> |
|[Set-CcCredential](set-cccredential.md) <br/> |Sets the credential of the current Cloud Connector deployment.  <br/> |
|[Set-CcExternalCertificateFilePath](set-ccexternalcertificatefilepath.md) <br/> |Specifies the path where the certificate for the Mediation Server or Edge Server is stored  <br/> |
|[Set-CcSiteDirectory](set-ccsitedirectory.md) <br/> |Sets the directory where site level configuration files for Cloud Connector will be stored. The folder will contain the base VHD and Cloud Connector configuration files.  <br/> |
|[Start-CcDownload](start-ccdownload.md) <br/> |Downloads the Cloud Connector bits and msi file synchronously.  <br/> |
|[Start-CcLogging](start-cclogging.md) <br/> |Generates the incoming and outgoing call log for a Cloud Connector appliance.  <br/> |
|[Stop-CcLogging](stop-cclogging.md) <br/> |Stops generating the incoming and outgoing call log for a Cloud Connector appliance.  <br/> |
|[Switch-CcVersion](switch-ccversion.md) <br/> |Disconnects the running appliance and switches to a newly deployed or backup appliance.  <br/> |
|[Uninstall-CcAppliance](uninstall-ccappliance.md) <br/> |Uninstalls the running Cloud Connector appliance from the host server.  <br/> |
|[Unregister-CcAppliance](unregister-ccappliance.md) <br/> |Unregisters the current Cloud Connector appliance from a PSTN site in the online tenant configuration.  <br/> |
|[Update-CcCACertificate](update-cccacertificate.md) <br/> Version 2.0 and later  <br/> |Reinstalls the Certification Authority Service AD Server to create a new root CA certificate.  <br/> |
|[Update-CcServerCertificate](update-ccservercertificate.md) <br/> Version 2.0 and later  <br/> |Renews the certificates for Cloud Connector when they are near expiration or already expired.  <br/> |
   

