---
title:  Microsoft Teams 2.1 preview
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: dansteve
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about the public preview of the new Microsoft Teams 2.1. Try out new features and provide feedback.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Microsoft Teams 2.1 Public Preview

## Manage new Teams rollout via Teams Policy

As an admin, you can manage which users in your organizations see or do not see the ***Try Teams (preview)*** toggle to use the Microsoft Teams (preview) client.

>[!Important]
>Note: Microsoft Teams (preview) is the new version of Microsoft Teams desktop client and currently available for Windows non-EDU desktop users only.
>
>Teams (preview) is currently not available for EDU, VDI, PSTN enabled, Government cloud (DoD, GCC, GCC high), Mac, Web, Consumer, and any desktop running Windows 10 version 10.0.19041 or earlier.
>
>Admins can use the policy to override and enable the toggle for PSTN users only.

This can be controlled on a per-user basis and Teams’ admin setting **UseNewTeamsClient** under 
"TeamsUpdateManagement" policy can be used to control availability of the toggle for users in your organization.

There are two methods to configure UseNewTeamsClient via Teams Powershell, via Teams admin center.

Configure the UseNewTeamsClient setting to one of the following possible values:

|Value|Description|
|:-----|:-----|
|MicrosoftChoice|Default setting. This value lets Microsoft control if the Teams (preview) toggle switch is shown based on product readiness.|
|UserChoice| This value lets the Teams (preview) toggle switch display to all users. Users can choose to opt in or out.|
|AdminDisabled|This value hides the Teams (preview) toggle switch from view. Users will not be able to opt-in to the new Teams.|

## Control setting via Teams PowerShell

Here are the steps needed to configure this setting:

Control setting via Teams PowerShell
Here are the steps needed to configure this setting:
1. Import the latest Teams PowerShell cmdlets (require version 4.9.1 or greater) by following [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams) instructions. Direct link: [PowerShell Gallery MicrosoftTeams 4.9.1](https://www.powershellgallery.com/packages/MicrosoftTeams/4.9.1).
2. Connect using an admin account using this command:

```powershell
Connect-MicrosoftTeams
```

3. Once connected and logged in via PowerShell, you can explore the list of related commands:
Enter *-CsTeamsUpdateManagementPolicy and tab through the commands (tab key).

4. Use the following commands to change the existing Update Management policy to opt in the assigned users to ensure that they have the option to try the new Teams:

```powershell
Set-CsTeamsUpdateManagementPolicy -identity <new_policy_name> -UseNewTeamsClient 
```

UserChoice
Example:
```powershell 
Set-CsTeamsUpdateManagementPolicy -identity MySetting -UseNewTeamsClient UserChoice
```

>[!Note]
>This method (existing policy modification) does not take effect immediately; allow up to 24 hours for the change to propagate to users. Users do not need to restart the app, but specifically for opt-in, they will need one restart following a fresh install to see the toggle.

5. Use the following commands to deploy a new policy to opt-out a specific user from seeing the toggle:

```powershell

New-CsTeamsUpdateManagementPolicy -identity <new_policy_name> -UseNewTeamsClient AdminDisabled

Grant-CsTeamsUpdateManagementPolicy -identity <user> -PolicyName <new_policy_name>

```

**Example:**

```powershell
New-CsTeamsUpdateManagementPolicy -identity MySetting -UseNewTeamsClient AdminDisabled
Grant-CsTeamsUpdateManagementPolicy -identity admin@contoso.org -PolicyName MySetting
```

>[!Note]
>This new policy assignmentmethod should take effect within one minute. Users do not need to restart the app.


## Control setting via Teams Admin Center

In addition to PowerShell, you can also use Teams Admin Center to manage the visibility of the toggle on a per-user basis.

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com).
2. Select Teams>Teams Update policies from the left pane, as shown below.
3. Select Add to create a new policy or select an existing policy to open Update policy.
4. Name the update policy, add a description, and select the setting for “Use new Teams client”, as shown below

|Setting |Description|
|:-----|:-----|
|Microsoft controlled| Default. This is the automatic default that allows Microsoft to control whether the Teams (preview) toggle switch is shown or not based on product readiness |
|User can choose| Use this value to show the Teams (preview) toggle switch, and allow 
users to opt-in to the new Teams, and switch back if they need to.|
|Not enabled| Use this value to hide the Teams (preview) toggle switch. Users will 
not be able to opt-in to the new Teams|

