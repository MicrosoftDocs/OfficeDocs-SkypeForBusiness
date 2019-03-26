---
title: 'Lync Server 2013: How Persistent Chat Server works'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: How Persistent Chat Server works
ms:assetid: 3d04e9a1-3f0c-458e-bcbe-d27c8c464276
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ683096(v=OCS.15)
ms:contentKeyID: 49684643
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# How Persistent Chat Server works in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-21_

Lync Server 2013, Persistent Chat Server enables you to participate in multiparty, topic-based conversations that persist over time. Persistent Chat Server can help your organization do the following:

  - Improve communication between geographically dispersed and cross-functional teams

  - Broaden information awareness and participation

  - Improve communication with your extended organization

  - Reduce information overload

  - Improve information awareness

  - Increase dispersion of important knowledge and information

You can deploy Persistent Chat Server as an optional role with Lync Server 2013. Persistent Chat services run on a dedicated pool, and a Persistent Chat Server pool depends on a Lync Server pool to route messages to it. Clients use eXtensible Chat Communication Over SIP (XCCOS). The Lync Server Front End Servers are configured to route the traffic to a Persistent Chat Server pool.

<div>

## High-Level Architecture

The following diagrams provide high-level perspectives of the Persistent Chat Server architecture and services.

**Persistent Chat Server High-Level Architecture**

![Persistent Chat Server architecture.](images/JJ683096.5db6f36f-4461-4d87-ba77-463b7ffe609b(OCS.15).jpg "Persistent Chat Server architecture.")

**Persistent Chat Server High-Level Services**

![Persistent Chat Server components.](images/JJ683096.b6d743aa-3a86-4081-aaef-4fe3257db4e7(OCS.15).jpg "Persistent Chat Server components.")

Two services run on the Persistent Chat Server Front End Servers:

  - Persistent Chat (Channel)

  - Compliance

<div>

## Persistent Chat (Channel) Service

The Persistent Chat (Channel) service is the core service responsible for Persistent Chat Server. This service provides the following functions:

  - Accepts incoming messages

  - Registers and lists online participants within a Persistent Chat room

  - Retransmits messages to other channel subscribers

  - Implements logic for channel management, chat room invitation, search, and new content notifications

The Persistent Chat (Channel) service stores and accesses chat room content and other system metadata (authorization rules, and so on) by using the Persistent Chat Store. This service stores files that are uploaded into chat rooms in the Persistent Chat File Store.

</div>

<div>

## Compliance Service

The Compliance service is an optional component of Persistent Chat Server and is responsible for archiving chat content and events to the Persistent Chat Compliance Store. If your organization has regulations that require Persistent Chat activity to be archived, you can deploy the optional Persistent Chat Compliance service. The Compliance service is installed on each Persistent Chat Server in a Persistent Chat pool. When configured, Persistent Chat Server compliance records user activity such as joining and leaving rooms, and posting and reading of messages. The Compliance service stores files that need to be archived in the Persistent Chat Compliance File Store.

</div>

<div>

## Persistent Chat Web Services

On the Lync Server Front End Servers, two services run that depend on Internet Information Services (IIS), and are implemented as web components:

  - **Persistent Chat Web Services for File Upload/Download** Responsible for posting and retrieving files from chat rooms.

  - **Persistent Chat Web Services for Chat Room Management** Responsible for providing users the ability to manage their chat rooms, and create new chat rooms.

</div>

</div>

<div>

## How Do I Start Using Persistent Chat Server?

Persistent Chat Server is an optional server role within the Lync Server 2013 infrastructure. If you install the Persistent Chat Server role, any users who have been enabled through policy by an administrator can use Persistent Chat with the Lync 2013 client.

For details about how to deploy Persistent Chat Server and enable users to leverage the capabilities by policy, see [Deploying Persistent Chat Server in Lync Server 2013](lync-server-2013-deploying-persistent-chat-server.md).

For details about how to configure settings on your Persistent Chat Server deployment, see [Deploying Persistent Chat Server in Lync Server 2013](lync-server-2013-deploying-persistent-chat-server.md) and [Managing Lync Server 2013, Persistent Chat Server](managing-lync-server-2013-persistent-chat-server.md).

For details about how to enable users by policy such that they can leverage Persistent Chat functionality in Lync 2013 client, see [Deploying Persistent Chat Server in Lync Server 2013](lync-server-2013-deploying-persistent-chat-server.md) and [Managing Lync Server 2013, Persistent Chat Server](managing-lync-server-2013-persistent-chat-server.md).

If you deployed Persistent Chat compliance, see [Managing Lync Server 2013, Persistent Chat Server](managing-lync-server-2013-persistent-chat-server.md) for details about how to configure settings for compliance.

</div>

<div>

## Persistent Chat Call Flows

The Persistent Chat client communicates with the Persistent Chat service by using XCCOS. The following sequences describe the sign-in process and a typical room subscription and message post scenario.

<div>

## Sign-in

The following call flow diagram and steps describe the sign-in process.

**Persistent Chat Client Sign-in Call Flow**

![Persistent Chat Server call flow diagram.](images/JJ683096.9b3b3c61-caca-42b6-853c-6a09e6ff5c44(OCS.15).jpg "Persistent Chat Server call flow diagram.")

