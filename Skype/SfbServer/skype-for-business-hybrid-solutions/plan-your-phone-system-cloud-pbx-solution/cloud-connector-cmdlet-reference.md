---
title: "Cloud Connector cmdlet reference"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 11/15/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 072b4bdc-0f1e-4fce-a41e-5c60d24556d5
description: "The following table lists the Skype for Business Cloud Connector Edition cmdlets with a brief description and links to more information."
---

# Cloud Connector cmdlet reference

> [!Important]
> Cloud Connector Edition will retire July 31, 2021 along with Skype for Business Online. Once your organization has upgraded to Teams, learn how to connect your on-premises telephony network to Teams using [Direct Routing](/MicrosoftTeams/direct-routing-landing-page).

The following table lists the Skype for Business Cloud Connector Edition cmdlets with a brief description and links to more information.
  
> [!NOTE]
> You must run all the cmdlets on the Cloud Connector host machine, and you must run the PowerShell session as Administrator. 
  
|Cmdlet name**|Description|
|---|---|
|[Backup-CcCertificationAuthority](backup-cccertificationauthority.md) <p> Version 1.4.2 and later|Backs up the certification authority service to a file and saves it to the CA folder under the site share directory.|
|[Convert-CcIsoToVhdx](convert-ccisotovhdx.md)|Creates a base virtual hard disk file (VHDX) using a customer supplied Windows Server 2012 R2 ISO file. The VHDX file will be used during the deployment ofCloud Connector.|
|[Enter-CcUpdate](enter-ccupdate.md)|Prepares the Cloud Connector host server for the update process by putting it in maintenance mode. The appliance is "drained"; that is, all existing calls will complete, but new calls are rejected.|
|[Exit-CcUpdate](exit-ccupdate.md)|Exits update maintenance mode on the Cloud Connector host server.|
|[Export-CcConfiguration](export-ccconfiguration.md)|Exports a Skype for Business Cloud Connector Edition configuration to a local file on the Skype for Business Cloud Connector Edition host server.|
|[Export-CcConfigurationSampleFile](export-ccconfigurationsamplefile.md)|Exports a Cloud Connector sample configuration file (.ini) to the appliance directory of a Cloud Connector appliance. You can modify and rename the file to use for your deployment.|
|[Export-CcRootCertificate](export-ccrootcertificate.md) <p> Version 1.4.2 and later|Exports the root CA certificate to a local file on the Cloud Connector host server.|
|[Get-CcApplianceDirectory](get-ccappliancedirectory.md)|Retrieves the working directory on the Cloud Connector host server. All deployment files are stored in this directory.|
|[Get-CcApplianceLogDirectory](get-ccappliancelogdirectory.md)|Shows the current directory where logs for a Cloud Connector appliance are stored.|
|[Get-CcApplianceStatus](get-ccappliancestatus.md) <p> Version 2.1 and later|Provides diagnostic information for the Cloud Connector appliance.|
|[Get-CcCredential](get-cccredential.md)|Returns the credential of the current Cloud Connector deployment.|
|[Get-CcExternalCertificateFilePath](get-ccexternalcertificatefilepath.md)|Returns the external certificate file path for the Cloud Connector deployment. The user prepares this certificate.|
|[Get-CcSiteDirectory](get-ccsitedirectory.md)|Shows the current directory where site level configuration files are stored. The folder contains the base VHD and Cloud Connector installation files. This folder should be shared with all other appliances of a Cloud Connector site.|
|[Get-CcSiteLogDirectory](get-ccsitelogdirectory.md)|Shows the current directory where the site level logs for Cloud Connector are stored.|
|[Get-CcVersion](get-ccversion.md) <p> Version 2.0 and later|Returns the version on Cloud Connector instance. Get-CCVersion can only be used in the host machine of Cloud Connector.|
|[Import-CcConfiguration](import-ccconfiguration.md) <p> Version 2.0 and later|Imports the Skype for Business Cloud Connector Edition configuration from a local file to the Cloud Connector host server.|
|[Install-CcAppliance](install-ccappliance.md)|Installs the Cloud Connector appliance—including the AD, Central Management Store, Mediation Server, and Edge Server virtual machines—on the host server.|
|[Publish-CcAppliance](publish-ccappliance.md)|Gets high availability information from the online tenant configuration and publishes it to the Cloud Connector appliance on the host server.|
|[Register-CcAppliance](register-ccappliance.md)|Registers appliance information to a PSTN site in an online tenant configuration. An appliance must be registered before it can be deployed and managed by the Cloud Connector management service.|
|[Remove-CcCertificationAuthorityFile](remove-cccertificationauthorityfile.md) <p> Version 1.4.2 and later|Removes the certification authority service backup file "\<SiteRootDirectory\>\CA\SfB CCE Root.p12" in the CA folder under the site share directory for Cloud Connector.|
|[Remove-CcLegacyServerCertificate](remove-cclegacyservercertificate.md) <p> Version 1.4.2 and later|Removes legacy server certificates on the Central Management Store, Mediation Server, and Edge Server after you execute the Renew-CcCACertificate or Renew CcServerCertificate cmdlets.|
|[Renew-CcCACertificate](renew-cccacertificate.md) <p> Version 1.4.2 only|Reinstalls the Certification Authority Service AD Server to create a new root CA certificate.|
|[Renew-CcServerCertificate](renew-ccservercertificate.md) <p> Version 1.4.2 only|Renews the certificates for Cloud Connector when they are near expiration or already expired.|
|[Reset-CcCACertificate](reset-cccacertificate.md) <p> Version 1.4.2 and later|Resets the certificate authority servers to install a new certificate authority certificate.|
|[Restore-CcCredentials](restore-cccredentials.md) <p> Version 2.1 and later|Cleans up credentials and prompts you to re-enter all the credentials used for the current Cloud Connector deployment.|
|[Search-CcLog](search-cclog.md)|Searches the incoming and outgoing call logs in the Cloud Connector appliance log directory|
|[Set-CcApplianceDirectory](set-ccappliancedirectory.md)|Sets the working directory on the Cloud Connector host server. All deployment files are stored in this directory.|
|[Set-CcCredential](set-cccredential.md)|Sets the credential of the current Cloud Connector deployment.|
|[Set-CcExternalCertificateFilePath](set-ccexternalcertificatefilepath.md)|Specifies the path where the certificate for the Mediation Server or Edge Server is stored|
|[Set-CcSiteDirectory](set-ccsitedirectory.md)|Sets the directory where site level configuration files for Cloud Connector will be stored. The folder will contain the base VHD and Cloud Connector configuration files.|
|[Start-CcDownload](start-ccdownload.md)|Downloads the Cloud Connector bits and msi file synchronously.|
|[Start-CcLogging](start-cclogging.md)|Generates the incoming and outgoing call log for a Cloud Connector appliance.|
|[Stop-CcLogging](stop-cclogging.md)|Stops generating the incoming and outgoing call log for a Cloud Connector appliance.|
|[Switch-CcVersion](switch-ccversion.md)|Disconnects the running appliance and switches to a newly deployed or backup appliance.|
|[Uninstall-CcAppliance](uninstall-ccappliance.md)|Uninstalls the running Cloud Connector appliance from the host server.|
|[Unregister-CcAppliance](unregister-ccappliance.md)|Unregisters the current Cloud Connector appliance from a PSTN site in the online tenant configuration.|
|[Update-CcCACertificate](update-cccacertificate.md) <p> Version 2.0 and later|Reinstalls the Certification Authority Service AD Server to create a new root CA certificate.|
|[Update-CcServerCertificate](update-ccservercertificate.md) <p> Version 2.0 and later|Renews the certificates for Cloud Connector when they are near expiration or already expired.|