5. Once the policy is defined, you can assign it to a specific user or users groups by selecting the Policy name>Assign users>Manage users. Enter the user to add and hit apply (as shown below for Contoso sales policy.

6. Once the policy is defined, you can also assign it to a specific user via Manage users under Users> Manage users drop-down.

Updating the policy setting using this way goes into effect within one minute. The user does not have to restart the app. 


## How to uninstall the new Teams client

Users who were using Teams preview before the policy was implemented can manually opt-out by using the Teams (preview) toggle. 

After they opt out, the toggle will not appear when they relaunch Teams. To prevent users from using this client and want to uninstall the client, users can just manually uninstall it from settings as per the below screenshot

### Remove Teams 2.1 for all users

To remove the Teams 2.1 from all users computers, use the following PowerShell command:

```powershell

Remove-AppxPackage 
```

Powershell cmdlet to remove Teams 2.x from all users on the machine:

Get-AppxPackage *MSTeams* -AllUsers |Remove-AppxPackage -AllUsers
For an individual user without administrator privilege, use this command:
Get-AppxPackage *MSTeams*|Remove-AppxPackag


## Before you begin

PSTN:   If your work includes any of the below activities, use Teams v1 until traditional phone services are available in Teams Preview:
•	Call Queues
•	Auto Attendants
•	Critical Functions: Data Centers - Security Operations Center (SOC)/Security Operations Center (SOC), Site Services, Logistics
•	CRITSIT support to external customers/ partners
•	Customer-facing rolesCalls
You can make Teams-to-Teams internet-based calls through Chat.

Traditional phone service (calls to and from telephone numbers) is not available. This includes emergency calls (i.e. 911 in North America, or 112 in India and parts of Europe.)

The Calls icon is not visible on the left rail and the dial pad is not available. Missed calls will show up in your Activity feed, but the callback button will not be available if the call is from a telephone number.  
Live captions and transcriptions are available for Teams-to-Teams calls.
Known issues

Increased power usage during calls may cause CPU throttling and negatively impact performance.
Please be aware:
Calls, to and from phone numbers, including emergency calls, are NOT available on Teams Preview.  



## What's available in 2.1

At a high level, Teams (preview) gives you:

- Activity feed (except app notifications)
- Chat
- Teams and channels (limited)
- Calendar and meetings (limited)
- Teams-to-Teams calls
- Files
- Apps (limited), including Microsoft Viva
- Support for multiple work (or school) accounts (exclusively available in New Teams!)


**What is still pending:**

- Calls to and from telephone numbers, also known as the public switched telephone network (PSTN)
- When a meeting starts, you won’t receive a notification with an option to join
- Some advanced meeting features, like breakout rooms
- Slash commands (For example " /chat")
- You can’t update your notification settings from within the app—you’ll be directed to Windows settings
- Support for Mac and web browsers


## Chat

|Teams 1.0 |Teams 2.1|Limitations|
|:-----|:-----|:-----|:-----|
| ||Can't add tabs to chat|
||Can't reorder pinned chats|
||Immersive reader not available

## Teams and channels

|Teams 1.0 |Teams 2.1|Limitations|
|:-----|:-----|:-----|:-----|
|:::image type="icon" source="media/green-checkmark.png" border="false":::|:::image type="icon" source="media/orange-checkmark-teams.png" border="false":::|- You can’t add a new member to a team.</br>- You can’t create, edit, delete, or archive a team.</br>- You won’t be notified when someone requests to join a team.</br>- You won’t see team renewal notifications.</br>- There isn’t the option to share a link to a team.</br>- Offline support isn’t available yet.</br>- You can’t add a new member to a private or shared channel.</br>- You can’t create, edit, or delete a channel.</br>- "Post in multiple channels" is not supported.|- You can’t invite an entire team to a shared channel.</br>- You can't manage Tabs. </br>- There isn’t the option to share a link to a channel.</br>- Ctrl+F isn’t yet available for searching within channels.</br>- Channel notification settings aren’t editable yet.</br>- The channel info pane isn't available.</br>- When a meeting is hosted in a channel, a banner won't appear at the top of the channel|


## Calendar and meetings

|Teams 1.0 |Teams 2.1|Limitations|
|:-----|:-----|:-----|:-----|
|:::image type="icon" source="media/green-checkmark.png" border="false":::|:::image type="icon" source="media/orange-checkmark-teams.png" border="false":::|- When a meeting starts, you won’t receive a notification with an option to join</br>- Breakout rooms</br>- Presenter toolbar</br>Whiteboard</br>Live Events</br>- “Present in Teams” feature in PowerPoint</br>- As a meeting organizer, you can enable Q&A from meeting options; however, attendees using New Teams won't be able to post questions or responses unless they switch to Classic Teams.</br>New app installation isn’t supported. However, some limited app capabilities are available.For example: As the meeting organizer, you cannot add the Polls app or create a new poll from New Teams. However, any attendees using New Teams will be able to participate in polls that you launch from Classic Teams. </br>Meeting start notification won't appear when a meeting starts with an option to join</br>- When using the “Share screen” option to share content, toast notifications will still pop up, even if you have notifications muted.</br>- Some meeting details won’t show up in New Teams.</br>- When you close a meeting window by selecting "X" in the upper-right corner, you won’t receive a prompt saying, “Are you sure you want to leave?”</br>- For channel meetings, you won’t see a banner at the top of a channel when a meeting hosted there is active.|


## Calls

|Teams 1.0 |Teams 2.1|Limitations|
|:-----|:-----|:-----|:-----|
|:::image type="icon" source="media/green-checkmark.png" border="false":::|:::image type="icon" source="media/green-checkmark.png" border="false":::|PSTN NOT SUPPORTED YET|


## Apps, including Microsoft Viva


|Teams 1.0 |Teams 2.1|Limitations|
|:-----|:-----|:-----|:-----|
|:::image type="icon" source="media/green-checkmark.png" border="false":::|:::image type="icon" source="media/orange-checkmark-teams.png" border="false":::|-You won't get notifications from any apps in your Activity feed.</br>-“Pop out app” is not yet available.</br>- You can only pin an app in Classic Teams. Once done, this will reflect in New Teams as well, but it may take up to 24 hours.</br>- Apps will not display content in meeting window. For apps like Polls please use meeting chat to respond to poll.</br>- You may notice some small differences in the user interface (UI).</br>- The App Store is currently not available.</br>


## Multi-Tenant Multi-Account

|Teams 1.0 |Teams 2.1|Only in 2.1|
|:-----|:-----|:-----|:-----|
||:::image type="icon" source="media/green-checkmark.png" border="false":::|- Multi-Tenant Multi-Account (MTMA) support|Receive real-time notifications from all the accounts you’re signed into.</br>- Participate in chats, meetings, and calls across multiple accounts and organizations. There’s no need to drop from a call or meeting to switch accounts—you can do it seamlessly.</br>- Set your presence and status for each account and organization individually.</br>- Intuitive visual indicators help differentiate between your different accounts and organizations, so you’re aware of which one you’re working in.|
