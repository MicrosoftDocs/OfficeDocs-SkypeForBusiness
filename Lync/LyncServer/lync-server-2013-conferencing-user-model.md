---
title: Lync Server 2013 conferencing user model
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: The conferencing user model
ms:assetid: ba4bbba9-f2e3-4cab-8eba-b51f12133cab
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205199(v=OCS.15)
ms:contentKeyID: 48185229
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# The conferencing user model in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

A critical part of the Lync Server conferencing user model is meeting size. After collecting data from the multiple data points (as described in the previous section), we determined the following:

  - Most meetings are actually small collaborative meetings with an average of four to six participants

  - Approximately 80 percent of meetings have fewer than 20 participants.

  - 99.98 percent of meetings have fewer than 100 participants.

In addition to meeting size, the conferencing user model also takes into account a variety of factors, such as:

  - **Concurrent meetings**   How many users are expected to be in meetings at the same time?

  - **Media mix**   What types of media are available and expected to be used by users in meetings?

  - **User types**   Are users internal users, remote users, federated users, or anonymous users?

  - **Meeting ramp up time**   How long does it take for all users of a meeting to join a meeting?

For details about the user model, see [User models in Lync Server 2013](lync-server-2013-user-models.md).

To determine the number of meetings and users to use for testing, we did the following:

  - Took the total number of users in an organization (for example, 80,000 users) and multiplied it by the meeting concurrency rate (for example, 5% of all users) to determine the total number of users expected to be in meetings at the same time (in this example, 4000 users).

  - Divided the total number of users by the number of Lync Server 2013, Front End Servers in the deployment (for example, 8 servers) to determine the estimated number of meeting participants per Front End Server (in this example, 500 users per Front End Server).

  - Divided the number of users per Front End Server by the average meeting size (for example, 4 users) to determine the estimated average number of meetings per Front End Server (in this example, 125 meetings per Front End Server).

  - To get the per media load on each Front End Server, we estimated the media mix. For example, assuming that 75% of the meetings require more than just audio support and 50% of those meetings require application sharing, an average of 47 meetings and 188 users connect concurrently to each Front End Server for application sharing.

  - Tested a variety of meeting sizes (based our user model of up to 250 users in a shared pool) to ensure server scalability.

</div>

<span> </span>

</div>

</div>

</div>

