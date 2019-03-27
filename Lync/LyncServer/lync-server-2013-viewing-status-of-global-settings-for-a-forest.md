---
title: 'Lync Server 2013: Viewing status of global settings for a forest'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: View status of global settings for a forest
ms:assetid: 2ab0f2f1-9908-4e6f-aff3-d6b3cc474b6b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn747889(v=OCS.15)
ms:contentKeyID: 63969590
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# View status of global settings for a forest in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-20_

Administrators should review the global settings for a Lync Server 2013 deployment monthly. The objective would be to review implemented settings against a set of known configurations—a baseline configuration to help guarantee that settings are valid and to determine whether the baseline documentation should be updated. Changes to global setting should be implemented through a Change Control process which should include documenting the new settings.

Global settings that should be reviewed are described in the following sections:

<div>

## Check general settings

Check general settings, including the supported Session Initiation Protocol (SIP) domains for Lync Server 2013.

SIP domain information can be returned by using Windows PowerShell and the **Get-CsSipDomain** cmdlet. To return this information, run the `Get-CsSipDomain` Windows PowerShell command.

Get-CsSipDomain will return information similar to this for all the authorized SIP domains:

Identity Name IsDefault

\-------- ---- ---------

fabrikam.com fabrikam.com True

na.fabrikam.com na.fabrikam.com False

If the IsDefault property is set to True, the corresponding domain is your default SIP domain. You can use the Set-CsSipDomain cmdlet to change the default SIP domain for your organization. However, you can't just delete the default SIP domain because that would leave you without a default domain. If you wanted to delete the fabrikam.com domain (as shown in the previous example), you would first have to configure na.fabrikam.com to be your default domain.

</div>

<div>

## Check meeting settings

Meeting settings include meeting policy definitions and support for participation of anonymous users in meetings.

Meeting configuration settings can be retrieved by using Windows PowerShell and the **Get-CsMeetingConfiguration** cmdlet. For example, this command returns information about the global meeting configuration settings:

Get-CsMeetingConfiguration –Identity "Global"Meeting configuration settings can also be configured at the site scope. Because of that, you might want to use the following command, which returns information about all the meeting configuration settings:

`Get-CsMeetingConfiguration`

The **Get-CsMeetingConfiguration** cmdlet returns information similar to the following:

Identity : Global

PstnCallersBypassLobby : True

EnableAssignedConferenceType : True

DesignateAsPresenter : Company

AssignedConferenceTypeByDefault : True

AdmitAnonymousUsersByDefault : True

Again, the final item in the list, **AdmitAnonymousUsersByDefault**, enables or disables the ability of anonymous users to participate in meetings.

When checking meeting configuration settings, you might find it useful to compare the current settings against the default equivalents. You can view the default meeting configuration settings by running the following command:

`New-CsMeetingConfiguration -Identity "Global" -InMemory`

The previous command creates an in-memory-only instance of the global meeting configuration settings, an instance that uses the default value for each property. No actual meeting configuration settings are created when you run the command. However, all the default property values will be displayed on-screen.

</div>

<div>

## Check Edge Servers and their settings

Edge Server information can be retrieved by using Windows PowerShell. This command returns information about all the Edge Servers configured for use in your organization:

`Get-CsService -EdgeServer`

The returned information includes all of the FQDN and port settings for each Edge Server:

Identity : EdgeServer: dc.fabrikam.com

Registrar : Registrar: LYNC-SE.fabrikam.com

AccessEdgeInternalSipPort : 5061

AccessEdgeExternalSipPort : 5061

AccessEdgeClientPort : 443

DataPsomServerPort : 8057

DataPsomClientPort : 444

MediaRelayAuthEdgePort : 5062

MediaRelayAuthInternalTurnTcpPort : 443

MediaRelayAuthExternalTurnTcpPort : 445

MediaRelayAuthInternalTurnUdpPort : 3478

MediaRelayAuthExternalTurnUdpPort : 3478

MediaCommunicationPortStart : 50000

MediaComunicationPortCount : 10000

AccessEdgeExternalFqdn : dc.fabrikam.com

DataEdgeExternalFqdn : dc.fabrikam.com

AVEdgeExternalFqdn :

InternalInterfaceFqdn :

ExternalMrasFqdn : dc.fabrikam.com

DependentServiceList : {Registrar:LYNC-SE.fabrikam.com,

ConferencingServer:LYNC-SE.fabrikam

com, MediationServer:LYNC-SE.

fabrikam.com}

ServiceId : fabrikam.com-EdgeServer-2

SiteId : site:fabrikam.com

PoolFqdn : dc.fabrikam.com

Version : 5

Role : EdgeServer

<div>

## Check federation settings

Check Federation settings, such as whether it is configured and, if the answer is "yes,", the FQDN and port. Federation is enabled and disabled by using the global collection of Access Edge configuration settings. Among other things, these mean that federation is configured on an all-or-nothing basis: either federation is enabled for the whole organization or federation is disabled for the whole organization

Your Access Edge configuration settings can be returned by using Windows PowerShell. To do that, run the following Windows PowerShell command:

