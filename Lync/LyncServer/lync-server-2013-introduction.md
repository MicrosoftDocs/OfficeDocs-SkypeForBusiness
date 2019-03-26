---
title: Lync Server 2013 introduction
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Introduction to Lync Server
ms:assetid: 99dd6b65-e591-421f-852b-ee9fe9588998
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398795(v=OCS.15)
ms:contentKeyID: 48184885
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Introduction to Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-07_

Lync Server 2013 and its client software, such as Lync 2013, enable your users to connect in new ways and to stay connected, regardless of their physical location. Lync and Lync Server bring together the different ways that people communicate in a single client interface, are deployed as a unified platform, and are administered through a single management infrastructure.

This table and the following sections illustrate the major feature sets, or *workloads*, that Lync Server provides for your users.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Workload</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IM and presence</p></td>
<td><p>Instant messaging (IM) and presence help your users find and communicate with one another efficiently and effectively.</p>
<p>IM provides an instant messaging platform with conversation history, and supports public IM connectivity with users of public IM networks such as MSN/Windows Live, Yahoo!, AOL, and Google Talk.</p>
<div>

> [!IMPORTANT]  
> <UL>
> <LI>
> <P>As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License (“PIC USL”) is no longer available for purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shut down date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Support for public instant messenger connectivity in Lync Server 2013</A>.</P>
> <LI>
> <P>The PIC USL is a per-user per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft’s ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which is winding down.</P>
> <LI>
> <P>More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice.</P></LI></UL>


</div>
<p>Presence establishes and displays a user’s personal availability and willingness to communicate through the use of common states such as <strong>Available</strong> or <strong>Busy</strong>, as well as more detailed states such as <strong>Be Right Back</strong> and <strong>Do Not Disturb</strong>. This rich presence information enables other users to immediately make effective communication choices.</p></td>
</tr>
<tr class="even">
<td><p>Conferencing</p></td>
<td><p>Lync Server includes support for IM conferencing, audio conferencing, web conferencing, video conferencing, and application sharing, for both scheduled and impromptu meetings. All these meeting types are supported with a single client. Lync Server also supports dial-in conferencing so that users of public switched telephone network (PSTN) phones can participate in the audio portion of conferences.</p>
<p>Conferences can seamlessly change and grow in real time. For example, a single conference can start as just instant messages between a few users, and escalate to an audio conference with desktop sharing and a larger audience instantly, easily, and without interrupting the conversation flow.</p></td>
</tr>
<tr class="odd">
<td><p>Enterprise Voice</p></td>
<td><p><em>Enterprise Voice</em> is the Voice over Internet Protocol (VoIP) offering in Lync Server. It delivers a voice option to enhance or replace traditional private branch exchange (PBX) systems. In addition to the complete telephony capabilities of an IP PBX, Enterprise Voice is integrated with rich presence, IM, collaboration, and meetings. Features such as call answer, hold, resume, transfer, forward and divert are supported directly, while personalized speed dialing keys are replaced by Contacts lists, and automatic intercom is replaced with IM.</p>
<p>Enterprise Voice supports high availability through call admission control (CAC), branch office survivability, and extended options for data resiliency.</p></td>
</tr>
<tr class="even">
<td><p>Support for remote users</p></td>
<td><p>You can provide full Lync Server functionality for users who are currently outside your organization’s firewalls by deploying servers called <em>Edge Servers</em> to provide a connection for these remote users. These remote users can connect to conferences by using a personal computer with Lync 2013 installed, the phone, or a web interface.</p>
<p>Deploying Edge Servers also enables you to <em>federate</em> with partner or vendor organizations. A federated relationship enables your users to put federated users on their Contacts lists, exchange presence information and instant messages with these users, and invite them to audio calls, video calls, and conferences.</p></td>
</tr>
<tr class="odd">
<td><p>Mobile client support</p></td>
<td><p>Additionally, with Lync Server mobility services, your users can access Lync functionality when using supported Apple iOS, Android, Windows Phone, or Nokia mobile devices and perform such activities as sending and receiving instant messages, viewing contacts, and viewing presence. In addition, mobile devices support some Enterprise Voice features, such as click to join a conference, Call via Work, single number reach, voice mail, and missed calls. Push notifications are also supported for mobile devices that do not support applications running in the background.</p></td>
</tr>
<tr class="even">
<td><p>Integration with other products</p></td>
<td><p>Lync Server integrates with several other products to provide additional benefits to your users and administrators.</p>
<p>Meeting tools are integrated into Outlook to enable organizers to schedule a meeting or start an impromptu conference with a single click and make it just as easy for attendees to join.</p>
<p>Presence information is integrated into Outlook and SharePoint.</p>
<p>Exchange Unified Messaging (UM) provides several integration features. Users can see if they have new voice mail within Lync Server. They can click a play button in the Outlook message to hear the audio voice mail, or view a transcription of the voice mail in the notification message.</p>
<p>Additionally, running Lync Server 2013 with Exchange 2013 enables several new features such as a unified contact store which can be accessed by clients of both products, as well as high-resolution photos for contacts which are stored in the Exchange 2013 database.</p></td>
</tr>
<tr class="odd">
<td><p>Simple deployment</p></td>
<td><p>To help you plan and deploy your servers and clients, Lync Server provides the Topology Builder.</p>
<p>Topology Builder is an installation component of Lync Server. You use Topology Builder to create, adjust and publish your planned topology. It also validates your topology before you begin server installations. When you install Lync Server on individual servers, the installation program deploys the server as directed in the topology.</p></td>
</tr>
<tr class="even">
<td><p>Simple management</p></td>
<td><p>After you deploy Lync Server, it offers the following powerful and streamlined management tools:</p>
<ul>
<li><p>Central configuration management, which enables you to manage changes centrally and have them replicated quickly to the entire deployment.</p></li>
<li><p>Lync Server Control Panel, a web-based graphical user interface for administrators. With this web-based UI, Lync Server administrators can manage their systems from anywhere on the corporate network, without needing specialized management software installed on their computers.</p></li>
<li><p>Lync Server Management Shell command-line management tool, which is based on the Windows PowerShell command-line interface. It provides a rich command set for administration of all aspects of the product, and enables Lync Server administrators to automate repetitive tasks using a familiar tool.</p></li>
</ul></td>
</tr>
</tbody>
</table>


While the IM and presence features are automatically installed in every Lync Server deployment, you can choose whether to deploy conferencing, Enterprise Voice, and remote user access, to tailor your deployment to your organization’s needs.

<div>

## In This Section

  - [IM and presence in Lync Server 2013](lync-server-2013-im-and-presence.md)

  - [Conferencing in Lync Server 2013](lync-server-2013-conferencing.md)

  - [Enterprise Voice in Lync Server 2013](lync-server-2013-enterprise-voice.md)

  - [Scalability with Lync Server 2013](lync-server-2013-scalability.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

