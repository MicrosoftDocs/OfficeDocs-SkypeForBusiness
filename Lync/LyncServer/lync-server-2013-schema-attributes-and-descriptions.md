---
title: 'Lync Server 2013: Schema attributes and descriptions'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Schema attributes and descriptions
ms:assetid: b009df76-9c22-471d-b57a-bda009a98261
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412841(v=OCS.15)
ms:contentKeyID: 48185083
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Schema attributes and descriptions in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-06_

This section describes all the schema attributes used by Lync Server 2013. For the classes associated with attributes, see [Schema attributes by class in Lync Server 2013](lync-server-2013-schema-attributes-by-class.md). For a list of classes and attributes that are new in Lync Server 2013, see [Schema changes in Lync Server 2013](lync-server-2013-schema-changes-in-lync-server-2013.md).

Attributes that are linked pairs are specified as forward links or back links. An attribute that refers to another object is a forward link; the attribute of the other object that refers back to the first object is a back link. Forward links are updatable, while back links are read-only.

Some attributes have a bit-mask value. For these attributes, each setting is represented by a bit, and the displayed decimal value represents the bit position. Bit positions start with bit 0. For example, 1 (binary) is bit 0 set and 10000 (binary) is bit 4 set. Each bit represents a property. The following are some examples:

  - 10000 (binary) has a decimal value of 16 (that is, bit 4 is set).

  - 100000000 (binary) has a decimal value of 256 (that is, bit 8 is set).

  - 1100 (binary) has a decimal value of 12 (that is, bits 2 and 3 are set; properties represented by both bits are enabled).

  - 1111000001 (binary) has a decimal value of 961 (that is, bits 0, 6, 7, 8, and 9 are set; properties for each of these bits are enabled).

<div id="sectionSection0" class="section">