`Get-CsAccessEdgeConfiguration`

In turn, that command will return data similar to this:

Identity : Global

AllowAnonymousUsers : False

AllowFederatedUsers : False

AllowOutsideUsers : False

BeClearingHouse : False

EnablePartnerDiscovery : False

EnableArchivingDisclaimer : False

KeepCrlsUpToDateForPeers : True

MarkSourceVerifiableOnOutgoingMessages : True

OutgoingTlsCountForFederatedPartners : 4

RoutingMethod : UseDnsSrvRouting

If the **AllowFederatedUsers** property is set to True, that means that federation is enabled for your organization. (Setting **AllowFederatedUsers** to True also means that, in a split domain scenario, your on-premises users will be able to communicate seamlessly with your in-the-cloud users.)

To retrieve the FQDN and port settings for your Edge Server, see the previous task (Edge Servers and their settings).

Enabling federation at the global scope only means that users can potentially communicate with federated users. To determine whether any individual users can actually communicate with federated users requires you to examine the external user access policy assigned to that user.

External user access information can be returned by using Windows PowerShell. For example, this command returns information for the global external user access policy:

`Get-CsExternalAccessPolicy -Identity "Global"`

And this command returns information for all the external user access policies:

`Get-CsExternalAccessPolicy`

The returned information will resemble this:

Identity : False

Description :

EnableFederationAccess : False

EnablePublicCloudAccess : False

EnablePublicCloudAccessAudioVideoAccess : False

EnableOutsideAccess : False

If **EnableFederationAccess** is set to True, then users managed by the given policy can communicate with federated users.

</div>

</div>

<div>

## Check archiving settings

Check archiving settings for internal and federated communications.Before verifying the settings for internal and external archiving, you should verify that archiving is enabled.

Archiving configuration settings can be verified by using Windows PowerShell and the Get-CsArchivingConfiguration cmdlet:

`Get-CsArchivingConfiguration -Identity "Global"`

Note that archiving settings can also be configured at the site scope. To return information about all the archiving settings, use this command:

`Get-CsArchivingConfiguration`

The Get-CsArchivingConfiguration cmdlet returns data similar to this:

Identity : Global

EnableArchiving : False

EnablePurging : False

PurgeExportedArchivesOnly : False

BlockOnArchiveFailure : False

KeepArchivingDataForDays : 14

PurgeHourOfDay : 2

ArchiveDuplicateMessages : True

CachePurgingInterval : 24

If the EnableArchiving property is set to False, that means that no communication sessions will be archived. If you want to archive instant messaging sessions only, use a command such as the following to enable the archiving of IM sessions:

`Set-CsArchivingConfiguration -Identity "Global" -EnableArchiving "IMOnly"`

To archive conferencing sessions and instant messaging sessions, use this command:

`Set-CsArchivingConfiguration -Identity "Global" -EnableArchiving "IMOnly"`

If you’d like to compare your current archiving settings with the default settings, run the following Windows PowerShell command:

`New-CsArchivingConfiguration -Identity "Global" -InMemory`

That command creates an in-memory-only instance of the global archiving configuration settings. This is not a real collection of settings that is used by Lync Server. However, it does display the default values for all the archiving configuration properties.

You can also use this command to return the FQDN of your Archiving servers:

`Get-CsService -ArchivingServer`

After you have verified that archiving is enabled, you can then view your archiving policies to determine whether internal and external communication sessions are being archived.

Archiving policy information can be retrieved by using the Get-CsArchivingPolicy cmdlet. For example, this command returns information about the global archiving policy:

`Get-CsArchivingPolicy -Identity "Global"`

Because archiving policies can also be configured at the site and the per-user scope, you might also want to use this command, which returns information about all the archiving policies:

`Get-CsArchivingPolicy`

The information that you receive from Get-CsArchivingPolicy will resemble this:

Identity : Global

Description :

ArchiveInternal : False

ArchiveExternal : False

Note that, by default, both internal and external archiving are disabled in an archiving policy.

</div>

<div>

## Check CDR settings

Check Call Detail Record (CDR) settings for peer-to-peer, conferencing, and Voice call detail recording. Detailed information about your CDR settings can be returned by using the **Get-CsCdrConfiguration** cmdlet. For example, this command returns information about the global collection of CDR configuration settings:

`Get-CsCdrConfiguration -Identity "Global"`

Because CDR can also be configured at the site scope, you might also want to run this command, which returns information about all the CDR configuration settings:

`Get-CsCdrConfiguration`

The Get-CsCdrConfiguration cmdlet returns information similar to this for each collection of CDR configuration settings:

Identity : Global

EnableCDR : True

EnablePurging : True

KeepCallDetailForDays : 60

KeepErrorReportForDays : 60

PurgeHourOfDay : 2

Similar information can be returned for QoE monitoring by using the Get-CsQoEConfiguration cmdlet. For example, this command returns information about the global collection of QoE configuration settings:

`Get-QoEConfiguration -Identity "Global"`

That information will resemble this:

Identity : Global

ExternalConsumerIssuedCertId :

EnablePurging : True

KeepQoEDataForDays : 60

