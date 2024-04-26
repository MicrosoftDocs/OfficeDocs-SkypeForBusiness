---
title: Manage Audio Conferencing settings for users
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: oscarr
ms.date: 02/21/2024
ms.topic: article
ms.assetid: 0f39dc9d-eb60-4c5a-9ae3-e34a01834d9b
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-audio-conferencing
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - Audio Conferencing
  - seo-marvel-mar2020
description: A Microsoft 365 or Office 365 admin can edit the Teams Audio Conferencing settings, including provider, default toll or toll-free number, conference ID, or PIN for a user.
---

# Manage the Audio Conferencing settings for a user in Microsoft Teams

As a Microsoft 365 or Office 365 admin, you can edit the Audio Conferencing settings—such as the provider, default toll or toll-free number, conference ID, or PIN—for an individual user in your organization. If you want to edit settings for your organization, see [Manage the Audio Conferencing settings for your organization](manage-the-audio-conferencing-settings-for-my-organization-in-teams.md).

## Using the Microsoft Teams admin center

1. In the left navigation, select **Users**, and then select the user from the list of available users.

2. Select **Edit**

3. Under **Audio Conferencing**, modify any of the following:

|**Setting**|**Description**|
|:-----|:-----|
|**Audio conferencing**|To turn audio conferencing on or off for the user, select **Edit** next to **Audio Conferencing**, and then in the **Audio Conferencing** pane, toggle **Audio conferencing** On or Off.|
|**Send conference info in email**  |Select this link only if you want to immediately send an email to the user with their Audio conferencing phone number. (This email doesn't include the PIN.) See [Send an email to a user with their Audio Conferencing information](send-an-email-to-a-user-with-their-dial-in-information-in-teams.md).  |
|**PIN** |Select **Reset PIN** if you need to reset the PIN for the user. For more information, see [Reset the Audio Conferencing PIN](reset-the-audio-conferencing-pin-in-teams.md). |
|**Default conferencing toll phone number** (required) |The numbers set on the audio conferencing bridge. Format the numbers as you want them to appear in Teams meeting requests. To change the default toll number, select **Edit** next to **Audio Conferencing** and in the **Audio Conferencing** pane, select a number under **Toll number**. You can also set phone numbers by adding them to the TeamsAudioConferencingPolicy and assigning the policy to your users. Phone numbers added to the policy take precedence over the phone numbers set using **Default conferencing Toll phone number**. If no phone numbers are added to the TeamsAudioConferencingPolicy, then the phone number set using **Default conferencing Toll phone number** is displayed in Microsoft Teams meeting requests. |
|**Invites from this user can include toll-free number**|This setting can only be changed using the TeamsAudioconferecningPolicy. |
|**Unauthenticated users can be the first person in the meeting**|To change this setting, toggle **Unauthenticated users can be the first person in the meeting** On or Off.
|**Dial-out permissions**|To change this setting, select **Edit** next to **Audio Conferencing** and in the **Audio Conferencing** pane, choose an option under **Dial-out from meetings**.|

:::image type="content" source="media/teams-manage-audio-conferencing-settings-for-a-user-image-2023.png" alt-text="Screenshot of Audio Conferencing settings for a user in the Microsoft Teams Admin Center.":::

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## Related topics

- [Manage the Audio Conferencing settings for your organization](manage-the-audio-conferencing-settings-for-my-organization-in-teams.md)

- [Audio Conferencing common questions](audio-conferencing-common-questions.md)
