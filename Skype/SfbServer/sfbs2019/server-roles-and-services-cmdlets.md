---
title: "Server roles and services cmdlets in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ff3561de-043e-4071-88f7-8de3cded52f6
description: "Many Microsoft Lync Server 2013 components run as server roles or as services. Lync Server 2013 ships with a number of cmdlets that enable you to manage these server roles and services."
---

# Server roles and services cmdlets in Lync Server 2013
[]
Many Microsoft Lync Server 2013 components run as server roles or as services. Lync Server 2013 ships with a number of cmdlets that enable you to manage these server roles and services.
  
## Server Roles and Services Cmdlets

Many (but not all) of the management tasks that apply to servers and service roles can be performed from the Lync Server Control Panel. For example, you can manage Archiving Server settings but not Address Book Server settings by using Lync Server Control Panel. However, all these tasks can be performed using cmdlets from the Lync Server Management Shell or from within a script; using a script enables you to automate certain tasks. The following is a list of cmdlets that relate directly to managing server roles and services:
  
 **[Address Book Server cmdlets in Lync Server 2013](address-book-server-cmdlets.md)**
  
> [Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)
    
> [New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)
    
> [Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)
    
> [Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)
    
> [Update-CsAddressBook](update-csaddressbook.md)
    
> [Debug-CsAddressBookReplication](debug-csaddressbookreplication.md)
    
> [Test-CsAddressBookService](test-csaddressbookservice.md)
    
> [Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)
    
 **[Archiving and Monitoring cmdlets in Lync Server 2013](archiving-and-monitoring-cmdlets.md)**
  
> [Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)
    
> [New-CsArchivingConfiguration](new-csarchivingconfiguration.md)
    
> [Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)
    
> [Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)
    
> [Export-CsArchivingData](export-csarchivingdata.md)
    
> [Invoke-CsArchivingDatabasePurge](invoke-csarchivingdatabasepurge.md)
    
> [Get-CsArchivingPolicy](get-csarchivingpolicy.md)
    
> [Grant-CsArchivingPolicy](grant-csarchivingpolicy.md)
    
> [New-CsArchivingPolicy](new-csarchivingpolicy.md)
    
> [Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)
    
> [Set-CsArchivingPolicy](set-csarchivingpolicy.md)
    
> [Set-CsArchivingServer](set-csarchivingserver.md)
    
> [Get-CsCdrConfiguration](get-cscdrconfiguration.md)
    
> [New-CsCdrConfiguration](new-cscdrconfiguration.md)
    
> [Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)
    
> [Set-CsCdrConfiguration](set-cscdrconfiguration.md)
    
> [Set-CsMonitoringServer](set-csmonitoringserver.md)
    
> [Get-CsQoEConfiguration](get-csqoeconfiguration.md)
    
> [New-CsQoEConfiguration](new-csqoeconfiguration.md)
    
> [Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)
    
> [Set-CsQoEConfiguration](set-csqoeconfiguration.md)
    
[Invoke-CsCdrDatabasePurge](invoke-cscdrdatabasepurge.md)
  
> [Export-CsArchivingData](export-csarchivingdata.md)
    
> [Invoke-CsQoEDatabasePurge](invoke-csqoedatabasepurge.md)
    
> [Get-CsReportingConfiguration](get-csreportingconfiguration.md)
    
> [New-CsReportingConfiguration](new-csreportingconfiguration.md)
    
> [Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)
    
> [Set-CsReportingConfiguration](set-csreportingconfiguration.md)
    
> [Get-CsTestUserCredential](get-cstestusercredential.md)
    
> [Remove-CsTestUserCredential](remove-cstestusercredential.md)
    
> [Set-CsTestUserCredential](set-cstestusercredential.md)
    
> [Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)
    
> [New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)
    
> [Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)
    
> [Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)
    
> [Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)
    
> [New-CsExtendedTest](new-csextendedtest.md)
    
 **[Database and Management Server cmdlets in Lync Server 2013](database-and-management-server-cmdlets.md)**
  
> [Get-CsConfigurationStoreLocation](get-csconfigurationstorelocation.md)
    
> [Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)
    
> [Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)
    
> [Install-CsDatabase](install-csdatabase.md)
    
> [Test-CsDatabase](test-csdatabase.md)
    
> [Uninstall-CsDatabase](uninstall-csdatabase.md)
    
- [Invoke-CsDatabaseFailover](invoke-csdatabasefailover.md)
    
- [Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)
    
- [Install-CsMirrorDatabase](install-csmirrordatabase.md)
    
- [Uninstall-CsMirrorDatabase](uninstall-csmirrordatabase.md)
    
> [Get-CsUserDatabaseState](get-csuserdatabasestate.md)
    
> [Set-CsUserDatabaseState](set-csuserdatabasestate.md)
    
> [Update-CsUserDatabase](update-csuserdatabase.md)
    
> [Move-CsManagementServer](move-csmanagementserver.md)
    
