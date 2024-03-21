---
title:  How to uninstall the classic Teams client
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 03/29/2024
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: 
search.appverid: MET150
f1.keywords:
- NOCSH
description: Uninstalling classic Teams client from client machines.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Uninstalling Classic Microsoft Teams

After installing the new Teams client and setting the **New Teams Only** policy (or reaching the end of life period for classic Teams), the classic Teams client will attempt to be removed after fourteen days. This removal will be attempted by Microsoft, but in some cases, due to permissions or other settings, the removal may fail. This article outlines the steps and considerations for IT administrators to uninstall the classic Teams client manually.

## Understanding Your Deployment Scenario

Before proceeding with the uninstallation, you should try to identify how Classic Teams was deployed in your organization. The most common configurations are:

1. **User-Deployed or Per-User Admin Deployment**:
   - Classic Teams was installed individually by users or by admins on a per-user basis, typically through the web, Microsoft Store, or admin tools.
   - **Action**: No immediate action required. classic Teams will be automatically uninstalled 14 days after the New Teams installation.

2. **Commercial Version of Microsoft 365 Apps Installed**:
   - Classic Teams and the Teams Machine-Wide Installer are present on devices.
   - **Action**: No immediate action required. The New Teams installation will replace classic Teams, and the Teams Machine-Wide Installer will be uninstalled by Microsoft 365 Apps in an upcoming update.

3. **Admin-Deployed Teams Machine-Wide Installer Without Microsoft 365 Apps**:
   - Classic Teams was deployed machine-wide by an admin without using Microsoft 365 Apps.
   - **Action**: Admins must proactively uninstall the Teams Machine-Wide Installer using their existing deployment tools.

## Uninstalling Classic Teams

### For User-Deployed or Per-User Admin Deployments

These users will not see the "Teams Machine-Wide Installer" in their system. As the **New Teams Only** policy rolls out, classic Teams will be automatically uninstalled 14 days after the New Teams installation. No further action is required unless users have not signed in for an extended period. In those cases, make sure that New Teams is deployed machine-wide to prevent users from being left without a Teams installation.

### For Commercial Version of Microsoft 365 Apps

The classic Teams app will be uninstalled automatically by the New Teams installation. The Teams Machine-Wide Installer will also be removed by M365 Apps in a future update. Ensure that the New Teams installation is not blocked by admin configuration.

### For Admin-Deployed Teams Machine-Wide Installer Without M365 Apps

Admins should use their existing deployment tools to uninstall the Teams Machine-Wide Installer. This action will trigger the uninstallation of classic Teams for each user as they sign in. Ensure that the new Teams client is installed machine-wide to avoid users being without a Teams installation.

### Special Considerations for VDI Environments

For **Persistent VDI** configurations, follow the steps for admin-deployed Teams Machine-Wide Installer without M365 Apps.

For **Non-Persistent VDI** configurations, administrators must manage the uninstallation process according to their device configuration.

## FAQs

- **How do I know if users still have Classic Teams?**
  Use your tenant dashboard or device management tools to scan for Classic Teams and the Machine-Wide Installer.

- **When will Classic Teams be removed automatically?**
  Classic Teams will be uninstalled 14 days after the New Teams installation and once users receive the "New Teams" policy settings.

- **How much network bandwidth is required for the New Teams update?**
  The initial update is approximately 150MB, with subsequent updates ranging from 15-30MB.

- **How can I remove all copies of Classic Teams from a multiuser device without each user signing in?**
  Manual deletion is possible but not recommended as it may leave residual files. Await further guidance on automated removal methods.

- **Will users be notified of the uninstallation attempt?**
  No, the process is designed to be silent to minimize disruptions.

## Additional Resources

For detailed instructions on using Intune to uninstall applications, please refer to the Microsoft documentation: [Uninstall an app with Intune](https://learn.microsoft.com/mem/intune/apps/apps-add#uninstall-an-app).

## Open Items and Future Updates

This guide will be updated with additional information on uninstalling Classic Teams from MacOS, VDI-specific guidance, PowerShell scripts for automation, and detection mechanisms. Stay tuned for updates on these topics and best practices for automating the uninstallation process through tools like Intune.

For any immediate concerns or queries, please reach out to your Microsoft support representative.