### Schema Attributes for Lync Server 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribute</th>
<th>Description</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>dnsHostName</p></td>
<td><p>An existing attribute in Active Directory Domain Services that is now associated with the <strong>msRTCSIP-Pool</strong> and <strong>msRTCSIP-MonitoringServer</strong> classes. This attribute specifies the fully qualified domain name (FQDN) of a pool or Monitoring Server.</p>
<p>A valid value for each segment is 63 characters; a valid value for the entire FQDN is 255 characters.</p></td>
<td><p>New in Microsoft Office Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msDS-SourceObjectDN</p></td>
<td><p>This attribute contains the string representation of the distinguished name (DN) of the object in another forest that corresponds to this object. This attribute is used for distribution group expansion and auto attendance. This attribute is defined in the default Active Directory schema for Windows Server 2003 R2.</p>
<p>To avoid requiring an upgrade of AD DS to Windows Server 2003 R2, Active Directory schema preparation extends the Windows Server 2003 schema with this attribute definition.</p></td>
<td><p>New in Microsoft Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msExchUCVoiceMailSettings</p></td>
<td><p>This multi-valued attribute holds voice mail settings. This attribute is shared with Exchange Unified Messaging (UM).</p></td>
<td><p>New in Microsoft Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msExchUserHoldPolicies</p></td>
<td><p>This multi-value attribute holds identifiers for hold policies that apply to the user. Hold policies preserve mailbox items for the user for the duration of the hold. This attribute is shared with Exchange 2013.</p></td>
<td><p>New in Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-AcpInfo</p></td>
<td><p>This attribute stores audio conferencing provider information for a user.</p></td>
<td><p>New in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationDestination</p></td>
<td><p>This attribute points to the trusted service entry for the application contact.</p></td>
<td><p>New in Microsoft Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationList</p></td>
<td><p>This attribute contains a list of hosted applications on the application server.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationOptions</p></td>
<td><p>This attribute specifies the options for the application contact.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationPrimaryLanguage</p></td>
<td><p>This attribute contains the primary language for the application contact.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationSecondaryLanguages</p></td>
<td><p>This multiple value attribute contains the secondary languages for the application contact.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationServerBL</p></td>
<td><p>This attribute contains a list of application servers that belong to this pool. The corresponding forward link to this back link attribute is <strong>msRTCSIP-ApplicationServerPoolLink</strong>.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationServerPoolLink</p></td>
<td><p>This attribute points to the pool to which this application server belongs. This is the forward link. The corresponding backward link is <strong>msRTCSIP-ApplicationServerBL</strong>.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchiveDefault (obsolete)</p></td>
<td><p>-</p></td>
<td><p>New in Live Communications Server 2005.</p>
<p>Obsolete in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ArchiveDefaultFlags (obsolete)</p></td>
<td><p>This attribute specifies the global default within the forest boundary for archiving all user communications. This is enforced by the archiving agent layer. The range of values for this attribute is as follows:</p>
<ul>
<li><p><strong>TRUE</strong>: Archive all users</p></li>
<li><p><strong>FALSE</strong>: Do not archive all users</p></li>
</ul>
<p>This attribute globally controls, within the forest boundary, how user communications within an internal network are archived.</p>
<p><strong>Live Communications Server 2005 behavior (now retired)</strong></p>
<p>The range of values for this attribute is as follows:</p>
<ul>
<li><p>0: Archive the message body [bit 0]</p></li>
<li><p>1: Do not archive the message body [bit 0]</p></li>
</ul>
<p><strong>Office Communications Server 2007 behavior</strong></p>
<p>The range of values for this attribute is as follows:</p>
<ul>
<li><p>0: ArchiveFederationDefaultWithoutBody (retired)</p></li>
<li><p>1-2: ArchiveInternalCommunications</p></li>
<li><p>3-4: ArchiveFederatedCommunications</p></li>
<li><p>5: RecordPresenceRegistrations</p></li>
<li><p>6: RecordIMCallDetails</p></li>
<li><p>7: RecordGroupIMCallDetails</p></li>
<li><p>8: RecordFileTransferInstances</p></li>
<li><p>9: RecordAudioCallDetails</p></li>
<li><p>10: RecordVideoCallDetails</p></li>
<li><p>11: RecordRemoteAssistanceCallDetails</p></li>
<li><p>12: RecordApplicationSharingDetails</p></li>
<li><p>13: RecordMeetingInstantiations</p></li>
<li><p>14: RecordMeetingJoins</p></li>
<li><p>15: RecordDataJoins</p></li>
<li><p>16: RecordAVJoins</p></li>
</ul></td>
<td><p>New in Live Communications Server 2005.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchiveFederationDefault (obsolete)</p></td>
<td><p>-</p></td>
<td><p>New in Live Communications Server 2005.</p>
<p>Obsolete in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ArchiveFederationDefaultFlags (obsolete)</p></td>
<td><p>-</p></td>
<td><p>New in Live Communications Server 2005.</p>
<p>Obsolete in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchivingEnabled</p></td>
<td><p>This attribute is an integer used as a bit field to control whether a single user’s communications are to be archived. This control is enforced by the archiving agent layer. It is marked for global catalog replication.</p>
<p>The scope of this attribute is specific to a single user or contact. The valid values (and associated bit positions) in Lync Server are as follows:</p>
<ul>
<li><p>0: Do not archive (no bit set)</p></li>
<li><p>1: Retired (bit position 0)</p></li>
<li><p>2: Retired (bit position 1)</p></li>
<li><p>4: Archive internal communications (bit position 2)</p></li>
<li><p>8: Archive federated communications (bit position 3)</p></li>
</ul>
<p>Previously valid values in Live Communications Server 2005 are as follows:</p>
<ul>
<li><p>0:Use the default value defined by <strong>msRTCSIP-ArchiveDefault</strong> and <strong>msRTCSIP-ArchiveFederation</strong> in this order of precedence:</p>
<ul>
<li><p>1: Archive</p></li>
<li><p>2: Do not archive</p></li>
<li><p>3: Archive without the message body</p></li>
</ul></li>
</ul></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ArchivingServerData (obsolete)</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchivingServerVersion (obsolete)</p></td>
<td><p>This attribute defines the version of the Archiving service. This attribute is a monotonously increasing integer type that increments with each official product release. The possible valid values are:</p>
<ul>
<li><p>Undefined: Live Communications Server 2003</p>
<p>                 Live Communications Server 2005</p>
<p>                 Live Communications Server 2005 with SP1</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
</ul></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-BackEndServer</p></td>
<td><p>This attribute specifies the FQDN of the Back End Server of the pool. Because there can only be a single Back End Server per pool, this is a single-valued attribute.</p>
<p>The valid value for each segment is 63 characters; the valid value for the entire FQDN is 255 characters.</p></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ConferenceDirectoryHomePool</p></td>
<td><p>This attribute contains the identifier of the pool that hosts the conference directory.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ConferenceDirectoryId</p></td>
<td><p>This attribute contains the identifier of a conference directory.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ConferenceDirectoryTargetPool</p></td>
<td><p>This attribute contains the identifier of the pool to which the conference directory is being moved.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Default</p></td>
<td><p>This Boolean attribute defines whether the phone usage is a default usage. If this attribute is set to <strong>TRUE</strong>, the phone usage is a default usage and cannot be deleted by the administrator. If this attribute is set to <strong>FALSE</strong>, the usage can be deleted.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultCWAExternalURL</p></td>
<td><p>This attribute identifies the Communicator Web Access URL for users who are outside the organization.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefaultCWAInternalURL</p></td>
<td><p>This attribute identifies the Communicator Web Access URL for users who are inside the organization.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultLocationProfileLink (obsolete)</p></td>
<td><p>This single-valued attribute contains the distinguished name (DN) of a location profile class object assigned to it.</p>
<p>Forward link: <strong>Link ID 11036</strong></p>
<p>The corresponding backward link is <strong>msRTCSIP-ServerReferenceBL</strong>.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefaultPolicy (obsolete)</p></td>
<td><p>This Boolean attribute specifies whether the policy is a default policy. The policy is a default policy when set to <strong>TRUE</strong>.</p></td>
<td><p>New in Office Communications Server 2007</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultRouteToEdgeProxy (obsolete)</p></td>
<td><p>This attribute specifies the FQDN of either the Edge Server running the Access Edge service, if it can be accessed directly, or of the hardware load balancer for a pool of servers running Access Edge service. If the servers running Access Edge service can be accessed only through one or more Directors, this attribute specifies the FQDN and, optionally, the port number of the Director or of the hardware load balancer serving a Director pool.</p>
<p>The valid value for each segment is 63 characters; the valid value for the entire FQDN is 255 characters.</p></td>
<td><p>New in Live Communications Server 2005.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefaultRouteToEdgeProxyPort (obsolete)</p></td>
<td><p>This attribute represents the port number that should be used to connect to the server running Access Edge service.</p>
<p>The valid value is an integer value specifying the port to be used. The default value is 5061.</p></td>
<td><p>New in Live Communications Server 2005.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefPresenceSubscriptionTimeout (obsolete)</p></td>
<td><p>This attribute represents the default presence subscription time-out period.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefRegistrationTimeout (obsolete)</p></td>
<td><p>This attribute represents the default registration time-out window.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefRoamingDataSubscriptionTimeout (obsolete)</p></td>
<td><p>This attribute represents the default roaming data subscription time-out window.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DeploymentLocator</p></td>
<td><p>This attribute is used in a split domain topology and contains a fully qualified domain name (FQDN).</p></td>
<td><p>New in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Description (obsolete)</p></td>
<td><p>This single-valued UNICODE string attribute contains a friendly description of this phone route or normalization rule.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DomainData</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DomainName</p></td>
<td><p>This attribute represents a domain configured for the Registrar.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EdgeProxyData</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EdgeProxyFQDN</p></td>
<td><p>This attribute specifies the FQDN of the server running Access Edge service.</p>
<p>The valid value for each segment is 63 characters; the valid value for the entire FQDN is 255 characters.</p></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnableBestEffortNotify (obsolete)</p></td>
<td><p>This attribute controls whether a server generates a Best Effort NOTIFY (BENOTIFY) request, instead of a NOTIFY request, in response to a SUBSCRIBE request from a client. BENOTIFY is a performance-enhancing extension to the subscribe notification handshake where the server generates BENOTIFY requests, instead of regular NOTIFY requests. The performance benefit is that a BENOTIFY request does not require a 200 OK response from the client as the NOTIFY request does.</p>
<p>The valid values are <strong>TRUE</strong> or <strong>FALSE</strong>.</p>
<div>

