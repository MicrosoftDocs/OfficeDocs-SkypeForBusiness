---
title: 'Lync Server 2013: Managing locations for SIP trunk service providers'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Managing locations for SIP trunk service providers
ms:assetid: d9b33b56-66c2-4dee-b056-faaf98925bf2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398959(v=OCS.15)
ms:contentKeyID: 48185548
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing locations for SIP trunk service providers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-02_

To configure Lync Server to automatically locate clients within a network, you need to either populate the Location Information service database with a network wiremap and publish the locations, or link to an external database that already contains the correct mappings. As part of this process, you need to validate the civic addresses of the locations with your E9-1-1 service provider. For details, see [Configure the location database in Lync Server 2013](lync-server-2013-configure-the-location-database.md) in the Deployment documentation.

You populate the Location Information service database with an Emergency Response Location (ERL), which consists of a civic address and the specific address within a building. The Location Information service **Location** field, which is the specific location within a building, has a maximum length of 20 characters (including spaces). Within that limited length, try to include the following:

  - An easy-to-understand name that identifies the location of the 911 caller to help ensure that emergency responders find the specific location promptly when they arrive at the civic address. This location name may include a building number, floor number, wing designator, room number, and so on. Avoid nicknames known only to employees, which might cause emergency responders to go to the wrong location.

  - A location identifier that helps users to easily see that their Lync client picked up the correct location. The Lync client automatically concatenates and displays the discovered **Location** and **City** fields in its header. A good practice is to add the street address of the building to each location identifier (for example, "1st Floor \<street number\>"). Without the street address, a generic location identifier such as "1st Floor" could apply to any building in the city.

  - If the location is approximate because it’s determined by a wireless access point, you can add the word Near (for example, "Near 1st Floor 1234").

<div>


> [!NOTE]  
> Locations added to the central location database are not available to the client until they are published by using a Lync Server Management Shell command and are replicated to the pool's local stores. For details, see <A href="lync-server-2013-publish-the-location-database.md">Publish the location database from Lync Server 2013</A> in the Deployment documentation.



</div>

The following sections discuss considerations that you need to take into account when populating and maintaining the location database.

<div>

## Populating the Location Database

The following questions can help you determine how to populate the location database.

  - **What process will you use to populate the location database?**  
    Where does the data exist, and what steps do you need to take to convert the data into the format required by the location database? Will you add locations individually, or in bulk, by using a CSV file?

<!-- end list -->

  - **Do you have a third party database that already contains a mapping of locations?**  
    By using Lync Server's Secondary Location Information service option to connect to a third-party database, you can group and manage locations by using an offline platform. A benefit to this approach is that in addition to associating locations to network identifiers, you can associate locations to a user. This means that the Location Information service can return multiple addresses, originating from the Secondary Location Information service, to a Lync Server client. The user can then choose the most appropriate location.
    
    To integrate with the Location Information service, the third-party database must follow the Lync Server Location Request/Response schema. For details, see "\[MS-E911WS\]: Web Service for E911 Support Protocol Specification" at <http://go.microsoft.com/fwlink/p/?linkid=213819>. For details about deploying a Secondary Location Information service, see [Configure a secondary Location Information service in Lync Server 2013](lync-server-2013-configure-a-secondary-location-information-service.md) in the Deployment documentation.

For details about populating the location database, see [Configure the location database in Lync Server 2013](lync-server-2013-configure-the-location-database.md) in the Deployment documentation.

</div>

<div>

## Maintaining the Location Database

After you populate the location database, you need to develop a strategy for updating the database as the network configuration changes. The following questions will help you determine how to maintain the location database.

  - **How will you update the location database?**  
    There are several scenarios that require an update to the location database, including adding WAPs, office recabling (resulting in different switch assignments), and subnet expansion. Will you directly update each individual location, or will you perform a bulk update of all the locations by using a CSV file?

<!-- end list -->

  - **Will you use an SNMP application to match Lync client MAC addresses to port and switch identifiers?**  
    If you use an SNMP application, you need to develop a manual process for keeping the switch chassis and port information consistent between the SNMP application and the location database. If the SNMP application returns a chassis IP address or port ID that is not included in the database, the Location Information service will not be able to return a location to the client.

</div>

</div>

<span> </span>

</div>

</div>

</div>

