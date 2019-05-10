---
title: Lync Server 2013 A/V conferencing overview
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: A/V conferencing overview
ms:assetid: 9583de87-4618-4a99-a47a-45e8cc4cc221
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ619186(v=OCS.15)
ms:contentKeyID: 49733747
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Overview of A/V conferencing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-13_

A/V conferencing enables real-time audio and video communications between your users. When you deploy conferencing, you can choose to enable and use both web conferencing and A/V conferencing, or just web conferencing.

To plan for A/V conferencing, you need to understand the network bandwidth required by the type of conferencing media that your organization requires. This could include audio, video, and panoramic video.

Before you enable users for A/V conferencing, ensure that your network can handle the resulting load. Without sufficient network bandwidth, the user experience may be severely degraded. You can use call admission control (CAC) to manage the network bandwidth used by A/V Conferencing. This is important for restricted networks, such as limited bandwidth links between central and branch sites. For details, see [Overview of call admission control in Lync Server 2013](lync-server-2013-overview-of-call-admission-control.md). For details about media bandwidth requirements, see [Network bandwidth requirements for media traffic in Lync Server 2013](lync-server-2013-network-bandwidth-requirements-for-media-traffic.md).

If you deploy audio conferencing in your network, your users will need audio devices such as headsets to participate in an audio conference. If you deploy video conferencing, you need to deploy video devices, such as webcams for users. We recommend that you use unified communications (UC) devices that are certified by Microsoft for all device types, to ensure an optimal user experience. For details about UC-certified devices, see "Phones and Devices for Lync" at [http://go.microsoft.com/fwlink/p/?LinkId=263861](http://go.microsoft.com/fwlink/p/?linkid=263861). For either audio or video devices, device deployment, and user training are important steps for you to consider and plan for.

The following sections describe the features for audio and video conferencing, including information about managing bandwidth and selecting the appropriate clients.

<div>

## Audio Conferencing Features

Lync Server 2013 provides several features that you can use to configure the audio conferencing experience for the user, including the following:

  - **Audience mute**   The presenter can use this setting to mute all the audio participants in the conference and put the conference in a state where non-presenters cannot unmute themselves.

  - **Conferencing Entry/Exit Announcements**   If you have enabled dial-in conferencing, presenters can use this setting to turn entry and exit announcements on or off to minimize distractions while a conference is in progress.

  - **Adding a user by dialing out**   Presenters and attendees that have been given permission, can add PSTN numbers to the conferences and have the conference dial-out to those numbers.

</div>

<div>

## Video Conferencing Features

Lync Server 2013 provides several features that you can use to configure the video conferencing experience for the user, including the following:

  - **Gallery View**   In video conferences that have more than two people, users automatically see everyone in the conference. If the conference has more than five participants, the video of the most active participants appear in the top row and only the photo appears for the other participants. Multiparty video is turned on by default. For details about configuring or turning off multiparty video, see [Configuring video bandwidth in Lync Server 2013](lync-server-2013-configuring-video-bandwidth.md).

  - **Panoramic Video**   If a RoundTable video conferencing device is installed in the conferencing room, this feature provides a full 360 degree view of the conference room. The panoramic video strip is only available with RoundTable devices.

  - **Presenter only video mode**   Presenters can configure the meeting so that only the video from the presenter is shown. This prevents distractions in large meetings when multiple video streams are available and locking to different sources. This mode also applies to video captured and provided by RoundTable devices.

  - **HD video**   Users can experience resolutions up to HD 1080P in two-party calls and multiparty conferences.

  - **Video Spotlight**   Presenters can configure the meeting so that only the video from a selected participant who is a video source is seen by the other participants in the conference. This mode also applies to video captured and provided by RoundTable devices for panoramic video.

</div>

</div>

<span> </span>

</div>

</div>

</div>

