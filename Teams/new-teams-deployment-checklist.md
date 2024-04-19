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

Organizations may have different settings in their environment, such as antivirus, network tettings, QoS, and so on. Enterprises that have deployed classic Teams should review their configurations to account for the new Teams binary location and make sure devices are on the latest OS update.

- Location: New Teams uses different files [ms-teams.exe & ms-teamsupdate.exe] and is in "Program Files\WindowsApps\MSTeams_<appversion>\".
- MSIX Installer technology stays current with the newest OS patches. Customers who may have had installation problems before could resolve them with the latest OS updates.

> [!NOTE]
> Adjust any third-party software that works with classic Teams app to use new Teams.

## Checklist

- **OS/WV2 version**: Make sure the device has an updated Operating System (OS) and WebView2 (WV2) version. see the [Windows](new-teams-bulk-install-client.md), [Mac](new-teams-mac-install-prerequisites.md), and [VDI](new-teams-vdi-requirements-deploy.md) articles for more information. **NOTE**: New Teams won't work on lower OS versions.
- **Device policies restrictions**: Policies must not block new Teams installation (MSIX) and the Teams Meeting add-in (MSI)  or the [Webview2 updater](/microsoft-edge/webview2/concepts/enterprise).
- **Network optimization**: Review any configuration explicitly using class times file paths or binary name for a good meeting experience. Some examples include configurations for:
  - [Local firewalls - addresses/ports](/microsoft-365/enterprise/urls-and-ip-address-ranges)
  - [Split tunneling](/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel)
  - [Proxies](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)
  - QoS:
    - [Implement Quality of Service metrics in Microsoft Teams](QoS-in-Teams.md)
    - [Implement Quality of Service (QoS) in Microsoft Teams clients](QoS-in-Teams-clients.md)
    - [Configure QoS settings in the Teams admin center](meetings-real-time-media-traffic.md)
- **External software blocks**: Any management software including [antivirus](/microsoftteams/troubleshoot/teams-administration/include-exclude-teams-from-antivirus-dlp), [AppLocker](applocker-in-teams.md), [WDAC](https://aka.ms/new-teams-WDAC), and [split tunnelling clients](/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel) referencing classic Teams should be updated to include new Teams.
- **Machine-wide deployment or multi-user devices**: Use [M365 apps](new-teams-deploy-with-m365apps.md) or [teamsbootstrapper](new-teams-bulk-install-client.md) to deploy new Teams machine-wide.
- **Classic Teams Min app version**: Version 1.6.00.27573 or higher is required to deploy the in-app update to new Teams. Otherwise, the admin should review their deployment and use M365 apps or manually install new Teams though the [teamsbootstrapper](new-teams-bulk-install-client.md).
- **Make sure all users have updated to new Teams**: As new Teams is deployed, track usage to validate intended users and systems are updated via the [Usage report for new Teams client](new-teams-usage-report.md).
- **Review to make sure your deployments replace any classic Teams installation references**: This includes new machine images, device management configuration, scripts, old builds of M365 apps, and so on.
