---
title: Manage Microsoft Teams features in your Office 365 organization
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 10/29/2018
ms.topic: article
ms.service: msteams
ms.reviewer: ritikag
search.appverid: MET150
description: Learn how to turn on or off Microsoft Teams apps in your Office 365 organization, including tabs, connectors, bots, or any combination of the three.
localization_priority: Normal
ms.custom:
- NewAdminCenter_Update
MS.collection: Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
---

# Manage Microsoft Teams features in your Office 365 organization

All Teams settings will soon be migrated to the new Microsoft Teams & Skype for Business Admin Center. The only Teams feature that is managed in the Office 365 admin center is Apps. 

Unless otherwise noted, the default value for an option is **On**.

## Office 365 tenant-wide settings 

In **Tenant-wide settings**, you can turn on or turn off Apps.

To edit **Tenant-wide settings** for Teams, go to the Microsoft Teams & Skype for Business Admin Center, and select **Legacy portal**. Choose **Settings** > **Services & add-ins** > **Microsoft Teams**. If you're signed in as an Office 365 admin, this link should take you there: 
>  
> https://portal.office.com/adminportal/home#/Settings/ServicesAndAddIns  

### Apps

Apps are tabs, connectors, bots, or any combination of these three, provided by a third-party service. There are Teams admin policies that can be configured in the Office 365 admin center to control which external third-party apps are allowed. These policies let you specify which apps are allowed and disallowed, new external app behavior, and whether side-loading apps is allowed. 

Under **Apps**, you can configure the following settings for your organization: 

![Screenshot of the Apps section.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image6.png)

- **Allow external apps in Microsoft Teams**: When this switch is turned on, users can add tabs and bots that are available to the Office 365 tenant. 
 
    ![Screenshot of the Allow external apps control in the Apps section.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image6.2.png)

- **Enable new external apps by default**: When this switch is turned on, users can activate new apps as soon as they're added to the Teams app catalog. Turn off this switch if you want to control new apps. Of course, if you turn it off, you have to remember to review new apps periodically so your organization doesn't miss out on cool new apps. 

- **Allow sideloading of external apps**: When this switch is turned on, users can install and turn on custom bots and tabs. 

To learn more, read [Admin settings for apps in Teams](admin-settings.md). 

## Teams org-wide settings

You can control organization-wide user settings in the Microsoft Teams & Skype for Business Admin Center. To edit org-wide settings, go to the Microsoft Skype for Business Admin Center, and then select **Org-wide settings**. You can configure the following settings.

### External access

**External access** lets your Teams and Skype for Business users communicate with users who are outside of your organization. To configure external access, go to [Let your Teams users chat and communicate with users in another Teams organization](let-your-teams-users-communicate-with-other-people.md).

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

#### Skype for Business interop

Use this setting to let Teams users chat with Skype for Business users. For detailed information about interoperability between Teams and Skype for Business, go to [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md).

#### Devices

These settings control resource account behavior for Surface Hub devices attending Microsoft Teams meetings. Use these settings to configure authentication requirements, require a content PIN, and turn on Surface Hub resource accounts to send messages.

- **Require a secondary form of authentication to access meeting content** – Select the level of access that users have when they enter the content PIN.
- **Set content PIN** – Require users to enter this PIN to prevent unauthorized access to documents. This prevents an unauthorized user from joining upcoming meetings and browsing attachments.
- **Resource accounts can send messages** – Turn this setting **On** to allow messages to be sent from the Surface Hub resource account.

#### Search

Microsoft Teams scoped directory search uses Exchange address book policy (APB) to allow organizations to create virtual boundaries that control how users can find and communicate with other users in their organization. You might want to use a scoped directory search in situations like these:

- Your organization has multiple companies within its tenant that you want to keep separate. 
- Your school wants to limit chats between faculty and students. 

Switch this setting **On** to turn on scoped directory searches.

### Teams upgrade

You can use these settings to configure how your users will be upgraded from Skype for Business to Microsoft Teams. 

#### Coexistence mode
You can specify a coexistence mode: **Teams only**, **Islands** (Teams and Skype for Business will coexist), or **Skype for Business only**. The Coexistence mode you choose determines the routing of incoming calls and chats and the app that is used by the user to initiate chats and calls or to schedule meetings. For more information about coexistence modes, go to [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md).

#### App preferences

Here you can choose the app that users will use to join Skype for Business meetings (Skype for Business or the [Skype Meetings App](https://support.office.com/en-us/article/What-is-Skype-Meetings-App-Skype-for-Business-Web-App-1FF3D412-718A-4982-8FF2-A4992608CDB5)). This setting isn't dependent on the coexistence mode setting.

## How can I tell which features are available?

See the [Office 365 Roadmap](https://www.microsoft.com/en-us/microsoft-365/roadmap?rtc=1&filters=Microsoft%20Teams) for information about new Teams features. For more information about new and upcoming features, see the Teams [What's New](https://support.office.com/en-us/article/what-s-new-in-microsoft-teams-d7092a6d-c896-424c-b362-a472d5f105de?ui=en-US&rs=en-US&ad=US) page and the [Tech Community Microsoft Teams blog](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/What-s-new-in-Teams-Microsoft-Ignite-Edition/ba-p/252531) for Teams. 

## More information

For information about which roles can perform admin functions, see [Use Microsoft Teams admin roles to manage Teams](using-admin-roles.md).
