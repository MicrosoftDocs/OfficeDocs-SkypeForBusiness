---
title: Manage Skype for Business settings in the Microsoft Teams admin center
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
f1.keywords:
- CSH
- ms.teamsadmincenter.org-widesettings.skypeforbusiness.overview
- ms.teamsadmincenter.org-widesettings.skypeforbusiness.presence
- ms.teamsadmincenter.org-widesettings.skypeforbusiness.skypemeetingbroadcast
- ms.teamsadmincenter.users.skypeforbusiness.settings
ms.custom: 
appliesto: 
- Skype for Business
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to manage settings for Skype for Business features in the Microsoft Teams admin center. 
---

# Manage Skype for Business settings in the Microsoft Teams admin center

<!-- Bookmark used by Context Sensitive Help (CSH). Do not delete. -->
<a name="sfb-settings"> </a>
<!-- Do not remove the bookmark link above. -->

As an admin, the Microsoft Teams admin center is where you manage Skype for Business features for Skype for Business users in your organization. You can manage settings [for your organization](#manage-skype-for-business-settings-for-your-organization) on the **Skype for Business** page and settings [for individual users](#manage-skype-for-business-settings-for-individual-users) on the **Skype for Business** tab of user detail pages.

You'll only see the **Skype for Business** page if the coexistence mode for your organization isn't set to **Teams only**. Similarly, you'll only see the **Skype for Business** tab for a user if the coexistence mode of the user isn't **Teams only**. To learn more about coexistence modes, see [Understand Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md) and [Set your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md).

> [!NOTE]
> Skype for Business settings were previously in **Legacy portal** in the Microsoft Teams admin center. With the retirement of the legacy portal, we migrated the settings to these new locations in the Teams admin center for Skype for Business management.

You must be assigned the [Azure AD admin role](/azure/active-directory/roles/permissions-reference) of Global admin or Skype for Business admin to manage Skype for Business features in the Microsoft Teams admin center.

## Manage Skype for Business settings for your organization

In the left navigation of the Microsoft Teams admin center, go to **Org-wide settings** > **Skype for Business**. From here, you can configure and manage Skype Meeting Broadcast, presence privacy, and mobile device notifications for all Skype for Business users in your organization.

### Skype Meeting Broadcast

<!-- Bookmark used by Context Sensitive Help (CSH). Do not delete. -->
<a name="sfb-org-wide-broadcast"> </a>
<!-- Do not remove the bookmark link above. -->

Use the following settings to manage [Skype Meeting Broadcast](https://support.microsoft.com/office/what-is-a-skype-meeting-broadcast-c472c76b-21f1-4e4b-ab58-329a6c33757d) in your organization.

:::image type="content" source="media/skype-for-business-settings-meeting-broadcast.png" alt-text="Screenshot of Skype Meeting Broadcast settings in the admin center.":::

- **Skype Meeting Broadcasts**: Turn this on to enable Skype Meeting Broadcast for your organization. After you enable this feature, you need to [set up your network for Skype Meeting Broadcast](/skypeforbusiness/set-up-your-network-for-skype-meeting-broadcast/set-up-your-network-for-skype-meeting-broadcast).
- **See preview features**: Turn this on to get early access to new features.
- **Organizers can schedule anonymous meetings**: Turn this on if you want to let organizers create broadcast events that allow anyone outside your organization to join without having to sign in. 
- **Record Skype Meeting Broadcast meetings**: Turn this on to enable organizers and presenters to record meetings.  
- **Helpdesk support URL for attendees**: Enter your organization's support URL that meeting attendees can use if they need help during a meeting.

### Presence and mobile notifications

<!-- Bookmark used by Context Sensitive Help (CSH). Do not delete. -->
<a name="sfb-org-wide-presence-mobile"> </a>
<!-- Do not remove the bookmark link above. -->


Use the following settings to manage Skype for Business presence privacy and mobile notifications in your organization.

:::image type="content" source="media/skype-for-business-settings-presence-mobile.png" alt-text="Screenshot of presence settings in the admin center.":::

#### Presence

By default, Skype for Business users in your organization can see the presence status (such as Available, Busy, or Away) of other Skype for Business users. Choose one of the following to set who can see the presence of your Skype for Business users.

- **Automatically display presence information**: Any Skype for Business user in your organization who hasn't been added to the user's **External** or **Blocked** list can see that user's presence.
- **Display presence information only to a user's contacts**: Any Skype for Business user in the user's Contacts list who isn't added to their **External** or **Blocked** list can see that user's presence. Users can override this setting in Skype for Business by going to **Settings** > **Tools** > **Options**.

#### Mobile notifications

You can set whether your Skype for Business mobile users get alerts about incoming and missed instant messages, voicemail messages, and missed calls through a push notification service. Depending on the mobile devices used in your organization, you can use the **Microsoft Push Notification Service**, the **Apple Push Notification Service**, or both.

Keep the following in mind:

- If you turn off push notifications, users will get all alerts the next time they start Skype for Business on their mobile device.
- By default, push notifications are turned on. Individual users can turn them off in Skype for Business on their mobile device.
- When you turn off push notifications, users can't turn them back on. 

> [!IMPORTANT]
> Microsoft uses other companies to provide real-time Skype for Business mobile notifications for Windows Phone, iPhone, and iPad users. See this [Privacy Statement](https://go.microsoft.com/fwlink/p/?linkid=247732).

## Manage Skype for Business settings for individual users

<!-- Bookmark used by Context Sensitive Help (CSH). Do not delete. -->
<a name="sfb-user-settings"> </a>
<!-- Do not remove the bookmark link above. -->

To manage Skype for Business settings for individual users, in the left navigation of the Teams admin center, go to **Users**, click the user's display name to open the user details page, and then select the **Skype for Business settings** tab. From here, you can configure external access and meeting settings for the user.

:::image type="content" source="media/skype-for-business-settings-user.png" alt-text="Screenshot of Skype for Business tab on user details page.":::

### External access settings

You can selectively allow or block whether a user can communicate with people outside your organization.

- **External Skype for Business users**: Turn this on if you want to allow the user to communicate with Skype for Business users in federated domains.
- **External Skype users**: Turn this on if you want to allow the user to communicate with Skype users. 

### Meeting settings

You can configure the following meeting settings for the user.

- **Audio & Video**: Choose one of the following audio and video settings:

    - **None**: User can't use audio or video.
    - **Audio only**: User can use audio but not video.
    - **Audio and video**: User can use audio and video.
    - **Audio and video (HD)**: User can use audio and high definition video.
    
- **Record conversations & meetings**: Turn this on to allow the user to record conversations and meetings.
- **Compliance**: Turn this on if you're legally required to retain electronically stored information.