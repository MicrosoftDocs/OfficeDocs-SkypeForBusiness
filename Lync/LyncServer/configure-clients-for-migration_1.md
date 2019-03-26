---
title: Configure clients for migration
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure clients for migration
ms:assetid: 8f17862b-d9d1-47f6-b248-51f4710f5030
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688130(v=OCS.15)
ms:contentKeyID: 49733729
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure clients for migration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-21_

This topic contains the recommended client deployment steps you should take prior to migrating to Lync Server 2013. These configuration changes should be made on Office Communications Server 2007 R2. It is very important that you perform these steps prior to migrating. For details, see [Planning for clients and devices in Lync Server 2013](lync-server-2013-planning-for-clients-and-devices.md).

<div>

## To configure clients prior to migration

1.  Deploy the most recent Office Communications Server 2007 R2 server, client, and device updates (hotfixes):
    
      - [Apply Office Communications Server 2007 R2 updates](apply-office-communications-server-2007-r2-updates.md)
    
      - [Description of the cumulative update package for Communicator 2007 R2](http://go.microsoft.com/fwlink/p/?linkid=335808)
    
      - [Obtaining Software Updates for Devices](http://go.microsoft.com/fwlink/?linkid=335809)

2.  On Office Communications Server 2007 R2, use Client Version Filtering to allow only Office Communications Server 2007 R2 clients with the most current updates installed to sign in.

3.  On Office Communications Server 2007 R2, use Client Version Filtering to block Lync Server 2013 clients from signing in. Follow the steps described in **Configuring Client Version Filtering** at [http://go.microsoft.com/fwlink/p/?linkId=202488](http://go.microsoft.com/fwlink/p/?linkid=202488) to add the version filters listed in the following table. For each version filter, assign the action **Block**.
    
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Client</th>
    <th>User agent header</th>
    <th>Version</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Lync 2013</p></td>
    <td><p>OC</p></td>
    <td><p>15.*.*.*</p></td>
    </tr>
    <tr class="even">
    <td><p>Lync Web App</p></td>
    <td><p>CWA</p></td>
    <td><p>5.*.*.*</p></td>
    </tr>
    <tr class="odd">
    <td><p>Lync Phone Edition</p></td>
    <td><p>OCPhone</p></td>
    <td><p>4.*.*.*</p></td>
    </tr>
    </tbody>
    </table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

