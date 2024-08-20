---
title:  How to uninstall the classic Teams client
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 04/02/2024
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: 
search.appverid: MET150
f1.keywords:
- NOCSH
description: Uninstalling classic Teams client from client machines if the automatic uninstall doesn't work, or if an admin needs to do a manual removal after the end of availability for classic Teams client and the upgrade to new Teams client.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Uninstalling classic Microsoft Teams

After installing the new Teams client and setting the **New Teams Only** policy (or reaching the end of life period for classic Teams), there will be an attempt to remove classic Teams client application after a period of time. This removal will be attempted by Microsoft, but in some cases, due to permissions or other settings, the removal may fail. This article outlines the steps and considerations for IT administrators to uninstall the classic Teams client manually.

> [!NOTE]
> This article discusses removing the classic Teams client application. Users may also, depending on how the classic Teams client was installed, also have the Machine-Wide Installer to remove, and this will also appear as an application, but its removal isn't covered in this documentation. For more information, see [How the Microsoft Teams MSI file works](msi-deployment.md#how-the-microsoft-teams-msi-file-works).

## Understanding Your Deployment Scenario

Before proceeding with the uninstallation, you should try to identify how classic Teams was deployed in your organization. The most common configurations are:

1. **User-Deployed or Peruser Admin Deployment**:
   - Classic Teams was installed individually by users or by admins on a per-user basis, typically through the web, Microsoft Store, or admin tools. In **Add or Remove Programs**, you'll only see an entry for classic Teams.
   - **Action**: No immediate action required. classic Teams will attempt to be automatically uninstalled some time after the new Teams installation.

2. **Commercial Version of Microsoft 365 Apps Installed**:
   - In **Start** > **Settings** > **Apps**, classic Teams and the Teams Machine-Wide Installer are both present.
   - **Action**: No immediate action required. The new Teams installation will replace classic Teams, which will be removed at a later point, and Microsoft 365 Apps will attempt to uninstall the Teams Machine-Wide Installer at a later point.

3. **Admin-Deployed Teams Machine-Wide Installer Without Microsoft 365 Apps**:
   - Classic Teams was deployed machine-wide by an admin without using Microsoft 365 Apps (typically by deploying the Teams Machine-Wide Installer directly).
   - **Action**: After new Teams is deployed, an attempt will be made to remove classic Teams after a period of time. If Microsoft 365 Apps is present, after new Teams is deployed, an attempt to remove the Teams Machine-Wide Installer will be made as well. Otherwise, admins must proactively uninstall the Teams Machine-Wide Installer using their existing deployment tools. For more information, see [Bulk install classic Teams using Windows Installer (MSI)](msi-deployment.md).

> [!NOTE]
> If your organization has the **New Teams as default** setting, which allows users to switch back, the uninstallation of classic Teams removes the switch option.

## Uninstalling classic Teams

> [!IMPORTANT]
> A rare issue with the uninstall of classic Teams has been detected and to be cautious Microsoft has paused the automatic uninstallation of classic Teams for customers who haven't already completed this step. This issue could result in the Teams Meeting Addin in Outlook failing to schedule or join Teams meetings. We are actively investigating this issue and will update once it's resolved. If your users are experiencing this issue, a workaround is to use Teams to schedule or join meetings.
>
> For customers who are experiencing this issue or who wish to perform the uninstall of classic Teams themselves and experience this issue, there are troubleshooting steps available here: [Teams meeting add-in missing from Outlook and new Teams](/microsoftteams/troubleshoot/meetings/teams-meeting-add-in-missing).

### For User-Deployed or Per-user Admin Deployments

These users won't see the "Teams Machine-Wide Installer" in their system. As the **New Teams Only** policy rolls out, classic Teams will be automatically uninstalled some time after the new Teams installation. No further action is required unless users haven't signed in for an extended period. In those cases, make sure that new Teams is deployed machine-wide to prevent users from being left without a Teams installation.

### For Commercial Version of Microsoft 365 Apps

