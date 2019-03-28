---
title: 'Lync Server 2013: Checking disk usage'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Checking disk usage
ms:assetid: 0f0cb9bf-3f11-43ff-be10-5c8e1b5c4f08
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720908(v=OCS.15)
ms:contentKeyID: 63969578
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Checking disk usage in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-04-30_

Hard disks drives are an important component of the Lync Server 2013 deployment. Without sufficient free disk volume, neither the operating system nor the Lync Server 2013 databases can function correctly. You must monitor the Lync Server 2013 back-end database statistics daily to help to make sure that servers do not run out of disk space, and to prepare to add storage resources as required.

Apart from checking space on disks hosting the operating system, program files, database, and transaction logs (Lync Server 2013 Back End), you should also monitor usage of the file system that includes disk space for file shares that contain the following important data:

  - Meeting content

  - Meeting content metadata

  - Meeting compliance logs

  - Application data files (used internally by the application server component)

  - Group Chat Server web service and compliance folders (to store files uploaded to the Group Chat web service)

  - Group Chat compliance XML files (that contain Group Chat compliance records)

  - Update files (for Device Update Service)

  - Address Book files

Lync Server 2013 needs hard disk space to store its databases and transaction logs in addition to files on file shares previously listed.

You should monitor the disk space regularly to help to make sure that the Lync Server 2013 deployment is not adversely affected because of insufficient storage resources.

Compare and maintain statistical information about available disk space on each Lync Server 2013 volume and expected growth of the databases and transaction log files. This helps with capacity planning and adding storage when the storage resources are required.

To accommodate troubleshooting and disaster recovery situations, we recommend that available free volume space be equal or greater than 110 percent of the size of database.

You can check free disk space by using the following methods:

1.  **System Center Operations Manager**   System Center Operations Manager can be used to warn administrators when volume space is constrained.

2.  **Running a script**   Monitor disk space by running a script that sends you a message if the available hard disk space falls below 20 percent. You can find a sample script on Microsoft Script Center on TechNet, examine: [http://gallery.technet.microsoft.com/scriptcenter/site/search?query=hard%20disk%20alert\&f%5B0%5D.Value=hard%20disk%20alert\&f%5B0%5D.Type=SearchText\&ac=5](http://gallery.technet.microsoft.com/scriptcenter/site/search?query=hard+disk+alert%26f%5b0%5d.value=hard+disk+alert%26f%5b0%5d.type=searchtext%26ac=5)

3.  **Windows Explorer**   Use Windows Explorer to check for disk space on volumes that store Lync Server 2013 logs and databases.

</div>

<span> </span>

</div>

</div>

</div>

