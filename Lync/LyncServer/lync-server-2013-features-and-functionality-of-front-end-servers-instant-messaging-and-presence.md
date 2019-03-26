---
title: 'Lync Server 2013: Features and functionality of Front End Servers, instant messaging, and presence'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Features and functionality of Front End Servers, instant messaging, and presence
ms:assetid: 05b29536-dcd7-49b5-934a-2ebf20ddc45c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398109(v=OCS.15)
ms:contentKeyID: 48183294
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Features and functionality of Front End Servers, instant messaging, and presence in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-17_

Front End Servers provide most Lync Server functionality. There are two editions available: Lync Server Enterprise Edition, which is designed primarily for larger organizations, and Lync Server Standard Edition, which is designed primarily for smaller organizations which want a smaller hardware investement and do not require high availability. Both editions support all Lync Server workloads including IM, presence, conferencing, and Enterprise Voice.

Instant messaging (IM) enables your users to communicate with each other in real time on their computers using text-based messages. Both two-party and multiparty IM sessions are supported. A participant in a two-party IM conversation can add a third participant to the conversation at any time. When this happens, the Conversation window changes to support conferencing features.

<div>


> [!IMPORTANT]
> Lync and Communicator clients when involved in a one to one communication, is often referred to as peer-to-peer. Technically, the two clients are communicating in a one to one conversation, with the Instant Messaging multipoint control unit (IMMCU) in the middle. The IMMCU is a component of Front End Server. Placing the IMMCU in the required communication workflow allows call detail recording and other features that the Front End Server enables. Communication is from a dynamic source port on the client to the Front End Server port TLS/TCP/5061 (assuming the use of the recommended transport layer security). By design, peer-to-peer communication (as well as multi-party IM) is possible only when Lync Server and the IMMCU is active and available.



</div>

*Presence* provides information to users about the status of other on the network. A user’s presence status provides information to help others decide whether they should try to contact the user and whether to use instant messaging, phone, or email. Presence encourages instant communication when possible, but it also provides information about whether a user is in a meeting or out of the office, indicating that instant communication is not possible. This presence status is displayed as a presence icon in Lync and other presence-aware applications, including the Microsoft Outlook messaging and collaboration client, Microsoft SharePoint technologies, Microsoft Word, and Microsoft Excel spreadsheet software. The presence icon represents the user’s current availability and willingness to communicate.

</div>

<span> </span>

</div>

</div>

</div>

