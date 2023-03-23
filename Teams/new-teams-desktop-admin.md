---
title:  The new Microsoft Teams desktop client
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
description: Learn about the new Microsoft Teams desktop client. Try out new features and provide feedback.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# The new Microsoft Teams desktop client 

>[!Note]
>This article describes the preview release of the new Teams desktop client. No changes have been made in how the service works, and the backend remains the same. There's no new mobile app (iOS or Android). This preview release doesn't have the complete feature set of classic Teams.

**In this article:**

- [What is new Teams?](#what-is-new-teams)
- [Prerequisites](#prerequisites)
- [How to roll out new Teams](#how-to-roll-out-new-teams)
- [How to uninstall the new Teams client](#how-to-uninstall-the-new-teams-client)
- [Remove the new Teams client for all users](#remove-new-teams-for-all-users)
- [Installation issues](#installation-issues)
- [What features are still missing?](#what-features-are-still-missing)
- [What features are changing?](#what-features-are-changing)
- [Known issues](#known-issues)

>[!Important]
>The new Teams client **is not** available for the following during the preview phase:
>
>**Platforms:**  Mac, VDI, Web</br>
>**Customer segments:** Special cloud (GCC High, DoD, Microsoft 365 operated by 21Vianet in China, Air-gapped), Consumer, Desktop running Windows 10 version 10.0.19041 or earlier

>[!Tip]
>Visit our [**Microsoft Adoption site**](https://aka.ms/newTeams) to learn about the new Teams!

## What is the new Teams?

The new Microsoft Teams client has been re-imagined from the ground up with a performance in mind providing a faster, simpler, and more flexible experience. With new Teams, the client installs and loads faster, letting you launch the app and join meetings more quickly, giving you more time to focus on the business tasks. 

New Teams ensures more efficient use of device resources. You can lower memory and disk usage with a Teams app optimized for your device. Whether you have users on multiple accounts or tenants, the new Teams can help eliminate the silos and bring them together in one place, giving them more extensibility and scale.

## Prerequisites

|Requirement|Version|
|:-----|:-----|
|Windows| Windows 10 version 10.0.19041 or higher or </br>Windows 11 version 22000.856 or higher|
|Teams app|Version 1.5.00.29212 to see the *Try the new Teams* toggle.</br></br>If you are at a lower version, click on the overflow menu (…) and click on check for updates, update, and restart your app. |
|Settings|Turn on the "Show Notification Banners" setting in **System > Notifications > Microsoft Teams** to receive Teams Notifications.|


## How to roll out new Teams

As an admin, you can manage which users in your organizations see or don't see the "Try the new Teams" toggle to use the new Teams.

:::image type="content" source="media/new-teams-toggle.png" alt-text="new teams try me toggle at the top of the screen":::

To control which users can see the toggle, use the Teams admin setting **UseNewTeamsClient** under the **TeamsUpdateManagement** policy. 

Manage this setting in the **Teams admin center** or using **Teams PowerShell**.</br>

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

</br>

### Remove new Teams for all users

To remove the new Teams from all users' computers, use the following PowerShell command:

```powershell

Remove-AppxPackage 
```

PowerShell cmdlet to remove new Teams from all users on all computers:

Get-AppxPackage *MSTeams* -AllUsers |Remove-AppxPackage -AllUsers
For an individual user without administrator privilege, use this command:
Get-AppxPackage *MSTeams*|Remove-AppxPackage

</br>

## Installation issues

**Policy settings restricting download & install**

If your users are experiencing issues installing the app, as an administrator you may have set some restrictions preventing them from downloading and installing it.  If they see this error, 

:::image type="content" source="media/new-teams-install-error.png" alt-text="error when attempting to install the new teams desktop client":::

It is possible that the MSIX package installation could be blocked by registry keys set by GPO policy/third party tool.

For a complete list of registry keys: [How Group Policy works with packaged apps - MSIX](/windows/msix/group-policy-msix)
 
“BlockNonAdminUserInstall “, “AllowAllTrustedApps” and “AllowDevelopmentWithoutDevLicense” are registry keys that could block new Teams MSIX package installation. These registry keys can be found at one of these locations:
  - Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\AppModelUnlock
  - Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Appx
 
There are a few policies that could alter these registry keys and block app installation in your organization due to restricted policy set by the admins. Some of the known GPO policies that may be preventing installation include: 

- Prevent non-admins users from installing packaged Windows apps
- Allow all trusted apps to install (disabled)

**To check this setting for your commputer**

1. In Windows, search for **Edit Group Policy**.
2. This will open the Local Group Policy Editor screen.
3. Go to **Computer Configuration > Windows Components > App package Deployment** to check settings for these policies: 
  - *Prevent non-admins users from installing packaged Windows apps*
  - *Allow all trusted apps to install*
4. Make sure that value for these settings is set as follows:

|Setting |Value|
|:-----|:-----|
|Prevent non-admins users from installing packaged Windows apps|Not configured|
|Allow all trusted apps to install|Not configured|

</br>

**Troubleshooting the App switcher toggle**</br>

- Relaunch your current client before turning the *Try the new Teams* toggle ON to make sure that you have latest changes. Also, if there is any Windows update pending, install them before you try new Teams.
- If you’re not seeing the toggle for new Teams, make sure you have the minimum required versions for Windows and Teams
- After you successfully switch to new Teams, if you can't find the toggle on the top left to switch between new Teams and Microsoft Teams (work or school), you can start the version you want by going to Start menu and searching for it or by clicking on it from the task bar. 

**Update and restart message**</br>

Issue: After opting into the new Teams, users may receive an “Update and restart” message in the title bar.
This is expected behavior. Select the link to restart.

**Windows 10 users may receive an error message**</br>

Issue:  Windows 10 users may receive the error “We’ve run into an issue” when they download and install the new Teams.</br>
Action:  [Download and install WebView2 Runtime](https://developer.microsoft.com/en-us/microsoft-edge/webview2/#download-section). Then restart the Teams desktop app and try again.

**Some people don't see the toggle to opt in.** </br>

Make sure the user has the minimum requirements met on their computer.  Next, have them sign out and back into the Teams desktop app.  
If the toggle still doesn't appear, then:

1. Right-click on the Teams app icon in your taskbar and select Quit
2. Open File Explorer. In the address bar, enter the following: %appdata%/Microsoft/Teams
3. Select the arrow, or press Enter. You’ll be taken to the contents of that folder.
4. Delete all contents of the folder (don’t worry,  Teams app won't be deleted, and no or on any of your custom settings). If you get any messages that a certain file or folder can’t be deleted, select Skip.
5. Relaunch the Teams app, then right-click on the icon and select Quit
6. Relaunch the Teams app one more time, and you should see the toggle switch.


## What features are still missing?

While many of the features you're familiar with in classic Teams are already in the new experience, others—like avatars and app notifications—are still being worked on. </br>

[**Find the latest information on upcoming features for the new Teams**](https://aka.ms/newTeams).

## What features are changing?

As we improve the client, the experience has been improved to align with similar features. Here are the changes.

|Classic Teams|New Teams|
|:-----|:-----|
|Purple toast notifications|You will no longer see the purple "toast" notifications, and the taskbar icon will behave a little different. Notifications will be via Windows native notifications to provide a consistent experience.|
|Adding a Wiki to a channel tab|In a channel, select the Notes app instead|
|Ability to add third party cloud storage|Use the Teams app from your third party cloud provider to collaborate with files in Teams. Note:  Teams admins also can turn off native OneDrive and SharePoint file entry points. Learn more at [Turn off Teams nave file upload policy](/microsoftteams/turn-off-teams-native-file-upload-policy)|
|Look up an organizational chart while in a 1:1 chat |Select a user’s avatar or profile photo anywhere in Teams and navigate to the organizational chart within the profile card.|
|Look up LinkedIn while in a 1:1 chat | Select a user’s avatar or profile photo anywhere in Teams and navigate to the LinkedIn tab within the profile card.|
|Adding a document library (DocLib) app to a tab in channels|Use the Sharepoint app instead. Then add the document library from there as a tab to the channel. Existing document libraries will automatically convert to a SharePoint document library on first use.|
|Uploading content to a DocLib folder|No need to select a folder, just upload directly to SharePoint. If you want to organize your uploads into a specific folder, go to the channel tab and move the file as needed.|
|Allow users to follow a user's presence and then notify them of availability|No longer available|
|Activity tab in chat| No longer available|

## Known issues

There are a few known issues we're working on.

### General

- **Issue:**  Organization tab isn't available on chat
Details: The organization tab has moved to a person's Microsoft 365 contact card. To view this, select a user's profile picture and then Organization on their card. This aligns with how you view org charts in other Microsoft 365 apps, creating a more consistent experience.

### Accessibility

- **Issue:**  There may be accessibility gaps between new and classic Teams.
If you discover any accessibility gaps, select **Give Feedback**.

### Apps

- **Issue:**  If custom apps are used, their icons are broken on the left pane.

- **Issue:**  New Teams doesn't have the option to install/uninstall any app yet. So, the only apps installed in classic Teams will show up in new Teams. If we want to add new app, please add them in classic Teams so that they get added to new Teams as well. 

- **Issue:**  While all  the basic capabilities within the app bar and flyout are supported, other advanced capabilities such as pinning, re-ordering, uninstalling, store navigation are still pending.


### Calendar

- **Issue:**   There is no option to add a Channel calendar to a channel.
Workaround:  Switch back to classic Teams to use this feature.

- **Issue:**   Unable to add an app in scheduling form
Workaround:  Switch back to classic Teams to use this feature.



### Calls

- **Issue:**  Increased power usage during calls may cause CPU throttling and negatively impact performance.
Workaround/details: We are working to resolve this.

- **Issue:**  Full HID capabilities (e.g. device mute/unmute, LED sync) are not yet supported.

- **Issue:**  When using the “share screen” option to share content or in DND mode, call toast notifications will still pop up.

- **Issue:**  Call toast stacking is not supported by default in Windows 10.
Workaround:  Open the action center to view secondary incoming call toasts


### Chats

- **Issue:**  When you pop out a chat, the window may appear blank for a few moments.

- **Issue:**  You may still receive notifications on the muted meeting chats.

- **Issue:**  You can't search for external users even if you enter full email address.


### Meetings

- **Issue:**  When using the “Share screen” option to share content, notifications will still pop up, even if you have notifications muted.</br>
Details: The meeting attendees may see preview content in those notifications.
Workaround: Use "Share window" or "PowerPoint Live" instead of "Share desktop".

- **Issue:**   Some meeting details won’t appear in new Teams.</br>
Details you won't see include forwards, "show as," and assigned meeting categories. 

- **Issue:**   When you close a meeting window by selecting "X" in the upper-right corner, you won’t receive a prompt saying, “Are you sure you want to leave?”</br>
Workaround:  If you leave a meeting by accident, re-join.

- **Issue:**  For channel meetings, you won’t see a banner at the top of a channel when a meeting hosted there's active.</br>
Workaround: ​Select Join in the channel conversation to join the meeting.

- **Issue:**   When you disable attendee mic/camera, it may not look like it's disabled to attendees.</br>
Details:  When you disable attendee mic/camera for a meeting, attendees will still be able to select the microphone and camera icons in the meeting toolbar. However nothing will happen until they come off mute or turn on their video.

- **Issue:**   Some people are experiencing poor resolution when screen-sharing during a meeting.</br>
Details: ​The product group is investigating this issue.

- **Issue:**  Some people are experiencing poor resolution when screen-sharing during a meeting.
Details: The product group is investigating this issue.

- **Issue:**  An error occurs when joining a meeting whose organizer is from an organization for which you either (1) do not have an account signed-in into the new Teams client or (2) none of your signed-in accounts are guested there.
Details: Before joining the meeting, turn off preview using the toggle button on the title bar.

- **Issue:**  When using the "Share screen" option to share content, toast notifications will still pop up, even if you have notifications muted.
Details: Meeting attendees may see preview content in those notifications.
Workaround: Use "Share window" or "PowerPoint Live" instead of "Share desktop."

- **Issue:**  Some meeting details won't show up in new Teams.
Details include forwards, "show as," and assigned meeting categories.

- **Issue:**  When you close a meeting window by selecting "X" in the upper-right corner, you won't receive a prompt saying, "Are you sure you want to leave?"
Workaround:  If you leave the meeting by accident, re-join. 

- **Issue:**  If you are using new Teams, you can't join or be assigned to a Breakout room as a participant. Meeting organizers: If you set up the Breakout Room in classic Teams, you won't be able to manage and open Breakout Rooms from new Teams.
Workaround: As an organizer, if you plan to run Breakout sessions, switch back to classic Teams and inform all participants that the meeting includes Breakout Rooms, and they all must switch to classic Teams to participate.

- **Issue:**  In Restricted Meetings, attendee Microphone/Camera UBAR buttons appear enabled, however Attendees Audio/Video doesn't flow into the meeting.

- **Issue:**  When a user raises their hand in Gallery view, two hands are displayed raised on their gallery (bottom left and upper right).

- **Issue:**  Selecting Room Audio has a blank UI, and it is unable to detect rooms or search on the Join screen.

- **Issue:**  In Settings->Devices, users can't preview their video. 

- **Issue:**  Users won't be able to start a "Screen sharing call".
Details:  Users on Windows 11 can’t share the app using the taskbar. 
Workaround Share the app or window using the share tray within Teams meeting. 

- **Issue:**  Users can’t use the advanced presenter modes (Standout, Side-by-side, Reporter, Cameo)
- **Issue:**  Users wont see the presenter toolbar when a screen sharing session is active.



### Multi-Tenant Multi-Account (MTMA)

- **Issue:**   When you open an app, you may see a banner saying you're signed into that app and Teams with different accounts. For example, if you go to the Approvals app, the banner will read: "There’s a small chance you’re signed in to Approvals and Teams with different accounts."
Workaround: If you sign out and back in, the banner shouldn't appear anymore. [Learn more about this issue](https://support.microsoft.com/en-us/office/troubleshooting-sign-in-to-apps-in-teams-943e9035-6225-4b23-b902-e0118cec7841).

- **Issue:** New tenant invitations may not appear or get updated for 24 hours.
Workaround:  Switch back to classic Teams if the user needs access earlier thatn 24 hours.


### Notifications

- **Issue:**   If a user receives a message where @mention *Everyone* is used, it will show in their feed as a personal mention.
Details: The @mention Everyone feature still to be implemented.

- **Issue:**  Some Teams users aren't receiving notifications of chat mentions, meetings or calls.
DYou aren't receiving notifications of chat mentions, meetings, or calls. 
Details:  Review your Windows Notification settings. From the upper-right corner of the Teams desktop app, select the ellipsis (...) > Settings & Notifications > Open Windows notification settings. Find Microsoft Teams (work preview) in the apps list and set your preferences.

### Presence

- **Issue:**  Occasionally when a user is in a meeting, their Presence Status shows as Available.
- **Issue:**  Sometimes, users are not able to reset presence status
- **Issue:**  The preview thumbnail for Teams appears but there are no presence buttons.


### Teams and Channels

- **Issue:**   You won't see a banner at the top of a channel for channel meetings when a meeting hosted is active. You can still join the meeting from the channel.

- **Issue:**   Member and guest counts are occasionally displayed incorrectly in the members' tab.

- **Issue:**   Limited options on Team Channel properties Dialog, including:
  - Pin, Manage Channel and Get Email Address available
  - Limited team site properties dialog – Hide, Manage Team, and Manage Tags available
  - Adding a tab to a channel is not currently available.
  - Webhooks not supported

- **Issue:**   Attendance report doesn't show after a meeting.
Workaround: To download, go to **Edit Meeting Details > Attendance > Download**.  It will always download the latest meeting's report.  There is no option to download a report of an older channel meeting at this time.

## Other areas:

- **Issue:**   Right-clicking on the back button (next to Search) doesn't bring the old history for you to navigate.

- **Issue:**   If Windows (Focus/Do not Disturb) mode is on you won’t receive Teams notifications.
Workaround: Turn on the "Show Notification Banners" setting in System > Notifications > Microsoft Teams to receive Teams Notifications and enable it with Focus/Do not Disturb mode.

- **Issue:**   If a user has more than one tenant to their account, if they sign out of their accounts and then join a meeting, it will not sign in with their primary tenant account, but any one of their accounts (including guest accounts).
Workaround: Before joining a meeting, sign in with primary tenant account.
