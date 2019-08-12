---
title: Manage Microsoft Teams settings for your organization
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: ritikag
search.appverid: MET150
description: Learn how to turn on or off Microsoft Teams org-wide settings for your organization, including apps, external access, guest access, Teams settings, and Teams upgrade preferences.
localization_priority: Priority
ms.custom:
- NewAdminCenter_Update
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

# Manage Microsoft Teams settings for your organization

## Teams apps settings in the Microsoft Teams admin center

You manage apps for your organization in **Teams apps** in the Microsoft Teams admin center. For example, you can set policies to control what apps are available org-wide or to specific Teams users and you can customize Teams by pinning the apps that are most important for your users.

To learn more, see [Admin settings for apps in  Teams](admin-settings.md).  

## Teams org-wide settings in the Microsoft Teams admin center

You can control organization-wide user settings in the Microsoft Teams admin center. To edit org-wide settings, go to the Microsoft Teams admin center, and then select **Org-wide settings**. You can configure the following settings.

### External access

**External access** lets your Teams and Skype for Business users communicate with users who are outside of your organization or domain. To configure external access, go to [Let your Teams users chat and communicate with users in another Teams organization](let-your-teams-users-communicate-with-other-people.md).

To add or block a domain:

1. Select **Add a domain**.
2. In the Add a domain pane, enter the domain name, and click the space bar to save the name.
3. Select **Allowed** or **Blocked**.
4. Select **Done** to save your changes. 

### Guest access

**Guest access** in Microsoft Teams allows teams in your organization to collaborate with people outside your organization by granting them access to teams and channels. Anyone with a business or consumer email account, such as Outlook, Gmail, or others, can participate as a guest in Teams with full access to team chats, meetings, and files. For more information, see [Guest access in Microsoft Teams](guest-access.md).

### Teams settings

In **Teams settings**, you can set up email integration, cloud storage options, Skype for Business interoperability, and devices.

#### Email integration

Turn on this feature so users can send email to a channel in Teams, using the channel email address. Users can do this for any channel belonging to a team they own. Users can also send emails to any channel in a team that has adding connectors turned on for team members. To turn on email integration, make sure that **Allow users to send emails to a channel email address** is **On**. 

#### Files

Here you can turn on or turn off file sharing and cloud file storage options. 

Users can upload and share files from cloud storage services in Teams channels and chats. Cloud storage options in Teams currently include ShareFile, Dropbox, Box, and Google Drive. Turn on the switch for the cloud storage providers that your organization wants to use.

#### Organization

Here you can turn on the **Organization** tab, which shows the detailed organizational chart for the user’s organization. For more information, see [Use the organization tab in Teams](https://support.office.com/article/use-the-organization-tab-in-teams-ff02568b-290a-46d6-ae7a-cda22f723894).

#### Devices

These settings control resource account behavior for Surface Hub devices attending Microsoft Teams meetings. Use these settings to configure authentication requirements, require a content PIN, and turn on Surface Hub resource accounts to send messages.

- **Require a secondary form of authentication to access meeting content** – Select the level of access that users have when they enter the content PIN.
- **Set content PIN** – Require users to enter this PIN to prevent unauthorized access to documents. This prevents an unauthorized user from joining upcoming meetings and browsing attachments.
- **Resource accounts can send messages** – Turn this setting **On** to allow messages to be sent from the Surface Hub resource account.

#### Search by name

Microsoft Teams scoped directory search uses Exchange address book policy (APB) to allow organizations to create virtual boundaries that control how users can find and communicate with other users in their organization. You might want to use a scoped directory search in situations like these:

- Your organization has multiple companies within its tenant that you want to keep separate. 
- Your school wants to limit chats between faculty and students. 

Switch this setting **On** to turn on scoped directory searches.

### Teams upgrade

You can use these settings to configure how your users will be upgraded from Skype for Business to Microsoft Teams. 

#### Coexistence mode
You can specify a coexistence mode: **Teams only**, **Islands** (Teams and Skype for Business will coexist), or **Skype for Business only**. The coexistence mode you choose determines the routing of incoming calls and chats and the app that is used by the user to initiate chats and calls or to schedule meetings. For more information about coexistence modes, go to [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md).

#### App preferences

Here you can choose the app that users will use to join Skype for Business meetings (Skype for Business or the [Skype Meetings App](https://support.office.com/en-us/article/What-is-Skype-Meetings-App-Skype-for-Business-Web-App-1FF3D412-718A-4982-8FF2-A4992608CDB5)). This setting isn't dependent on the coexistence mode setting.

## How can I tell which features are available?

See the [Microsoft 365 Roadmap](https://www.microsoft.com/en-us/microsoft-365/roadmap?rtc=1&filters=Microsoft%20Teams) for information about new Teams features. For more information about new and upcoming features, see the Teams [What's New](https://support.office.com/en-us/article/what-s-new-in-microsoft-teams-d7092a6d-c896-424c-b362-a472d5f105de?ui=en-US&rs=en-US&ad=US) page and the [Tech Community Microsoft Teams blog](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/What-s-new-in-Teams-Microsoft-Ignite-Edition/ba-p/252531) for Teams. 

## More information

For information about which roles can perform admin functions, see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).