PurgeHourOfDay : 1

EnableExternalConsumer : False

ExternalConsumerName :

ExternalConsumerURL :

EnableQoE : True

If you want to compare your current CDR settings with the default CDR settings, the default values can be reviewed by running this command:

`New-CsCdrConfiguration -Identity "Global" -InMemory`

Likewise, the default values for QoE monitoring can be retrieved by using this command:

`New-CsQoEConfiguration -Identity "Global" -InMemory`

You can also return the FQDN of your Monitoring servers by running this command:

`Get-CsService -MonitoringServer`

</div>

<div>

## Check voice settings

The voice settings typically important to administrators are contained in voice policies and voice routes: voice policies contain the settings that determine the capabilities exposed to individual users (such as the ability to forward or transfer calls), while voice routes determine how (and if) calls are routed across the PSTN.

Voice policy information can be retrieved by using Windows PowerShell. For example, this command returns information about the global voice policy:

`Get-CsVoicePolicy -Identity "Global"`

And this command returns information about all the voice policies configured for use in the organization:

`Get-CsVoicePolicy`

The information returned by the Get-CsVoicePolicy cmdlet resembles the following:

Identity : Global

PstnUsages : {}

Description :

AllowSimulRing : True

AllowCallForwarding : True

AllowPSTNReRouting : True

Name : DefaultPolicy

EnableDelegation : True

EnableTeamCall : True

EnableCallTransfer : True

EnableCallPark : False

EnableMaliciousCallTracing : False

EnableBWPolicyOverride : False

PreventPSTNTollBypass : False

You can also create queries that returned a subset of your voice policies. For example, this command returns all the voice policies that allow call forwarding:

`Get-CsVoicePolicy | Where-Object {$_.AllowCallForwarding -eq $True}`

And this command returns all the voice policies that don’t allow call forwarding:

`Get-CsVoicePolicy | Where-Object {$_.AllowCallForwarding -eq $False}`

In Windows PowerShell, use the Get-CsVoiceRouting cmdlet to return information about your voice routes:

`Get-CsVoiceRoute`

That command returns information such as this for all the voice routes:

Identity : LocalRoute

Priority : 0

Description :

NumberPattern : ^(\\+1\[0-9\]{10})$

PstnUsages : {}

PstnGatewayList : {}

Name : LocalRoute

SuppressCallerId :

AlternateCallerId :

Lync Server allows you to create voice routes that do not have a PSTN usage and do not specify a PSTN gateway. However, you can't actually route calls over a voice route that does not have these two property values configured. Because of that, you might find it useful to periodically run this command, which returns the identity of any voice route that does not have a PSTN usage:

`Get-CsVoiceRoute | Where-Object {$_.PstnUsages -eq $Null} | Select-Object Identity`

Similarly, this command returns the identity of any voice route that has not been configured to have a PSTN gateway:

`Get-CsVoiceRoute | Where-Object {$_.PstnGatewayList -eq $Null}} | Select-Object Identity`

</div>

<div>

## Check Conferencing Attendant settings

Check conferencing Attendant settings for PSTN dial-in conferencing. Conferencing Attendant settings can only be retrieved by using the **Get-CsDialInConferencingConfiguration** cmdlet. These settings are not available in the Lync Server Control Panel. To view your Conferencing Attendant settings, use a Windows PowerShell command similar to the following, which returns the global collection of Conferencing Attendant settings:

`Get-CsDialInConferencingConfiguration -Identity "Global"`

Note that Conferencing Attendant settings can also be configured at the site scope. To return information about all the Conferencing Attendant settings, use this command instead:

`Get-CsDialInConferencingConfiguration`

The Get-CsDialInConferencingConfiguration cmdlet returns data similar to this:

Identity : Global

EntryExitAnnouncementsType : UseNames

EnableNameRecording : True

EntryExitAnnouncementsEnabledByDefault : False

If EntryExitAnnouncementsEnabledByDefault is set to False, that means the conferencing announcements are disabled. To enable entry and exit announcements, run a Windows PowerShell command similar to this:

`Set-CsDialInConferencingConfiguration -Identity "Global" -EntryExitAnnouncementsEnabledByDefault $True`

</div>

<div>

## See Also


[Get-CsSipDomain](https://docs.microsoft.com/powershell/module/skype/Get-CsSipDomain)  
[Get-CsMeetingConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsMeetingConfiguration)  
[Get-CsService](https://docs.microsoft.com/powershell/module/skype/Get-CsService)  
[Get-CsAccessEdgeConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsAccessEdgeConfiguration)  
[Get-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/Get-CsExternalAccessPolicy)  
[Get-CsArchivingConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsArchivingConfiguration)  
[Get-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsCdrConfiguration)  
[Get-CsQoEConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsQoEConfiguration)  
[Get-CsVoicePolicy](https://docs.microsoft.com/powershell/module/skype/Get-CsVoicePolicy)  
[Get-CsVoiceRoute](https://docs.microsoft.com/powershell/module/skype/Get-CsVoiceRoute)  
[Get-CsDialInConferencingConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsDialInConferencingConfiguration)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