> [!NOTE]  
> Live Communications Server 2003 does not support BENOTIFY requests. To interoperate with server applications written with the Live Communications Server 2003 server API running on Live Communications Server 2005 and third-party servers, BENOTIFY requests can be disabled by setting its value to <STRONG>FALSE</STRONG>. BENOTIFY is not currently part of the IETF (Internet Engineering Task Force) SIP standardization process.


</div></td>
<td><p>New in Live Communications Server 2005.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EnableFederation (obsolete)</p></td>
<td><p>This attribute is a global switch that IT administrators use to configure whether users are allowed to communicate with users from other organizations. It enables an administrator to overwrite an individual user’s <strong>FederationEnabled</strong> attribute. This attribute can be useful to help protect the internal network from Internet attacks that may be caused by worms, viruses, or targeted attacks on the company.</p>
<p>The valid values (and associated bit positions) are as follows:</p>
<ul>
<li><p>1: Enabled for public IM connectivity (bit position 0)</p></li>
<li><p>2: Reserved (bit position 1)</p></li>
<li><p>4: Reserved (bit position 2)</p></li>
<li><p>8: Reserved (bit position 3)</p></li>
<li><p>16: Remote call control Enabled [Telephony] (bit position 4)</p></li>
<li><p>64: AllowOrganizeMeetingWithAnonymousParticipants (allow users to invite anonymous users to meetings (bit position 6)</p></li>
<li><p>128: UCEnabled (enable users for unified communications) (bit position 7)</p></li>
<li><p>256: EnabledForEnhancedPresence (enable user for public IM connectivity) (bit position 8)</p></li>
<li><p>512: RemoteCallControlDualMode (bit position 9)</p></li>
</ul></td>
<td><p>New in Live Communications Server 2005.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnterpriseServices</p></td>
<td><p>This attribute indicates whether the Enterprise Services are loaded on the given server.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ExtensionData</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ExternalAccessCode</p></td>
<td><p>This attribute contains the dial code for external access.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-FederationEnabled</p></td>
<td><p>This attribute controls whether a single user is enabled for federation. It is enforced by the Enterprise Services layer. It is marked for global catalog replication.</p>
<p>The valid values are <strong>TRUE</strong> or <strong>FALSE</strong>.</p></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-FrontEndServers</p></td>
<td><p>This attribute is a multi-valued list of the domain names of all Enterprise Edition servers associated with a pool.</p>
<p>Back link: <strong>Link ID 11023</strong></p>
<p>The corresponding forward link to this back link is <strong>msRTCSIP-PoolAddress</strong>.</p></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Gateways (obsolete)</p></td>
<td><p>This multi-valued string attribute contains a list of gateways and ports (per gateway).</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalSettingsData (obsolete)</p></td>
<td><p>This attribute stores name:value pairs. The already-defined name:value pair is for the <strong>allow polling for presence</strong> setting.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-GroupingID</p></td>
<td><p>This attribute is a unique identifier of a group that is used to group address book entries.</p></td>
<td><p>New in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-HomeServer (obsolete)</p></td>
<td><p>-</p></td>
<td><p>New in Live Communications Server 2003 (not used).</p>
<p>Obsolete in Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-HomeServerString (obsolete)</p></td>
<td><p>-</p></td>
<td><p>New in Live Communications Server 2003.</p>
<p>Obsolete in Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-HomeUsers (obsolete)</p></td>
<td><p>-</p></td>
<td><p>New in Live Communications Server 2003 (not used).</p>
<p>Obsolete in Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-InternetAccessEnabled</p></td>
<td><p>This attribute controls whether a single user is enabled for outside user access. It is enforced by the Enterprise Services layer. It is marked for global catalog replication.</p>
<p>The valid values are <strong>TRUE</strong> or <strong>FALSE</strong>.</p></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-IsMaster (obsolete)</p></td>
<td><p>-</p></td>
<td><p>New in Live Communications Server 2003</p>
<p>Obsolete in Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Line</p></td>
<td><p>This single-valued attribute contains the device ID (either the SIP URI or the TEL URI of the phone the user controls) used by Lync for telephony. This attribute is marked for Global Catalog replication and is indexed. If a user is enabled for Enterprise Voice, this attribute stores the E.164 normalized version of the user’s phone number.</p></td>
<td><p>New in Microsoft Office Live Communications Server 2005 with SP1</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LineServer</p></td>
<td><p>This single-valued attribute contains the SIP URI of the CSTA-SIP gateway server. This attribute is marked for Global Catalog replication but is not indexed.</p></td>
<td><p>New in Microsoft Office Live Communications Server 2005 with SP1</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocalNormalizationData (obsolete)</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocalNormalizationLinks (obsolete)</p></td>
<td><p>This multi-valued attribute contains a list of local normalization distinguished names (DN) associated with this location profile. The type of this attribute is a DN binary. There is a one-to-many relationship between location profile and local normalization rules. The ordering of the list of local normalization DNs must be maintained in the order specified by the administrator. The preservation of order is maintained by the binary portion of the DN binary, which specifies the order index.</p>
<p>Forward link: <strong>Link ID 11034</strong></p>
<p>The corresponding back link to this forward link attribute is <strong>msRTCSIP-LocationProfileBL</strong>.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocalNormalizationOptions</p></td>
<td><p>This attribute contains a list of options for the normalization rule.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationName (obsolete)</p></td>
<td><p>This single-valued attribute contains a friendly name for the location profile that indicates which location this profile represents. Because there can be multiple location profiles, the administrator needs a way to distinguish between different profiles.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-locationProfileBL (obsolete)</p></td>
<td><p>This multi-valued attribute contains a list of location profile distinguished names. This attribute specifies the back link to one or more location profiles.</p>
<p>Back link: <strong>Link ID 11035</strong></p>
<p>This attribute corresponds to the forward link <strong>msRTCSIP-LocalNormalizationLinks</strong>.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationProfileData (obsolete)</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocationProfileOptions</p></td>
<td><p>This attribute contains the options for the location profile.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MappingContact</p></td>
<td><p>This multiple-value attribute holds a list of application contacts.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MappingLocation</p></td>
<td><p>This multiple-value attribute holds a list of location profiles.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MaxNumOutstandingSearchPerServer (obsolete)</p></td>
<td><p>This attribute represents the maximum number of outstanding search requests per server.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MaxNumSubscriptionsPerUser (obsolete)</p></td>
<td><p>The attribute represents the maximum number of subscriptions per user.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MaxPresenceSubscriptionTimeout (obsolete)</p></td>
<td><p>This attribute represents the maximum subscription time-out window.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MaxRegistrationsTimeout (obsolete)</p></td>
<td><p>This attribute represents the maximum registrations time-out window.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MaxRoamingDataSubscriptionTimeout (obsolete)</p></td>
<td><p>This attribute represents the maximum roaming data subscriptions time-out window.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUData</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUFactoryAddress</p></td>
<td><p>This attribute is a service control point attribute under the computer class that specifies a link back to the multipoint control unit (MCU) Factory to which it belongs. This service control point and attribute is created for every Microsoft MCU. Each Microsoft MCU must find the Back End Server of the pool to which it belongs, in order to retrieve pool-level settings from it.</p>
<p>The value of this attribute is the distinguished name (DN) of the MCU Factory. This is a single-valued attribute and marked for global catalog replication.</p>
<p>Forward link: <strong>Link ID 11026</strong></p>
<p>The corresponding back link to this forward link attribute is <strong>msRTCSIP-MCUServers</strong>.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactoryData</p></td>
<td><p>This is a multi-string reserved attribute. Settings stored in this attribute are represented as name=value pairs. Currently defined name=value pairs are:</p>
<ul>
<li><p>FactoryURL = &lt;URL&gt;</p></li>
</ul></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUFactoryPath</p></td>
<td><p>This is a single-valued attribute that contains the distinguished name (DN) of a single MCU factory associated with a pool.</p>
<p>Forward link: <strong>Link ID 11024</strong></p>
<p>The corresponding back link to this forward link attribute is <strong>msRTCSIP-PoolAddresses</strong>.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactoryProviderID</p></td>
<td><p>This attribute is a single-valued string that specifies the GUID of the MCU factory provider. Based on the GUID value, the MCU factory process determines whether to service this MCU type. If the GUID value is <strong>{F0810510-424F-46ef-84FE-6CC720DF1791}</strong>, then the MCU factory process (available by default in Lync Server) will process it. For any other GUID value, the MCU factory process will not service the MCU type.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUServers</p></td>
<td><p>This attribute is a multi-valued list of distinguished names (DN). This attribute contains a list of all MCU servers of the same type and vendor associated with this MCU factory. The valid value for each segment is 63 characters; the valid value for the entire FQDN is 255 characters.</p>
<p>Back link: Link ID 11027</p>
<p>The corresponding forward link to this back link is <strong>msRTCSIP-MCUFactoryAddress</strong>.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUType</p></td>
<td><p>This attribute is a single-valued string that specifies the medium the MCU can handle.</p>
<p>Supported valid types are:</p>
<ul>
<li><p>meeting</p></li>
<li><p>audio-video</p></li>
<li><p>chat</p></li>
<li><p>phone-conf</p></li>
</ul></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUVendor</p></td>
<td><p>This attribute is a single-valued string that specifies an MCU vendor’s name. All Microsoft MCUs will specify this attribute to be <strong>Microsoft Corporation</strong>.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MeetingFlags (obsolete)</p></td>
<td><p>This attribute defines different meeting options that are enabled globally for all users or contact objects. This attribute is a bit-mask value of integer type.</p>
<p>The valid values (and associated bit positions) are as follows:</p>
<ul>
<li><p>0: AllowOrganizeMeetingWithAnonymousParticipants is None (do not allow users to invite anonymous users to meetings) (no bits set)</p></li>
<li><p>4: AllowOrganizeMeetingWithAnonymousParticipants is Everyone (allow all users to invite anonymous users to meetings) (bit position 2)</p></li>
<li><p>8: AllowOrganizeMeetingWithAnonymousParticipants is UsePerUserSetting (allow users to invite anonymous users to meetings based on per user setting) (bit position 3)</p></li>
<li><p>16: UserPerUserMeetingPolicy (meeting policy is defined per user) (bit position 4)</p></li>
</ul></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MeetingPolicy (obsolete)</p></td>
<td><p>This attribute specifies the distinguished name (DN) of the policy the administrator has assigned for this user as a single-valued attribute.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MinPresenceSubscriptionTimeout (obsolete)</p></td>
<td><p>This attribute represents the minimum presence subscription time-out window.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MinRegistrationTimeout (obsolete)</p></td>
<td><p>This attribute represents the minimum registration time-out window.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MinRoamingDataSubscriptionTimeout (obsolete)</p></td>
<td><p>This attribute represents the minimum roaming data subscription time-out window.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MirrorBackEndServer</p></td>
<td><p>This attribute is used to store the mirrored SQL Server backend used by the Front End pool.</p></td>
<td><p>New in Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MobilityFlags</p></td>
<td><p>This attribute contains options and flags that define mobility settings.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MobilityPolicy</p></td>
<td><p>This attribute contains the DN for a mobility policy object.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-NumDevicesPerUser (obsolete)</p></td>
<td><p>This attribute represents the allowed number of devices on which a user can register for SIP communications and subscribe to presence.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-OptionFlags</p></td>
<td><p>This attribute specifies the options that are enabled for the user or contact object. This attribute is a bit-mask value of type integer. Each option is represented by a bit. This attribute is marked for global catalog replication.</p>
<p>The valid values (and associated bit positions) are as follows:</p>
<ul>
<li><p>1: Enabled for public instant messaging (IM) connectivity (bit position 0)</p></li>
<li><p>2: Reserved (bit position 1)</p></li>
<li><p>4: Reserved (bit position 2)</p></li>
<li><p>8: Reserved (bit position 3)</p></li>
<li><p>16: Remote call control Enabled [Telephony] (bit position 4)</p></li>
<li><p>64: AllowOrganizeMeetingWithAnonymousParticipants (allow users to invite anonymous users to meetings (bit position 6)</p></li>
<li><p>128: UCEnabled (enable users for UC) (bit position 7)</p></li>
<li><p>256: EnabledForEnhancedPresence (enable user for public IM connectivity) (bit position 8)</p></li>
<li><p>512: RemoteCallControlDualMode (bit position 9)</p></li>
</ul></td>
<td><p>New in Live Communications Server 2005 with SP1.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-OriginatorSID</p></td>
<td><p>This attribute is used in resource and central forest topologies to enable single sign-on when a user’s ObjectSID from the Windows NT Server principal account is copied into this attribute of the corresponding user or contact object in the resource or central forest. Communicator Web Access searches for a user in AD DS using this attribute or the user’s ObjectSID. This attribute is marked for global catalog replication.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-OwnerUrn</p></td>
<td><p>This attribute is the Uniform Resource Name (URN) of the owner for an application contact.</p></td>
<td><p>New in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Pattern (obsolete)</p></td>
<td><p>This single-valued string attribute contains a pattern used for matching dial numbers into E.164 format. If the dial number matches this pattern, the translation is applied to the dialed number.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PhoneRouteBL (obsolete)</p></td>
<td><p>This multi-valued attribute contains a list of phone route distinguished names (DN). This attribute specifies the back link to one or more phone routes.</p>
<p>Back link: <strong>Link ID 11033</strong></p>
<p>This attribute corresponds to the forward link <strong>msRTCSIP-RouteUsageLinks</strong>.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PhoneRouteData (obsolete)</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PhoneRouteName (obsolete)</p></td>
<td><p>This single valued UNICODE string attribute specifies the friendly name of the phone route, so it can easily be referenced by the administrator.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PhoneUsageData (obsolete)</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PolicyContent (obsolete)</p></td>
<td><p>This attribute is a single-valued Unicode string. This string attribute contains the policy definition in XML format. The XML schema definition is common across different policy types, only the settings are different for each policy type.</p>
<p>The XML schema definition (XSD) is defined as follows:</p>
<pre><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;xs:schema id=&quot;instance&quot; xmlns=&quot;&quot; xmlns:xs=&quot;http://www.w3.org/2001/XMLSchema&quot; xmlns:msdata=&quot;urn:schemas-microsoft-com:xml-msdata&quot;&gt;
  &lt;xs:element name=&quot;instance&quot; msdata:IsDataSet=&quot;true&quot;&gt;
    &lt;xs:complexType&gt;
      &lt;xs:choice maxOccurs=&quot;unbounded&quot;&gt;
        &lt;xs:element name=&quot;property&quot; nillable=&quot;true&quot;&gt;
          &lt;xs:complexType&gt;
            &lt;xs:simpleContent msdata:ColumnName=&quot;property_Text&quot; msdata:Ordinal=&quot;1&quot;&gt;
              &lt;xs:extension base=&quot;xs:string&quot;&gt;
                &lt;xs:attribute name=&quot;name&quot; type=&quot;xs:string&quot; /&gt;
              &lt;/xs:extension&gt;
            &lt;/xs:simpleContent&gt;
          &lt;/xs:complexType&gt;
        &lt;/xs:element&gt;
      &lt;/xs:choice&gt;
    &lt;/xs:complexType&gt;
  &lt;/xs:element&gt;
&lt;/xs:schema&gt;</code></pre></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PolicyData (obsolete)</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PolicyType (obsolete)</p></td>
<td><p>This single-valued Unicode string attribute contains the policy type. Valid policy types are as follows:</p>
<ul>
<li><p>meeting</p></li>
<li><p>telephony</p></li>
</ul></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolAddress</p></td>
<td><p>This attribute specifies a link back to the pool to which a computer belongs. This attribute is set regardless of whether the computer is running the Standard Edition or the Enterprise Edition of Lync Server. This attribute is marked for global catalog replication.</p>
<p>The valid value is the domain name of the pool.</p>
<p>Forward link: <strong>Link ID 11022</strong></p>
<p>The corresponding back link to this forward link attribute is <strong>msRTCSIP-FrontEndServers</strong>.</p></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolAddresses</p></td>
<td><p>This is a multi-valued attribute that contains a list of the distinguished names (DN) of pools with which the MCU factory is associated.</p>
<p>Back link: <strong>Link ID 11025</strong></p>
<p>The corresponding forward link to this back link is <strong>msRTCSIP-MCUFactoryPath</strong>.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolData</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>New in Live Communications Server 2005 with SP1.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolDisplayName</p></td>
<td><p>This attribute specifies an arbitrary name for a pool that is displayed by the management console. This name can be changed by the administrator.</p>
<p>The valid value is a string representing the name of a pool.</p></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolDomainFQDN</p></td>
<td><p>This attribute is a single-valued string value. The value of this attribute, when present, represents the pool’s domain FQDN if the administrator wants to create a Front End pool with an FQDN that does not conform to the Active Directory domain structure in which the Front End pool is created (for example, a SIP namespace disjoined from Domain Name System (DNS) namespace).</p>
<p>We recommend that you map the Front End pool domain FQDN to the domain name portion as the Active Directory domain in which the pool resides. Therefore, when no value is present in this attribute, the Front End pool FQDN will default to the Active Directory domain name structure, as denoted by the <strong>dnsHostName</strong> attribute.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolFunctionality</p></td>
<td><p>A multi-valued list of the domain names of all Lync Server, Enterprise Edition servers associated with a pool. This attribute of type integer defines whether the pool is capable of instant messaging (IM) and presence, and meetings.</p>
<p>The possible valid value types are as follows:</p>
<ul>
<li><p>Undefined: IM and Presence Service (Live Communications Server 2005 and 2003)</p></li>
<li><p>1: IM and Presence Service (Lync Server)</p></li>
<li><p>2: IM and Presence and Meeting Service (Lync Server)</p></li>
</ul></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolType</p></td>
<td><p>This attribute specifies whether a server pool is running Standard Edition server or Enterprise Edition server. This attribute is a bit-mask value of type integer. Each option is represented by a bit.</p>
<p>The valid values (and associated bit positions) are as follows:</p>
<ul>
<li><p>1: Standard Edition server, hosts users (bit position 0)</p></li>
<li><p>2: Enterprise Edition server, hosts users (bit position 1)</p></li>
<li><p>4: Standard Edition server, hosts applications (bit position 2)</p></li>
<li><p>8: Enterprise Edition server, hosts applications (bit position 3)</p></li>
</ul>
<p>Because Lync Server does not support pools that host only applications, the only valid values are as follows:</p>
<ul>
<li><p>5: Standard Edition server, hosts users and applications (bit positions 0 and 2)</p></li>
<li><p>10: Enterprise Edition server, hosts users and applications (bit positions 1 and 3)</p></li>
</ul></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolVersion</p></td>
<td><p>This attribute defines the pool version. It is an integer type that is incremented with each major product release.</p>
<p>The possible valid value types are as follows:</p>
<ul>
<li><p>0: Live Communications Server 2003</p></li>
<li><p>1: Live Communications Server 2005</p></li>
<li><p>2: Live Communications Server 2005 with SP1</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
<li><p>5: Lync Server 2010</p></li>
</ul></td>
<td><p>Live Communications Server 2005 with SP1.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PresenceFlags</p></td>
<td><p>This attribute contains options and flags that define presence settings.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PresencePolicy</p></td>
<td><p>This attribute contains the DN for a presence policy object.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PrimaryHomeServer</p></td>
<td><p>This attribute enables a user or contact for SIP messaging. It is added to the contact class because in the central forest topology, contact objects, not user objects, are SIP enabled.</p>
<p>The valid value is the DN of the Standard Edition server or Enterprise Edition Front End pool where a user is homed.</p></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PrimaryUserAddress</p></td>
<td><p>This attribute contains the SIP address of a given user.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PrivateLine</p></td>
<td><p>This attribute contains the device ID of the private line device.</p></td>
<td><p>New in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Routable</p></td>
<td><p>This attribute is a Boolean attribute used to determine whether Lync Server is authorized to route to this service using its GRUU address. If this value is set to <strong>TRUE</strong>, Lync Server is authorized to route to this service. If this value is set to <strong>FALSE</strong>, Lync Server is not authorized to route to this service.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-RouteUsageAttribute (obsolete)</p></td>
<td><p>This single-valued UNICODE string attribute defines an attribute that qualifies the usage for a phone route. Selection of a phone route is determined based on two elements: the usage attribute assigned to the phone route and the caller’s allowed policy usage attributes. The first phone route with a usage attribute that matches the caller’s allowed usage is selected.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-RouteUsageLinks (obsolete)</p></td>
<td><p>This multi-valued distinguished name (DN) attribute contains a list of route usage distinguished names.</p>
<p>Forward link: <strong>Link ID 11032</strong></p>
<p>This attribute is a forward link to the corresponding back link <strong>msRTCSIP-PhoneRouteBL</strong>.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-RoutingPoolDN</p></td>
<td><p>This attribute contains the DN that points to the pool that all SIP traffic addressed to this MCU or Trusted Service must go through.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-RuleName (obsolete)</p></td>
<td><p>This single-valued UNICODE string attribute specifies the friendly name of the normalization rule, so it can easily be referenced by an administrator.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-SchemaVersion</p></td>
<td><p>This attribute represents the schema version currently deployed in the organization.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-SearchMaxRequests (obsolete)</p></td>
<td><p>This attribute limits the number of search results to be returned from a directory search when a user searches for a contact using Communicator. This attribute will override the value provided by the client.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-SearchMaxResults (obsolete)</p></td>
<td><p>This attribute limits the number of search requests returned.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ServerBL</p></td>
<td><p>This multi-valued attribute is a back link that contains a list of distinguished names (DN). These DNs point to a pool or <strong>TrustedService</strong> object.</p>
<p>This attribute corresponds to the forward link <strong>msRTCSIP-TrustedServiceLinks</strong>.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ServerData</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ServerReferenceBL (obsolete)</p></td>
<td><p>This multi-valued attribute contains a list of distinguished names. These distinguished names are back links that reference other server objects that can be assigned a default location profile.</p>
<p>Back link: <strong>Link ID 11037</strong></p>
<p>The corresponding forward link to this back link is <strong>msRTCSIP-DefaultLocationProfileLink</strong>.</p>
<p>This back link attribute references pools and Mediation Servers only.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ServerVersion</p></td>
<td><p>This attribute defines the version information of the server. This version number applies to all server roles. It is a monotonously increasing integer that increments with each official product release.</p>
<p>The possible valid values are as follows:</p>
<ul>
<li><p>Undefined: Live Communications Server 2003</p>
<p>                 Live Communications Server 2005</p>
<p>                 Live Communications Server 2005 with SP1</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
<li><p>5: Lync Server 2010</p></li>
<li><p>6: Lync Server 2013</p></li>
</ul></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-SourceObjectType</p></td>
<td><p>This single-valued attribute of integer type specifies the type of object the <strong>msDS-SourceObjectDN</strong> points to, as follows:</p>
<ul>
<li><p>null | 0x00000001: Represents a Windows NT Server principal user object from a different forest</p></li>
<li><p>The following attributes represent a group type from a different forest for distribution group expansion:</p>
<ul>
<li><p>0x00000002: ADS_GROUP_TYPE_GLOBAL_GROUP</p></li>
<li><p>0x00000004: ADS_GROUP_TYPE_DOMAIN_LOCAL_GROUP</p></li>
<li><p>0x00000004: ADS_GROUP_TYPE_LOCAL_GROUP</p></li>
<li><p>0x00000008: ADS_GROUP_TYPE_UNIVERSAL_GROUP</p></li>
<li><p>0x80000000: ADS_GROUP_TYPE_SECURITY_ENABLED</p></li>
<li><p>0x90000000: Represents an Auto-Attendant or subscriber access object from the same forest or a different forest</p></li>
</ul></li>
</ul></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-SubscriptionAuthRequired (obsolete)</p></td>
<td><p>-</p></td>
<td><p>New in Live Communications Server 2003.</p>
<p>Obsolete in Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TargetHomeServer</p></td>
<td><p>This attribute enables you to move a user or contact object from one Lync Server pool to another. This attribute is added to the contact class, because in the central forest topology, contact objects, not user objects, are SIP enabled.</p>
<p>The valid value is the DN of the destination Standard Edition server or Front End pool to which a user is to be moved.</p></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TargetPhoneNumber (obsolete)</p></td>
<td><p>This single-valued string attribute contains a phone number pattern or range to route to the specified gateways defined in <strong>msRTCSIP-Gateways</strong>.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TargetUserPolicies</p></td>
<td><p>This attribute stores name-value pairs for target policies for Lync Server users.</p></td>
<td><p>New in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TenantId</p></td>
<td><p>This attribute stores the unique identifier for a tenant.</p></td>
<td><p>New in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Translation (obsolete)</p></td>
<td><p>This attribute is used by the voice feature of Lync Server and contains the translation string to apply on the dialed number, if a match is found.</p></td>
<td><p>New in Office Communications Server 2007.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedMCUData</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedMCUFQDN</p></td>
<td><p>This attribute is a string value that contains the FQDN of the MCU. This is a single-valued attribute. The valid value for each segment is 63 characters; the valid value for the entire FQDN is 255 characters.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedProxyData</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedProxyFQDN</p></td>
<td><p>This attribute is a string value that contains the FQDN of the server running Proxy Server. This attribute is single-valued. The valid value for each segment is 63 characters; the valid value for the entire FQDN is 255 characters.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServerData</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedServerFQDN</p></td>
<td><p>This attribute is a single-valued attribute that represents the FQDN of a trusted server.</p></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServerVersion</p></td>
<td><p>This attribute specifies the version number of a server in the trusted server list.</p>
<p>The possible valid values are as follows:</p>
<ul>
<li><p>NULL: Live Communications Server 2003</p></li>
<li><p>2: Live Communications Server 2005</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
<li><p>5: Lync Server 2010</p></li>
<li><p>6: Lync Server 2013</p></li>
</ul></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedServiceFlags</p></td>
<td><p>This attribute defines the options that are enabled for the trusted service.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServiceLinks</p></td>
<td><p>This multi-valued attribute contains a list of distinguished names (DN) that reference a trusted service object, such as a Media Relay Authentication Service. A Media Relay Authentication Service (physically collocated on the Edge Server running the A/V Conferencing service) must be associated with a pool to support audio scenarios for remote users.</p>
<p>The corresponding back link to this forward link attribute is <strong>msRTCSIP-ServerBL</strong>.</p></td>
<td><p>UC</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedServicePort</p></td>
<td><p>This attribute is an integer that defines the port number used to connect to this GRUU service.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServiceType</p></td>
<td><p>This attribute is a string value that defines the type of GRUU service it represents.</p>
<p>The valid GRUU service types are as follows:</p>
<ul>
<li><p>MediationServer</p></li>
<li><p>Gateway</p></li>
<li><p>Media Relay Authentication Service (MRAS)</p></li>
<li><p>QoSM</p></li>
<li><p>msRTCSIP-UserExtension CWA</p></li>
</ul></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedWebComponentsServerData</p></td>
<td><p>This attribute is reserved for future use.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedWebComponentsServerFQDN</p></td>
<td><p>This attribute is a string value that contains the FQDN of the IIS running Lync Server Web Services. This is a single-valued attribute. The valid value for each segment is 63 characters; the valid value for the entire FQDN is 255 characters.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UCFlags (obsolete)</p></td>
<td><p>This attribute defines different UC options that are enabled globally to all user or contact objects. This attribute is a bit-mask value of integer type. Each option is represented by the presence of a bit.</p>
<p>The possible valid value (and associated bit position) are as follows:</p>
<ul>
<li><p>4: UsePerUserUCPolicy (bit position 2)</p></li>
</ul>
<p>When this bit is set, the UC policy is defined per user.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UCPolicy (obsolete)</p></td>
<td><p>This single-valued attribute contains the distinguished name (DN) of the UC policy that the administrator has assigned for this user.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserDomainList (obsolete)</p></td>
<td><p>This attribute provides a list of all the domains in a forest that host SIP-enabled users. The default is an empty list, indicating that all domains in the forest are SIP-enabled.</p>
<p>Valid values are multiple strings representing the domain names of individual domains.</p></td>
<td><p>New in Live Communications Server 2005.</p>
<p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UserEnabled</p></td>
<td><p>This attribute determines whether the user is currently enabled for Lync Server.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserExtension</p></td>
<td><p>This multi-valued attribute contains a list of name-value pairs in the format of &quot;name=value.&quot; This attribute is marked for global catalog replication.</p></td>
<td><p>New in Live Communications Server 2005 with SP1.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UserLocationProfile</p></td>
<td><p>This attribute contains the distinguished name (DN) that points to a location profile object.</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserPolicies</p></td>
<td><p>This attribute stores name-value pairs for user policies.</p></td>
<td><p>New in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UserPolicy</p></td>
<td><p>This is a multi-valued attribute containing a list of distinguished names with binary (DN_WITH_BINARY) pointing to global user policies of different types. The binary part indicates the type of policy to which the DN portion points.</p>
<p>The valid binary values are as follows:</p>
<ul>
<li><p>0x00000001: Meeting policy</p></li>
<li><p>0x00000002: UC policy</p></li>
<li><p>0x00000005: Presence policy</p></li>
</ul></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserRoutingGroupId</p></td>
<td><p>This is the SIP routing group ID. Users in the same group will register to the same Front End Server.</p></td>
<td><p>New in Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponentsData</p></td>
<td><p>This is a multi-valued attribute. This attribute is reserved for future use.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-WebComponentsPoolAddress</p></td>
<td><p>This single-valued attribute points to the pool or Standard Edition server to which the web components belong.</p>
<p>Forward link: <strong>Link ID 11028</strong></p>
<p>The corresponding back link to this forward link attribute is <strong>msRTCSIP-WebComponentsServers</strong>.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponentsServers</p></td>
<td><p>This attribute is a multi-valued list of distinguished names. This attribute contains a list of all Web servers associated with this pool.</p>
<p>Back link: <strong>Link ID 11029</strong></p>
<p>The corresponding forward link to this back link is <strong>msRTCSIP-WebComponentsPoolAddress</strong>.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-WMIInstanceId (obsolete)</p></td>
<td><p>-</p></td>
<td><p>New in Live Communications Server 2003.</p>
<p>Obsolete in Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>OtherIPPhone</p></td>
<td><p>This existing Active Directory attribute is used by telephony to specify the list of alternate TCP/IP addresses for a phone.</p></td>
<td><p>New in Windows Server 2008 operating system.</p></td>
</tr>
<tr class="even">
<td><p>PhoneOfficeOther</p></td>
<td><p>This existing Active Directory attribute is used by the voice components in Lync Server, for contact objects only, for the purpose of routing calls to the unified messaging auto-attendant and subscriber access numbers. The unconditional call forwarding address is stored in this multi-valued attribute. This account is created for the specific purpose of auto-attendant and subscriber access. This account’s attributes should not be modified by administrators.</p></td>
<td><p>New in Windows 2000 operating system.</p></td>
</tr>
<tr class="odd">
<td><p>ProxyAddresses</p></td>
<td><p>This existing Active Directory multi-valued attribute is part of the base Active Directory schema introduced in Windows 2000. This attribute contains the various X400, X500, and SMTP addresses of the user’s email. In Live Communications Server 2003 and later, the user’s SIP URI is added to this list, using the &quot;sip:&quot; tag.</p>
<p>The following applications search the user’s SIP URI from this attribute:</p>
<ul>
<li><p>Microsoft Office Outlook 2003 messaging and collaboration client</p></li>
<li><p>Microsoft Office SharePoint Server 2007</p></li>
</ul></td>
<td><p>New in Windows 2000 operating system.</p></td>
</tr>
<tr class="even">
<td><p>TelephoneNumber</p></td>
<td><p>This existing Active Directory attribute contains the telephone number for the user.</p></td>
<td><p>New in Windows 2000 operating system.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

