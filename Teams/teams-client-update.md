---
title: Teams updates
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
ms.reviewer: 
ms.date: 06/28/2024
search.appverid: MET150
f1.keywords: 
  - NOCSH
description: This article outlines the process behind updating the Microsoft Teams desktop client.
ms.localizationpriority: Medium
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

> [!NOTE]
> This article contains information for the new Teams client. The classic Teams client has ended support, and is no longer receiving updates.

# Why it's important to keep Teams updated.

Keeping Microsoft Teams up to date is crucial for maximizing productivity and staying connected. Regular updates mean you have access to the latest features, security enhancements, and bug fixes. Updating not only improves the overall performance and reliability of the application, it also helps you and your team collaborate more efficiently. By staying current with updates, you reduce the risk of having issues and ensure compatibility with other tools, making it easier to focus on your work without interruptions. 

## Servicing agreement

As part of a modern online service, the Teams client is updated once per month. The client automatically installs updates when they become available to that client. Because we stagger the availability of updates worldwide, some clients in your organization might receive new updates before others. Because Teams is governed by the Modern Lifecycle Policy, it's expected that users remain on the most up-to-date version of the desktop client. Auto-updates ensure that users have the latest capabilities, performance enhancements, security, and service reliability.

To identify when desktop clients fall out of date, an in-app alert is displayed if the user’s current version is between one and three months old, and if there's a new version available. This in-app messaging encourages users to update to the latest version of Teams or, if necessary, to reach out to their IT admin to do so. Users on Teams desktop clients that are more than three months old will see a blocking page. This page gives the options to update now, reach out to their IT admin, or continue to Teams on the web.

Teams desktop clients on Government Clouds currently have an exception to this servicing agreement until further notice.

