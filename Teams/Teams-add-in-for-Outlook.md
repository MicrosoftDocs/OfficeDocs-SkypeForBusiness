---
title: Use the Microsoft Teams Meeting add-in in Outlook
author: ChuckEdmonson
ms.author: chucked
manager: serdars
audience: Admin
ms.date: 06/25/2019
ms.topic: article
ms.service: msteams
ms.reviewer: sonua
localization_priority: Normal
search.appverid: MET150
description: Microsoft Teams installs an add-in into Outlook that lets users schedule a Teams meeting from Outlook.
ms.custom:
- NewAdminCenter_Update
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

Use the Teams Meeting add-in in Outlook
=======================================

The Teams Meeting add-in lets users schedule a Teams meeting from Outlook. The add-in is available for Outlook on Windows, Mac, web, and mobile.

## Teams Meeting add-in in Outlook for Windows

The Teams Meeting add-in is automatically installed for users who have Microsoft Teams and either Office 2010, Office 2013 or Office 2016 installed on their Windows PC. Users will see the Teams Meeting add-in on the Outlook Calendar ribbon.

![Screenshot of Teams Meeting add-in on Outlook ribbon](media/Teams-add-in-for-Outlook.png)

> [!NOTE]
> - If users do not see the Teams Meeting add-in, instruct them to close Outlook and Teams, then restart the Teams client first, then sign in to Teams, and then restart the Outlook client, in that specific order.
> - Windows 7 users must install the [Update for Universal C Runtime in Windows](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows) in Windows for the Teams Meeting add-in to work.

## Teams Meeting add-in in Outlook for Mac

The Teams Meeting button in Outlook for Mac will appear in the Outlook for Mac ribbon if Outlook is running Production Build 16.24.414.0 and later.​

The meeting coordinates (the Teams join link and dial-in numbers) will be added to the meeting invite after the user clicks **Send**.  

## Teams Meeting add-in in Outlook Web App

The Teams Meetings button in Outlook Web App will appear as part of new event creation if the user is on an early version of the new Outlook on the web. See the [Outlook Blog](https://techcommunity.microsoft.com/t5/Outlook-Blog/Designed-to-be-fast-The-Outlook-on-the-web-user-experience-gets/ba-p/234909?utm_source=t.co&utm_medium=referral) to learn about how users can try the early version of the new Outlook on the web.

![Screenshot of Teams Meeting add-in in Outlook Web App](media/teams-meeting-add-in-web.png)

The meeting coordinates (the Teams join link and dial-in numbers) will be added to the meeting invite after the user clicks **Send**.  

## Teams Meeting add-in in Outlook mobile (iOS and Android)

The Teams Meeting button shows up in latest builds of the Outlook iOS and Android app.

![Screenshot of Teams Meeting add-in in Outlook mobile](media/teams-meeting-add-in-mobile.png)

The meeting coordinates (the Teams join link and dial-in numbers) will be added to the meeting invite after the user clicks **Send**.  

## Teams Meeting add-in in and FindTime for Outlook
FindTime is an add-in for Outlook that helps users reach a consensus on a meeting time across companies. Once the meeting invitees have provided their preferred times, FindTime sends out the meeting invite on the user's behalf. If the **Online meeting** option is selected in FindTime, FindTime will schedule a Skype for Business or Microsoft Teams meeting. (FindTime will use whichever has been set by your organization as the default online meeting channel.)

> [!NOTE]  
> If you saved a Skype for Business setting in your [Findtime dashboard](https://findtime.microsoft.com/UserDashboard), FindTime will use that instead of Microsoft Teams. If you want to use Microsoft Teams, delete the Skype for Business setting in your dashboard.

See [Schedule meetings with FindTime](https://support.office.com/article/scheduling-meetings-with-findtime-4dc806ed-fde3-4ea7-8c5e-b5d1fddab4a6) for more information.

## Authentication requirements

The Teams Meeting add-in requires users to sign in to Teams using Modern Authentication. If users do not use this method to sign in, they’ll still be able to use the Teams client, but will be unable to schedule Teams online meetings using the Outlook add-in. You can fix this by doing one of the following:

- If Modern Authentication is not configured for your organization, you should configure Modern Authentication.
- If Modern Authentication is configured, but they canceled out on the dialog box, you should instruct users to sign in again using multi-factor authentication.

To learn more about how to configure authentication, see [Identity models and authentication in Microsoft Teams](identify-models-authentication.md).

## Enable private meetings

**Allow scheduling for private meetings** must be enabled in the Microsoft Teams admin center for the add-in to get deployed. In the admin center, go to **Meetings** > **Meeting Policies**, and in the **General** section, toggle **Allow scheduling private meetings** to On.)

![Screenshot of the settings in the Microsoft Teams admin center.](media/teams-add-in-for-outlook-image1.png)

The Teams client installs the correct add-in by determining if users need the 32-bit or 64-bit version.

> [!NOTE]
> Users might need to restart Outlook after an installation or upgrade of Teams to get the latest add-in.​

## Teams upgrade policy and the Teams Meeting add-in for Outlook

Customers can [choose their upgrade journey from Skype for Business to Teams](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md). Tenant admins can use the Teams co-existence mode to define this journey for their users. Tenant admins have the option to enable users to use Teams alongside Skype for Business (Islands mode). 

When users who are in Island mode schedule a meeting in Outlook, they typically expect to be able to choose whether to schedule a Skype for Business or a Teams meeting. In Outlook on the web, Outlook Windows, and Outlook Mac, users see both Skype for Business and Teams add-ins when in Islands mode. Due to certain limitations in the initial release, Outlook mobile can only support creating Skype for Business **or** Teams meetings. See the following table for details.

| Coexistence mode in the Teams admin center | Default meetings provider in Outlook mobile |
| --------------------------------------|---------------------------------------------|
| Islands | Skype for Business |
| Skype for Business only | Skype for Business |
| Skype for Business with Teams collaboration | Skype for Business |
| Skype for Business with Teams collaboration and meetings | Teams |
| Teams only | Teams |

## Other considerations

The Teams Meeting add-in is still building functionality, so be aware of the following:

- The add-in is for scheduled meetings with specific participants, not for meetings in a channel. Channel meetings must be scheduled from within Teams.
- The add-in will not work if an Authentication Proxy is in the network path of user's PC and Teams Services.
- Users can't schedule live events from within Outlook. Go to Teams to schedule live events. For more information, see [What are Microsoft Teams live events?](teams-live-events/what-are-teams-live-events.md).

## Troubleshooting

If you cannot get the Teams Meeting add-in for Outlook to install, try these troubleshooting steps.

- Ensure all available updates for Outlook desktop client have been applied.
- Restart the Teams desktop client.
- Sign out and then sign back in to the Teams desktop client.
- Restart the Outlook desktop client. (Make sure Outlook isn’t running in admin mode.)
- Make sure the logged-in user account name does not contain spaces. (This is a known issue, and will be fixed in a future update.)
- Make sure single sign-on (SSO) is enabled.

If your administrator has configured Microsoft Exchange to [control access to Exchange Web Server (EWS)](https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-control-access-to-ews-in-exchange), a delegate won't be able to schedule a Teams meeting on behalf of the boss. The solution for this configuration is under development and will be released in the future. 

For general guidance about how to disable add-ins, see [View, manage, and install add-ins in Office programs](https://support.office.com/article/View-manage-and-install-add-ins-in-Office-programs-16278816-1948-4028-91E5-76DCA5380F8D).

Learn more about [meetings and calling in Microsoft Teams](https://support.office.com/article/Meetings-and-calls-d92432d5-dd0f-4d17-8f69-06096b6b48a8).
