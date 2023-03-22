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
- [How to roll out new Teams](#how-to-roll-out-new-teams)
- [Release roadmap](#release-roadmap)
- [What features are changing?](#what-features-are-changing)
- [Known issues](#known-issues)


>[!Important]
>The new Teams client **is not** available for the following during the preview phase:
>
>**Platforms:**  Mac, VDI, Web</br>
>**Customer segments:** Special cloud (GCC High, DoD, Gallatin, Air-gapped), Consumer, Desktop running Windows 10 version 10.0.19041 or earlier

## What is the new Teams?

Reimagined from the ground up with a performance-first mindset, the new Teams client provides a faster, simpler, and more flexible experience. With new Teams, the client installs and loads faster, letting you launch the app and join meetings more quickly, giving you more time to focus on the business tasks. 

New Teams ensures more efficient use of device resources. You can lower memory and disk usage with a Teams app optimized for your device. Whether you have users on multiple accounts or tenants, the new Teams can help eliminate the silos and bring them together in one place, giving them more extensibility and scale.

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

### Remove new Teams for all users

To remove the new Teams from all users' computers, use the following PowerShell command:

```powershell

Remove-AppxPackage 
```

PowerShell cmdlet to remove new Teams from all users on all computers:

Get-AppxPackage *MSTeams* -AllUsers |Remove-AppxPackage -AllUsers
For an individual user without administrator privilege, use this command:
Get-AppxPackage *MSTeams*|Remove-AppxPackage

## What features are available?

While many of the features you're familiar with in classic Teams are already in the new experience,  others—like avatars and app notifications—are still being worked on. </br>

[**Follow our release roadmap for the latest information on upcoming features for the new Teams**](/adoption-dev.azurewebsites.net/en-us/dev/new-microsoft-teams).

## What features are changing?

As we improve the client, the experience has been improved to align with similar features. Here are the changes.

|Classic Teams|New Teams|
|:-----|:-----|:-----|
|Adding a Wiki to a channel|In a channel, select the Notes app instead|
|Ability to add third party cloud storage|Refer to the Cloud storage partner program (CSPP)|
|Looking up an organizational chart while in a 1:1 chat |Select a user’s avatar or profile photo anywhere in Teams and navigate to the organizational chart within the profile card.|
|Looking up LinkedIn while in a 1:1 chat | Select a user’s avatar or profile photo anywhere in Teams and navigate to the LinkedIn tab within the profile card.|
|Add the DocLib app to a tab in channels|Use the Sharepoint app instead|
|Uploading content to a DocLib folder|Go to a specific folder and upload to SharePoint app|
|Legacy web app companion (WAC) viewer|Use the OneUp viewer|
|Allow users to follow a user's presence and then notify them of availability|No longer available|
|Activity tab in chat| No longer available|

## Known issues

There are a few known issues we're working on.

### Installation

- **Issue:** </br>After opting into the new Teams, you may receive an “Update and restart” message in the title bar.
Receiving this message is expected behavior. Go ahead and select the link to restart.

- **Issue:** </br>Windows 10 users may receive an error message that states “We’ve run into an issue” when you download/install new Teams.
Download and install WebView2 Runtime. After you’ve finished, restart the Teams desktop app and try again.


- **Issue:** </br>Sign-in using email address <first name>.<last name>@microsoft.com isn't yet supported.
Use your primary Azure account name (your alias) to sign into new Teams.

- **Issue:** </br>Some people don't see the toggle to opt in.
First, double check the system requirements. You'll need a Windows device and an up-to-date version of classic Teams.

Next, try signing out and back into the Teams desktop app.

1. Select your profile pic in the upper-right corner
2. Select Sign out
3. When the app relaunches, sign back in

If you still don’t see the toggle, try:

1. Right-click on the Teams app icon in your taskbar and select Quit
2. Open File Explorer. In the address bar, enter the following: %appdata%/Microsoft/Teams
3. Select the arrow, or press Enter. You’ll be taken to the contents of that folder.
4. Delete all contents of the folder (don’t worry,  Teams app won't be deleted, and no or on any of your custom settings). If you get any messages that a certain file or folder can’t be deleted, select Skip.
5. Relaunch the Teams app, then right-click on the icon and select Quit
6. Relaunch the Teams app one more time, and you should see the switcher.



### General

- **Issue:** </br>Organization tab isn't available on chat
Details: The organization tab has moved to a person's Microsoft 365 contact card. To view this, select someone's profile pic and then Organization on their card. This aligns with how you view org charts in other Microsoft 365 apps, creating a more consistent experience.

### Accessibility

- **Issue:** </br>There may be accessibility gaps between new and classic Teams.
If you discover any accessibility gaps, select **Give Feedback**.


### Calls

- **Issue:** </br>Increased power usage during calls may cause CPU throttling and negatively impact performance.
Workaround/details: The product group is working to resolve this issue.

### Meetings

- **Issue:** </br>When using the “Share screen” option to share content, notifications will still pop up, even if you have notifications muted.</br>
Details: The meeting attendees may see preview content in those notifications.
Workaround: Use "Share window" or "PowerPoint Live" instead of "Share desktop".

- **Issue:** </br> Some meeting details won’t appear in new Teams.</br>
Details you won't see include forwards, "show as," and assigned meeting categories. 

- **Issue:** </br> When you close a meeting window by selecting "X" in the upper-right corner, you won’t receive a prompt saying, “Are you sure you want to leave?”</br>
Workaround:  If you leave a meeting by accident, re-join.

- **Issue:** </br>For channel meetings, you won’t see a banner at the top of a channel when a meeting hosted there's active.</br>
Workaround: ​Select Join in the channel conversation to join the meeting.

- **Issue:** </br> When you disable attendee mic/camera, it may not look like it's disabled to attendees.</br>
Details:  When you disable attendee mic/camera for a meeting, attendees will still be able to select the microphone and camera icons in the meeting toolbar. However nothing will happen until they come off mute or turn on their video.

- **Issue:** </br> Some people are experiencing poor resolution when screen-sharing during a meeting.</br>
Details: ​The product group is investigating this issue.


### Multi-Tenant Multi-Account (MTMA)

- **Issue:** </br> When you open an app, you may see a banner saying you're signed into that app and Teams with different accounts. For example, if you go to the Approvals app, the banner will read: "There’s a small chance you’re signed in to Approvals and Teams with different accounts."
Workaround: If you sign out and back in, the banner shouldn't appear anymore. [Learn more about this issue](https://support.microsoft.com/en-us/office/troubleshooting-sign-in-to-apps-in-teams-943e9035-6225-4b23-b902-e0118cec7841).

### Notifications

- **Issue:** </br>Some Teams users aren't receiving notifications of chat mentions, meetings or calls.
Details: In some cases, this is due to bugs that the product group is working to fix.
Check to make sure that you have notifications turned on in Windows system notifications. In the upper-right corner of the Teams desktop app, select the ellipsis (...) > Settings & Notifications > Open Windows notification settings. Find Microsoft Teams (work preview) in the apps list and set your preference.

In the future, when notifications are turned off, you'll see a banner indicating this.
