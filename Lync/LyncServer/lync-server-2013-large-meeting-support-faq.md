---
title: 'Lync Server 2013: Large meeting support FAQ'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Lync Server large meeting support FAQ
ms:assetid: 34b4fb6a-e35c-47e8-8ab1-f8331741fed2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204804(v=OCS.15)
ms:contentKeyID: 48183837
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Large meeting support FAQ for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

The following sections provide answers to common questions for creating and running large meetings.

<div>

## Q: How many users can participate in a large meeting?

The Lync Server user model specifies limits of 250 users in a shared pool or 1000 users in a pool dedicated to large meetings, but these numbers only represent the number of users we tested and only for the specific set of hardware that we used in our testing. Based on our testing, we recommend those limits for maximum sizes. However, you control the actual number of participants allowed in meetings in your organization by configuring one or more conferencing policies (which you configure using Windows PowerShell cmdlets in the Lync Server Management Shell or using the Lync Server Control Panel). The number that you specify in a conferencing policy can be any 32-bit whole number between 1 and 4,294,967,295, but the recommended size is between 2 and 250 participants, inclusive; and the default value is 250.

</div>

<div>

## Q: How many meetings or other workloads can I have in a pool that is dedicated to large meetings?

To ensure the best user experience in large meetings of up to 1000 participants, we recommend hosting only a single large meeting at a time on a pool that is dedicated to large meetings. We also recommend not allowing any other workloads to run on that pool when the large meeting is in progress.

</div>

<div>

## Q: Should the organizers of large meeting be homed on the dedicated pool?

No. We recommend not homing any users other than the dedicated staff that manages scheduling of large meetings on the dedicated pool. This prevents other real-time communications traffic from causing problems with large meetings that are hosted in the pool. You should schedule large meetings on the dedicated pool using a user account of the large meeting scheduling staff. You should add the user account of the meeting organizer (the user who requests a large meeting) as a presenter for the large meeting.

</div>

<div>

## Q: What media modalities can I use in a large meeting?

Large meetings with up to 1000 users can include audio, video, PowerPoint sharing, whiteboards, and presence polling.

</div>

<div>

## Q: Can I use group instant messaging (IM) in large meetings?

Yes. However, large numbers of instant messages, especially when sent by a large number of meeting participants, can affect the user experience due to problems with fast text scrolling in the IM window. Delivering a large amount of instant messages to up to 1000 users can also introduce significant server loads, which can affect performance. Generally, IM is only required for questions and answers (Q\&As).

</div>

<div>

## Can users join large meetings by dialing in from a phone?

Yes. If the Lync Server 2013 pool is properly deployed and enabled for dial-in conferencing, users will be able to join the large meetings by dialing in. Our testing has shown that up to 15% of the 1000 users can join the large meeting over a 10 minute period.

</div>

<div>

## Q: Can I host large meetings in a virtual topology?

We have not tested large meetings in a virtual topology, so we do not support the use of virtual machines to host a dedicated pool for large meetings.

</div>

</div>

<span> </span>

</div>

</div>

</div>

