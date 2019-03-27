---
title: 'Lync Server 2013: Mobility features and capabilities'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Mobility features and capabilities
ms:assetid: 12517a88-2531-44a5-bea5-d8884aff53eb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh689983(v=OCS.15)
ms:contentKeyID: 48183457
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Mobility features and capabilities in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-19_

    The information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

The mobility feature introduced in the Cumulative Updates for Lync Server 2013: February 2013 supports Lync 2010 Mobile and Lync 2013 Mobile clients functionality. When you deploy the Lync Server 2013 Mobility Service, users can use supported Apple iOS, Android, and Windows Phone, or Nokia Symbian mobile devices to perform activities such as sending and receiving instant messages, viewing contacts, and viewing presence. In addition, mobile devices support some Enterprise Voice features, such as click to join a conference, Call via Work, single number reach, voice mail, and missed calls. New features introduced in the Cumulative Updates for Lync Server 2013: February 2013 include Voice over IP (VoIP) capability and video (H.264) for meeting attendee.

The mobility feature introduced in the Cumulative Updates for Lync Server 2013: February 2013 supports Lync 2013 Mobile client functionality. The Cumulative Updates for Lync Server 2013: February 2013 install Unified Communications Web API, or UCWA. UCWA is the component used for Lync 2013 Mobile clients. In Lync Server 2013, Mcx is used for Lync 2010 Mobile clients. Cumulative Updates for Lync Server 2013: February 2013 introduce UCWA as the new entry point for mobility services. Lync Server 2013 concurrently implements the Mobility Service (Mcx), introduced in the Cumulative Updates for Lync Server 2010: November 2011, and provides support for Lync 2010 Mobile. When you deploy the Cumulative Updates for Lync Server 2013: February 2013, users can use supported Apple iOS, Android, and Windows Phone mobile devices to perform such activities as:

<div>


> [!IMPORTANT]  
> Features supported by the Mobility Service from the Cumulative Updates for Lync Server 2010: November 2011 are noted with (Mcx). All listed features are supported by the UCWA, introduced in the Cumulative Updates for Lync Server 2013: February 2013.



</div>

  - Send and receive instant messages (Mcx)

  - View presence (Mcx)

  - View contacts (Mcx)

  - Click to join a conference (Mcx)

  - Call via work (Mcx)

  - Single number reach (Mcx)

  - Voice mail (Mcx)

  - Missed call notification (Mcx)

  - Voice over IP (VoIP)

  - Attendee video (H.264)

<div>


> [!NOTE]  
> Lync 2010 Mobile provided a client for Nokia Symbian devices. Lync 2013 Mobile will not have a client for Nokia Symbian-based devices.



</div>

Apple iPad users will have access to enhanced capabilities. After joining a meeting by using audio call back, an iPad user will be able to view uploaded Microsoft PowerPoint presentations within a meeting, share applications and desktops, view the meeting participant list, and receive notifications of other content types that are being shared within the meeting.

<div>


> [!TIP]  
> With single number reach, a user receives calls on a mobile phone that were dialed to the work number. With Call via Work, the user places an outbound call from the Lync Mobile client by using a work phone number instead of the mobile phone number. With dial-out, the client sends a request to Mcx or UCWA (based on the Lync Mobile version) to make the call for them. The server initiates the call and then calls the user back on the mobile phone. When the user answers, the server completes the call by dialing the other party. By using Call via Work, users can maintain their work identity during a call, which means that the call recipient does not see the caller's mobile number, and the caller avoids incurring outbound calling charges.



</div>

<div>


> [!NOTE]  
> Not all features work exactly the same on all mobile devices. For details about features supported on mobile devices, see the Mobile Client Comparison Tables at <A href="http://go.microsoft.com/fwlink/p/?linkid=234777">http://go.microsoft.com/fwlink/p/?LinkId=234777</A>. For details about supported devices and operating systems, see the requirements topics under <A href="lync-server-2013-planning-for-mobile-clients.md">Planning for mobile clients in Lync Server 2013</A>.



</div>

When you use the Lync Server 2013 Autodiscover feature, mobile applications can automatically locate Lync Server 2013 Web Services without requiring users to manually enter the URLs in their device settings. Manually entering URLs in mobile device settings is also supported, primarily for troubleshooting purposes.

<div>


> [!IMPORTANT]  
> The Mcx and UCWA are complimentary services and both are deployed to support Lync 2010 Mobile and Lync 2013 Mobile clients. Lync 2013 Mobile will not be able to sign in to Lync Server 2010 deployments. Lync 2010 Mobile and Lync 2013 Mobile will be able to use a Lync Server 2013 deployment with the Cumulative Updates for Lync Server 2013: February 2013 applied.



</div>

The mobility feature also supports *push notifications* for mobile devices that do not support applications running in the background. A push notification is a notification that is sent to a mobile device about an event that occurs while a mobile application is inactive. For example, a missed instant messaging (IM) invitation can result in a push notification.

Mcx, UCWA, Autodiscover Service, and support for push notifications are provided in Lync Server 2013. Updated client features, capabilities, and the use of UCWA as the mobility entry point are introduced in the Cumulative Updates for Lync Server 2013: February 2013.

</div>

<span> </span>

</div>

</div>

</div>