1.  The Persistent Chat client first sends a SIP SUBSCRIBE to retrieve the in-band provisioning document from the server. This document indicates if Persistent Chat is enabled or disabled for the user and the list of SIP URIs for the Persistent Chat Server pool.

2.  The Persistent Chat client sends a SIP INVITE message to the SIP URI of the Persistent Chat Server that it obtained in the previous step. The INVITE sequence is followed by 200 OK and ACK, and the Persistent Chat client has now opened a SIP session with a Persistent Chat Server endpoint. Consequently, the Persistent Chat client communicates with Persistent Chat Server by sending SIP INFO messages that contain either chat messages or commands requesting the server to take an action. All of these messages are acknowledged with either 200 OK or 503 Service Unavailable (that is, in the event of heavy server load). If the client receives a 503 response, it will retry the message. (This example does not include a 503 response.) If the server accepts the message or command and sends 200 OK, it provides a response to the client in the form of a separate SIP INFO message. This response includes a reference to the originating command.

3.  The Persistent Chat client sends a SIP INFO message that contains the XCCOS **getserverinfo** command. Persistent Chat Server replies with a new SIP INFO message that contains information about the Persistent Chat service configuration.

4.  The Persistent Chat client sends a SIP INFO message that contains the XCCOS **getassociations** command. Persistent Chat Server replies with a new SIP INFO message that contains the list of rooms of which the user is a member. The Persistent Chat client repeats the command to retrieve the list of rooms of which the user is a manager.

5.  The Persistent Chat client gets the list of followed rooms from the "presence" document, where each followed room is represented by a "roomSetting" category. All followed rooms are joined by a single SIP INFO message that contains the XCCOS **bjoin** command that contains the list of room URIs. Because the list of followed rooms is kept on the server, any client on any computer has the same list of followed rooms for the specified user URI. The Persistent Chat client also keeps the list of opened rooms (if this option is enabled by the user) in the local computer registry, and joins each of these rooms at sign-in by sending a SIP INFO message that contains the XCCOS **join** command for each opened room. Because this list is kept in the registry, it can be different on two Persistent Chat clients running on different computers.

6.  For each room joined, the Persistent Chat client sends a SIP INFO message that contains the XCCOS **bccontext** command. Persistent Chat Server replies with a new SIP INFO message that contains the most recent chat message in the room.

7.  The Persistent Chat client sends a SIP INFO message that contains a XCCOS **getinv** (that is, get invitation) command to request any new room invitations that the client has not yet seen. In a separate SIP INFO message, Persistent Chat Server returns a list of those rooms.

</div>

<div>

## Subscribe to a Room and Post a Message

The following call flow diagram and steps describe a typical room subscription and message post scenario.

**Persistent Chat Client Room Subscription and Message Posting Call Flow**

![Room subscription and message post scenario.](images/JJ683096.2d3c417e-c91b-42bd-964e-285b72bb2e44(OCS.15).jpg "Room subscription and message post scenario.")

1.  From the Persistent Chat client, User1 clicks **Join a Chat Room**, clicks **Search**, and then enters some search criteria. The Persistent Chat client sends a SIP INFO message that contains the XCCOS **chansrch** (room search) command, along with the search criteria. Persistent Chat Server queries the back-end database and replies in a new SIP INFO message that contains a list of available rooms that meet the search criteria.

2.  User1 selects the chat room that he or she wants to join, and then clicks **Follow this room**. The Persistent Chat client sends Persistent Chat Server a SIP INFO message that contains the XCCOS **join** command and the room ID of the chat room that the user selected. Persistent Chat Server replies with a SIP INFO message that contains the provisioning data.

3.  The Persistent Chat client sends Persistent Chat Server a SIP INFO message that contains the XCCOS **bccontext** (backchat context) command. Persistent Chat Server retrieves the chat history, and returns it to the Persistent Chat client in a separate SIP INFO message. At this point, the user enters the chat room and is ready to participate.

4.  User1 enters a new message, and then clicks **Send**. The Persistent Chat client posts the message to the chat room in a SIP INFO XCCOS **grpchat** command. Persistent Chat Server stores a copy of this new message in the Persistent Chat back-end database.

5.  Persistent Chat Server sends a separate copy of the SIP INFO XCCOS **grpchat** message to User2, who has already entered the chat room.

</div>

</div>

<div>

## Persistent Chat Compliance Call Flows

Persistent Chat Server uses Message Queuing (also known as MSMQ) and an additional compliance database (mgccomp) to process compliance data. As an example of how compliance events are processed, the following sequence of events describes how a message post event is processed.

1.  A user posts a message to a room.

2.  Persistent Chat Server places information pertaining to the event in a private Message Queuing queue.

3.  Persistent Chat Compliance server reads this event from the queue, and places it into the mgccomp database for processing later.

4.  Periodically, the Persistent Chat Compliance server processes a set of events in the database, and sends them to the Persistent Chat Compliance adapter for processing.

5.  If the adapter successfully processes the data, Persistent Chat Compliance server deletes the events from the mgccomp database.

</div>

</div>

<span> </span>

</div>

</div>

</div>

