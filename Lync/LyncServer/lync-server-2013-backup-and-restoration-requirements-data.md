---
title: 'Lync Server 2013: Backup and restoration requirements: data'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: 'Backup and restoration requirements: data'
ms:assetid: ecfb8e4d-cb4f-476d-9772-4486bd683c04
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202194(v=OCS.15)
ms:contentKeyID: 51541526
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Backup and restoration requirements in Lync Server 2013: data

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-26_

Lync Server uses settings and configuration information that are stored in databases, and data that is stored in databases and file stores. This topic describes the data that you need to back up to be able to restore service if your organization experiences a failure or outage, and also identifies the data and components used by Lync Server that you need to back up separately.

<div>

## Settings and Configuration Requirements

This topic includes procedures for backing up and restoring the settings and configuration information that is required for recovery of Lync Server service. The configuration information is located in the Central Management store or on another back-end database or on Standard Edition server.

The following table identifies the settings and configuration information that you need to back up and restore.

### Settings and Configuration Data

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Type of data</th>
<th>Where stored</th>
<th>Description / When to back up</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Topology configuration information</p></td>
<td><p>Central Management store (database: Xds.mdf)</p></td>
<td><p>Topology, policy, and configuration settings.</p>
<p>Back up with your regular backups and after you use Lync Server Control Panel or cmdlets to modify your configuration or policies.</p></td>
</tr>
<tr class="even">
<td><p>Location information</p></td>
<td><p>Central Management store (database: Lis.mdf)</p></td>
<td><p>Enterprise Voice Enhanced 9-1-1 (E9-1-1) configuration information. This information is generally static.</p>
<p>Back up with your regular backups.</p></td>
</tr>
<tr class="odd">
<td><p>Response Group configuration information</p></td>
<td><p>Back End Server or Standard Edition server (database: RgsConfig.mdf)</p></td>
<td><p>Response Group agent groups, queues, and workflows.</p>
<p>Back up with your regular backups and after you add or change agent groups, queues, or workflows.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Data Requirements

Here is a list of the Lync Server data that you need to back up so that you can restore Lync Server service in the event of a failure.

Note that some types of data are not required for recovery. This topic does not contain procedures for backing up these types of data, which include the following:

  - Transient user data, such as endpoints and subscriptions, active conferencing servers, and transient conferencing states (database: RtcDyn.mdf)

  - Address Book data (databases: Rtcab.mdf and Rtcab1.mdf). The Address Book database is regenerated automatically from Active Directory Domain Services.

  - Dynamic information for the Call Park application (database: CpsDyn.mdf)

  - Transient Response Group data, such as agent sign-in state and call waiting information (database: RgsDyn.mdf)

  - The compliance database for Persistent Chat (database: MgcComp.mdf). If you have Persistent Chat compliance enabled, the information in the Persistent Chat Compliance database is transient as long as you have an adapter configured to read information from the database and convert it to an alternate format. Hence the compliance database for Persistent Chat is considered transient.
    
    Lync Server 2013 Persistent Chat Server ships with an XML adapter. You can also install custom adapters that take this data and move it to other sources, such as Exchange Hosted Archives.

The following table identifies the data that you need to back up and restore.

