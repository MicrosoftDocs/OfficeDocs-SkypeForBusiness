---
title: "Skype for Business Server cmdlets index"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 9/20/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cd37aba7-3d27-4db9-b69f-3a6da1fb4b4a
description: "Skype for Business Server 2015 ships with more than 700 cmdlets that enable administrators to manage Skype for Business Server using the Skype for Business Server Management Shell. You can retrieve help for a cmdlet directly from the command line by typing a command similar to the following:"
---

# Skype for Business Server cmdlets index
[]
Skype for Business Server 2015 ships with more than 700 cmdlets that enable administrators to manage Skype for Business Server using the Skype for Business Server Management Shell. You can retrieve help for a cmdlet directly from the command line by typing a command similar to the following:
  
```
Get-Help New-CsVoicePolicy -Full
```

The preceding command retrieves the complete help available for the **New-CsVoicePolicy** cmdlet. To view help for a different cmdlet, substitute **New-CsVoicePolicy** with the name of the cmdlet for which you want to retrieve help.
  
To retrieve a full list of cmdlets available for managing Skype for Business Server, type the following at the shell command prompt: 
  
```
Get-Command * -Module SkypeforBusiness -CommandType cmdlet
```

## Skype for Business Server Cmdlets

Following is a list of the cmdlets that are included with Skype for Business Server:
  
