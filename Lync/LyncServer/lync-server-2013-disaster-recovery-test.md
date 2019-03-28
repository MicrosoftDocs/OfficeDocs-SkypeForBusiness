---
title: 'Lync Server 2013: Disaster recovery test'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Disaster recovery test
ms:assetid: 04f5e747-d837-4350-9fc0-8605dbf025a7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn747887(v=OCS.15)
ms:contentKeyID: 63969571
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Disaster recovery test in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-01-26_

Perform a system recovery for a Lync Server 2013 pool server to test your documented disaster recovery process. This test will simulate a complete hardware failure for one server, and will help guarantee that the resources, plans, and data is available for recovery. Try to rotate the focus of the test each month so that your organization tests the failure of a different server or other piece of equipment every time.

Note that the schedule by which organizations perform Disaster Recovery testing will vary. It is very important that disaster recovery testing is not ignored or neglected.

<div>


Export your Lync Server 2013 topology, policies, and configuration settings to a file. Among other things, this file can then be used to restore this information to the Central Management store after an upgrade, a hardware failure, or some other issue has resulted in data loss.

Import your Lync Server 2013 topology, policies, and configuration settings to either the Central Management store or to the local computer as shown in the following commands:

`Import-CsConfiguration -ByteInput <Byte[]> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]`

`Import-CsConfiguration -FileName <String> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]`

To back up production Lync Server 2013 data:

  - Back up the RTC and LCSLog databases by using the standard SQL Server backup process to dump the database to a file or tape dump device.

  - Use third-party backup application to back up the data to file or to tape.

  - Use the Export-CsUserData cmdlet to create an XML export of the whole RTC database.

  - Use the file system backup or third-party to back up meeting content and compliance logs.

  - Use the Export-CsConfiguration command-line tool to back up Lync Server 2013 settings.

The first step in the failover procedure includes a forced move of users from the production pool to the Disaster Recovery pool.

This will be a forced move because the production pool won't be available to accept the user relocation.

The Lync Server 2013 move user process is effectively a change to an attribute on the user account object in addition to a record update on the RTC SQL database.

This data can be restored through the following two processes:

  - RTC database can be restored from the original backup dump device from the production SQL Server using the standard SQL Server restore process, or using a third-party backup/restore utility.

  - User contact data can be restored with the DBIMPEXP.exe utility using the XML file that was created from the production SQL Server export.

After this data is restored, users can effectively connect to the Disaster Recovery Lync Server 2013 pool, and operate as usual.

To enable users to connect to the Disaster Recovery Lync Server 2013 pool, a DNS record change will be required.

The production Lync Server 2013 pool will be referenced by clients using the auto-configuration and DNS SRV records of:

  - SRV: \_sip.\_tls.\<domain\> /CNAME: SIP.\<domain\>

  - CNAME: SIP.\<domain\> /cvc-pool-1.\<domain\>

To facilitate the failover, this CNAME record must be updated to reference the DROCSPool FQDN:

  - CNAME: SIP.\<domain\> /DROCSPool.\<domain\>

  - Sip.\<domain\>

  - AV.\<domain\>

  - webconf.\<domain\>

  - OCSServices.\<domain\>

<div>


> [!IMPORTANT]  
> For detailed administration and management procedures, see <A href="lync-server-2013-backing-up-and-restoring-lync-server.md">Backing up and restoring Lync Server 2013</A>.



</div>

</div>

<div>

## See Also


[Planning for high availability and disaster recovery in Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)  
[Backup and high availability cmdlets in Lync Server 2013](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)  


[Import-CsConfiguration](https://docs.microsoft.com/powershell/module/skype/Import-CsConfiguration)  
[Backing up and restoring Lync Server 2013](lync-server-2013-backing-up-and-restoring-lync-server.md)  
[Managing Lync Server 2013 disaster recovery, high availability, and Backup Service](lync-server-2013-managing-lync-server-disaster-recovery-high-availability-and-backup-service.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

