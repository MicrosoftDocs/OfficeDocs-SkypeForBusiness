---
title:  Troubleshooting the new Teams installation
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 06/30/2023
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
description: Troubleshoot new Teams installation 
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Troubleshooting installation issues in the new Teams client

## Policy settings restricting download & install

If your users are experiencing issues installing the app, as an administrator you may have set some restrictions preventing them from downloading and installing it. They may see this error: 

:::image type="content" source="media/new-teams-install-error.png" alt-text="error when attempting to install the new teams desktop client":::

It's possible that the MSIX package installation could be blocked by registry keys set by GPO policy/third party tool. For a complete list of registry keys: [How Group Policy works with packaged apps - MSIX](/windows/msix/group-policy-msix)

The registry keys that could block new Teams MSIX package installation are: 
 
- *BlockNonAdminUserInstall*
- *AllowAllTrustedApps*
- *AllowDevelopmentWithoutDevLicense*

</br>

These registry keys can be found at one of these locations:
  - Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\AppModelUnlock
  - Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Appx

</br>
There are a few policies that could alter these registry keys and block app installation in your organization due to restricted policy set by the admins. Some of the known GPO policies that may be preventing installation include:

- Prevent non-admins users from installing packaged Windows apps
- Allow all trusted apps to install (disabled)

#### To check this setting for your computer

1. In Windows, search for **Edit Group Policy** or right-click the Windows Key and select **Run > type "gpedit.msc".**
2. This opens the Local Group Policy Editor screen.
3. Go to **Go to Computer Configuration > Administrative Templates > Windows Components > App package Deployment** to check settings for these policies: 
  - *Prevent non-admins users from installing packaged Windows apps*
  - *Allow all trusted apps to install*
4. Make sure that value for these settings is set as follows:

|Setting |Value|
|:-----|:-----|
|Prevent non-admins users from installing packaged Windows apps|Not configured|
|Allow all trusted apps to install|Not configured|

</br>

## Troubleshooting the App switcher toggle

- Relaunch your current client before turning the *Try the new Teams* toggle ON to make sure that you have latest changes. Also, if there's any Windows update pending, including security updates, install them before you try new Teams.
- If you’re not seeing the toggle for new Teams, make sure you have the minimum required versions for Windows and Teams
- After you successfully switch to new Teams, if you can't find the toggle on the top left to switch between new Teams and Microsoft Teams (work or school), you can start the version you want by going to Start menu and searching for it or by clicking on it from the task bar. 


## Policies that could block the user from seeing the App switcher toggle

The following list of policies can block users from seeing the app switcher toggle.

- Your admin has **sign in restrictions** set up [Learn more about how to restrict Teams sign in on desktop devices](/microsoftteams/sign-in-teams#how-to-restrict-teams-sign-in-on-desktop-devices) 
- If the user is on a VDI computer (Citrix, VMware etc.). 
- If the user is signed in to classic Teams with a *Teams for Life* account and a work account. 
- If the user is signed in to classic Teams with a *Teams for Life* account.
- If you have an MSIX client. 


### How do I know which one of the above policies is blocking me?

1. Open logs in this path: %appdata%/Microsoft/Teams 
1. Open logs.txt 
1. Search for **appswitcher_appstateservice_check**.
1. Check the **enggComplete** flag:  
   - If true, the Microsoft has turned the setting for you. 
   - If false, you didn’t the settings from MSFT yet or need an app relaunch (see below for steps to relaunch the app) 
1. Check **isAboveWin10Vibranium**.
   - If true, the OS version is >= what is needed for app switcher  
   - If false, the OS is older than what we support. 
1. Check the code to find out the cause.

|Code|Meaning|
|:-----|:-----|
|TFLONLY|You're only signed in to *Teams for Life*|
|TFLANDTFW| You're signed in to *Teams for Life* and *Teams for Work*|
|SPECIALCLOUD| You're signed in to a special cloud that isn’t supported.|
|CROSSCLOUD| You're signed in to a government cloud.| 
|VDI|You're signed in to a VDI machine (VMware, Citrix, AVD/WV).|


### Update and restart message in title bar

Issue: After opting into the new Teams, users may receive an “Update and restart” message in the title bar.
Action: This is expected behavior. Select the link to restart.

### Windows 10 users may receive an error message

Issue: Windows 10 users may receive the error “We’ve run into an issue” when they download and install the new Teams.</br>
Action: [Download and install WebView2 Runtime](https://developer.microsoft.com/en-us/microsoft-edge/webview2/#download-section). Then restart the Teams desktop app and try again.

### Some people don't see the toggle to opt in

Make sure the user has the minimum requirements met on their computer.  Next, have them sign out and back into the Teams desktop app.  
If the toggle still doesn't appear, then 

1. Right-click on the Teams app icon in your taskbar and select Quit.
1. Open File Explorer. In the address bar, enter the following: `%appdata%/Microsoft/Teams`.
1. Select the arrow, or press Enter. You're taken to the contents of that folder.
1. Delete all contents of the folder (don’t worry, Teams app won't be deleted, and no or on any of your custom settings). If you get any messages that a certain file or folder can’t be deleted, select Skip.
1. Relaunch the Teams app, then right-click on the icon and select Quit.
1. Relaunch the Teams app one more time, and you should see the toggle switch.




