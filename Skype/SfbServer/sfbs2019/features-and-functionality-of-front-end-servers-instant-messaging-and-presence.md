---
title: "Features and functionality of Front End Servers, instant messaging, and presence in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 05b29536-dcd7-49b5-934a-2ebf20ddc45c
description: "Front End Servers provide most Lync Server functionality. There are two editions available: Lync Server Enterprise Edition, which is designed primarily for larger organizations, and Lync Server Standard Edition, which is designed primarily for smaller organizations which want a smaller hardware investement and do not require high availability. Both editions support all Lync Server workloads including IM, presence, conferencing, and Enterprise Voice."
---

# Features and functionality of Front End Servers, instant messaging, and presence in Lync Server 2013
[]
Front End Servers provide most Lync Server functionality. There are two editions available: Lync Server Enterprise Edition, which is designed primarily for larger organizations, and Lync Server Standard Edition, which is designed primarily for smaller organizations which want a smaller hardware investement and do not require high availability. Both editions support all Lync Server workloads including IM, presence, conferencing, and Enterprise Voice.
  
Instant messaging (IM) enables your users to communicate with each other in real time on their computers using text-based messages. Both two-party and multiparty IM sessions are supported. A participant in a two-party IM conversation can add a third participant to the conversation at any time. When this happens, the Conversation window changes to support conferencing features.
  
> [!IMPORTANT]
> Lync and Communicator clients when involved in a one to one communication, is often referred to as peer-to-peer. Technically, the two clients are communicating in a one to one conversation, with the Instant Messaging multipoint control unit (IMMCU) in the middle. The IMMCU is a component of Front End Server. Placing the IMMCU in the required communication workflow allows call detail recording and other features that the Front End Server enables. Communication is from a dynamic source port on the client to the Front End Server port TLS/TCP/5061 (assuming the use of the recommended transport layer security). By design, peer-to-peer communication (as well as multi-party IM) is possible only when Lync Server and the IMMCU is active and available. 
  
Presence provides information to users about the status of other on the network. A user's presence status provides information to help others decide whether they should try to contact the user and whether to use instant messaging, phone, or email. Presence encourages instant communication when possible, but it also provides information about whether a user is in a meeting or out of the office, indicating that instant communication is not possible. This presence status is displayed as a presence icon in Lync and other presence-aware applications, including the Microsoft Outlook messaging and collaboration client, Microsoft SharePoint technologies, Microsoft Word, and Microsoft Excel spreadsheet software. The presence icon represents the user's current availability and willingness to communicate. 
  

