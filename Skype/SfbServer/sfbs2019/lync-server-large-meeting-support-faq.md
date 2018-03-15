---
title: "Large meeting support FAQ for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 34b4fb6a-e35c-47e8-8ab1-f8331741fed2
description: "In this articleQ: How many users can participate in a large meeting?Q: How many meetings or other workloads can I have in a pool that is dedicated to large meetings?Q: Should the organizers of large meeting be homed on the dedicated pool?Q: What media modalities can I use in a large meeting?Q: Can I use group instant messaging (IM) in large meetings?Can users join large meetings by dialing in from a phone?Q: Can I host large meetings in a virtual topology?"
---

# Large meeting support FAQ for Lync Server 2013
[]
 **In this article**
  
[Q: How many users can participate in a large meeting?](#sectionSection0)
  
[Q: How many meetings or other workloads can I have in a pool that is dedicated to large meetings?](#sectionSection1)
  
[Q: Should the organizers of large meeting be homed on the dedicated pool?](#sectionSection2)
  
[Q: What media modalities can I use in a large meeting?](#sectionSection3)
  
[Q: Can I use group instant messaging (IM) in large meetings?](#sectionSection4)
  
[Can users join large meetings by dialing in from a phone?](#sectionSection5)
  
[Q: Can I host large meetings in a virtual topology?](#sectionSection6)
  
The following sections provide answers to common questions for creating and running large meetings.
  
## Q: How many users can participate in a large meeting?
<a name="sectionSection0"> </a>

The Lync Server user model specifies limits of 250 users in a shared pool or 1000 users in a pool dedicated to large meetings, but these numbers only represent the number of users we tested and only for the specific set of hardware that we used in our testing. Based on our testing, we recommend those limits for maximum sizes. However, you control the actual number of participants allowed in meetings in your organization by configuring one or more conferencing policies (which you configure using Windows PowerShell cmdlets in the Lync Server Management Shell or using the Lync Server Control Panel). The number that you specify in a conferencing policy can be any 32-bit whole number between 1 and 4,294,967,295, but the recommended size is between 2 and 250 participants, inclusive; and the default value is 250.
  
## Q: How many meetings or other workloads can I have in a pool that is dedicated to large meetings?
<a name="sectionSection1"> </a>

To ensure the best user experience in large meetings of up to 1000 participants, we recommend hosting only a single large meeting at a time on a pool that is dedicated to large meetings. We also recommend not allowing any other workloads to run on that pool when the large meeting is in progress.
  
## Q: Should the organizers of large meeting be homed on the dedicated pool?
<a name="sectionSection2"> </a>

No. We recommend not homing any users other than the dedicated staff that manages scheduling of large meetings on the dedicated pool. This prevents other real-time communications traffic from causing problems with large meetings that are hosted in the pool. You should schedule large meetings on the dedicated pool using a user account of the large meeting scheduling staff. You should add the user account of the meeting organizer (the user who requests a large meeting) as a presenter for the large meeting.
  
## Q: What media modalities can I use in a large meeting?
<a name="sectionSection3"> </a>

Large meetings with up to 1000 users can include audio, video, PowerPoint sharing, whiteboards, and presence polling.
  
## Q: Can I use group instant messaging (IM) in large meetings?
<a name="sectionSection4"> </a>

Yes. However, large numbers of instant messages, especially when sent by a large number of meeting participants, can affect the user experience due to problems with fast text scrolling in the IM window. Delivering a large amount of instant messages to up to 1000 users can also introduce significant server loads, which can affect performance. Generally, IM is only required for questions and answers (Q&amp;As). 
  
## Can users join large meetings by dialing in from a phone?
<a name="sectionSection5"> </a>

Yes. If the Lync Server 2013 pool is properly deployed and enabled for dial-in conferencing, users will be able to join the large meetings by dialing in. Our testing has shown that up to 15% of the 1000 users can join the large meeting over a 10 minute period. 
  
## Q: Can I host large meetings in a virtual topology?
<a name="sectionSection6"> </a>

We have not tested large meetings in a virtual topology, so we do not support the use of virtual machines to host a dedicated pool for large meetings.
  