For information on new version releases, check [Message Center](https://admin.microsoft.com/AdminPortal/Home#/MessageCenter) or go to **Help** > **What’s new** in the client.

## Teams client updates timeline

New updates for the Teams desktop client are released twice a month after thorough internal testing and validation through our Technology Adoption Program (TAP). The desktop client is rolled out to customers gradually.

> [!IMPORTANT]
> When there's a critical update, Teams bypasses the regular schedule and releases the update immediately.

Other factors that help your client to stay up-to-date:

- Operating System (OS):
  - Meets the minimum OS requirements for Teams.
  - Your OS version is up-to-date (non-LTSC update channel) and still under support.
  - Your OS has the latest patches installed.
- Webview2:
  - Webview2 updates automatically on windows, you should make sure it isn’t blocked. This is updated by Teams on macOS.
  - Webview2 must be a supported version (latest version).

For more information, see [Teams client system requirements](teams-client-system-requirements.md).

## How the updates work

- **Update checks**: Teams applications on both Windows and Mac devices check for updates when the application starts up and every few hours in the background, whether the application is running or not. A user must be signed into the machine for updates to happen.
- **Download**: Updates are downloaded based on availability and staged to the user session. By using Windows Defender Optimization, only the delta that's different from the current installed version (the differential update) is downloaded.
- **Restart**: Restarting the application is required for the update to take effect.
- **Manual**: The update starts automatically when the application is idle. A user can choose to restart sooner by selecting the **Restart** button next to the ellipsis (...) button in the client. 

### Issues with Windows update and best practices

- Windows delivery optimization service is disabled or configured with unsupported mode (100). This blocks the updater’s ability to download the update payload.
  - There's a Windows Delivery Optimization service configuration requirement: [Upgrade to the new Teams client using policies](new-teams-deploy-using-policies.md).
  - Note that enabling the Peer to Peer capability isn't required. 
- Team’s app package is modified by a user. The MSIX packages are installed machine-wide under the Program Files directory. The file ACLs are tightly controlled and monitored by the Windows OS. If the file ACLs are modified or changed by a user, the system deems the application to be in a corrupted state. This leads to unexpected behaviors such as crashing, unexpected app termination, and a failure to update.
  - It’s essential to make sure the files under the installation directory (%programfiles%\windowsapps) aren't altered in any way.
- Network settings that block Team’s CDN endpoints cause delivery optimization service failures and a failure to update the app.
  - You must allow Microsoft M365 endpoints in network configuration. For more information see [Microsoft 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges).
  - Avoid SSL inspection on M365 endpoints. SSL inspection is known to cause high update download failure rate and retries.
- Running on an out of support OS, or a Windows version that doesn't have the latest updates and patches can lower the success of Teams updates.
  - Windows 11 improves the Teams application update success rate and reliability as it has the most current installer.
  - Make sure you install all OS patches before deploying Teams on Windows 10 or Windows 11.

## Updating Teams on Mac devices

- The Teams desktop client updates itself using Microsoft AutoUpdate (MAU), similar to other Microsoft applications. Learn more about MAU at [Configuring Microsoft AutoUpdate (MAU) for Organization Specific Updates](/microsoft-365-apps/mac/mau-configure-organization-specific-updates).
- Teams uses default MAU Office channels for updates, as well as a custom channel for Teams-specific scenarios. The post-installation script registers the app with MAU’s default Office channel (Current, Preview, or Beta) to ensure the app can be updated by MAU without running itself.
- When the update is downloaded while Teams is running, we leverage MAU’s Install On Clone feature, to prepare the installation. Once a user quits the application, MAU will finish updates by moving the clone to the /Applications folder. Teams for Mac doesn't automatically restart to apply updates. It always waits for user to take the action.
- Users can also manually check for updates by selecting **Check for updates** from the Help menu bar item. This action opens Microsoft AutoUpdate (MAU).

### How to configure MAU

- No special configuration is required if the MAU preferences are left at default values.
- If your organization employs managed MAU preferences, the Teams app preferences should look like this:

XXX WHAT CODE FORMAT IS THIS I NEED TO KNOW TO MARK IT PROPERLY

    <key>/Applications/Microsoft Teams.app</key>
    <dict>
      <key>Application ID</key>
      <string>TEAMS21</string>
      <key>LCID</key>
      <integer>1033</integer>
    </dict>

### Issues with Mac update and best practices

- Microsoft AutoUpdate (MAU) not being installed or being blocked on your device.
  - Since MAU is an integral part of New Teams, it's included with the Teams installer. When Teams is first installed, MAU is also installed unless it's already present on the device. However, there have been instances where MAU has been deliberately removed or blocked by firewalls.
  - To see if you have MAU installed, select **Check for Updates** from the Help menu bar item. This should open the MAU user interface, but if MAU isn't installed, nothing will happen.
  - To make sure that MAU is allowed to function correctly, we need to first check the MAU configuration (link to How to troubleshoot MAU configuration XXX NO LINK HERE). If the configuration is correct and MAU is installed (link to the How to configure MAU section XXX NO LINK PROVIDED), and it still doesn't work, it's likely being blocked, and the user should contact their administrator.
- MAU is outdated.
  - Microsoft Teams needs MAU version 4.52.22101101 at a minimum, but it's strongly recommended to use version 4.73.24071426 or higher for crucial security updates. Note that MAU self-updates, and a manual update should not be required under the default settings.
- Your organization uses a custom MAU profile and the Teams portion isn't configured correctly.
  - As previously mentioned, Teams handles MAU registration autonomously within user preferences. There are instances when an organization deploys custom MAU preferences using an MDM management system. In such cases, the managed preferences take precedence. Occasionally, these settings might be incorrectly configured. Common issues include a complete lack of Teams configuration, outdated configurations for Classic Teams, or configurations that reference the old name **Microsoft Teams (work or school).app**.

### How to troubleshoot a MAU configuration

XXX I'm not putting this in until I confirm with Meera Krishna that this doesn't exist in the support docs.


XXX LEAVING VDI IN FOR NOW.

## What about updates to Teams on VDI?

Teams clients on Virtual Desktop Infrastructure (VDI) aren't automatically updated the way that non-VDI Teams clients are. You have to update the VM image by installing a new MSI as described in the instructions to [Install Teams on VDI](teams-for-vdi.md). You must uninstall the current version to update to a newer version.
