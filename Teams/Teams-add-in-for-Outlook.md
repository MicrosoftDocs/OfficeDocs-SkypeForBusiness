---
title: Use the Microsoft Teams Meeting add-in in Outlook
author: LanaChin
ms.author: v-lanac
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: sonua
localization_priority: Normal
search.appverid: MET150
description: Microsoft Teams installs an add-in into Outlook that lets users schedule a Teams meeting from Outlook.
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
---

Use the Teams Meeting add-in in Outlook
=======================================

The Teams Meeting add-in lets users schedule a Teams meeting from Outlook. The add-in is available for Outlook on Windows, Mac, web, and mobile.

## Teams Meeting add-in in Outlook for Windows

The Teams Meeting add-in is automatically installed for users who have Microsoft Teams and either Office 2013, Office 2016, or Office 2019 installed on their Windows PC. Users will see the Teams Meeting add-in on the Outlook Calendar ribbon.

![Screenshot of Teams Meeting add-in on Outlook ribbon](media/Teams-add-in-for-Outlook.png)

> [!NOTE]
> - There is **no direct URL** that links to the Teams add-in.
> - There are additional considerations if your organization runs both Teams and Skype for Business. Under some circumstances, the Teams add-in is not available in Outlook. See [Upgrade from Skype for Business to Teams](https://docs.microsoft.com/microsoftteams/upgrade-to-teams-on-prem-overview#meetings) for details.
> - User permissions to execute the Regsvr32.exe file is a minimum requirement for the Teams Meeting add-in to be installed on the computer.
> - If users do not see the Teams Meeting add-in, instruct them to close Outlook and Teams, then restart the Teams client first, then sign in to Teams, and then restart the Outlook client, in that specific order.
> - If you are using an Office Outlook installation from the Microsoft Store, the Teams Meeting add-in isn't supported. Users who require this add-in are advised to install Click-to-Run version of Office, as outlined in [Office on Windows 10 in S mode](https://support.office.com/article/faq-office-on-windows-10-in-s-mode-717193b5-ff9f-4388-84c0-277ddf07fe3f) article.

## Teams Meeting add-in in Outlook for Mac

The Teams Meeting button in Outlook for Mac will appear in the Outlook for Mac ribbon if Outlook is running production build 16.24.414.0 and later and is activated with a Microsoft 365 or Office 365 client subscription.​

The meeting coordinates (the Teams join link and dial-in numbers) will be added to the meeting invite after the user clicks **Send**.  

## Teams Meeting add-in in Outlook Web App

The Teams Meetings button in Outlook Web App will appear as part of new event creation if the user is on an early version of the new Outlook on the web. See the [Outlook Blog](https://techcommunity.microsoft.com/t5/Outlook-Blog/Designed-to-be-fast-The-Outlook-on-the-web-user-experience-gets/ba-p/234909?utm_source=t.co&utm_medium=referral) to learn about how users can try the early version of the new Outlook on the web.

![Screenshot of Teams Meeting add-in in Outlook Web App](media/teams-meeting-add-in-web.png)

The meeting coordinates (the Teams join link and dial-in numbers) will be added to the meeting invite after the user clicks **Send**.  

## Teams Meeting add-in in Outlook mobile (iOS and Android)

The Teams Meeting button shows up in latest builds of the Outlook iOS and Android app.

![Screenshot of Teams Meeting add-in in Outlook mobile](media/teams-meeting-add-in-mobile.png)

The meeting coordinates (the Teams join link and dial-in numbers) will be added to the meeting invite after the user clicks **Send**.  

## Teams Meeting add-in and FindTime for Outlook

FindTime is an add-in for Outlook that helps users reach consensus on a meeting time across companies. Once the meeting invitees have provided their preferred times, FindTime sends out the meeting invite on the user's behalf. If the **Online meeting** option is selected in FindTime, FindTime will schedule a Skype for Business or Microsoft Teams meeting. (FindTime will use whichever has been set by your organization as the default online meeting channel.)

> [!NOTE]  
> If you saved a Skype for Business setting in your [Findtime dashboard](https://findtime.microsoft.com/UserDashboard), FindTime will use that instead of Microsoft Teams. If you want to use Microsoft Teams, delete the Skype for Business setting in your dashboard.

For more information, see [Schedule meetings with FindTime](https://support.office.com/article/scheduling-meetings-with-findtime-4dc806ed-fde3-4ea7-8c5e-b5d1fddab4a6).

## Authentication requirements

The Teams Meeting add-in requires users to sign in to Teams using Modern Authentication. If users do not use this method to sign in, they'll still be able to use the Teams client, but will be unable to schedule Teams online meetings using the Outlook add-in. You can fix this by doing one of the following:

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

When users who are in Island mode schedule a meeting in Outlook, they typically expect to be able to choose whether to schedule a Skype for Business or a Teams meeting. In Outlook on the web, Outlook Windows, and Outlook Mac, users see both Skype for Business and Teams add-ins when in Islands mode by default. You can configure a Teams meeting policy setting to control whether users in Islands mode can only use the Teams Meeting add-in or both the Teams Meeting and Skype for Business Meeting add-ins.

Due to certain limitations in the initial release, Outlook mobile can only support creating Skype for Business **or** Teams meetings. See the following table for details.

| Coexistence mode in the Teams admin center | Default meetings provider in Outlook mobile |
| --------------------------------------|---------------------------------------------|
| Islands | Skype for Business |
| Skype for Business only | Skype for Business |
| Skype for Business with Teams collaboration | Skype for Business |
| Skype for Business with Teams collaboration and meetings | Teams |
| Teams only | Teams |

### Set whether users in Islands mode can only use the Teams Meeting add-in or both the Teams Meeting and Skype for Business Meeting add-ins

As an admin, you can configure a Teams meeting policy setting to control which Outlook meeting add-in is used for *users who are in Islands mode*. You can specify whether users can only use the Teams Meeting add-in or both the Teams Meeting and Skype for Business Meeting add-ins to schedule meetings in Outlook.

You can only apply this policy to users who are in Islands mode and have the **AllowOutlookAddIn** parameter set to **True** in their Teams meeting policy. For steps on how to set this policy, see [set the meeting provider for users in Islands mode](meeting-policies-in-teams.md#meeting-policy-settings---meeting-provider-for-islands-mode).

## Other considerations

The Teams Meeting add-in is still building functionality, so be aware of the following:

- The Teams Meeting add-in requires an Exchange mailbox for the primary user scheduling the meeting. Ensure that you have at least one Exchange mailbox configured in your Outlook profile and use it to schedule Teams meetings with the add-in. For Exchange requirements, see [How Exchange and Teams interact](https://docs.microsoft.com/microsoftteams/exchange-teams-interact).
- The add-in is for scheduled meetings with specific participants, not for meetings in a channel. Channel meetings must be scheduled from within Teams.
- The add-in will not work if an Authentication Proxy is in the network path of the user's PC and Teams Services.
- Users can't schedule live events from within Outlook. Go to Teams to schedule live events. For more information, see [What are Microsoft Teams live events?](teams-live-events/what-are-teams-live-events.md).

Learn more about [meetings and calling in Microsoft Teams](https://support.office.com/article/Meetings-and-calls-d92432d5-dd0f-4d17-8f69-06096b6b48a8).

## Troubleshooting

Use the following steps to troubleshoot issues with the Teams Meeting add-in.

### Teams Meeting add-in in Outlook for Windows does not show

If you cannot get the Teams Meeting add-in for Outlook to install, try these troubleshooting steps.

[Download](https://aka.ms/SaRA-TeamsAddInScenario) and run the [Microsoft Support Recovery Assistant](https://aka.ms/SaRA_Home) to perform automated troubleshooting steps and fixes.

Alternatively, perform the following steps manually:

- Windows 7 users must install the [Update for Universal C Runtime in Windows](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows) for the Teams Meeting add-in to work.
- Check that the user has a Teams Upgrade policy which enables scheduling meetings in Teams. See [Upgrade from Skype for Business to Teams](https://docs.microsoft.com/microsoftteams/upgrade-to-teams-on-prem-overview#meetings) for more details.
- Check that the user has a Teams Meeting policy that permits the Outlook Add-in. See [Manage meeting policies in Teams](https://docs.microsoft.com/microsoftteams/meeting-policies-in-teams#allow-the-outlook-add-in) for more details.
- Ensure the user has the Teams desktop client installed. The meeting add-in will not be installed when only using the Teams web client.
- Ensure the user has Outlook 2013 or later installed.
- Make sure the user has permission to execute regsvr32.exe.
- Ensure that all available updates for Outlook desktop client have been applied.
- Follow these steps:
  - Restart the Teams desktop client.
  - Sign out and then sign back in to the Teams desktop client.
  - Restart the Outlook desktop client. (Make sure Outlook isn't running in admin mode.)

If you still don't see the add-in, make sure that it isn't disabled in Outlook.

- In Outlook, choose **File** and then **Options**.
- Select the **Add-ins** tab of **Outlook Options** dialog box.
- Confirm that **Microsoft Teams Meeting Add-in for Microsoft Office** is listed in the **Active Application Add-ins** list
- If the Teams Meeting Add-in is listed in the **Disabled Application Add-ins** list, select **COM Add-ins** in **Manage** and then select **Go…**
- Set the checkbox next to **Microsoft Teams Meeting Add-in for Microsoft Office**.
- Choose **OK** on all dialog boxes and restart Outlook.

For general guidance about how to manage add-ins, see [View, manage, and install add-ins in Office programs](https://support.office.com/article/View-manage-and-install-add-ins-in-Office-programs-16278816-1948-4028-91E5-76DCA5380F8D).

If the add-in still does not show, use the following steps to verify the registry settings.

> [!NOTE]
> Incorrectly editing the registry may severely damage your system. Before making changes to the registry, you should back up any valued data on the computer.
- Launch RegEdit.exe
- Navigate to HKEY_CURRENT_USER\Software\Microsoft\Office\Outlook\Addins
- Verify TeamsAddin.FastConnect exists.
- Within TeamsAddin.FastConnect, verify LoadBehavior exists and is set to 3.
  - If LoadBehavior has a value other than 3, change it to 3 and restart Outlook.

### Delegate scheduling does not work

If your administrator has configured Microsoft Exchange to [control access to Exchange Web Server (EWS)](https://docs.microsoft.com/exchange/client-developer/exchange-web-services/how-to-control-access-to-ews-in-exchange), a delegate won't be able to schedule a Teams meeting on behalf of the boss. The solution for this configuration is under development and will be released in the future. As a workaround, your administrator can add the following string to the EWS Allow List: "*SchedulingService*". 


## Related topics

[Teams Troubleshooting](https://docs.microsoft.com/MicrosoftTeams/troubleshoot/teams)
