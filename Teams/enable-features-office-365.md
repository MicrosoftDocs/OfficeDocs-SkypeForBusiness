---
title: Manage settings for your organization
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: ritikag
search.appverid: MET150
description: Learn how to turn on or off Microsoft Teams org-wide settings, including apps, external access, guest access, Teams settings, and Teams upgrade preferences.
ms.localizationpriority: high
ms.collection: 
  - M365-collaboration
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.orgwidesettings.teamssettings.targetingintro
  - ms.teamsadmincenter.teamssettings.overview
  - NewAdminCenter_Update
  - seo-marvel-mar2020
appliesto: 
  - Microsoft Teams
---

# Manage Microsoft Teams settings for your organization

## Teams apps settings in the Microsoft Teams admin center

You manage apps for your organization in **Teams apps** in the [Microsoft Teams admin center](https://admin.teams.microsoft.com). For example, you can set policies to control what apps are available org-wide or to specific Teams users and you can customize Teams by pinning the apps that are most important for your users.

To learn more, see [Admin settings for apps in  Teams](admin-settings.md).  

## Teams external access and guest access settings in the Microsoft Teams admin center

You can control external and guest access settings in the Microsoft Teams admin center. To edit these settings, go to the Microsoft Teams admin center, and then select **Users**. You can configure the following settings.

### External access

**External access** lets your Teams and Skype for Business users communicate with users who are outside of your organization or domain. To configure external access, go to [Let your Teams users chat and communicate with users in another Teams organization](./manage-external-access.md).

To add or block a domain:

1. Select **Add a domain**.
2. In the Add a domain pane, enter the domain name, and select the space bar to save the name.
3. Select **Allowed** or **Blocked**.
4. Select **Done** to save your changes. 

### Guest access

**Guest access** in Microsoft Teams allows teams in your organization to collaborate with people outside your organization by granting them access to teams and channels. Anyone with a business or consumer email account, such as Outlook, Gmail, or others, can participate as a guest in Teams with full access to team chats, meetings, and files. For more information, see [Guest access in Microsoft Teams](guest-access.md).

## Teams settings and Teams upgrade settings in the Microsoft Teams admin center

You can control Teams settings and Teams upgrade settings in the Microsoft Teams admin center. To edit these settings, go to the Microsoft Teams admin center, and then select **Teams**. You can configure the following settings.

### Teams settings

In **Teams settings**, you can set up features for teams including notifications and feeds, email integration, cloud storage options, and devices.

#### Notifications and feeds

Here you can control whether suggested feeds appear in users' activity feed in Teams. To learn more about the activity feed, see [Explore the Activity feed in Teams](https://support.office.com/article/explore-the-activity-feed-in-teams-91c635a1-644a-4c60-9c98-233db3e13a56).

#### Tagging

Tags let users communicate with a subset of people on a team. Tags can be added to one or more team members. After a tag is added, it can be used in @mentions by anyone on the team in a channel post to communicate with only those people who are assigned that tag. Use these settings to control who can add tags and how tags are used across your organization. To learn more, see [Manage tags in Teams](manage-tags.md).

#### Email integration

Turn on this feature so users can send email to a channel in Teams, using the channel email address. Users can do this for any channel belonging to a team they own. Users can also send emails to any channel in a team that has adding connectors turned on for team members. To turn on email integration, make sure that **Allow users to send emails to a channel email address** is **On**. Next, check to make sure that the domain for the sender's email address isn't blocked in Teams Admin Center>Org-Wide settings>Teams Settings>Email integration>**Accept channel email from these SMTP domains**. It should be either blank or includes all the domains that you expect to receive emails from. Next, you need to make sure you have the necessary rules in place to ensure [the email to the Teams channel email address isn't blocked](/office365/servicedescriptions/exchange-online-protection-service-description/anti-spam-and-anti-malware-protection-eop#customize-anti-spam-policies).

#### Files

Here you can turn on or turn off file sharing and cloud file storage options.

Users can upload and share files from cloud storage services in Teams channels and chats. Cloud storage options in Teams currently include Dropbox, Box, Citrix files, Google Drive, and Egnyte. Turn on the switch for the cloud storage providers that your organization wants to use.

#### Organization

Here you can turn on the **Organization** tab, which shows the detailed organizational chart for the user's organization. For more information, see [Use the organization tab in Teams](https://support.office.com/article/use-the-organization-tab-in-teams-ff02568b-290a-46d6-ae7a-cda22f723894).

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

#### Safety and communications

Supervised chat allows organizations and schools to limit chat capabilities using role-based permissions. These permissions control the amount of supervision a user requires while chatting with others. Learn more about [supervised chat](supervise-chats-edu.md).

### Teams upgrade settings

You can use these settings to configure how your users will be upgraded from Skype for Business to Microsoft Teams. 

#### Coexistence mode
You can specify a coexistence mode: 

- **Teams only**
- **Islands** (Teams and Skype for Business will coexist)
- **Skype for Business only**
- **Skype for Business with Teams collaboration** (Users receive chats and calls and schedule meetings in Skype for Business but use  Teams for group collaboration)
- **Skype for Business with Teams collaboration and meetings** (Users receive chats and calls in Skype for Business but use Teams for group collaboration and to schedule meetings)

The coexistence mode you choose determines the routing of incoming calls and chats and the app that is used by the user to initiate chats and calls or to schedule meetings. For more information about coexistence modes, go to [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md).

#### App preferences

Here you can choose the app that users will use to join Skype for Business meetings (Skype for Business or the [Skype Meetings App](https://support.office.com/article/What-is-Skype-Meetings-App-Skype-for-Business-Web-App-1FF3D412-718A-4982-8FF2-A4992608CDB5)). This setting isn't dependent on the coexistence mode setting.

### Planning settings in the Microsoft Teams admin center

#### Network Planner

Network Planner helps you determine and organize network requirements for connecting Teams users across your organization.  Learn how to [Use the Network Planner for Microsoft Teams](./network-planner.md).

You can also select the "Download the Teams app in the background for Skype for Business users" option as well.  By default this setting is set to On. With this setting enabled it will download the Teams app in the background for users running the Skype for Business app on Windows PCs. This happens if the Coexistence mode for the user is Teams Only, or if a pending upgrade notification is enabled in the Skype for Business app.

## Other settings in the Microsoft Teams admin center

### Skype for Business

Use this page to manage Skype for Business features for Skype for Business users in your organization. To learn more, see [Manage Skype for Business settings in the Microsoft Teams admin center](skype-for-business-settings.md).

## How can I tell which features are available?

See the [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?rtc=1&filters=Microsoft%20Teams) for information about new Teams features. For more information about new and upcoming features, see the Teams [What's New](https://support.office.com/article/what-s-new-in-microsoft-teams-d7092a6d-c896-424c-b362-a472d5f105de?ui=en-US&rs=en-US&ad=US) page and the [Tech Community Microsoft Teams blog](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/What-s-new-in-Teams-Microsoft-Ignite-Edition/ba-p/252531) for Teams. 

## More information

For information about which roles can perform admin functions, see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).
