---
title: 'Lync Server 2013: Best practices for backup and restoration'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Best practices for backup and restoration
ms:assetid: abbce0e4-973a-4624-a0c1-e0f22e1d348b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202184(v=OCS.15)
ms:contentKeyID: 51541500
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Best practices for backup and restoration for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

This section includes two types of best practices:

  - Best practices for backup and restoration.

  - Best practices for minimizing the impact of a disaster.

<div>

## Best Practices for Backup and Restoration

To facilitate your backup and restoration process, apply the following best practices when you back up or restore your data:

  - Perform regular backups at appropriate intervals. The simplest and most commonly used backup type and rotation schedule is a full, nightly backup of the entire SQL Server database. Then, if restoration is necessary, the restoration process requires only one backup, and no more than a day’s data should be lost.

  - If you use cmdlets or the Lync Server Control Panel to make configuration changes, use the **Export-CsConfiguration** cmdlet to take a snapshot backup of the topology configuration file (Xds.mdf) after you make the changes, so that you won't lose the changes if you need to restore your databases. Note that this configuration is backed up in XML format and compressed as a ZIP file.

  - Make sure that the shared folder you plan to use for backing up Lync Server has sufficient disk space to hold all the backed up data.

  - Schedule backups when Lync Server usage is typically low, to improve server performance and user experience.

  - Make sure that the location where you back up data is secure (we recommend a remote location).

  - Keep the backup files where they will be available, in case you need to restore the data.

  - Plan for and schedule periodic testing of the restoration processes that are supported by your organization.

  - Validate your backup and restoration processes in advance to make sure that they work as expected.

</div>

<div>

## Best Practices for Minimizing the Impact of a Disaster

The best strategy for dealing with disastrous service interruptions (caused by unmanageable events such as power outages or sudden hardware failures) is to assume they will happen, and to plan accordingly.

If Lync services, with a minimum of disruption and outage, are business-critical for your organization, you should consider implementing paired pools of Front End Servers, as described in [Planning for high availability and disaster recovery in Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md). Then, if one of these pools has a disaster, an administrator can switch the users of that pool to be served by the other pool, with a minimum of downtime.

The disaster management plans that you develop as part of your backup and restoration strategy should include the following:

  - Keeping your software media, and your software and firmware updates, readily available.

  - Maintaining hardware and software records.

  - Backing up your data regularly and monitoring the integrity of your backups.

  - Training your staff in disaster recovery, documenting procedures, and implementing disaster recovery simulation drills.

  - Keeping spare hardware available, or, if you have a service level agreement (SLA), contracting with hardware vendors and suppliers for prompt replacements.

  - Separating the location of your transaction log files (.ldf files) and database files (.mdf files).

</div>

</div>

<span> </span>

</div>

</div>

</div>