The classic Teams app will be uninstalled automatically by the new Teams installation. Microsoft 365 Apps will remove the Teams Machine-Wide Installer in a future update. You should make sure that the new Teams installation isn't blocked by admin configuration.

### For Admin-Deployed Teams Machine-Wide Installer Without Microsoft 365 Apps

> [!CAUTION]
> Before proceeding, ensure new Teams is deployed machine-wide using the Microsoft 365 apps version or through the [Bulk upgrade to the new Microsoft Teams client](new-teams-bulk-install-client.md) option, or users may be left without a Teams client.

Admins should use their existing deployment tools to uninstall the Teams Machine-Wide Installer. This action will trigger the uninstallation of classic Teams for each user as they sign in.

### An example uninstall using Intune on Windows

To uninstall an application across all devices using Intune on Windows, you can follow these steps:  

1. Sign in to the Microsoft Endpoint Manager admin center [https://endpoint.microsoft.com/](https://endpoint.microsoft.com/).
2. Go to Devices > Windows > Windows Apps.
3. Select the **Add** button and then select **Windows app (Win32)**.
4. In the **Add app** wizard, select **App package file** and upload the .intunewin file for the application you want to uninstall.
5. In the **Detection rules** section, select **Manually configure detection rules**.
6. In the **Detection rules** section, select the **Add** button and select **File**.
7. In the **File** section, enter the path and file name of the uninstaller for the application you want to uninstall.
8. In the **Uninstall command** section, enter the command to run the uninstaller silently. For example, if the uninstaller is "uninstall.exe" and the silent switch is "/quiet", the command would be:
   - "MsiExec.exe -x {731F6BAA-A986-45A4-8936-7C3AAAAA760B} /quiet"

You can learn more at [Uninstall an app with Intune for Windows](/mem/intune/apps/apps-add).

### Special Considerations for VDI Environments

- For **Persistent VDI** configurations, follow the steps for admin-deployed Teams Machine-Wide Installer without Microsoft 365 Apps.
- For **Non-Persistent VDI** configurations, admins must manage the uninstallation process according to their device configuration.

### Removing Classic Teams on macOS

To remove the Classic Teams client from a macOS device, execute the following commands in the terminal:

```
# Remove Classic Teams
sudo rm -rf /Applications/Microsoft\ Teams\ classic.app
# Remove Classic Teams cache
rm -rf ~/Library/Application\ Support/Microsoft/Teams
```

Make sure you have the necessary permissions to execute these commands. This process will completely remove the Classic Teams client and its associated file.

## FAQs

- **How do I know if users still have classic Teams?**
  Use your tenant dashboard or device management tools to scan for classic Teams and the Teams Machine-Wide Installer.

- **When will classic Teams be removed automatically?**
  If the policy is set to **New Teams only**, Classic Teams will be uninstalled some time after the new Teams installation completes, and once users receive the new Teams policy settings. If the Teams Machine-Wide Installer is present, Microsoft 365 Apps can uninstall it for each user as they sign in.

- **How much network bandwidth is required for the new Teams update?**
  The initial update is approximately 150 MB, with subsequent updates ranging from 120-150 MB. This update is automatically downloaded and installed from the internet once per device (multi-user devices don't download the binaries for each user). An admin can also choose to do an offline installation using the [bulk installer](new-teams-bulk-install-client.md). The [MSIX app package updates](/windows/msix/desktop/managing-your-msix-deployment-update) article has more details.

- **How can I remove all copies of classic Teams from a multi-user device without each user signing in?**
  Manual deletion is possible but not recommended as it may leave residual files.

- **Will users be notified of the uninstallation attempt?**
  No, the process is designed to be silent to minimize disruptions.

- **Are there any workarounds for the uninstallation timer?**
  No, this timer isn't configurable. Admins can use device management software, such as Intune, to directly uninstall classic Teams.

## Future updates

This article will be updated at a later time with additional information on:

- VDI-specific guidance
