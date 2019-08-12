---
title: 'Lync Server 2013: Configure the location database'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure the location database
ms:assetid: 8544be31-6958-47ef-b926-fdc80d56191c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398679(v=OCS.15)
ms:contentKeyID: 48184704
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure the location database in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-17_

To enable clients to automatically detect their location within a network, you first need to configure the location database. If you do not configure a location database, and **Location Required** in the location policy is set to **Yes** or **Disclaimer**, the user will be prompted to manually enter a location.

To configure the location database, you will perform the following tasks:

1.  Populate the database with a mapping of network elements to locations. If you use an Emergency Location Identification Number (ELIN) gateway, you need to include the ELIN in the \<CompanyName\> field.

2.  Validate the addresses against the master street address guide (MSAG) that is maintained by the E9-1-1 service provider.

3.  Publish the updated database.

<div>


> [!NOTE]  
> Alternately, you can define a secondary location source database that can be used in placed of the location database. For details, see <A href="lync-server-2013-configure-a-secondary-location-information-service.md">Configure a secondary Location Information service in Lync Server 2013</A>.



</div>

<div>

## In This Section

  - [Populate the location database in Lync Server 2013](lync-server-2013-populate-the-location-database.md)

  - [Validate addresses in Lync Server 2013](lync-server-2013-validate-addresses.md)

  - [Publish the location database from Lync Server 2013](lync-server-2013-publish-the-location-database.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

