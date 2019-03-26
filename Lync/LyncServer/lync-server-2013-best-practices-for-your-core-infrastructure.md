---
title: 'Lync Server 2013: Best practices for your core infrastructure'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Best practices for your core infrastructure in Lync Server 2013
ms:assetid: 44aff88d-536c-4613-a81e-5398c9c6a648
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn518328(v=OCS.15)
ms:contentKeyID: 61071242
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Best practices for your core infrastructure in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-01-27_

You have probably already taken steps to design fault tolerance in your system, using practices such as ensuring hardware redundancy, guarding against power loss, routinely installing security updates and antivirus measures, and Monitoring Server activity. These practices benefit not only your Microsoft Lync Server 2013 infrastructure, but also your entire network. If you have not implemented these practices, we recommend that you do so before deploying Lync Server 2013.

To help protect the servers in your Lync Server 2013 deployment from accidental or purposeful harm that might result in downtime, take the following precautions:

  - Keep your servers up-to-date with security updates. Subscribing to the Microsoft Security Notification Service helps ensure that you receive immediate notification of security bulletin releases for any Microsoft product. To subscribe, go to the Microsoft Technical Security Notifications website at [http://go.microsoft.com/fwlink/p/?LinkId=145202](http://go.microsoft.com/fwlink/p/?linkid=145202).

  - Ensure that access rights are set up correctly.

  - Keep your servers in a physical environment that prevents unauthorized access. Ensure that adequate antivirus software is installed on all your servers. Keep the software up-to-date with the latest virus signature files. Use the automatic update feature of your antivirus application to keep the virus signatures current.

  - We recommend that you disable the Windows Server operating system services that are not required on the computers where you install Lync Server 2013.

  - Encrypt operating systems and disk drives where data is stored with a full-volume encryption system, unless you can guarantee constant and complete control of the servers, total physical isolation, and proper and secure decommissioning of replaced or failed disk drives.

  - Disable all external Direct Memory Access (DMA) ports of the server, unless you can guarantee very tight control over the physical access to the servers. DMA-based attacks, which can be initiated fairly easily, could expose very sensitive information, such as private encryption keys.

</div>

<span> </span>

</div>

</div>

</div>

