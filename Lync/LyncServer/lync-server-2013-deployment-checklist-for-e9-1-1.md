---
title: 'Lync Server 2013: Deployment checklist for E9-1-1'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deployment checklist for E9-1-1
ms:assetid: cc6a656a-6043-4b9b-85c2-5708b9bb1c06
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398864(v=OCS.15)
ms:contentKeyID: 48185655
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment checklist for E9-1-1 in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-03_

To plan effectively for Enhanced 9-1-1 (E9-1-1), be sure to include the following deployment requirements:

  - Prerequisites for deploying E9-1-1.

  - Steps that are required to deploy E9-1-1.

<div>

## Deployment Prerequisites for E9-1-1

Before you deploy E9-1-1, you must already have deployed your Lync Server internal servers, including a Central Management store, a Front End pool or a Standard Edition server, one or more Mediation Servers or Mediation Server pools, and Lync Server clients. In addition, an E9-1-1 deployment requires a SIP trunk to a qualified E9-1-1 service provider or an Emergency Location Identification Number (ELIN) gateway to your public switched telephone network (PSTN). Lync Server supports using E9-1-1 service providers only inside the United States.

</div>

<div>

## Deployment Process

The following table provides an overview of the E9-1-1 deployment process. For details about deployment steps, see [Configure Enhanced 9-1-1 in Lync Server 2013](lync-server-2013-configure-enhanced-9-1-1.md) in the Deployment documentation.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Phase</th>
<th>Steps</th>
<th>Roles</th>
<th>Deployment documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configure voice usages, routes, and trunk configurations</p></td>
<td><ol>
<li><p>Create a new PSTN usage record. This is the same name that is used for the <strong>PSTN Usage</strong> setting in the location policy.</p></li>
<li><p>Create or assign a voice route to the PSTN usage record created in the previous step and then point the gateway attribute to the E9-1-1 SIP trunk or ELIN gateway.</p></li>
<li><p>For a SIP trunk E9-1-1 service provider, set the trunk that will be handling E9-1-1 calls over the SIP to pass PIDF-LO data by using the <strong>Set-CsTrunkConfiguration –EnablePIDFLOSupport</strong> cmdlet.</p></li>
<li><p>Optionally, for a SIP trunk E9-1-1 service provider, create or assign a local PSTN route for calls that are not handled by the E9-1-1 service provider’s SIP trunk. This route will be used if the connection to the E9-1-1 service provider is not available. If supported by your E9-1-1 service provider, assign a trunk configuration rule to the gateway that translates the 911 dial string into the direct inward dialing (DID) number of the national/regional Emergency Call Response Center (ECRC).</p></li>
</ol></td>
<td><p>CSVoiceAdmin</p></td>
<td><p><a href="lync-server-2013-configure-an-e9-1-1-voice-route.md">Configure an E9-1-1 voice route in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Create location policies and assign them to users and subnets</p></td>
<td><ol>
<li><p>Review the global location policy.</p></li>
<li><p>Create a location policy with a user-level scope; or, if the organization has more than one site with different emergency usages, create a location policy with a network-level scope.</p></li>
<li><p>Assign the location policy to network sites.</p></li>
<li><p>Add the appropriate subnets to the network site.</p></li>
<li><p>(Optional) Assign the location policy to user policies.</p></li>
</ol></td>
<td><p>CSVoiceAdmin</p>
<p>CSLocationAdmin (except for creating Location Policies)</p></td>
<td><p><a href="lync-server-2013-create-location-policies.md">Create location policies in Lync Server 2013</a></p>
<p><a href="lync-server-2013-add-a-location-policy-to-a-network-site.md">Add a location policy to a network site in Lync Server 2013</a></p>
<p><a href="lync-server-2013-associate-subnets-with-network-sites-for-e9-1-1.md">Associate subnets with network sites for E9-1-1 in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Configure the location database</p></td>
<td><ol>
<li><p>Populate the database with a mapping of network elements to locations.</p></li>
<li><p>For ELIN gateways, add the ELINs to the &lt;CompanyName&gt; column.</p></li>
<li><p>Configure the connection to the E9-1-1 service provider for validating addresses.</p></li>
<li><p>Validate the addresses with the E9-1-1 service provider.</p></li>
<li><p>Publish the updated database.</p></li>
<li><p>For ELIN gateways, upload the ELINs to your PSTN carrier's Automatic Location Identification (ALI) database.</p></li>
</ol></td>
<td><p>CSVoiceAdmin</p>
<p>CSLocationAdmin</p></td>
<td><p><a href="lync-server-2013-configure-the-location-database.md">Configure the location database in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure Advanced Features (optional)</p></td>
<td><ol>
<li><p>Configure the URL for the SNMP application.</p></li>
<li><p>Configure the URL for the location of the Secondary Location Information service.</p></li>
</ol></td>
<td><p>CSVoiceAdmin</p></td>
<td><p><a href="lync-server-2013-configure-an-snmp-application.md">Configure an SNMP application in Lync Server 2013</a></p>
<p><a href="lync-server-2013-configure-a-secondary-location-information-service.md">Configure a secondary Location Information service in Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

