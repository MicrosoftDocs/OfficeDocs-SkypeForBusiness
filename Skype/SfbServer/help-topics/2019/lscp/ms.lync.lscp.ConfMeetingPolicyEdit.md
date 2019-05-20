---
title: "Conferencing Policy Create New or Edit Existing"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.ConfMeetingPolicyEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: ebd2f120-b57a-4c94-9509-20e098f4b0f4
ROBOTS: NOINDEX, NOFOLLOW
description: "A Conferencing policy defines the features and capabilities that users have available during a conference (also known as meeting)."
---

# Conferencing Policy: Create New or Edit Existing

A Conferencing policy defines the features and capabilities that users have available during a conference (also known as meeting).

## UI Reference

The following list describes the fields on the page.

- **Scope** Identifies the scope of the conferencing policy that you are creating or modifying: global, site, or user.

- **Name** Each conferencing policy requires a name. Global and site conferencing policies are named by default, and the name cannot be changed. For user conferencing policies, use a descriptive name that identifies the user or group of users.

    > [!NOTE]
    > After you save the conferencing policy, the name cannot be changed.

- **Description** This field is optional. Use it to provide additional details about the conferencing policy.

- **Organizer policy** The settings in this section apply to the user who organizes a conference. If a setting is selected, the user can organize a conference that has the specified characteristic. If a setting is not selected, the user can't organize a conference with this characteristic. These settings do not determine what the user has access to as a participant in other conferences.

    Click the up arrow or down arrow next to the label to close or open the section.

- **Maximum meeting size** the maximum number of users that are allowed at a conference. By default, the maximum conference size is 250.

- **Allow participants to invite anonymous users** Select this check box to allow users to invite anonymous users to conferences. Anonymous users are users who do not have credentials in your organization's Active Directory Domain Services and who, therefore, are not authenticated.

- **Recording** Specify whether or not participants can record conferences. The options are **None** or **Enable recording**.

- **Allow federated and anonymous participants to record** Select this check box to allow external and unauthenticated participants to record conferences.

- **Audio/video** Specify whether participants can use audio and video:

  - **None** Select this option to prevent the use of audio and video.

  - **Enable IP audio** Select this option to allow the use of audio but not video.

  - **Enable IP audio/video** Select this option to allow both audio and video.

- **Enable PSTN dial-in conferencing** If you enabled audio in **Audio/video**, select this check box to allow users to dial in to conferences by using the public switched telephone network (PSTN).

- **Allow anonymous participants to dial out** Select this check box if you allow users to dial in to conferences and you want to allow unauthenticated (anonymous) users to join a conference by using dial out phoning. With dial-out phoning, the conference server calls the user, and the user answers the phone to join the conference.

- **Allow participants not enabled for Enterprise Voice to dial out** If you enabled audio in **Audio/video**, select this check box to allow users who are not enabled for Enterprise Voice to join a conference by using dial-out phoning. With dial-out phoning the conferencing server telephones the user, and then the user answers the phone to join the conference.

- **Allow multiple video streams** If you enabled video in **Audio/video**, select this check box to allow users to organize conferences with Gallery View video. When this check box is selected, this setting allows users to organize conferences that send multiple video streams. When this check box is not selected, users can only organize conferences that send a single video stream.

    > [!NOTE]
    > This option determines the type of video stream supported by the conference. It does not determine whether participants can receive multiple video streams. The **Enable participants to join with multiple video streams** option determines whether participants can receive multiple video streams.

- **Data collaboration** Specify whether or not the conference allows data collaboration. The options are **None** or **Enable data collaboration**.

    The following settings apply to data collaboration:

  - **Allow federated and anonymous participants to download content** If you allow data collaboration, select this check box to allow external and unauthenticated users to download content, such as slides or handouts, from a conference.

  - **Allow participants to transfer files** If you allow data collaboration, select this check box to allow file transfers to all participants during a conference.

  - **Enable annotations** If you allow data collaboration, select this check box to allow participants to make on-screen annotations on content shared during the conference.

  - **Enable PowerPoint annotations** If you allow annotation, select this check box to allow participants to make annotations in PowerPoint slides shared during the conference.

  - **Enable polls** If you allow data collaboration, select this check box to allow participants to hold a poll during a conference.

- **Application sharing** Specify whether or not the conference allows application sharing. The options are **Disable application sharing** or **Enable application sharing**.

    The following settings apply to application sharing:

  - **Allow participants to take control** If you allow application sharing, select this check box to allow participants to take control of applications or desktops that are shared during the conference.

  - **Allow federated and anonymous participants to take control** If you allow application sharing, select this check box to allow external and unauthenticated participants to take control of applications or desktops that are shared during the conference.

- **Participant policy** The settings in this section apply to users as participants in a conference or two-party session. Because the following settings are per-user settings, one user in a conference or two-party session may have different capabilities than another user in the same conference or two-party session.

    Click the up arrow or down arrow next to the label to close or open the section.

- Select **Enable application and desktop sharing** to allow users to share applications or their desktop while participating in a conference or two-party session. Select **Disable application and desktop sharing** to prevent users from sharing applications or their desktop while participating in a conference or two-party session.

- **Enable peer-to-peer file transfer** Select this check box to allow person-to-person file transfers (that is, file transfers that do not involve all participants) during a conference or two-party session.

- **Enable peer-to-peer recording** Select this check box to allow users to record two-party sessions.

- **Enable participants to join with multiple video streams** Select this check box to allow participants to receive Gallery View video in conferences that allow it. If this option is not selected, participants can only receive a single video stream regardless of what the conference allows.

    > [!NOTE]
    > The **Allow multiple video streams** determines whether a conference allows multiple video streams.

For details about conferencing features and capabilities, see [Overview of Conferencing](https://technet.microsoft.com/library/5bb90e69-3d4f-4d59-a1ee-2550de84439f.aspx) in the Planning documentation. For details about working with conferencing policies, see [Conferencing Policies](https://technet.microsoft.com/library/8f92eb7c-ee66-4df6-a726-4bff93b122cb.aspx) in the Operations documentation.


