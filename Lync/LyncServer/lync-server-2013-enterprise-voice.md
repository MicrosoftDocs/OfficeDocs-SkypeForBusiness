---
title: Lync Server 2013 Enterprise Voice
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enterprise Voice
ms:assetid: c9da8099-6f4f-4346-ac67-f041bb96072c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg417163(v=OCS.15)
ms:contentKeyID: 48185404
ms.date: 04/08/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enterprise Voice in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-04-08_

With Enterprise Voice, Lync Server delivers a stand-alone Voice over Internet Protocol (VoIP) offering to enhance or replace traditional private branch exchange (PBX) systems. Enterprise Voice users can call colleagues on your organization’s VoIP network or PBX, and they can call traditional phone numbers outside your organization. The Enterprise Voice solution includes common calling features such as answer, forward, transfer, hold, divert, release and park, and Enhanced 9-1-1 (E9-1-1) calling (E9-1-1 is available only in the United States.) Enterprise Voice also supports a broad range of current and older IP and USB devices.

<div>

## Placing and Receiving Calls

Using Lync, users can place calls by typing a name or phone number on their keyboard, or using a dial pad displayed on their screen. Users can also initiate calls directly from their Contacts list. You can also deploy Lync Phone Edition devices, which are stand-alone IP phone devices provided by Microsoft partners.

Users can have multiple phone devices registered with Lync Server, and can switch between them easily.

Users are alerted to incoming calls on all their devices simultaneously, with customizable ringtones on IP phone devices and a notification similar to an instant message on their PC.

Users can also set a single telephone number that connects to their desk phone, PC and mobile phone, so they can be reached no matter where they are.

</div>

<div>

## Basic Call Features

While on a call, a user can answer additional incoming calls or initiate outgoing calls, and the existing active call is automatically put on hold. Calls can be transferred from one user to another, either directly or after the first user speaks privately with the second user. Users can also transfer calls to another device; for example, they could transfer an active call to their mobile phone as they walk out the door of their office.

</div>

<div>

## Richer Communications

When talking to another user with Lync, users can easily add text, video, or desktop sharing to the call. The Do-Not-Disturb feature is integrated with the presence settings in Lync.

With Exchange Unified Messaging (UM), Lync and Lync Server integrate with Microsoft Exchange Server 2013 and Microsoft Outlook 2013. Users can see if they have new voice mail both in their Lync window and in email. While in email they can click to play the voice mail audio in an email message, or view a transcript of the voice mail message.

</div>

<div>

## Advanced Calling Features

Enterprise Voice includes several advanced calling features as well, such as Lync call delegation, team calling, Group Call Pickup, and Response Groups.

Lync call delegation enables users to delegate call handling to one or more assistants, by going to **Tools** \> **Options** \> **Call Forwarding Settings**. The delegate can perform multiple calling tasks on behalf of the user, including screening calls, placing calls, and initiating conferences.

<div>


> [!IMPORTANT]  
> You may be looking for another similarly named feature, Lync calendar delegation. It doesn't require the Enterprise Voice feature and does allow users to schedule online Lync meetings from Outlook. If you've come here looking for that info, we recommend checking out <A href="https://docs.microsoft.com/powershell/module/skype/Set-CsClientPolicy">Set-CsClientPolicy</A> for information on enabling Exchange delegate sync.



</div>

Team calling enables a user to have incoming calls simultaneously ring the phones of teammates so that anyone on the team can answer the call.

Group Call Pickup, a new feature in Cumulative Updates for Lync Server 2013: February 2013, lets users answer incoming calls to their colleagues from their own phones. Group Call Pickup differs from team calling primarily in that an incoming call rings only at the intended recipient's phone, but any other user can choose to answer it by dialing a call pickup group number.

Response Groups can be set up for queuing and intelligently routing calls to designated agents. Common uses include IT helpdesks, human resources hotlines, and other internal contact centers.

</div>

<div>

## Enterprise Voice Administration

Lync Server uses standards and published interfaces to interoperate with existing infrastructure. It supports both gateway and SIP options (such as SIP trunking) for interconnection to IP PBX systems and the PSTN networks, so that you can migrate users to Enterprise Voice over time, while minimizing disruption. Lync Server supports traditional codecs such as G.711, G.722, and G.723.1 for interoperability with traditional VoIP solutions.

With call admission control (CAC), administrators can set limits on the amount of Lync Server voice and video traffic carried on constrained network links, and specify the action to be taken if a new call would exceed the limit. The actions could include routing by an alternate path, or refusing the call.

Lync Server works with third-party Survivable Branch Appliances to provide local calling services and connection to PSTN at branch offices, in case of WAN failure at the central site.

</div>

</div>

<span> </span>

</div>

</div>

</div>

