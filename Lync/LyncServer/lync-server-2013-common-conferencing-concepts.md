---
title: 'Lync Server 2013: Common conferencing concepts'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Common conferencing concepts
ms:assetid: a21d4987-1c0a-44c8-8a39-9c17ffb57f3c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688158(v=OCS.15)
ms:contentKeyID: 49733762
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Common conferencing concepts in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-19_

Several concepts are common to all types of conferencing. These are described in the following sections.

<div>

## Policies and Bandwidth Management

Lync Server 2013 enables administrators to set policies for the types of meetings that users can organize. This helps you enforce your organization’s policies and control bandwidth usage. You can define a wide variety of meeting policies, and assign them to individual users and groups of users. You can also set policies that govern peer-to-peer conversations. For details about setting conferencing policies, see [Conferencing policies in Lync Server 2013](lync-server-2013-conferencing-policies.md) in the Operations documentation. For details about bandwidth management, see [Overview of call admission control in Lync Server 2013](lync-server-2013-overview-of-call-admission-control.md) and [Configuring video bandwidth in Lync Server 2013](lync-server-2013-configuring-video-bandwidth.md).

</div>

<div>

## Archiving and Compliance Features

Lync Server 2013 provides features you can use if your organization must follow compliance regulations. You can use the archiving abilities to archive content presented in meetings, and also the content of instant messaging (IM) conversations and IM conferences. For details, see [Planning for Archiving in Lync Server 2013](lync-server-2013-planning-for-archiving.md) in the Planning documentation. You can use compliance features of Persistent Chat Server to archive multiparty, topic-based conversations that persist over time. For details, see [Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) in the Planning documentation.

</div>

<div>

## Monitoring Feature

The Monitoring Server feature can capture call detail records (CDRs), which you can use to track which users talk to which other users using Lync Server 2013. For details about deploying and configuring monitoring, see [Deploying monitoring in Lync Server 2013](lync-server-2013-deploying-monitoring.md).

</div>

<div>

## Enabling External Participation in Conferences

You can greatly increase the benefits of your investment in Lync Server 2013 conferencing by enabling external users to also participate in conferences when invited. External users can include:

  - **Remote Users**   Your organization’s own users, when they are working outside your firewalls and are using their laptops or other Lync Server 2013 devices.

  - **Federated Users**   Users from companies you work with who also run Lync Server 2013. To enable your users to easily contact these users, you create federated relationships with these companies.

  - **Anonymous Users**   Any other external users who are invited specifically by your users to join specific conferences. A meeting organizer in your company can send an email invitation for a conference to an external user. The email includes a link that the outside user can click to join the conference.

To enable any or all of these scenarios, you need to deploy an Edge Server to help enable secure communications between your Lync Server 2013 deployment and external users. The Lync Server 2013 solution using Edge Servers provides higher quality media than other solutions such as a virtual private network (VPN). For details, see [Planning for external user access in Lync Server 2013](lync-server-2013-planning-for-external-user-access.md).

Additionally, whether or not you deploy Edge Servers, you can enable users (that is, either inside or outside your organization) to dial in from standard PSTN phones to join on-premises audio conferences. This is accomplished by deploying Lync Server 2013 dial-in conferencing.

</div>

<div>

## Compatibility Among Meeting Types and Client Versions

If you are going to have Lync Server 2013 interoperate with previous versions of Office Communications Server and its clients, you must be aware of the following issues:

  - Users using Lync Server 2013 cannot schedule Live Meeting conferences, or modify any migrated meetings of this type.

  - Users using Lync Server 2013 who need to attend Live Meeting conferences hosted on servers running Office Communications Server 2007 R2 must have the Live Meeting client installed on their computer (in addition to Lync Server 2013) to attend these meetings.

  - When Live Meeting conferences are migrated to Lync Server 2013, meeting content does not migrate. If this content is needed, it must be uploaded again.

</div>

</div>

<span> </span>

</div>

</div>

</div>

