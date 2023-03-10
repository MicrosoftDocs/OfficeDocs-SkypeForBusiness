---
title:  Microsoft new Teams (preview)
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
description: Learn about the public preview of the new Microsoft Teams. Try out new features and provide feedback.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# The new Microsoft Teams desktop client

The new Microsoft Teams, the latest version of the Microsoft Teams desktop client is now available. The new Teams has been rebuilt from the ground up, and you can now preview the next evolution of Microsoft Teams. 

- Better performance—the goal is 2x faster than "classic Teams"
- Lower CPU, memory usage, and disk space consumption
- Your device will consume less battery
- More reliable all-around​​​​​​​
- Multi-account support - letting you collaborate seamlessly across accounts and tenants  

|What|Description|
|:-----|:-----|
|![Get started](/office/media/icons/deploy-teams-blue.png)|[How to roll out new Teams](#how-to-roll-out-new-teams)|
|![Features](/office/media/icons/whats-new-megaphone-teams.png)|[What's available in new Teams](#whats-available-in-the-new-teams)|



The new Teams is still in development and currently does not have the full feature set of classic Teams. New Teams will not be available to the following platforms or customer segments during the public preview phase.

|Platforms|Customer segments|
|:-----|:-----|
|- Mac</br>- VDI</br>- Web|- Education</br>- Special cloud (GCC High, DoD, Gallatin, Air-gapped)</br>- Consumer</br>- desktop running Windows 10 version 10.0.19041 or earlier|

Stay on classic Teams for now if:

- You are using a custom line of business apps or apps from the AppStore
- You are using Virtual Desktop Infrastructure (VDI)
- You use a Mac or Web browser for Teams

It is easy to toggle back and forth between using the classic and new Teams, so you might choose to take advantage of the new Teams performance enhancements on some days and switch back to classic when more advanced features are required.



>[!Note]
>This release is strictly a new desktop client. No changes have been made in how the service works and the backend remains the same. There is no new mobile app (iOS or Android) as the new Teams is focused on desktop, web, and VDI.


## Before you begin

The new Teams is still in development and currently does not have the full feature set of classic Teams. Review the list below for feature limitations.

Stay on classic Teams for now if:

- You are using a custom line of business apps or apps from the AppStore
- You are using Virtual Desktop Infrastructure (VDI)
- You use a Mac or Web browser for Teams

It is easy to toggle back and forth between using the classic and new Teams, so you might choose to take advantage of the new Teams performance enhancements on some days and switch back to classic when more advanced features are required.

|What|Description|
|:-----|:-----|
|![Deploy](/office/media/icons/deploy-teams-blue.png)|[How to roll out new Teams](#how-to-roll-out-new-teams)|
|:::image type="content" source="(/office/media/icons/whats-new-megaphone-teams.png)" alt-text="whats in new teams":::|[What's available in new Teams](#whats-available-in-the-new-teams)


## How to roll out new Teams

As an admin, you can manage which users in your organizations see or don't see the "Try Teams (preview)" toggle to use the new Teams.
To control which users can see the toggle, use the Teams admin setting  **UseNewTeamsClient** under the **TeamsUpdateManagement** policy. 

Manage this setting in the Teams admin center or using Teams PowerShell.

# [**Teams Admin Center**](#tab/teams-admin-center)

Configure setting via Teams Admin Center

In addition to PowerShell, you can also use Teams Admin Center to manage the visibility of the toggle on a per-user basis.

1. Sign in to the [Microsoft Teams admin center](https://admin.teams.microsoft.com).
2. Select Teams>Teams Update policies from the left pane, as shown below.
3. Select Add to create a new policy or select an existing policy to open Update policy.
4. Name the update policy, add a description, and select the setting for “Use new Teams client”, as shown below

|Setting |Description|
|:-----|:-----|
|Microsoft controlled| Default. The value lets Microsoft control whether the Teams (preview) toggle switch is shown or not based on product readiness |
|User can choose| Use this value to show the new Teams toggle switch, and allow 
users to opt in to the new Teams, and switch back if they need to.|
|Not enabled| Use this value to hide the new Teams toggle switch. Users will not be able to opt in to the new Teams|

5. Once the policy is defined, you can assign it to a specific user or users groups by selecting the Policy name>Assign users>Manage users. Enter the user to add and hit apply (as shown below for Contoso sales policy.
6. Once the policy is defined, you can assign it to a specific user via under **Users> Manage users** drop-down.

If you update the policy setting in the Teams Admin Center, the new setting goes into effect within one minute. The user doesn't have to restart the app.

# [**Powershell**](#tab/powershell)

Configure the UseNewTeamsClient setting to one of the following possible values:

|Value|Description|
|:-----|:-----|
|MicrosoftChoice|Default setting. This value lets Microsoft control if the Teams (preview) toggle switch is shown based on product readiness.|
|UserChoice| This value lets the new Teams toggle switch display to all users. Users can choose to opt in or out.|
|AdminDisabled|This value hides the new Teams toggle switch from view. Users won't be able to opt in to the new Teams.|Here are the steps needed to configure this setting in PowerShell.

1. Import the latest Teams PowerShell cmdlets (require version 4.9.1 or greater) by following [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams) instructions. Direct link: [PowerShell Gallery Microsoft Teams 4.9.1](https://www.powershellgallery.com/packages/MicrosoftTeams/4.9.1).
2. Connect to an admin account using this command:

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
>This new policy assignment method should take effect within one minute. Users do not need to restart the app.

---

### How to uninstall the new Teams client

Any user who was using the new Teams before the policy was implemented can manually opt out by using the new Teams toggle. 

After they opt out, the toggle won't appear when they relaunch Teams. To prevent users from using this client and want to uninstall the client, users can manually uninstall it from settings.

### Remove new Teams for all users

To remove the new Teams from all users' computers, use the following PowerShell command:

```powershell

Remove-AppxPackage 
```

PowerShell cmdlet to remove new Teams from all users on all computers:

Get-AppxPackage *MSTeams* -AllUsers |Remove-AppxPackage -AllUsers
For an individual user without administrator privilege, use this command:
Get-AppxPackage *MSTeams*|Remove-AppxPackag


## What's available in the new Teams

Teams (preview) gives you:

- Activity feed (except app notifications)
- [Chat](#chat)
- [Teams and channels (limited)](#teams-and-channels)
- [Calendar and meetings (limited)](#calendar-and-meetings)
- Teams-to-Teams calls
- Files
- [Apps](#apps)
- [Support for multiple work (or school) accounts (exclusively available in New Teams!)](#multi-tenant-multi-account)


### Chat

Most chat features are available, including GIFs and emojis. There are just a few limitations.

|Classic|New|Limitations|
|:-----|:-----|:-----|
|:::image type="content" source="media/purple-square.png" alt-text="full featured":::Full featured|:::image type="content" source="media/orange-square.png" alt-text="available  ":::Available with limitations|- Can't add tabs to chat</br></br>- Can't reorder pinned chats</br></br>- Immersive reader not available|

### Teams and channels

New Teams features a brand-new channel experience that hasn’t been released in classic Teams yet. You’ll find the latest conversations at the top of your feed. You can also pop out channel conversations just like you do with chats, and drill down to individual channel conversations. 

When you need some of the more advanced functionality, switch back to classic Teams.

Here are the limitations:

|Classic|New|Limitations|
|:-----|:-----|:-----|
|:::image type="content" source="media/purple-square.png" alt-text="full featured":::Full featured|:::image type="content" source="media/orange-square.png" alt-text="available ":::Available with limitations|- You can’t add a new member to a team.</br></br>- You can’t create, edit, delete, or archive a team. You won’t be notified when someone requests to join a team.</br></br>- You won’t see team renewal notifications.</br></br>- There isn’t the option to share a link to a team.</br></br>- Offline support isn’t available yet.</br></br>- You can’t add a new member to a private or shared channel.</br></br>- You can’t create, edit, or delete a channel.</br></br>"Post in multiple channels" isn't supported.</br></br>- You can’t invite an entire team to a shared channel.</br></br>- You can't manage Tabs.</br></br>- There isn’t the option to share a link to a channel.</br></br>- Ctrl+F isn’t yet available for searching within channels.</br></br>- Channel notification settings aren’t editable yet.</br></br>- The channel info pane isn't available.</br></br>- When hosting a meeting in a channel, a banner won't appear at the top of the channel|



### Calendar and meetings

You can schedule and join meetings in the new Teams with basic functionality and experience the better performance of the new Teams. If you need more advanced meeting features, use classic Teams for the time being. ​​​​​​​

On days when you have many meetings, you may want to use classic Teams to make sure you get meeting-start notifications.

|Classic|New|Limitations|
|:-----|:-----|:-----|
|:::image type="content" source="media/purple-square.png" alt-text="full featured":::Full featured|:::image type="content" source="media/orange-square.png" alt-text="available  ":::Available with limitations|- When a meeting starts, you won’t receive a notification with an option to join</br></br>- Breakout rooms not supported</br></br>- Presenter toolbar not supported</br></br>- Whiteboard not supported</br></br>-Live Events not supported</br></br>- “Present in Teams” feature in PowerPoint not available</br></br>- As a meeting organizer, you can enable Q&A from meeting options; however, attendees using new Teams can only post questions or responses if they switch back to classic Teams.</br></br>- New app installation isn’t supported. However, some limited app capabilities are available. Example: As the meeting organizer, you can't add the Polls app or create a new poll from new Teams. However, any attendees using new Teams can participate in polls you launch from classic Teams. </br></br>- When using the “Share screen” option to share content, toast notifications will still pop up, even if you have notifications muted.</br></br>- Some meeting details won’t show up in new Teams.</br></br>- When you close a meeting window by selecting "X" in the upper-right corner, you won’t receive a prompt saying, “Are you sure you want to leave?”</br></br>- For channel meetings, you won’t see a banner at the top of a channel when a meeting hosted there's active.|


### Calls

You can make Teams-to-Teams internet-based calls through Chat.  However, traditional phone service (calls to and from telephone numbers) isn't available. This includes emergency calls (911 in North America, or 112 in India and parts of Europe.)

The Calls icon isn't visible on the left rail and the dial pad isn't available. Missed calls will show up in your Activity feed, but the callback button won't be available if the call is from a telephone number.  Live captions and transcriptions are available for Teams-to-Teams calls.

**Known issue**: Increased power usage during calls may cause CPU throttling and negatively impact performance.


|Classic|New|Limitations|
|:-----|:-----|:-----|
|:::image type="content" source="media/purple-square.png" alt-text="full featured":::Full featured|:::image type="content" source="media/orange-square.png" alt-text="available  ":::Available with limitations||


### Apps

The following apps are available in the new Teams. If you need to use an app that’s not on this list, switch back to classic Teams. You are using a custom line of business apps or apps from the AppStore stay on classic Teams until these are fully supported.

>[!Note]
>You must install the apps in classic Teams first.

|Microsoft Viva|Microsoft 365|Miscellaneous|
|:-----|:-----|:-----|
|Viva Connections</br>Viva Engage</br>Viva Goals</br>Viva Insights</br>Viva Learning|Excel</br>OneNote</br>PowerPoint</br>Power Apps</br>Word|Approvals</br>Tasks by Planner and To Do</br>Math</br>Shifts</br>Shifts (Intl)</br>Wiki|


|Classic|New|Limitations|
|:-----|:-----|:-----|
|:::image type="content" source="media/purple-square.png" alt-text="full featured":::Full featured|:::image type="content" source="media/orange-square.png" alt-text="available  ":::Available with limitations|- No notifications from any apps in your Activity feed.</br></br>- “Pop out app” isn't yet available.</br></br>- You can only pin an app in classic Teams. Once done, this will reflect in New Teams as well, but it may take up to 24 hours.</br></br>- Apps won't display content in meeting window. For apps like Polls, use meeting chat to respond to poll.</br></br>- You may notice some small differences in the user interface (UI).</br></br>- The App Store is currently not available.|


### Multi-Tenant Multi-Account

|Classic|New|Highlights|
|:-----|:-----|:-----|
|:::image type="content" source="media/orange-square.png" alt-text=" not available ":::Not available|:::image type="content" source="media/purple-square.png" alt-text="full featured":::Available only in new Teams|- Multi-tenant Multi-account (MTMA) support</br></br>- Receive real-time notifications from all the accounts you’re signed into</br></br>- Participate in chats, meetings, and calls across multiple accounts and organizations. Switch accounts without having to drop from a call or meeting </br></br>- Set your presence and status for each account and organization individually</br></br>- Intuitive visual indicators help differentiate between your different accounts and organizations, so you’re aware of which one you’re working in|
