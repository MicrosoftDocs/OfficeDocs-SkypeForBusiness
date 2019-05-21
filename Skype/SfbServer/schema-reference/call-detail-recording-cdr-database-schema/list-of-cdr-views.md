---
title: "List of CDR views"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 7/15/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2f72aead-d1da-4185-b75c-f6c31d76a6b3
description: "Views provide an easy way to access information about the most common scenarios used for returning data from the CDR database. It is recommended that you use views for building custom reports instead of using the actual CDR database tables ; that's because the database views are more likely to maintain backwards compatibility with future releases."
---

# List of CDR views
 
Views provide an easy way to access information about the most common scenarios used for returning data from the CDR database. It is recommended that you use views for building custom reports instead of using the actual CDR database tables ; that's because the database views are more likely to maintain backwards compatibility with future releases.
  
|**View Name**|**Description**|
|:-----|:-----|
|[ClientVersions view](clientversions-0.md) <br/> |Returns information about the client software/devices used in a communication session.  <br/> |
|[ConferenceMessageCount view](conferencemessagecount-0.md) <br/> |Returns information about the number of messages sent by users in a conference.  <br/> |
|[Conferences view](conferences-0.md) <br/> |Returns conference information, including start time, end time, and conference organizer.  <br/> |
|[ConferenceSessionDetails view](conferencesessiondetails.md) <br/> |Returns session details for all conferencing sessions, including start and end time, user IDs, response codes, and diagnostic IDs.  <br/> |
|[ConferenceUris view](conferenceuris-0.md) <br/> |Returns information about conference URIs used in a conference  <br/> |
|[ErrorReport view](errorreport-0.md) <br/> |Returns information about errors that occurred during a session.  <br/> |
|[FileTransfers view](filetransfers.md) <br/> |Returns information about file transfer sessions, including the file name and whether the transfer was accepted, rejected, or cancelled.  <br/> |
|[FocusJoinsAndLeaves view](focusjoinsandleaves-0.md) <br/> |Returns information about conference join and leave activities.  <br/> |
|[McuJoinsAndLeaves view](mcujoinsandleaves-0.md) <br/> |Returns combined information about conference join and leave activities (each conference join is paired with the corresponding conference leave).  <br/> |
|[Mcus view](mcus-0.md) <br/> |Returns information about Conferencing servers.  <br/> |
|[Media view](media-0.md) <br/> |Returns information about the types of media used in peer-to-peer communication sessions.  <br/> |
|[ProgressReport view](progressreport-0.md) <br/> |Returns information about completed sessions.  <br/> |
|[Registration view](registration-0.md) <br/> |Returns information about registrations with Skype for Business Server 2015.  <br/> |
|[SessionDetails view](sessiondetails-0.md) <br/> |Returns information about peer-to-peer sessions, including VoIP-VoIP phone calls, two-party IM sessions, or other peer-to-peer communication sessions.  <br/> |
|[User view](user.md) <br/> |Returns information about the users who have participated in communication sessions.  <br/> |
|[VoIPDetails view](voipdetails.md) <br/> |Returns information for peer-to-peer sessions involving at least one VoIP (Voice over IO) user.  <br/> |
   