> [!NOTE]
> Skype for Business cmdlet reference has moved to docs.microsoft.com. Clicking on the links below will take you to the new docs.microsoft.com page. The content is now open sourced and available for community contributions through GitHub. Interested in contributing? Check out the README in the repo here: [https://github.com/MicrosoftDocs/office-docs-powershell](https://github.com/MicrosoftDocs/office-docs-powershell)
  
- [Approve-CsDeviceUpdateRule](approve-csdeviceupdaterule.md)
    
- [Backup-CsPool](backup-cspool.md)
    
- [Clear-CsDeviceUpdateFile](clear-csdeviceupdatefile.md)
    
- [Clear-CsDeviceUpdateLog](clear-csdeviceupdatelog.md)
    
- [Clear-CsPersistentChatRoom](clear-cspersistentchatroom.md)
    
- [Convert-CsUserData](convert-csuserdata.md)
    
- [Debug-CsAddressBookReplication](debug-csaddressbookreplication.md)
    
- [Debug-CsDataConference](debug-csdataconference.md)
    
- [Debug-CsIntraPoolReplication](debug-csintrapoolreplication.md)
    
- [Debug-CsInterPoolReplication](debug-csinterpoolreplication.md)
    
- [Debug-CsLisConfiguration](debug-cslisconfiguration.md)
    
- [Debug-CsUnifiedContactStore](debug-csunifiedcontactstore.md)
    
- [Disable-CsAdDomain](disable-csaddomain.md)
    
- [Disable-CsAdForest](disable-csadforest.md)
    
- [Disable-CsComputer](disable-cscomputer.md)
    
- [Disable-CsHostingProvider](disable-cshostingprovider.md)
    
- [Disable-CsMeetingRoom](disable-csmeetingroom.md)
    
- [Disable-CsPublicProvider](disable-cspublicprovider.md)
    
- [Disable-CsUser](disable-csuser.md)
    
- [Enable-CsAdDomain](enable-csaddomain.md)
    
- [Enable-CsAdForest](enable-csadforest.md)
    
- [Enable-CsComputer](enable-cscomputer.md)
    
- [Enable-CsHostingProvider](enable-cshostingprovider.md)
    
- [Enable-CsMeetingRoom](enable-csmeetingroom.md)
    
- [Enable-CsPublicProvider](enable-cspublicprovider.md)
    
- [Enable-CsReplica](enable-csreplica.md)
    
- [Enable-CsTopology](enable-cstopology.md)
    
- [Enable-CsUser](enable-csuser.md)
    
- [Export-CsArchivingData](export-csarchivingdata.md)
    
- [Export-CsConfiguration](export-csconfiguration.md)
    
- [Export-CsLisConfiguration](export-cslisconfiguration.md)
    
- [Export-CsPersistentChatData](export-cspersistentchatdata.md)
    
- [Export-CsRgsConfiguration](export-csrgsconfiguration.md)
    
- [Export-CsUserData](export-csuserdata.md)
    
- [Get-CsAccessEdgeConfiguration](get-csaccessedgeconfiguration.md)
    
- [Get-CsAdContact](get-csadcontact.md)
    
- [Get-CsAdDomain](get-csaddomain.md)
    
- [Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)
    
- [Get-CsAddressBookNormalizationConfiguration](get-csaddressbooknormalizationconfiguration.md)
    
- [Get-CsAddressBookNormalizationRule](get-csaddressbooknormalizationrule.md)
    
- [Get-CsAdForest](get-csadforest.md)
    
- [Get-CsAdminRole](get-csadminrole.md)
    
- [Get-CsAdminRoleAssignment](get-csadminroleassignment.md)
    
- [Get-CsAdPrincipal](get-csadprincipal.md)
    
- [Get-CsAdServerSchema](get-csadserverschema.md)
    
- [Get-CsAdUser](get-csaduser.md)
    
- [Get-CsAllowedDomain](get-csalloweddomain.md)
    
- [Get-CsAnalogDevice](get-csanalogdevice.md)
    
- [Get-CsAnnouncement](get-csannouncement.md)
    
- [Get-CsApplicationEndpoint](get-csapplicationendpoint.md)
    
- [Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)
    
- [Get-CsArchivingPolicy](get-csarchivingpolicy.md)
    
- [Get-CsAudioTestServiceApplication](get-csaudiotestserviceapplication.md)
    
- [Get-CsAutodiscoverConfiguration](get-csautodiscoverconfiguration.md)
    
- [Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)
    
- [Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)
    
- [Get-CsBackupServiceStatus](get-csbackupservicestatus.md)
    
- [Get-CsBandwidthPolicyServiceConfiguration](get-csbandwidthpolicyserviceconfiguration.md)
    
- [Get-CsBlockedDomain](get-csblockeddomain.md)
    
- [Get-CsCallParkOrbit](get-cscallparkorbit.md)
    
- [Get-CsCallViaWorkPolicy](get-cscallviaworkpolicy.md)
    
- [Get-CsCdrConfiguration](get-cscdrconfiguration.md)
    
- [Get-CsCertificate](get-cscertificate.md)
    
- [Get-CsClientAccessLicense](get-csclientaccesslicense.md)
    
- [Get-CsClientCertificate](get-csclientcertificate.md)
    
- [Get-CsClientPinInfo](get-csclientpininfo.md)
    
- [Get-CsClientPolicy](get-csclientpolicy.md)
    
- [Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md)
    
- [Get-CsClientVersionPolicy](get-csclientversionpolicy.md)
    
- [Get-CsClientVersionPolicyRule](get-csclientversionpolicyrule.md)
    
- [Get-CsClsAgentStatus](get-csclsagentstatus.md)
    
- [Get-CsClsConfiguration](get-csclsconfiguration.md)
    
- [Get-CsClsRegion](get-csclsregion.md)
    
- [Get-CsClsSearchTerm](get-csclssearchterm.md)
    
- [Get-CsClsScenario](get-csclsscenario.md)
    
- [Get-CsClsSecurityGroup](get-csclssecuritygroup.md)
    
- [Get-CsCommonAreaPhone](get-cscommonareaphone.md)
    
- [Get-CsComputer](get-cscomputer.md)
    
- [Get-CsConferenceDirectory](get-csconferencedirectory.md)
    
- [Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md)
    
- [Get-CsConferencingConfiguration](get-csconferencingconfiguration.md)
    
- [Get-CsConferencingPolicy](get-csconferencingpolicy.md)
    
- [Get-CsConfigurationStoreLocation](get-csconfigurationstorelocation.md)
    
- [Get-CsConversationHistoryConfiguration](get-csconversationhistoryconfiguration.md)
    
- [Get-CsCpsConfiguration](get-cscpsconfiguration.md)
    
- [Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)
    
- [Get-CsDeviceUpdateConfiguration](get-csdeviceupdateconfiguration.md)
    
- [Get-CsDeviceUpdateRule](get-csdeviceupdaterule.md)
    
- [Get-CsDiagnosticConfiguration](get-csdiagnosticconfiguration.md)
    
- [Get-CsDiagnosticHeaderConfiguration](get-csdiagnosticheaderconfiguration.md)
    
- [Get-CsDialInConferencingAccessNumber](get-csdialinconferencingaccessnumber.md)
    
- [Get-CsDialInConferencingConfiguration](get-csdialinconferencingconfiguration.md)
    
- [Get-CsDialInConferencingDtmfConfiguration](get-csdialinconferencingdtmfconfiguration.md)
    
- [Get-CsDialInConferencingLanguageList](get-csdialinconferencinglanguagelist.md)
    
- [Get-CsDialPlan](get-csdialplan.md)
    
- [Get-CsEffectivePolicy](get-cseffectivepolicy.md)
    
- [Get-CsEnhancedEmergencyServiceDisclaimer](get-csenhancedemergencyservicedisclaimer.md)
    
- [Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)
    
- [Get-CsExUmContact](get-csexumcontact.md)
    
- [Get-CsFileTransferFilterConfiguration](get-csfiletransferfilterconfiguration.md)
    
- [Get-CsFIPSConfiguration](get-csfipsconfiguration.md)
    
- [Get-CsGroupPickupUserOrbit](get-csgrouppickupuserorbit.md)
    
- [Get-CsHealthMonitoringConfiguration](get-cshealthmonitoringconfiguration.md)
    
- [Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)
    
- [Get-CsHostingProvider](get-cshostingprovider.md)
    
- [Get-CsImConfiguration](get-csimconfiguration.md)
    
- [Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)
    
- [Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)
    
- [Get-CsLisCivicAddress](get-csliscivicaddress.md)
    
- [Get-CsLisLocation](get-cslislocation.md)
    
- [Get-CsLisPort](get-cslisport.md)
    
- [Get-CsLisServiceProvider](get-cslisserviceprovider.md)
    
- [Get-CsLisSubnet](get-cslissubnet.md)
    
- [Get-CsLisSwitch](get-cslisswitch.md)
    
- [Get-CsLisWirelessAccessPoint](get-csliswirelessaccesspoint.md)
    
- [Get-CsLocationPolicy](get-cslocationpolicy.md)
    
- [Get-CsManagementConnection](get-csmanagementconnection.md)
    
- [Get-CsManagementStoreReplicationStatus](get-csmanagementstorereplicationstatus.md)
    
- [Get-CsMcxConfiguration](get-csmcxconfiguration.md)
    
- [Get-CsMediaConfiguration](get-csmediaconfiguration.md)
    
- [Get-CsMeetingConfiguration](get-csmeetingconfiguration.md)
    
- [Get-CsMeetingRoom](get-csmeetingroom.md)
    
- [Get-CsMobilityPolicy](get-csmobilitypolicy.md)
    
- [Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)
    
- [Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)
    
- [Get-CsNetworkInterface](get-csnetworkinterface.md)
    
- [Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)
    
- [Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)
    
- [Get-CsNetworkRegion](get-csnetworkregion.md)
    
- [Get-CsNetworkRegionLink](get-csnetworkregionlink.md)
    
- [Get-CsNetworkSite](get-csnetworksite.md)
    
- [Get-CsNetworkSubnet](get-csnetworksubnet.md)
    
- [Get-CsOAuthConfiguration](get-csoauthconfiguration.md)
    
- [Get-CsOAuthServer](get-csoauthserver.md)
    
- [Get-CsOutboundCallingNumberTranslationRule](get-csoutboundcallingnumbertranslationrule.md)
    
- [Get-CsOutboundTranslationRule](get-csoutboundtranslationrule.md)
    
- [Get-CsPartnerApplication](get-cspartnerapplication.md)
    
- [Get-CsPersistentChatAddin](get-cspersistentchataddin.md)
    
- [Get-CsPersistentChatCategory](get-cspersistentchatcategory.md)
    
- [Get-CsPersistentChatComplianceConfiguration](get-cspersistentchatcomplianceconfiguration.md)
    
- [Get-CsPersistentChatConfiguration](get-cspersistentchatconfiguration.md)
    
- [Get-CsPersistentChatEligiblePrincipal](get-cspersistentchateligibleprincipal.md)
    
- [Get-CsPersistentChatEndpoint](get-cspersistentchatendpoint.md)
    
- [Get-CsPersistentChatPolicy](get-cspersistentchatpolicy.md)
    
- [Get-CsPersistentChatRoom](get-cspersistentchatroom.md)
    
- [Get-CsPersistentChatState](get-cspersistentchatstate.md)
    
- [Get-CsPinPolicy](get-cspinpolicy.md)
    
- [Get-CsPool](get-cspool.md)
    
- [Get-CsPoolBackupRelationship](get-cspoolbackuprelationship.md)
    
- [Get-CsPoolFabricState](get-cspoolfabricstate.md)
    
- [Get-CsPoolUpgradeReadinessState](get-cspoolupgradereadinessstate.md)
    
- [Get-CsPresencePolicy](get-cspresencepolicy.md)
    
- [Get-CsPresenceProvider](get-cspresenceprovider.md)
    
- [Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)
    
- [Get-CsPresenceManagementState](get-cspresencemanagementstate.md)
    
- [Set-CsPresenceManagementState](set-cspresencemanagementstate.md)
    
- [Get-CsProxyConfiguration](get-csproxyconfiguration.md)
    
- [Get-CsPstnUsage](get-cspstnusage.md)
    
- [Get-CsPublicProvider](get-cspublicprovider.md)
    
- [Get-CsPushNotificationConfiguration](get-cspushnotificationconfiguration.md)
    
- [Get-CsQoEConfiguration](get-csqoeconfiguration.md)
    
- [Get-CsRegistrarConfiguration](get-csregistrarconfiguration.md)
    
- [Get-CsReportingConfiguration](get-csreportingconfiguration.md)
    
- [Get-CsRgsAgentGroup](get-csrgsagentgroup.md)
    
- [Get-CsRgsConfiguration](get-csrgsconfiguration.md)
    
- [Get-CsRgsHolidaySet](get-csrgsholidayset.md)
    
- [Get-CsRgsHoursOfBusiness](get-csrgshoursofbusiness.md)
    
- [Get-CsRgsQueue](get-csrgsqueue.md)
    
- [Get-CsRgsWorkflow](get-csrgsworkflow.md)
    
- [Get-CsRoutingConfiguration](get-csroutingconfiguration.md)
    
- [Get-CsServerApplication](get-csserverapplication.md)
    
- [Get-CsServerVersion](get-csserverversion.md)
    
- [Get-CsService](get-csservice.md)
    
- [Get-CsSimpleUrlConfiguration](get-cssimpleurlconfiguration.md)
    
- [Get-CsSipDomain](get-cssipdomain.md)
    
- [Get-CsSipResponseCodeTranslationRule](get-cssipresponsecodetranslationrule.md)
    
- [Get-CsSite](get-cssite.md)
    
- [Get-CsStaticRoutingConfiguration](get-csstaticroutingconfiguration.md)
    
- [Get-CsStorageServiceConfiguration](get-csstorageserviceconfiguration.md)
    
- [Get-CsTelemetryConfiguration](get-cstelemetryconfiguration.md)
    
- [Get-CsTestDevice](get-cstestdevice.md)
    
- [Get-CsTestUserCredential](get-cstestusercredential.md)
    
- [Get-CsThirdPartyVideoSystem](get-csthirdpartyvideosystem.md)
    
- [Get-CsThirdPartyVideoSystemPolicy](get-csthirdpartyvideosystempolicy.md)
    
- [Get-CsTopology](get-cstopology.md)
    
- [Get-CsTrunk](get-cstrunk.md)
    
- [Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)
    
- [Get-CsTrustedApplication](get-cstrustedapplication.md)
    
- [Get-CsTrustedApplicationComputer](get-cstrustedapplicationcomputer.md)
    
- [Get-CsTrustedApplicationEndpoint](get-cstrustedapplicationendpoint.md)
    
- [Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)
    
- [Get-CsUCPhoneConfiguration](get-csucphoneconfiguration.md)
    
- [Get-CsUICulture](get-csuiculture.md)
    
- [Get-CsUnassignedNumber](get-csunassignednumber.md)
    
- [Get-CsUser](get-csuser.md)
    
- [Get-CsUserAcp](get-csuseracp.md)
    
- [Get-CsUserDatabaseState](get-csuserdatabasestate.md)
    
- [Get-CsUserPoolInfo](get-csuserpoolinfo.md)
    
- [Get-CsUserReplicatorConfiguration](get-csuserreplicatorconfiguration.md)
    
- [Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)
    
- [Get-CsUserServicesPolicy](get-csuserservicespolicy.md)
    
- [Get-CsVideoInteropServerConfiguration](get-csvideointeropserverconfiguration.md)
    
- [Get-CsVideoInteropServerSyntheticTransactionConfiguration](get-csvideointeropserversynthetictransactionconfiguration.md)
    
- [Get-CsVideoTrunk](get-csvideotrunk.md)
    
- [Get-CsVideoTrunkConfiguration](get-csvideotrunkconfiguration.md)
    
- [Get-CsVoiceConfiguration](get-csvoiceconfiguration.md)
    
- [Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)
    
- [Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)
    
- [Get-CsVoicePolicy](get-csvoicepolicy.md)
    
- [Get-CsVoiceRoute](get-csvoiceroute.md)
    
- [Get-CsVoiceRoutingPolicy](get-csvoiceroutingpolicy.md)
    
- [Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)
    
- [Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)
    
- [Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)
    
- [Get-CsWindowsService](get-cswindowsservice.md)
    
- [Get-CsXmppAllowedPartner](get-csxmppallowedpartner.md)
    
- [Get-CsXmppGatewayConfiguration](get-csxmppgatewayconfiguration.md)
    
- [Grant-CsArchivingPolicy](grant-csarchivingpolicy.md)
    
- [Grant-CsCallViaWorkPolicy](grant-cscallviaworkpolicy.md)
    
- [Grant-CsClientPolicy](grant-csclientpolicy.md)
    
- [Grant-CsClientVersionPolicy](grant-csclientversionpolicy.md)
    
- [Grant-CsConferencingPolicy](grant-csconferencingpolicy.md)
    
- [Grant-CsDialPlan](grant-csdialplan.md)
    
- [Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md)
    
- [Grant-CsHostedVoicemailPolicy](grant-cshostedvoicemailpolicy.md)
    
- [Grant-CsLocationPolicy](grant-cslocationpolicy.md)
    
- [Grant-CsMobilityPolicy](grant-csmobilitypolicy.md)
    
- [Grant-CsOUPermission](grant-csoupermission.md)
    
- [Grant-CsPersistentChatPolicy](grant-cspersistentchatpolicy.md)
    
- [Grant-CsPinPolicy](grant-cspinpolicy.md)
    
- [Grant-CsPresencePolicy](grant-cspresencepolicy.md)
    
- [Grant-CsSetupPermission](grant-cssetuppermission.md)
    
- [Grant-CsThirdPartyVideoSystemPolicy](grant-csthirdpartyvideosystempolicy.md)
    
- [Grant-CsUserServicesPolicy](grant-csuserservicespolicy.md)
    
- [Grant-CsVoicePolicy](grant-csvoicepolicy.md)
    
- [Grant-CsVoiceRoutingPolicy](grant-csvoiceroutingpolicy.md)
    
- [Import-CsAnnouncementFile](import-csannouncementfile.md)
    
- [Import-CsCertificate](import-cscertificate.md)
    
- [Import-CsCompanyPhoneNormalizationRules](import-cscompanyphonenormalizationrules.md)
    
- [Import-CsConfiguration](import-csconfiguration.md)
    
- [Import-CsDeviceUpdate](import-csdeviceupdate.md)
    
- [Import-CsLegacyConferenceDirectory](import-cslegacyconferencedirectory.md)
    
- [Import-CsLegacyConfiguration](import-cslegacyconfiguration.md)
    
- [Import-CsLisConfiguration](import-cslisconfiguration.md)
    
- [Import-CsPersistentChatData](import-cspersistentchatdata.md)
    
- [Import-CsRgsAudioFile](import-csrgsaudiofile.md)
    
- [Import-CsRgsConfiguration](import-csrgsconfiguration.md)
    
- [Import-CsUserData](import-csuserdata.md)
    
- [Install-CsAdServerSchema](install-csadserverschema.md)
    
- [Install-CsDatabase](install-csdatabase.md)
    
- [Install-CsMirrorDatabase](install-csmirrordatabase.md)
    
- [Invoke-CsArchivingDatabasePurge](invoke-csarchivingdatabasepurge.md)
    
- [Invoke-CsBackupServiceSync](invoke-csbackupservicesync.md)
    
- [Invoke-CsCdrDatabasePurge](invoke-cscdrdatabasepurge.md)
    
- [Invoke-CsComputerFailBack](invoke-cscomputerfailback.md)
    
- [Invoke-CsComputerFailOver](invoke-cscomputerfailover.md)
    
- [Invoke-CsDatabaseFailover](invoke-csdatabasefailover.md)
    
- [Invoke-CsManagementServerFailover](invoke-csmanagementserverfailover.md)
    
- [Invoke-CsManagementStoreReplication](invoke-csmanagementstorereplication.md)
    
- [Invoke-CsPoolFailBack](invoke-cspoolfailback.md)
    
- [Invoke-CsPoolFailOver](invoke-cspoolfailover.md)
    
- [Invoke-CsQoEDatabasePurge](invoke-csqoedatabasepurge.md)
    
- [Invoke-CsStorageServiceFlush](invoke-csstorageserviceflush.md)
    
- [Invoke-CsUcsRollback](invoke-csucsrollback.md)
    
- [Lock-CsClientPin](lock-csclientpin.md)
    
- [Merge-CsLegacyTopology](merge-cslegacytopology.md)
    
- [Move-CsAnalogDevice](move-csanalogdevice.md)
    
- [Move-CsApplicationEndpoint](move-csapplicationendpoint.md)
    
- [Move-CsCommonAreaPhone](move-cscommonareaphone.md)
    
- [Move-CsConferenceDirectory](move-csconferencedirectory.md)
    
- [Move-CsExUmContact](move-csexumcontact.md)
    
- [Move-CsLegacyUser](move-cslegacyuser.md)
    
- [Move-CsManagementServer](move-csmanagementserver.md)
    
- [Move-CsMeetingRoom](move-csmeetingroom.md)
    
- [Move-CsRgsConfiguration](move-csrgsconfiguration.md)
    
- [Move-CsThirdPartyVideoSystem](move-csthirdpartyvideosystem.md)
    
- [Move-CsUser](move-csuser.md)
    
- [New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)
    
- [New-CsAddressBookNormalizationConfiguration](new-csaddressbooknormalizationconfiguration.md)
    
- [New-CsAddressBookNormalizationRule](new-csaddressbooknormalizationrule.md)
    
- [New-CsAdminRole](new-csadminrole.md)
    
- [New-CsAllowedDomain](new-csalloweddomain.md)
    
- [New-CsAnalogDevice](new-csanalogdevice.md)
    
- [New-CsAnnouncement](new-csannouncement.md)
    
- [New-CsArchivingConfiguration](new-csarchivingconfiguration.md)
    
- [New-CsArchivingPolicy](new-csarchivingpolicy.md)
    
- [New-CsAutodiscoverConfiguration](new-csautodiscoverconfiguration.md)
    
- [New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)
    
- [New-CsBandwidthPolicyServiceConfiguration](new-csbandwidthpolicyserviceconfiguration.md)
    
- [New-CsBlockedDomain](new-csblockeddomain.md)
    
- [New-CsCallParkOrbit](new-cscallparkorbit.md)
    
- [New-CsCallViaWorkPolicy](new-cscallviaworkpolicy.md)
    
- [New-CsCdrConfiguration](new-cscdrconfiguration.md)
    
- [New-CsClientPolicy](new-csclientpolicy.md)
    
- [New-CsClientPolicyEntry](new-csclientpolicyentry.md)
    
- [New-CsClientVersionConfiguration](new-csclientversionconfiguration.md)
    
- [New-CsClientVersionPolicy](new-csclientversionpolicy.md)
    
- [New-CsClientVersionPolicyRule](new-csclientversionpolicyrule.md)
    
- [New-CsClsRegion](new-csclsregion.md)
    
- [New-CsClsConfiguration](new-csclsconfiguration.md)
    
- [New-CsClsProvider](new-csclsprovider.md)
    
- [New-CsClsScenario](new-csclsscenario.md)
    
- [New-CsClsSecurityGroup](new-csclssecuritygroup.md)
    
- [New-CsCommonAreaPhone](new-cscommonareaphone.md)
    
- [New-CsConferenceDirectory](new-csconferencedirectory.md)
    
- [New-CsConferencingConfiguration](new-csconferencingconfiguration.md)
    
- [New-CsConferencingPolicy](new-csconferencingpolicy.md)
    
- [New-CsCpsConfiguration](new-cscpsconfiguration.md)
    
- [New-CsDeviceUpdateConfiguration](new-csdeviceupdateconfiguration.md)
    
- [New-CsDiagnosticConfiguration](new-csdiagnosticconfiguration.md)
    
- [New-CsDiagnosticHeaderConfiguration](new-csdiagnosticheaderconfiguration.md)
    
- [New-CsDiagnosticsFilter](new-csdiagnosticsfilter.md)
    
- [New-CsDialInConferencingAccessNumber](new-csdialinconferencingaccessnumber.md)
    
- [New-CsDialInConferencingConfiguration](new-csdialinconferencingconfiguration.md)
    
- [New-CsDialInConferencingDtmfConfiguration](new-csdialinconferencingdtmfconfiguration.md)
    
- [New-CsDialPlan](new-csdialplan.md)
    
- [New-CsExtendedTest](new-csextendedtest.md)
    
- [New-CsExternalAccessPolicy](new-csexternalaccesspolicy.md)
    
- [New-CsExUmContact](new-csexumcontact.md)
    
- [New-CsFileTransferFilterConfiguration](new-csfiletransferfilterconfiguration.md)
    
- [New-CsFIPSConfiguration](new-csfipsconfiguration.md)
    
- [New-CsGroupPickupUserOrbit](new-csgrouppickupuserorbit.md)
    
- [New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)
    
- [New-CsHostedVoicemailPolicy](new-cshostedvoicemailpolicy.md)
    
- [New-CsHostingProvider](new-cshostingprovider.md)
    
- [New-CsImConfiguration](new-csimconfiguration.md)
    
- [New-CsImFilterConfiguration](new-csimfilterconfiguration.md)
    
- [New-CsIssuedCertId](new-csissuedcertid.md)
    
- [New-CsKerberosAccount](new-cskerberosaccount.md)
    
- [New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)
    
- [New-CsLocationPolicy](new-cslocationpolicy.md)
    
- [New-CsMcxConfiguration](new-csmcxconfiguration.md)
    
- [New-CsMediaConfiguration](new-csmediaconfiguration.md)
    
- [New-CsMeetingConfiguration](new-csmeetingconfiguration.md)
    
- [New-CsMobilityPolicy](new-csmobilitypolicy.md)
    
- [New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)
    
- [New-CsNetworkBWAlternatePath](new-csnetworkbwalternatepath.md)
    
- [New-CsNetworkBWPolicy](new-csnetworkbwpolicy.md)
    
- [New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)
    
- [New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)
    
- [New-CsNetworkMediaBypassConfiguration](new-csnetworkmediabypassconfiguration.md)
    
- [New-CsNetworkRegion](new-csnetworkregion.md)
    
- [New-CsNetworkRegionLink](new-csnetworkregionlink.md)
    
- [New-CsNetworkSite](new-csnetworksite.md)
    
- [New-CsNetworkSubnet](new-csnetworksubnet.md)
    
- [New-CsOAuthServer](new-csoauthserver.md)
    
- [New-CsOutboundCallingNumberTranslationRule](new-csoutboundcallingnumbertranslationrule.md)
    
- [New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)
    
- [New-CsPartnerApplication](new-cspartnerapplication.md)
    
- [New-CsPersistentChatAddin](new-cspersistentchataddin.md)
    
- [New-CsPersistentChatCategory](new-cspersistentchatcategory.md)
    
- [New-CsPersistentChatComplianceConfiguration](new-cspersistentchatcomplianceconfiguration.md)
    
- [New-CsPersistentChatConfiguration](new-cspersistentchatconfiguration.md)
    
- [New-CsPersistentChatEndpoint](new-cspersistentchatendpoint.md)
    
- [New-CsPersistentChatPolicy](new-cspersistentchatpolicy.md)
    
- [New-CsPersistentChatRoom](new-cspersistentchatroom.md)
    
- [New-CsPinPolicy](new-cspinpolicy.md)
    
- [New-CsPresencePolicy](new-cspresencepolicy.md)
    
- [New-CsPresenceProvider](new-cspresenceprovider.md)
    
- [New-CsPrivacyConfiguration](new-csprivacyconfiguration.md)
    
- [New-CsProxyConfiguration](new-csproxyconfiguration.md)
    
- [New-CsPublicProvider](new-cspublicprovider.md)
    
- [New-CsPushNotificationConfiguration](new-cspushnotificationconfiguration.md)
    
- [New-CsQoEConfiguration](new-csqoeconfiguration.md)
    
- [New-CsRegistrarConfiguration](new-csregistrarconfiguration.md)
    
- [New-CsReportingConfiguration](new-csreportingconfiguration.md)
    
- [New-CsRgsAgentGroup](new-csrgsagentgroup.md)
    
- [New-CsRgsAnswer](new-csrgsanswer.md)
    
- [New-CsRgsCallAction](new-csrgscallaction.md)
    
- [New-CsRgsHoliday](new-csrgsholiday.md)
    
- [New-CsRgsHolidaySet](new-csrgsholidayset.md)
    
- [New-CsRgsHoursOfBusiness](new-csrgshoursofbusiness.md)
    
- [New-CsRgsPrompt](new-csrgsprompt.md)
    
- [New-CsRgsQuestion](new-csrgsquestion.md)
    
- [New-CsRgsQueue](new-csrgsqueue.md)
    
- [New-CsRgsTimeRange](new-csrgstimerange.md)
    
- [New-CsRgsWorkflow](new-csrgsworkflow.md)
    
- [New-CsRoutingConfiguration](new-csroutingconfiguration.md)
    
- [New-CsServerApplication](new-csserverapplication.md)
    
- [New-CsSimpleUrl](new-cssimpleurl.md)
    
- [New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)
    
- [New-CsSimpleUrlEntry](new-cssimpleurlentry.md)
    
- [New-CsSipDomain](new-cssipdomain.md)
    
- [New-CsSipProxyCustom](new-cssipproxycustom.md)
    
- [New-CsSipProxyRealm](new-cssipproxyrealm.md)
    
- [New-CsSipProxyTCP](new-cssipproxytcp.md)
    
- [New-CsSipProxyTLS](new-cssipproxytls.md)
    
- [New-CsSipProxyTransport](new-cssipproxytransport.md)
    
- [New-CsSipProxyUseDefault](new-cssipproxyusedefault.md)
    
- [New-CsSipProxyUseDefaultCert](new-cssipproxyusedefaultcert.md)
    
- [New-CsSipResponseCodeTranslationRule](new-cssipresponsecodetranslationrule.md)
    
- [New-CsStaticRoute](new-csstaticroute.md)
    
- [New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)
    
- [New-CsStorageServiceConfiguration](new-csstorageserviceconfiguration.md)
    
- [New-CsTelemetryConfiguration](new-cstelemetryconfiguration.md)
    
- [New-CsTestDevice](new-cstestdevice.md)
    
- [New-CsThirdPartyVideoSystem](new-csthirdpartyvideosystem.md)
    
- [New-CsThirdPartyVideoSystemPolicy](new-csthirdpartyvideosystempolicy.md)
    
- [New-CsTrunkConfiguration](new-cstrunkconfiguration.md)
    
- [New-CsTrustedApplication](new-cstrustedapplication.md)
    
- [New-CsTrustedApplicationComputer](new-cstrustedapplicationcomputer.md)
    
- [New-CsTrustedApplicationEndpoint](new-cstrustedapplicationendpoint.md)
    
- [New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)
    
- [New-CsUCPhoneConfiguration](new-csucphoneconfiguration.md)
    
- [New-CsUnassignedNumber](new-csunassignednumber.md)
    
- [New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)
    
- [New-CsUserServicesConfiguration](new-csuserservicesconfiguration.md)
    
- [New-CsUserServicesPolicy](new-csuserservicespolicy.md)
    
- [New-CsVideoInteropServerConfiguration](new-csvideointeropserverconfiguration.md)
    
- [New-CsVideoInteropServerSyntheticTransactionConfiguration](new-csvideointeropserversynthetictransactionconfiguration.md)
    
- [New-CsVideoTrunkConfiguration](new-csvideotrunkconfiguration.md)
    
- [New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)
    
- [New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)
    
- [New-CsVoicePolicy](new-csvoicepolicy.md)
    
- [New-CsVoiceRegex](new-csvoiceregex.md)
    
- [New-CsVoiceRoute](new-csvoiceroute.md)
    
- [New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)
    
- [New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)
    
- [New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)
    
- [New-CsWebLink](new-csweblink.md)
    
- [New-CsWebOrigin](new-csweborigin.md)
    
- [New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)
    
- [New-CsWebTrustedCACertificate](new-cswebtrustedcacertificate.md)
    
- [New-CsXmppAllowedPartner](new-csxmppallowedpartner.md)
    
- [Publish-CsLisConfiguration](publish-cslisconfiguration.md)
    
- [Publish-CsTopology](publish-cstopology.md)
    
- [Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)
    
- [Remove-CsAddressBookNormalizationConfiguration](remove-csaddressbooknormalizationconfiguration.md)
    
- [Remove-CsAddressBookNormalizationRule](remove-csaddressbooknormalizationrule.md)
    
- [Remove-CsAdminRole](remove-csadminrole.md)
    
- [Remove-CsAllowedDomain](remove-csalloweddomain.md)
    
- [Remove-CsAnalogDevice](remove-csanalogdevice.md)
    
- [Remove-CsAnnouncement](remove-csannouncement.md)
    
- [Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)
    
- [Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)
    
- [Remove-CsAutodiscoverConfiguration](remove-csautodiscoverconfiguration.md)
    
- [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)
    
- [Remove-CsBackupServiceConfiguration](remove-csbackupserviceconfiguration.md)
    
- [Remove-CsBandwidthPolicyServiceConfiguration](remove-csbandwidthpolicyserviceconfiguration.md)
    
- [Remove-CsBlockedDomain](remove-csblockeddomain.md)
    
- [Remove-CsCallParkOrbit](remove-cscallparkorbit.md)
    
- [Remove-CsCallViaWorkPolicy](remove-cscallviaworkpolicy.md)
    
- [Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)
    
- [Remove-CsCertificate](remove-cscertificate.md)
    
- [Remove-CsClientPolicy](remove-csclientpolicy.md)
    
- [Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md)
    
- [Remove-CsClientVersionPolicy](remove-csclientversionpolicy.md)
    
- [Remove-CsClientVersionPolicyRule](remove-csclientversionpolicyrule.md)
    
- [Remove-CsClsConfiguration](remove-csclsconfiguration.md)
    
- [Remove-CsClsRegion](remove-csclsregion.md)
    
- [Remove-CsClsScenario](remove-csclsscenario.md)
    
- [Remove-CsClsSecurityGroup](remove-csclssecuritygroup.md)
    
- [Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)
    
- [Remove-CsConferenceDirectory](remove-csconferencedirectory.md)
    
- [Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)
    
- [Remove-CsConferencingConfiguration](remove-csconferencingconfiguration.md)
    
- [Remove-CsConferencingPolicy](remove-csconferencingpolicy.md)
    
- [Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)
    
- [Remove-CsConversationHistoryConfiguration](remove-csconversationhistoryconfiguration.md)
    
- [Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)
    
- [Remove-CsDeviceUpdateConfiguration](remove-csdeviceupdateconfiguration.md)
    
- [Remove-CsDeviceUpdateRule](remove-csdeviceupdaterule.md)
    
- [Remove-CsDiagnosticConfiguration](remove-csdiagnosticconfiguration.md)
    
- [Remove-CsDiagnosticHeaderConfiguration](remove-csdiagnosticheaderconfiguration.md)
    
- [Remove-CsDialInConferencingAccessNumber](remove-csdialinconferencingaccessnumber.md)
    
- [Remove-CsDialInConferencingConfiguration](remove-csdialinconferencingconfiguration.md)
    
- [Remove-CsDialInConferencingDtmfConfiguration](remove-csdialinconferencingdtmfconfiguration.md)
    
- [Remove-CsDialPlan](remove-csdialplan.md)
    
- [Remove-CsEnhancedEmergencyServiceDisclaimer](remove-csenhancedemergencyservicedisclaimer.md)
    
- [Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md)
    
- [Remove-CsExUmContact](remove-csexumcontact.md)
    
- [Remove-CsFileTransferFilterConfiguration](remove-csfiletransferfilterconfiguration.md)
    
- [Remove-CsFIPSConfiguration](remove-csfipsconfiguration.md)
    
- [Remove-CsGroupPickupUserOrbit](remove-csgrouppickupuserorbit.md)
    
- [Remove-CsHealthMonitoringConfiguration](remove-cshealthmonitoringconfiguration.md)
    
- [Remove-CsHostedVoicemailPolicy](remove-cshostedvoicemailpolicy.md)
    
- [Remove-CsHostingProvider](remove-cshostingprovider.md)
    
- [Remove-CsImConfiguration](remove-csimconfiguration.md)
    
- [Remove-CsImFilterConfiguration](remove-csimfilterconfiguration.md)
    
- [Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)
    
- [Remove-CsLisLocation](remove-cslislocation.md)
    
- [Remove-CsLisPort](remove-cslisport.md)
    
- [Remove-CsLisServiceProvider](remove-cslisserviceprovider.md)
    
- [Remove-CsLisSubnet](remove-cslissubnet.md)
    
- [Remove-CsLisSwitch](remove-cslisswitch.md)
    
- [Remove-CsLisWirelessAccessPoint](remove-csliswirelessaccesspoint.md)
    
- [Remove-CsLocationPolicy](remove-cslocationpolicy.md)
    
- [Remove-CsManagementConnection](remove-csmanagementconnection.md)
    
- [Remove-CsMcxConfiguration](remove-csmcxconfiguration.md)
    
- [Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)
    
- [Remove-CsMeetingConfiguration](remove-csmeetingconfiguration.md)
    
- [Remove-CsMobilityPolicy](remove-csmobilitypolicy.md)
    
- [Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)
    
- [Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)
    
- [Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)
    
- [Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)
    
- [Remove-CsNetworkRegion](remove-csnetworkregion.md)
    
- [Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)
    
- [Remove-CsNetworkSite](remove-csnetworksite.md)
    
- [Remove-CsNetworkSubnet](remove-csnetworksubnet.md)
    
- [Remove-CsOAuthServer](remove-csoauthserver.md)
    
- [Remove-CsOutboundCallingNumberTranslationRule](remove-csoutboundcallingnumbertranslationrule.md)
    
- [Remove-CsOutboundTranslationRule](remove-csoutboundtranslationrule.md)
    
- [Remove-CsPartnerApplication](remove-cspartnerapplication.md)
    
- [Remove-CsPersistentChatAddin](remove-cspersistentchataddin.md)
    
- [Remove-CsPersistentChatCategory](remove-cspersistentchatcategory.md)
    
- [Remove-CsPersistentChatComplianceConfiguration](remove-cspersistentchatcomplianceconfiguration.md)
    
- [Remove-CsPersistentChatConfiguration](remove-cspersistentchatconfiguration.md)
    
- [Remove-CsPersistentChatEndpoint](remove-cspersistentchatendpoint.md)
    
- [Remove-CsPersistentChatMessage](remove-cspersistentchatmessage.md)
    
- [Remove-CsPersistentChatPolicy](remove-cspersistentchatpolicy.md)
    
- [Remove-CsPersistentChatRoom](remove-cspersistentchatroom.md)
    
- [Remove-CsPinPolicy](remove-cspinpolicy.md)
    
- [Remove-CsPresencePolicy](remove-cspresencepolicy.md)
    
- [Remove-CsPresenceProvider](remove-cspresenceprovider.md)
    
- [Remove-CsPrivacyConfiguration](remove-csprivacyconfiguration.md)
    
- [Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)
    
- [Remove-CsPublicProvider](remove-cspublicprovider.md)
    
- [Remove-CsPushNotificationConfiguration](remove-cspushnotificationconfiguration.md)
    
- [Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)
    
- [Remove-CsRegistrarConfiguration](remove-csregistrarconfiguration.md)
    
- [Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)
    
- [Remove-CsRgsAgentGroup](remove-csrgsagentgroup.md)
    
- [Remove-CsRgsHolidaySet](remove-csrgsholidayset.md)
    
- [Remove-CsRgsHoursOfBusiness](remove-csrgshoursofbusiness.md)
    
- [Remove-CsRgsQueue](remove-csrgsqueue.md)
    
- [Remove-CsRgsWorkflow](remove-csrgsworkflow.md)
    
- [Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)
    
- [Remove-CsServerApplication](remove-csserverapplication.md)
    
- [Remove-CsSimpleUrlConfiguration](remove-cssimpleurlconfiguration.md)
    
- [Remove-CsSipDomain](remove-cssipdomain.md)
    
- [Remove-CsSipResponseCodeTranslationRule](remove-cssipresponsecodetranslationrule.md)
    
- [Remove-CsStaticRoutingConfiguration](remove-csstaticroutingconfiguration.md)
    
- [Remove-CsStorageServiceConfiguration](remove-csstorageserviceconfiguration.md)
    
- [Remove-CsTelemetryConfiguration](remove-cstelemetryconfiguration.md)
    
- [Remove-CsTestDevice](remove-cstestdevice.md)
    
- [Remove-CsTestUserCredential](remove-cstestusercredential.md)
    
- [Remove-CsThirdPartyVideoSystem](remove-csthirdpartyvideosystem.md)
    
- [Remove-CsThirdPartyVideoSystemPolicy](remove-csthirdpartyvideosystempolicy.md)
    
- [Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md)
    
- [Remove-CsTrustedApplication](remove-cstrustedapplication.md)
    
- [Remove-CsTrustedApplicationComputer](remove-cstrustedapplicationcomputer.md)
    
- [Remove-CsTrustedApplicationEndpoint](remove-cstrustedapplicationendpoint.md)
    
- [Remove-CsTrustedApplicationPool](remove-cstrustedapplicationpool.md)
    
- [Remove-CsUCPhoneConfiguration](remove-csucphoneconfiguration.md)
    
- [Remove-CsUnassignedNumber](remove-csunassignednumber.md)
    
- [Remove-CsUserAcp](remove-csuseracp.md)
    
- [Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)
    
- [Remove-CsUserServicesConfiguration](remove-csuserservicesconfiguration.md)
    
- [Remove-CsUserServicesPolicy](remove-csuserservicespolicy.md)
    
- [Remove-CsUserStoreBackupData](remove-csuserstorebackupdata.md)
    
- [Remove-CsVideoInteropServerConfiguration](remove-csvideointeropserverconfiguration.md)
    
- [Remove-CsVideoInteropServerSyntheticTransactionConfiguration](remove-csvideointeropserversynthetictransactionconfiguration.md)
    
- [Remove-CsVideoTrunkConfiguration](remove-csvideotrunkconfiguration.md)
    
- [Remove-CsVoiceConfiguration](remove-csvoiceconfiguration.md)
    
- [Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)
    
- [Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)
    
- [Remove-CsVoicePolicy](remove-csvoicepolicy.md)
    
- [Remove-CsVoiceRoute](remove-csvoiceroute.md)
    
- [Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)
    
- [Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)
    
- [Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)
    
- [Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)
    
- [Remove-CsXmppAllowedPartner](remove-csxmppallowedpartner.md)
    
- [Repair-CsInterPoolConfDataRecovery](repair-csinterpoolconfdatarecovery.md)
    
- [Request-CsCertificate](request-cscertificate.md)
    
- [Reset-CsDeviceUpdateRule](reset-csdeviceupdaterule.md)
    
- [Restore-CsDeviceUpdateRule](restore-csdeviceupdaterule.md)
    
- [Revoke-CsClientCertificate](revoke-csclientcertificate.md)
    
- [Revoke-CsOUPermission](revoke-csoupermission.md)
    
- [Reset-CsPoolRegistrarState](reset-cspoolregistrarstate.md)
    
- [Reset-CsRoutingGroup](reset-csroutinggroup.md)
    
- [Revoke-CsSetupPermission](revoke-cssetuppermission.md)
    
- [Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)
    
- [Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)
    
- [Set-CsAddressBookNormalizationConfiguration](set-csaddressbooknormalizationconfiguration.md)
    
- [Set-CsAddressBookNormalizationRule](set-csaddressbooknormalizationrule.md)
    
- [Set-CsAdminRole](set-csadminrole.md)
    
- [Set-CsAllowedDomain](set-csalloweddomain.md)
    
- [Set-CsAnalogDevice](set-csanalogdevice.md)
    
- [Set-CsAnnouncement](set-csannouncement.md)
    
- [Set-CsApplicationServer](set-csapplicationserver.md)
    
- [Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)
    
- [Set-CsArchivingPolicy](set-csarchivingpolicy.md)
    
- [Set-CsArchivingServer](set-csarchivingserver.md)
    
- [Set-CsAudioTestServiceApplication](set-csaudiotestserviceapplication.md)
    
- [Set-CsAutodiscoverConfiguration](set-csautodiscoverconfiguration.md)
    
- [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)
    
- [Set-CsBackupServiceConfiguration](set-csbackupserviceconfiguration.md)
    
- [Set-CsBandwidthPolicyServiceConfiguration](set-csbandwidthpolicyserviceconfiguration.md)
    
- [Set-CsBlockedDomain](set-csblockeddomain.md)
    
- [Set-CsCallParkOrbit](set-cscallparkorbit.md)
    
- [Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)
    
- [Set-CsCallViaWorkPolicy](set-cscallviaworkpolicy.md)
    
- [Set-CsCdrConfiguration](set-cscdrconfiguration.md)
    
- [Set-CsCertificate](set-cscertificate.md)
    
- [Set-CsClientPin](set-csclientpin.md)
    
- [Set-CsClientPolicy](set-csclientpolicy.md)
    
- [Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md)
    
- [Set-CsClientVersionPolicy](set-csclientversionpolicy.md)
    
- [Set-CsClientVersionPolicyRule](set-csclientversionpolicyrule.md)
    
- [Set-CsClsConfiguration](set-csclsconfiguration.md)
    
- [Set-CsClsRegion](set-csclsregion.md)
    
- [Set-CsClsScenario](set-csclsscenario.md)
    
- [Set-CsClsSearchTerm](set-csclssearchterm.md)
    
- [Set-CsClsSecurityGroup](set-csclssecuritygroup.md)
    
- [Set-CsCommonAreaPhone](set-cscommonareaphone.md)
    
- [Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)
    
- [Set-CsConferenceServer](set-csconferenceserver.md)
    
- [Set-CsConferencingConfiguration](set-csconferencingconfiguration.md)
    
- [Set-CsConferencingPolicy](set-csconferencingpolicy.md)
    
- [Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)
    
- [Set-CsConversationHistoryConfiguration](set-csconversationhistoryconfiguration.md)
    
- [Set-CsCpsConfiguration](set-cscpsconfiguration.md)
    
- [Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md)
    
- [Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)
    
- [Set-CsDiagnosticHeaderConfiguration](set-csdiagnosticheaderconfiguration.md)
    
- [Set-CsDialInConferencingAccessNumber](set-csdialinconferencingaccessnumber.md)
    
- [Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md)
    
- [Set-CsDialInConferencingDtmfConfiguration](set-csdialinconferencingdtmfconfiguration.md)
    
- [Set-CsDialPlan](set-csdialplan.md)
    
- [Set-CsDirector](set-csdirector.md)
    
- [Set-CsEdgeServer](set-csedgeserver.md)
    
- [Set-CsEnhancedEmergencyServiceDisclaimer](set-csenhancedemergencyservicedisclaimer.md)
    
- [Set-CsExternalAccessPolicy](set-csexternalaccesspolicy.md)
    
- [Set-CsExUmContact](set-csexumcontact.md)
    
- [Set-CsFileTransferFilterConfiguration](set-csfiletransferfilterconfiguration.md)
    
- [Set-CsFIPSConfiguration](set-csfipsconfiguration.md)
    
- [Set-CsGroupPickupUserOrbit](set-csgrouppickupuserorbit.md)
    
- [Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)
    
- [Set-CsHostedVoicemailPolicy](set-cshostedvoicemailpolicy.md)
    
- [Set-CsHostingProvider](set-cshostingprovider.md)
    
- [Set-CsImFilterConfiguration](set-csimfilterconfiguration.md)
    
- [Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)
    
- [Set-CsKerberosAccountPassword](set-cskerberosaccountpassword.md)
    
- [Set-CsImConfiguration](set-csimconfiguration.md)
    
- [Set-CsLisLocation](set-cslislocation.md)
    
- [Set-CsLisPort](set-cslisport.md)
    
- [Set-CsLisServiceProvider](set-cslisserviceprovider.md)
    
- [Set-CsLisSubnet](set-cslissubnet.md)
    
- [Set-CsLisSwitch](set-cslisswitch.md)
    
- [Set-CsLisWirelessAccessPoint](set-csliswirelessaccesspoint.md)
    
- [Set-CsLocationPolicy](set-cslocationpolicy.md)
    
- [Set-CsManagementConnection](set-csmanagementconnection.md)
    
- [Set-CsMcxConfiguration](set-csmcxconfiguration.md)
    
- [Set-CsManagementServer](set-csmanagementserver.md)
    
- [Set-CsMediaConfiguration](set-csmediaconfiguration.md)
    
- [Set-CsMediationServer](set-csmediationserver.md)
    
- [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)
    
- [Set-CsMeetingRoom](set-csmeetingroom.md)
    
- [Set-CsMobilityPolicy](set-csmobilitypolicy.md)
    
- [Set-CsMonitoringServer](set-csmonitoringserver.md)
    
- [Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)
    
- [Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)
    
- [Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)
    
- [Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)
    
- [Set-CsNetworkRegion](set-csnetworkregion.md)
    
- [Set-CsNetworkRegionLink](set-csnetworkregionlink.md)
    
- [Set-CsNetworkSite](set-csnetworksite.md)
    
- [Set-CsNetworkSubnet](set-csnetworksubnet.md)
    
- [Set-CsOAuthConfiguration](set-csoauthconfiguration.md)
    
- [Set-CsOAuthServer](set-csoauthserver.md)
    
- [Set-CsOutboundCallingNumberTranslationRule](set-csoutboundcallingnumbertranslationrule.md)
    
- [Set-CsOutboundTranslationRule](set-csoutboundtranslationrule.md)
    
- [Set-CsPartnerApplication](set-cspartnerapplication.md)
    
- [Set-CsPersistentChatActiveServer](set-cspersistentchatactiveserver.md)
    
- [Set-CsPersistentChatAddin](set-cspersistentchataddin.md)
    
- [Set-CsPersistentChatCategory](set-cspersistentchatcategory.md)
    
- [Set-CsPersistentChatComplianceConfiguration](set-cspersistentchatcomplianceconfiguration.md)
    
- [Set-CsPersistentChatConfiguration](set-cspersistentchatconfiguration.md)
    
- [Set-CsPersistentChatPolicy](set-cspersistentchatpolicy.md)
    
- [Set-CsPersistentChatRoom](set-cspersistentchatroom.md)
    
- [Set-CsPersistentChatState](set-cspersistentchatstate.md)
    
- [Set-CsPinPolicy](set-cspinpolicy.md)
    
- [Set-CsPresencePolicy](set-cspresencepolicy.md)
    
- [Set-CsPresenceProvider](set-cspresenceprovider.md)
    
- [Set-CsPresenceManagementState](set-cspresencemanagementstate.md)
    
- [Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)
    
- [Set-CsProxyConfiguration](set-csproxyconfiguration.md)
    
- [Set-CsPstnGateway](set-cspstngateway.md)
    
- [Set-CsPstnUsage](set-cspstnusage.md)
    
- [Set-CsPublicProvider](set-cspublicprovider.md)
    
- [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md)
    
- [Set-CsQoEConfiguration](set-csqoeconfiguration.md)
    
- [Set-CsRegistrar](set-csregistrar.md)
    
- [Set-CsRegistrarConfiguration](set-csregistrarconfiguration.md)
    
- [Set-CsReportingConfiguration](set-csreportingconfiguration.md)
    
- [Set-CsRgsAgentGroup](set-csrgsagentgroup.md)
    
- [Set-CsRgsConfiguration](set-csrgsconfiguration.md)
    
- [Set-CsRgsHolidaySet](set-csrgsholidayset.md)
    
- [Set-CsRgsHoursOfBusiness](set-csrgshoursofbusiness.md)
    
- [Set-CsRgsQueue](set-csrgsqueue.md)
    
- [Set-CsRgsWorkflow](set-csrgsworkflow.md)
    
- [Set-CsRoutingConfiguration](set-csroutingconfiguration.md)
    
- [Set-CsServerApplication](set-csserverapplication.md)
    
- [Set-CsSimpleUrlConfiguration](set-cssimpleurlconfiguration.md)
    
- [Set-CsSipDomain](set-cssipdomain.md)
    
- [Set-CsSipResponseCodeTranslationRule](set-cssipresponsecodetranslationrule.md)
    
- [Set-CsSite](set-cssite.md)
    
- [Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)
    
- [Set-CsStorageServiceConfiguration](set-csstorageserviceconfiguration.md)
    
- [Set-CsTelemetryConfiguration](set-cstelemetryconfiguration.md)
    
- [Set-CsTestDevice](set-cstestdevice.md)
    
- [Set-CsTestUserCredential](set-cstestusercredential.md)
    
- [Set-CsThirdPartyVideoSystem](set-csthirdpartyvideosystem.md)
    
- [Set-CsThirdPartyVideoSystemPolicy](set-csthirdpartyvideosystempolicy.md)
    
- [Set-CsTrunkConfiguration](set-cstrunkconfiguration.md)
    
- [Set-CsTrustedApplication](set-cstrustedapplication.md)
    
- [Set-CsTrustedApplicationEndpoint](set-cstrustedapplicationendpoint.md)
    
- [Set-CsTrustedApplicationPool](set-cstrustedapplicationpool.md)
    
- [Set-CsUCPhoneConfiguration](set-csucphoneconfiguration.md)
    
- [Set-CsUICulture](set-csuiculture.md)
    
- [Set-CsUnassignedNumber](set-csunassignednumber.md)
    
- [Set-CsUser](set-csuser.md)
    
- [Set-CsUserAcp](set-csuseracp.md)
    
- [Set-CsUserDatabaseState](set-csuserdatabasestate.md)
    
- [Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)
    
- [Set-CsUserServer](set-csuserserver.md)
    
- [Set-CsUserServicesConfiguration](set-csuserservicesconfiguration.md)
    
- [Set-CsUserServicesPolicy](set-csuserservicespolicy.md)
    
- [Set-CsVideoGateway](set-csvideogateway.md)
    
- [Set-CsVideoInteropServer](set-csvideointeropserver.md)
    
- [Set-CsVideoInteropServerConfiguration](set-csvideointeropserverconfiguration.md)
    
- [Set-CsVideoInteropServerSyntheticTransactionConfiguration](set-csvideointeropserversynthetictransactionconfiguration.md)
    
- [Set-CsVideoTrunkConfiguration](set-csvideotrunkconfiguration.md)
    
- [Set-CsVoiceConfiguration](set-csvoiceconfiguration.md)
    
- [Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)
    
- [Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)
    
- [Set-CsVoicePolicy](set-csvoicepolicy.md)
    
- [Set-CsVoiceRoute](set-csvoiceroute.md)
    
- [Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)
    
- [Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)
    
- [Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)
    
- [Set-CsWebServer](set-cswebserver.md)
    
- [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)
    
- [Set-CsXmppAllowedPartner](set-csxmppallowedpartner.md)
    
- [Set-CsXmppGatewayConfiguration](set-csxmppgatewayconfiguration.md)
    
- [Start-CsWindowsService](start-cswindowsservice.md)
    
- [Start-CsPool](start-cspool.md)
    
- [Stop-CsWindowsService](stop-cswindowsservice.md)
    
- [Sync-CsUserData](sync-csuserdata.md)
    
- [Sync-CsClsLogging](sync-csclslogging.md)
    
- [Test-CsAddressBookService](test-csaddressbookservice.md)
    
- [Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)
    
- [Test-CsASConference](test-csasconference.md)
    
- [Test-CsAudioConferencingProvider](test-csaudioconferencingprovider.md)
    
- [Test-CsAVConference](test-csavconference.md)
    
- [Test-CsAVEdgeConnectivity](test-csavedgeconnectivity.md)
    
- [Test-CsCertificateConfiguration](test-cscertificateconfiguration.md)
    
- [Test-CsClientAuthentication](test-csclientauthentication.md)
    
- [Test-CsComputer](test-cscomputer.md)
    
- [Test-CsDatabase](test-csdatabase.md)
    
- [Test-CsDataConference](test-csdataconference.md)
    
- [Test-CsDialInConferencing](test-csdialinconferencing.md)
    
- [Test-CsDialPlan](test-csdialplan.md)
    
- [Test-CsExStorageConnectivity](test-csexstorageconnectivity.md)
    
- [Test-CsExStorageNotification](test-csexstoragenotification.md)
    
- [Test-CsExUMConnectivity](test-csexumconnectivity.md)
    
- [Test-CsExUMVoiceMail](test-csexumvoicemail.md)
    
- [Test-CsFederatedPartner](test-csfederatedpartner.md)
    
- [Test-CsGroupExpansion](test-csgroupexpansion.md)
    
- [Test-CsGroupIM](test-csgroupim.md)
    
- [Test-CsIM](test-csim.md)
    
- [Test-CsInterTrunkRouting](test-csintertrunkrouting.md)
    
- [Test-CsKerberosAccountAssignment](test-cskerberosaccountassignment.md)
    
- [Test-CsLisCivicAddress](test-csliscivicaddress.md)
    
- [Test-CsLisConfiguration](test-cslisconfiguration.md)
    
- [Test-CsLocationPolicy](test-cslocationpolicy.md)
    
- [Test-CsManagementServer](test-csmanagementserver.md)
    
- [Test-CsMcxConference](test-csmcxconference.md)
    
- [Test-CsMcxP2PIM](test-csmcxp2pim.md)
    
- [Test-CsMcxPushNotification](test-csmcxpushnotification.md)
    
- [Test-CsOUPermission](test-csoupermission.md)
    
- [Test-CsP2PAV](test-csp2pav.md)
    
- [Test-CsP2PVideoInteropServerSipTrunkAV](test-csp2pvideointeropserversiptrunkav.md)
    
- [Test-CsPersistentChatMessage](test-cspersistentchatmessage.md)
    
- [Test-CsPhoneBootstrap](test-csphonebootstrap.md)
    
- [Test-CsPresence](test-cspresence.md)
    
- [Test-CsPstnOutboundCall](test-cspstnoutboundcall.md)
    
- [Test-CsPstnPeerToPeerCall](test-cspstnpeertopeercall.md)
    
- [Test-CsRegistration](test-csregistration.md)
    
- [Test-CsReplica](test-csreplica.md)
    
- [Test-CsSetupPermission](test-cssetuppermission.md)
    
- [Test-CsTopology](test-cstopology.md)
    
- [Test-CsTrunkConfiguration](test-cstrunkconfiguration.md)
    
- [Test-CsUcwaConference](test-csucwaconference.md)
    
- [Test-CsUnifiedContactStore](test-csunifiedcontactstore.md)
    
- [Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)
    
- [Test-CsVoicePolicy](test-csvoicepolicy.md)
    
- [Test-CsVoiceRoute](test-csvoiceroute.md)
    
- [Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)
    
- [Test-CsVoiceUser](test-csvoiceuser.md)
    
- [Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)
    
- [Test-CsWebApp](test-cswebapp.md)
    
- [Test-CsWebAppAnonymous](test-cswebappanonymous.md)
    
- [Test-CsWebScheduler](test-cswebscheduler.md)
    
- [Test-CsXmppIM](test-csxmppim.md)
    
- [Uninstall-CsDatabase](uninstall-csdatabase.md)
    
- [Uninstall-CsMirrorDatabase](uninstall-csmirrordatabase.md)
    
- [Unlock-CsClientPin](unlock-csclientpin.md)
    
- [Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)
    
- [Update-CsAddressBook](update-csaddressbook.md)
    
- [Update-CsAdminRole](update-csadminrole.md)
    
- [Update-CsTenantMeetingUrl](update-cstenantmeetingurl.md)
    
- [Update-CsUserData](update-csuserdata.md)
    
- [Update-CsUserDatabase](update-csuserdatabase.md)
    

