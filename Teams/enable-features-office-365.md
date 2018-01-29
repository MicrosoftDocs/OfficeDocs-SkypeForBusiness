---
title: Turn on Microsoft Teams features in your Office 365 organization
author: LolaJacobsen
ms.author: lolaj
manager: lolaj
ms.date: 01/29/2018
ms.topic: article
ms.service: msteams
description: Learn all the Microsoft Teams features you can turn on or turn off in your Office 365 organization, including tenant-wide settings, email integration, apps, cloud storage, and more.
MS.collection: Strat_MT_TeamsAdmin

---

Turn on Microsoft Teams features in your Office 365 organization
======================================================

Teams has multiple settings that can be turned on or turned off at the Office 365 tenant level. With Teams turned on for a tenant, any user that is also enabled for Teams will inherit the settings from the tenant level.

Below is the list of features an Office 365 administrator can turn on or turn off in Teams. 

Unless otherwise noted, the default value for an option is On.

> [!NOTE] 
> To manage admin settings for Teams, go to the Office 365 admin center and open **Settings** > **Services & add-ins**, then choose **Microsoft Teams**. If you're signed in as an Office 365 admin, this link should take you there: 
>  
> https://portal.office.com/adminportal/home#/Settings/ServicesAndAddIns  

> [!IMPORTANT]
> An Office 365 admin can turn off Microsoft Teams at any time in the Office 365 admin center. Be aware that users with active Microsoft Teams licenses will continue to see the Teams app tile even if you turn off Teams. For details about how to remove licenses from users, see [Manage user access to Microsoft Teams](user-access.md). After Teams is disabled, access from the Teams client is blocked, but data available through other clients and services is still available, such as files via SharePoint and OneDrive. All data remains in place unless the teams are explicitly deleted.

Office 365 tenant-wide settings 
---------------------

In **Tenant-wide settings**, you can turn on or turn off options in General, Email integration, Apps, and Custom cloud storage.

To edit **Tenant-wide settings** for Teams, go to the Office 365 admin center. Choose **Settings** > **Services & add-ins** > **Microsoft Teams**.

### General

The General section lets you configure the following settings for your organization:

> ![Screenshot of the General section in Tenant-wide settings.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image1.png)