### Data Stored in Databases

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Type of data</th>
<th>Where stored</th>
<th>Description / When to back up</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Persistent user data</p></td>
<td><p>Back End Server or Standard Edition server (database: RTCXDS.mdf)</p></td>
<td><p>User rights, user Contacts lists, server or pool data, scheduled conferences, and so on. This user data does not include content uploaded to a conference.</p>
<p>Back up with your regular backups. This information is dynamic, but the loss of updates is not catastrophic to Lync Server if you need to restore to your last regular backup. If Contacts lists are critical to your organization, you can back up this data more frequently.</p></td>
</tr>
<tr class="even">
<td><p>Archiving data</p></td>
<td><p>Archiving database (database: LcsLog.mdf)</p>
<p>This data may be stored on Exchange 2013, if you have enabled the Microsoft Exchange integration option. Otherwise, this data is kept in a Lync Server Archiving database, which may be collocated with another Lync Server database, or stand-alone on a separate database server.</p></td>
<td><p>Instant messaging (IM) and meeting content.</p>
<p>This data is not critical to Lync Server, but it may be critical to your organization for regulatory purposes. Determine your back up schedule accordingly.</p></td>
</tr>
<tr class="odd">
<td><p>Monitoring data</p></td>
<td><p>Monitoring databases (LcsCDR.mdf and QoeMetrics.mdf)</p>
<p>These databases may be collocated with another Lync Server database, or stand-alone on a separate database server.</p></td>
<td><p>Call detail records (LcsCDR.mdf) and Quality of Experience (QoE) metrics (QoeMetrics.mdf).</p>
<p>Call detail records are dynamic and may be critical to your business. Determine your back up schedule by considering whether you need these records for regulatory reasons.</p>
<p>Quality of experience information is dynamic. Loss of QoE data is not critical for the operation of Lync Server, but it may be critical to your business. Determine your back up schedule based on how critical this information is to your organization.</p></td>
</tr>
<tr class="even">
<td><p>Persistent Chat data</p></td>
<td><p>Persistent Chat database (mgd.mdf).</p>
<p>This database may be collocated with another Lync Server database, or stand-alone on a separate database server.</p></td>
<td><p>Persistent Chat Data is actual chat content being posted in chat rooms. This data is often business critical.</p>
<p>You can choose to use SQL Server backup, or export the database by using the <strong>Export-CsPersistentChatData</strong> cmdlet that is provided in Lync Server. For recovery of the data, you can import and restore the database to the point of the last full backup, which means you cannot restore the database to the point of failure.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## File Store Data Requirements

In an Enterprise Edition deployment, the Lync Server file store is typically located on a file server. In a Standard Edition deployment, the Lync Server file store is located by default on the Standard Edition server. Typically, there is one Lync Server file store that is shared for a site. The Persistent Chat file store uses the same file share as the Lync Server file store.

File store locations are identified as \\\\server\\share name. To find the specific locations of your file stores, open Topology Builder and look in the **File stores** node.

The following table identifies the file stores you need to back up and restore.

### File Stores

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Type of data</th>
<th>Where stored</th>
<th>Description / when to back up</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server file store</p></td>
<td><p>Typically on a file server, file cluster, or a Standard Edition server</p></td>
<td><p>Meeting content, meeting content metadata, meeting compliance logs, application data files, update files for device updates, audio files for Response Group, Call Park, and Announcement applications, and files posted into Persistent Chat rooms.</p>
<p>Back up with your regular backups.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Additional Backup Requirements