> [Set-CsManagementServer](set-csmanagementserver.md)
    
- [Invoke-CsManagementServerFailover](invoke-csmanagementserverfailover.md)
    
 **[Edge Server cmdlets in Lync Server 2013](edge-server-cmdlets.md)**
  
> [Get-CsAccessEdgeConfiguration](get-csaccessedgeconfiguration.md)
    
> [Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)
    
> [Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)
    
> [New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)
    
> [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)
    
> [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)
    
> [Test-CsAVEdgeConnectivity](test-csavedgeconnectivity.md)
    
> [Set-CsEdgeServer](set-csedgeserver.md)
    
 **[Other server role cmdlets in Lync Server 2013](other-server-role-cmdlets.md)**
  
> [Set-CsConferenceServer](set-csconferenceserver.md)
    
> [Set-CsUserServer](set-csuserserver.md)
    
 **[Registrar and Director cmdlets in Lync Server 2013](registrar-and-director-cmdlets.md)**
  
> [Set-CsDirector](set-csdirector.md)
    
> [Reset-CsPoolRegistrarState](reset-cspoolregistrarstate.md)
    
> [Set-CsRegistrar](set-csregistrar.md)
    
> [Get-CsRegistrarConfiguration](get-csregistrarconfiguration.md)
    
> [New-CsRegistrarConfiguration](new-csregistrarconfiguration.md)
    
> [Remove-CsRegistrarConfiguration](remove-csregistrarconfiguration.md)
    
> [Set-CsRegistrarConfiguration](set-csregistrarconfiguration.md)
    
> [Test-CsRegistration](test-csregistration.md)
    
 **[Services cmdlets in Lync Server 2013](services-cmdlets.md)**
  
> [Get-CsService](get-csservice.md)
    
> [Get-CsWindowsService](get-cswindowsservice.md)
    
> [Start-CsWindowsService](start-cswindowsservice.md)
    
> [Stop-CsWindowsService](stop-cswindowsservice.md)
    
 **[Troubleshooting server roles and services cmdlets in Lync Server 2013](troubleshooting-server-roles-and-services-cmdlets.md)**
  
> [Get-CsAudioTestServiceApplication](get-csaudiotestserviceapplication.md)
    
> [Set-CsAudioTestServiceApplication](set-csaudiotestserviceapplication.md)
    
> [Get-CsHealthMonitoringConfiguration](get-cshealthmonitoringconfiguration.md)
    
> [New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)
    
> [Remove-CsHealthMonitoringConfiguration](remove-cshealthmonitoringconfiguration.md)
    
> [Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)
    
> [Get-CsDiagnosticConfiguration](get-csdiagnosticconfiguration.md)
    
> [New-CsDiagnosticConfiguration](new-csdiagnosticconfiguration.md)
    
> [Remove-CsDiagnosticConfiguration](remove-csdiagnosticconfiguration.md)
    
> [Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)
    
> [New-CsDiagnosticsFilter](new-csdiagnosticsfilter.md)
    
> [Get-CsDiagnosticHeaderConfiguration](get-csdiagnosticheaderconfiguration.md)
    
> [New-CsDiagnosticHeaderConfiguration](new-csdiagnosticheaderconfiguration.md)
    
> [Remove-CsDiagnosticHeaderConfiguration](remove-csdiagnosticheaderconfiguration.md)
    
> [Set-CsDiagnosticHeaderConfiguration](set-csdiagnosticheaderconfiguration.md)
    
 **[Web server and services cmdlets in Lync Server 2013](web-server-and-services-cmdlets.md)**
  
> [New-CsSimpleUrl](new-cssimpleurl.md)
    
> [Get-CsSimpleUrlConfiguration](get-cssimpleurlconfiguration.md)
    
> [New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)
    
> [Remove-CsSimpleUrlConfiguration](remove-cssimpleurlconfiguration.md)
    
> [Set-CsSimpleUrlConfiguration](set-cssimpleurlconfiguration.md)
    
> [New-CsSimpleUrlEntry](new-cssimpleurlentry.md)
    
> [Set-CsWebServer](set-cswebserver.md)
    
> [Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)
    
> [New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)
    
> [Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)
    
> [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)
    
> [New-CsWebTrustedCACertificate](new-cswebtrustedcacertificate.md)
    
> [New-CsKerberosAccount](new-cskerberosaccount.md)
    
> [Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)
    
> [New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)
    
> [Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)
    
> [Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)
    
> [Test-CsKerberosAccountAssignment](test-cskerberosaccountassignment.md)
    
> [Set-CsKerberosAccountPassword](set-cskerberosaccountpassword.md)
    
- [Test-CsWebApp](test-cswebapp.md)
    
- [Test-CsWebAppAnonymous](test-cswebappanonymous.md)
    
## See also

#### 

[Lync Server PowerShell Blog](https://go.microsoft.com/fwlink/p/?linkId=203150)