-   **Show organizational chart in personal profile:** When this setting is turned on, it shows the organizational chart icon in the user’s contact card, and when clicked, it displays the detailed organizational chart.

    ![Screenshot of the organizational chart icon in a user's contact card.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image2.png)

    ![Screenshot of an organization chart.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image3.png)

-  **Use Skype for Business for recipients who don’t have Teams:** When this setting is turned on, Teams conversations automatically show up in Skype for Business for users that aren't enabled for Teams.  

-   **Allow T-bot proactive help messages:** When this setting is turned on, T-bot will initiate a private chat session with users to help them use Teams.

    ![Screenshot of T-Bot section in Teams interface.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image4.png)

Email integration
-----------------

Turn on this feature so users can send email to a channel in Teams, using the channel email address. Users can do this for any channel belonging to a team they own. Users can also send emails to any channel in a team that has adding connectors enabled for team members. And, even if a user doesn’t have permission to create a channel email address, if someone who does have permission creates that address, the user can access it from the **More options** menu for that channel.

Configure the following **Email integration** settings for your organization: 

   ![Screenshot of the Email integration section in Tenant-wide settings.](media/QS-edu-email-integration.png)

-   **Allow users to send emails to channels:** When turned on, mail hooks are enabled, and users can post messages to a channel by sending an email to the email address of a Teams channel. 

 
-   **Allow users to send emails to channels:** When turned on, mail hooks are enabled, and users can post messages to a channel by sending an email to the email address of Teams channel. 

    To find the email address for a channel, click the **More options** menu for the channel and then select **Get email address**. 

-   **Restricted Senders List:** Senders domains can be further restricted to ensure that only allowed SMTP domains can send emails to the Teams channels.

Apps
----

Apps are tabs, connectors, bots, or any combination of these three, provided by a third-party service. There are Teams admin policies that can be configured in the Office 365 admin center to control which external third-party apps are allowed. These policies let you specify which apps are allowed and disallowed, new external App behavior, and whether side-loading apps is allowed. 

Under **Apps**, you can configure the following settings for your organization: 

![Screenshot of the Apps section.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image6.png)

- **Allow external apps in Microsoft Teams**: When this switch is turned on, users can add tabs and bots that are available to the Office 365 tenant. 
 
    ![Screenshot of the Allow external apps control in the Apps section.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image6.2.png)

- **Enable new external apps by default**: When this switch is turned on, users can activate new apps as soon as they're added to the Teams app catalog. Turn off this switch if you want to control new apps. Of course, if you turn it off, you have to remember to review new apps periodically so your organization doesn't miss out on cool new apps. 

- **Allow sideloading of external apps**: When this switch is turned on, users can install and enable custom bots and tabs. 

To learn more, read [Admin settings for apps in Teams](admin-settings.md). 



Custom cloud storage
--------------------

Cloud storage options in Teams currently include Box, Dropbox, Google Drive, and ShareFile. Users can upload and share files from cloud storage services in Teams channels and chats. Turn on the switch for the cloud storage providers that your organization wants to use. 

![Screenshot of the Custom cloud storage section.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image7.png)

User settings by license
------------------------

In **User settings by license**, you can turn on or turn off options in Teams and channels, Calls and meetings, and Messaging.

Teams and channels
------------------

A team is designed to bring together a group of people who work closely to get things done. Teams can be dynamic for project-based work (for example, launching a product or creating a digital war room). Or, teams can be ongoing, to reflect the internal structure of your organization.

The maximum number of teams that an Office 365 tenant can have is currently 500,000. A global admin can create an unlimited number of teams. A user can create 250 teams. A team owner can add 2500 members to a team.

As an admin, you can manage team owners and members by using the Groups dashboard in the Office 365 admin center. To learn more, click **Use the Groups dashboard in the Office 365 admin center to manage teams** under **Teams and channels**.

You can control which users in your organization can create teams in Teams. The same creation settings defined by Office 365 groups apply to Teams. For more information about managing Office 365 groups, see [Create Office 365 groups](https://support.office.com/en-us/article/Create-Office-365-groups-74a1ef8b-3844-4d08-9980-9f8f7a36000f) and [Control who can create Office 365 Groups](https://support.office.com/en-us/article/Control-who-can-create-Office-365-Groups-4c46c8cb-17d0-44b5-9776-005fced8e618).

> [!NOTE]
> You can't create teams from the Groups dashboard. Teams must be created by using the Teams desktop client or web app.

By default, every user can create a team or group. Choose **Teams** on the left side in the Teams client (desktop client or web app), then choose **Create and join team** at the bottom of the client, below the team list.

![Screenshot of the User settings by license section.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image8.png)

Channels are subcategories of teams. Anyone on the team can add a channel and participate in the conversations in a channel. You might create a channel for an activity or for a department. Conversations, files, and wikis are specific to each channel, but all members of the team can see them.

## Calls and meetings

Configure the following **Calls and meetings** settings for your organization:

![Screenshot of the Calls and meetings section.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image9.png)

The maximum number of people in a meeting is 80. There can be 20 members in a private chat, including the user who created the chat.

-   **Allow scheduling for private meetings**: When turned on, users can schedule private meetings that are not listed in any channel.

-   **Allow ad-hoc channel meetup**

-   **Allow scheduling for channel meetings**: When turned on, users can schedule a meeting for a channel that all channel members can easily join with a single click.

-   **Allow videos in meetings:** Specifies whether the use of video is allowed in meetings.

-   **Allow screen sharing in meetings**: Specifies whether screen sharing is allowed in meetings.

-   **Allow private calling**: When turned on, users can make private calls.

## Messaging 

The Messaging section lets you configure the following settings for your organization:

![Screenshot of the Messaging section.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image10.png)

-   **Enable Giphy so users can add gifs to conversations**: When turned on, users can use animated pictures within the conversations.

-   **Content Rating**: When animated images are turned on, content rating can be applied to restrict the type of animated images that can be displayed in conversations. Available content rating options are:

    -   No restriction
    -   Moderate (the default value)
    -   Strict

-   **Enable memes that users can edit and add to conversations**: When turned on, users can use internet memes to make humorous posts.

-   **Enable stickers that users can edit and add to conversations**: When turned on, users can post images with editable text to get channel members attention.

-   **Allow owners to delete all messages**: When turned on, channel owners can remove all messages in a channel.

-   **Allow users to edit their own messages**: When turned on, users can edit their own messages.

-   **Allow users to delete their own messages**: When turned on, users can delete their own messages.

-   **Allow users to chat privately**: When turned on, users can engage in private chats that are visible only to the people in the chat, instead of everyone on the team.


| |  |  |
|---------|---------|---------|
|![Decision Point icon.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image11.png)     |Decision Point         |What settings for Microsoft Teams will your organization enable?         |
|![Next steps icon.](media/Enable_Microsoft_Teams_features_in_your_Office_365_organization_image12.png)     |Next Steps        |Document these decisions in the table in [Assign roles and permissions in Microsoft Teams](assign-roles-permissions.md).         |