To help ensure your ability to restore Lync Server services in the event of a failure, you must back up some necessary components that are not part of Lync Server itself. The following components are not backed up or restored as part of the Lync Server backup and restoration process described in this document:

  - **Active Directory Domain Services**   You need to back up AD DS by using Active Directory tools at the same time that you back up Lync Server. It is important to keep AD DS synchronized with Lync Server, to avoid problems that can occur when Lync Server expects contact objects that do not match those in AD DS. AD DS stores the following settings which are used by Lync Server:
    
      - User SIP URI and other user settings.
    
      - Contact objects for applications such as Response Group and Conferencing Attendant.
    
      - A pointer to the Central Management Store.
    
      - Kerberos Authentication Account (an optional computer object) and Lync Server security groups.
    
    For details about backing up and restoring AD DS in Windows Server 2008, see "AD DS Backup and Recovery Step-by-Step Guide" at [http://go.microsoft.com/fwlink/p/?linkId=209105](http://go.microsoft.com/fwlink/p/?linkid=209105).

  - **Certification authority and certificates**   Use your organization's policy for backing up your certification authority (CA) and certificates. If you use exportable private keys, you can back up the certificate and the private key, and then export them if you use the procedures in this document to restore Lync Server. If you use an internal CA, you can re-enroll if you need to restore Lync Server. It is important that you retain the private key in a secure location where it will be available if a computer fails.

  - **System Center Operations Manager**   If you use Microsoft System Center Operations Manager (formerly Microsoft Operations Manager) to monitor your Lync Server deployment, you can optionally back up the data it creates while it is monitoring Lync Server. Use your standard SQL Server backup process to back up System Center Operations Manager files. These files are not restored during recovery.

  - **Public switched telephone network (PSTN) gateway configuration**   If you use Enterprise Voice or Survivable Branch Appliances, you need to back up the PSTN gateway configuration. See your vendor for details about backing up and restoring PSTN gateway configurations.

  - **Coexisting versions of Lync Server or Office Communications Server**   If your Lync Server 2013 deployment coexists with Lync Server 2010 or an earlier version of Office Communications Server, you can’t use the procedures in this document for backing up or restoring the earlier version. Instead, you must use the backup and restoration procedures documented specifically for your earlier version. For details about backing up and restoring Lync Server 2010, see [http://go.microsoft.com/fwlink/p/?linkId=265417](http://go.microsoft.com/fwlink/p/?linkid=265417) . For details about backing up and restoring Microsoft Office Communications Server 2007 R2, see [http://go.microsoft.com/fwlink/p/?linkId=168162](http://go.microsoft.com/fwlink/p/?linkid=168162).

  - **Infrastructure information**   You need to back up information about your infrastructure, such as your firewall configuration, load balancing configuration, Internet Information Services (IIS) configuration, Domain Name System (DNS) records and IP addresses, and Dynamic Host Configuration Protocol (DHCP) configuration. For details about backing up these components, check with their respective vendors.

  - **Microsoft Exchange and Exchange Unified Messaging (UM)**   Backup and restore Microsoft Exchange and Exchange UM as described in the Microsoft Exchange documentation. For details about backing up and restoring Exchange Server 2013, see [http://go.microsoft.com/fwlink/?LinkId=285384](http://go.microsoft.com/fwlink/?linkid=285384). For details about backing up and restoring Exchange Server 2010, see [http://go.microsoft.com/fwlink/p/?linkId=209179](http://go.microsoft.com/fwlink/p/?linkid=209179).
    
    Note that Lync Server 2013 introduces the ability to have user contact lists, high definition user photos, and archiving data stored in Exchange 2013. See the following list to see how to back up these types of data:
    
      - **High definition photos** are backed up as part of the Exchange Server backup.
    
      - **Unified contact store** is introduced in Lync Server 2013. Unified contact store enables users to keep all their contact information in Exchange 2013.
        
        You should make sure that backups are up-to-date for users in terms of whether their user contacts are stored in the unified contact store or on the Lync Back End Server. The following scenarios illustrate where migrating user contacts to the unified contact store can cause issues for the backup and restore process.
        
        **Scenario 1:** User contacts are migrated to the unified contact store, and a restore is performed from a Lync Server backup taken prior to the migration of user contacts. In this scenario, the user will have a state of outdated contacts for up to one day until Lync Server Migration Task begins migrating user contacts to Exchange. (Note that because the user contacts were previously migrated to the unified contact store, the Exchange contact information will be used). No administrator intervention is needed in this scenario.
        
        **Scenario 2:** User contacts were previously stored in the unified contact store, but then rolled back. A restore is performed from a Lync Server backup taken when the user contacts were stored in the unified contact store. In this scenario, an error message of `Error: Incorrect Exchange Version` in the client or Lyss server logs may indicate this as an issue. The user will be able to access their contact list in Lync 2013 directly from Exchange, but client’s state will not match the Lync Server state. To fix this, an administrator will need to run the **Invoke-CsUCSRollback** cmdlets for the affected users.
    
      - **Archiving Data** can be stored in Exchange 2013. This data is not critical to Lync Server, but it may be critical to your organization for regulatory purposes. If archiving data is stored in Exchange and is critical to your organization, then follow Exchange backup and restore procedures. Note that archiving data stored in Exchange cannot be moved back to Lync Server. Additionally, there is no way to move data already stored in the Lync archiving database to Exchange.

</div>

</div>

<span> </span>

</div>

</div>

</div>

