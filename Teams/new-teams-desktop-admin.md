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
description: Learn about the preview of the new Microsoft Teams. Try out new features and provide feedback.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# The new Microsoft Teams desktop client (preview)

In this article:
- [What is new Teams?](#what-is-new-teams)
- [How to roll out new Teams](#how-to-roll-out-new-teams)
- [Release roadmap](#release-roadmap)
- [What features are changing?](#what-features-are-changing)
- [Known issues](#known-issues)

This article describes the preview release of the new Teams desktop client. No changes have been made in how the service works, and the backend remains the same. There's no new mobile app (iOS or Android). This preview release doesn't have the complete feature set of classic Teams.

**Important:** The new Teams client **is not** available to the following platforms or customer segments during the preview phase:

|Platforms|Customer segments|
|:-----|:-----|
|Mac</br>VDI</br>Web|Special cloud (GCC High, DoD, Gallatin, Air-gapped)</br>Consumer</br>Desktop running Windows 10 version 10.0.19041 or earlier

## What is new Teams?

Reimagined from the ground up with a performance-first mindset, the new Teams client provides a faster, simpler, and more flexible experience. With new Teams, the client installs and loads faster, letting you launch the app and join meetings more quickly, giving you more time to focus on the business tasks. 

New Teams ensures more efficient use of device resources. You can lower memory and disk usage with a Teams app optimized for your device. Whether you have users on multiple accounts or tenants, the new Teams can help eliminate the silos and bring them together in one place, giving them more extensibility and scale.

## How to roll out new Teams

As an admin, you can manage which users in your organizations see or don't see the "Try the new Teams" toggle to use the new Teams.

To control which users can see the toggle, use the Teams admin setting **UseNewTeamsClient** under the **TeamsUpdateManagement** policy. 

Manage this setting in the **Teams admin center** or using **Teams PowerShell**.

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
|Not enabled| Use this value to hide the new Teams toggle switch. Users won't be able to opt in to the new Teams|

5. Once the policy is defined, you can assign it to a specific user or users groups by selecting the Policy name>Assign users>Manage users. Enter the user to add and select apply.
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

4. Use the following commands to change the existing Update Management policy to opt in the assigned users to allow them to try the new Teams:

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
Get-AppxPackage *MSTeams*|Remove-AppxPackage

## New Teams release roadmap

While all significant areas of new Teams will be available at the initial preview release, more features will be added over the next few months with support for more platforms later in this calendar year (CY).

|Area|March 2023|Q2 CY23|Q3 CY23|Q4 CY23|
|:-----|-----|:-----|:-----|:-----|
|Platform|Desktop||Mac|VDI</br>Web|
|Activity & Notifications|:::image type="content" source="media/purple-square.png" alt-text="Available":::|||||
|Chats|:::image type="content" source="media/purple-square.png" alt-text="Available":::||Add tabs to chat</br></br>Immersive reader||
|Teams|:::image type="content" source="media/purple-square.png" alt-text="Available":::||Add a new member to a team</br></br>Create, edit, delete, or archive a team</br></br>Notified  when someone requests to join a team</br></br>Team renewal notifications</br></br>Option to share a link to a team</br></br>Offline support</br></br>||
|Channels|:::image type="content" source="media/purple-square.png" alt-text="Available":::||Add a new member to a private or shared channel.</br></br>Create, edit, or delete a channel.</br></br>Post in multiple channels </br></br>Invite an entire team to a shared channel.</br></br>Manage Tabs.</br></br>Option to share a link to a channel.</br></br>Ctrl+F ability for searching within channels.</br></br>Edit channel notification settings.</br></br>Channel info pane|||
|Calendars & Meetings|:::image type="content" source="media/purple-square.png" alt-text="Available":::|Breakout rooms</br></br>Whiteboard|Presenter toolbar|Live Events</br></br>Present in Teams feature in PowerPoint</br></br>New app installation||
|Calls|:::image type="content" source="media/purple-square.png" alt-text="Available":::|||Voicemail shortcut on dial pad </br></br>Contacts and speed dial </br></br>Live captions and transcriptions  for external calls</br></br>Call merges and transfers  for external calls</br></br>Call forwarding and routing </br></br>Call queues</br></br>Reverse number lookup</br></br>Voice-enabled channels</br></br>Delegation</br></br>Shared lines</br></br>Survivable branch appliance(SBA) |||
|Apps|:::image type="content" source="media/purple-square.png" alt-text="Available":::||Notifications from apps in your Activity feed</br></br>Pop out app</br></br>Pin apps</br></br>|AppStore|
|Multi-tenant multi-account|:::image type="content" source="media/purple-square.png" alt-text="Available":::||||

## What features are changing?

As we improve the client, the experience has been improved to align with similar features. Here are the changes.

|Classic Teams|New Teams|
|:-----|:-----|:-----|
|Wiki|The Wiki app has been replaced by the Notes app|
|Ability to add third party cloud storage|Refer to the Cloud storage partner program (CSPP)|
|Looking up an organizational chart while in a 1:1 chat  |   Click on a user’s avatar or profile photo anywhere in Teams and navigate to the organizational chart within the profile card.|
|Looking up LinkedIn while in a 1:1 chat   |   Click on a user’s avatar or profile photo anywhere in Teams and navigate to the LinkedIn tab within the profile card.|
|Channels DocLib app|Use the Sharepoint app in channels instead|
|DocLib folder select in channel upload|Go to a specific folder and upload|
|Legacy web app companion (WAC) viewer|Use the OneUp viewer|
|Allow users to follow another users presence and then notify them of availability|No longer available|
|Activity tab| No longer available|


## Known issues

There are a few known issues we're working on.

### Installation

- **Issue:** </br>After opting into the new Teams, you may receive an “Update and restart” message in the title bar.
Receiving this message is expected behavior. Go ahead and select the link to restart.

- **Issue:** </br>Windows 10 users may receive an error message that states “We’ve run into an issue” when you download/install new Teams.
Download and install WebView2 Runtime. After you’ve finished, restart the Teams desktop app and try again.

If you're still running into problems, contact the Global Helpdesk.

- **Issue:** </br>Sign-in using email address <first name>.<last name>@microsoft.com isn't yet supported.
Use your primary Azure account name (your alias) to sign into new Teams.

- **Issue:** </br>Some people don't see the toggle to opt in.
First, double check the system requirements. You'll need a Windows device and an up-to-date version of classic Teams.

Next, try signing out and back into the Teams desktop app.

1. Select your profile pic in the upper-right corner
2. Select Sign out
3. When the app relaunches, sign back in

If you still don’t see the toggle, try this:

1. Right-click on the Teams app icon in your taskbar and select Quit
2. Open File Explorer. In the address bar, enter the following: %appdata%/Microsoft/Teams
3. Select the arrow, or press Enter. You’ll be taken to the contents of that folder.
4. Delete all contents of the folder (don’t worry, this won't delete the Teams app or affect any of your custom settings). If you get any messages that a certain file or folder can’t be deleted, select Skip.
5. Relaunch the Teams app, then right-click on the icon and select Quit
6. Relaunch the Teams app one more time, and you should see the switcher.

If these steps don’t work, reach out to the Global Helpdesk.

### General

- **Issue:** </br>Organization tab isn't available on chat
Details: The organization tab has moved to a person's Microsoft 365 contact card. To view this, select someone's profile pic and then Organization on their card. This aligns with how you view org charts in other Microsoft 365 apps, creating a more consistent experience.

### Accessibility

- **Issue:** </br>There may be accessibility gaps between new and classic Teams.
If you discover any accessibility gaps, please select the ellipsis (...) > Help > Report a problem in the Teams desktop app. This will alert the product group to the issue.

If you would like a response or the issue is impacting your work, please contact the Global Helpdesk.

### Calls

- **Issue:** </br>Increased power usage during calls may cause CPU throttling and negatively impact performance.
Workaround/details: The product group is working to resolve this issue.

### Meetings

- **Issue:** </br>When a meeting starts, you won’t receive a Teams notification with an option to join (for example, a meeting-start notification).</br>
Workaround/details: ​Join the meeting from your Teams calendar (or chat/channel) or Outlook.

- **Issue:** </br>When using the “Share screen” option to share content, notifications will still pop up, even if you have notifications muted.</br>
Details: The meeting attendees may see preview content in those notifications.
Workaround: Use "Share window" or "PowerPoint Live" instead of "Share desktop".

- **Issue:** </br> Some meeting details won’t appear in new Teams.</br>
Details: This includes forwards, "show as," and assigned meeting categories. 

- **Issue:** </br> When you close a meeting window by selecting "X" in the upper-right corner, you won’t receive a prompt saying, “Are you sure you want to leave?”</br>
Workaround:  If you leave a meeting by accident, re-join.

- **Issue:** </br>For channel meetings, you won’t see a banner at the top of a channel when a meeting hosted there's active.</br>
Workaround: ​Select Join in the channel conversation to join the meeting.

- **Issue:** </br> When you disable attendee mic/camera, it may not look like it's disabled to attendees.</br>
Details:  When you disable attendee mic/camera for a meeting, attendees will still be able to select the microphone and camera icons in the meeting toolbar. However nothing will happen until they come off mute or turn on their video.

- **Issue:** </br> Some people are experiencing poor resolution when screen-sharing during a meeting.</br>
Details: ​The product group is investigating this issue.

### Messaging

- **Issue:** </br>Compose box isn't defaulting to typing field once switching to Chat. Workaround:  Select to start typing. 

### Multi-Tenant Multi-Account (MTMA)

- **Issue:** </br> When you open an app, you may see a banner saying you're signed into that app and Teams with different accounts. For example, if you go to the Approvals app, the banner will read: "There’s a small chance you’re signed in to Approvals and Teams with different accounts."
Workaround: If you sign out and back in, the banner shouldn't appear anymore. [Learn more about this issue](/office/troubleshooting-sign-in-to-apps-in-teams-943e9035-6225-4b23-b902-e0118cec7841).

### Notifications

- **Issue:** </br>Some Teams users aren't receiving notifications of chat mentions, meetings or calls.
Details: In some cases, this is due to bugs that the product group is working to fix.
Check to make sure that you have notifications turned on in Windows system notifications. In the upper-right corner of the Teams desktop app, select the ellipsis (...) > Settings & Notifications > Open Windows notification settings. Find Microsoft Teams (work preview) in the apps list and set your preference.

In the future, when notifications are turned off, you'll see a banner indicating this.
