---
title:  Deployment checklist for new Teams client
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 04/22/2024
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: amitsri
search.appverid: MET150
f1.keywords:
- NOCSH
description: A checklist of things you need to do and check in your environment prior to moving from the classic Teams client to the new Teams client. Helpful for medium and large business specifically.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Preparation checklist for organizations updating to the new Teams client

As part of the deployment for the new Teams update, there are changes that need to be made to the executables, locations and installer package of the client. Organizations may have different settings in their environment, such as antivirus, network settings, QoS, and so on. Enterprises that have deployed classic Teams should review their configurations to account for the new Teams and make sure devices are on the latest OS update.

- Name and location: New Teams uses different files [ms-teams.exe & ms-teamsupdate.exe] and is located in: "Program Files\WindowsApps\MSTeams_[appversion]\".
- MSIX Installer technology stays current with the newest OS patches. Customers who may have had installation problems before could resolve them with the latest OS updates.

> [!NOTE]
> Adjust any third-party software that works with classic Teams app to use new Teams.

## Checklist

- **OS/WV2 prerequisites**: Make sure the device has an updated Operating System (OS) and WebView2 (WV2) version. see the [Windows](new-teams-bulk-install-client.md), [Mac](new-teams-mac-install-prerequisites.md), and [VDI](new-teams-vdi-requirements-deploy.md) articles for more information. **NOTE**: New Teams won't work on lower OS versions.
- **Device policies restrictions**: [Policies](/microsoftteams/troubleshoot/teams-administration/fix-new-teams-installation-issues#policy-settings-prevent-download-and-installation) must not block new Teams installation (MSIX) and the Teams Meeting add-in (MSI)  or the [Webview2 updater](/microsoft-edge/webview2/concepts/enterprise).
- **Network considerations**: Review any configuration explicitly using classic Teams file paths or binary name for a good meeting experience. Some examples include configurations for:
  - **Local Firewalls:**  If you're using Windows Firewall policies to define inbound/outbound rules specific to the Teams application, you'll need to update them to reference the new executable name and path. With each update, the new Teams executable path changes. One approach for creating rules that account for the path change is to use Windows Defender Application Control (WDAC) application tagging policies. For an example of this, refer to the following guidance: [WDAC Application Tagging for New Teams](https://aka.ms/new-teams-WDAC).
  - **Split Tunneling/Proxy:** If you're referencing a [split tunneling](/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel) and/or [proxy](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles) configuration, ensure that any references to the Classic Teams executable and path are updated to include the new Teams executable and path.
  - **Quality of Service (QoS):** If your organization has set up QoS, please refer to the following guidance related to new Teams:
    - [Implement Quality of Service metrics in Microsoft Teams](QoS-in-Teams.md)
    - [Implement Quality of Service (QoS) in Microsoft Teams clients](QoS-in-Teams-clients.md)
    - [Configure QoS settings in the Teams admin center](meetings-real-time-media-traffic.md)
- **Software blocks**: Any management software including [Antivirus](/microsoftteams/troubleshoot/teams-administration/include-exclude-teams-from-antivirus-dlp) or [AppLocker](applocker-in-teams.md) that references classic Teams should be updated to include new Teams. For third-party products, please refer to the manufacturer's documentation.
- **Machine-wide deployment or multi-user devices**: Use [M365 apps](new-teams-deploy-with-m365apps.md) or [teamsbootstrapper](new-teams-bulk-install-client.md) to deploy new Teams machine-wide.
- **Classic Teams minimum application version**: Version 1.6.00.27573 or higher is required to deploy the in-app update to new Teams. Otherwise, the admin should review their deployment and use M365 apps or manually install new Teams though the [teamsbootstrapper](new-teams-bulk-install-client.md).
- **Make sure all users have updated to new Teams**: As new Teams is deployed, track usage to validate that intended users and systems are updated via the [usage report for new Teams client](new-teams-usage-report.md).
- **Review to make sure your deployments replace any classic Teams installation references**: This includes new machine images, device management configuration, scripts, old builds of M365 apps, documentation, nd so on.

## Learn more

- [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md)
- [Upgrade to new Microsoft Teams with Microsoft 365 Apps](new-teams-deploy-with-m365apps.md)
- [New Teams for Mac - Overview and prerequisites](new-teams-mac-install-prerequisites.md)
- [Upgrade to new Teams for Virtualized Desktop Infrastructure (VDI)](new-teams-vdi-requirements-deploy.md)
