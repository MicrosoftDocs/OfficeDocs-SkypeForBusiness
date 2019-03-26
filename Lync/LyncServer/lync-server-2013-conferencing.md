---
title: Lync Server 2013 conferencing
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Conferencing
ms:assetid: 6129b7e0-9abd-488e-a54e-86094eb9df7a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg417161(v=OCS.15)
ms:contentKeyID: 48184274
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Conferencing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-11_

With unified conferencing in Lync Server 2013, users can collaborate, share information, and coordinate their efforts in real time. All your users can use the full breadth of spontaneous collaboration, scheduled meetings, and meeting tools. Voice and video conferencing capabilities can be used from any location with an Internet connection, and users away from a computer can participate in audio conferences by dialing in with a public switched telephone network (PSTN) phone.

Meeting tools integrated into Outlook enable organizers to schedule a meeting or start an impromptu conference with a single click, and also make it just as easy for attendees to join. A web client extends rich conference features to participants who are not running the desktop version of Lync.

<div>

## Audio and Video Conferencing

Lync Server provides a user experience that is familiar to users of traditional audio bridge services including PSTN dial-in services with touch-tone call control commands. At the same time, it incorporates powerful scheduling, joining, and management features available only with an integrated unified communications platform.

With a single click, users can schedule a meeting from Outlook. Details, such as meeting time, location, and attendees, follow the familiar Outlook template. Additionally, conference call-specific information, such as dial-in number, meeting IDs, and personal identification number (PIN) reminders, are automatically populated.

To help ensure that only the authorized people participate in a call, Lync Server provides multiple levels of authentication for participants. Users who join by using Lync are already authenticated by the Active Directory Domain Services and do not need to enter a PIN, pass code, or meeting ID.

Lync simplifies the video conferencing user experience by incorporating video into the unified client so that scheduling a meeting with video or escalating to video spontaneously is seamless and easy.

Lync Server makes it easy to add video to a standard phone call in just one click. When there are multiple participants in a video call or a conference, each user can see video from up to five other users simultaneously, or a presenter can choose just one video source to be seen exclusively by everyone.

High-definition video (resolution 1270 x 720; aspect ratio 16:9) and VGA video (resolution 640 x 480; aspect ratio 4:3) are supported for peer-to-peer calls between users running Lync on high-end computers. The resolution viewed by each participant in a single conversation may differ, depending on the video capabilities of each user’s respective hardware.

IT administrators can set policies to restrict or disable high-definition or VGA video on clients, depending on computer capability, network bandwidth, and the presence of a camera able to deliver the required resolution. These policies are enforced through in-band provisioning.

</div>

<div>

## Web conferencing

Lync Server integrates conferencing sharing features such as desktop, application, attachment, whiteboard, poll and PowerPoint into the streamlined Lync. Combined with audio or video conferencing, the result is a highly immersive and collaborative session that is simple to facilitate.

To improve the overall experience of users presenting or viewing PowerPoint presentations, Lync Server 2013 employs Office Web Apps to handle PowerPoint presentations. Users can share a picture or copy and paste text using a Whiteboard in the Lync meeting. Presenters can conduct polls in the Lync meeting to solicit feedback from the attendees.

Desktop sharing enables presenters to broadcast any visuals, applications, webpages, documents, software, or part of their desktops to remote participants in real time, right from Lync. Audience members can follow along with mouse movements and keyboard input. Presenters can choose to share the entire screen or only a portion. By sharing their desktops, presenters are able to engage with their audiences in interactive product or software demos from any location.

Application sharing enables presenters to share control of software on their desktops without losing sight of participant feedback or text questions. Presenters can also delegate control of the application to meeting participants.

</div>

<div>

## Dial-in Conferencing

For users that are not using a personal computer, there are several methods available for joining a Lync Server conference call. A PSTN user can dial an access number, access the meeting bridge, and then enter the meeting ID. For more secure meetings, the user can also be required to enter his or her PIN to authenticate against Active Directory. Lync Server also supports Lync Phone Edition devices, which are stand-alone IP phone devices provided by Microsoft partners.

</div>

</div>

<span> </span>

</div>

</div>

</div>

