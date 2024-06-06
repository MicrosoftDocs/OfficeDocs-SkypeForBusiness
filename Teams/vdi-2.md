---
title:  Teams for Virtualized Desktop Infrastructure (VDI) 2.0
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.date: 06/07/2024
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: fklurfan
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about Teams for Virtualized Desktop Infrastructure (VDI) 2.0.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Teams for VDI 2.0

VDI 2.0 is a new architecture for optimizing the delivery of multimedia workloads in virtual desktops.

## Components

|Component |Role |Update |Size |Notes |
|----------|-----|-------|-----|------|
|New Teams **vdiBridge**     |Server-side virtual channel module. |New version with every new Teams version. |Bundled with new Teams. | |
|Custom virtual channel (VC) |Custom VC owned by Microsoft Teams. |Stable API - no updates foreseen. | |Check the Citrix Studio policy **Virtual channel allow list**. |
|Plugin                      |Client-side VC dll. Responsible also for SlimCore download and clean-up. |Not frequent (ideally no updates). |Approximately 200 KB. |Bundled with [RD Client 1.2.5405.0](/azure/virtual-desktop/whats-new-client-windows) or Windows App 1.3.252 or higher. Citrix CWA 2402 or higher can fetch and install the plugin. |
|SlimCore                    |Media engine (operating system specific, not VDI vendor specific). |Auto-updated to a new version with each new Teams version. |Approximately 50 MB. |MSIX package hosted on Microsoft’s public CDN, [https://res.cdn.office.net/*](https://res.cdn.office.net/*) |

## System requirements

|Requirement |Minimum version |
|------------|----------------|
|New Teams   |24124.2315.2911.3357                                                                                      |
|AVD/W365    |Windows App: 1.3.252</br>Remote Desktop Client: 1.2.5405.0                                                |
|Citrix      |VDA: 2203 LTSR CU2 or 2212 CR</br>Citrix Workspace app: 2203 LTSR (any CU), 2402 LTSR or 2302 CR          |
|Endpoint    |Windows 10 1809 (SlimCore minimum requirement)</br>GPOs must not block MSIX installations (see Step 3 on the section below, Sideloading must be enabled)</br>Minimum CPU: Intel Celeron (or equivalent) @ 1.10GHz, 4 Cores, Minimum RAM: 4GB |

## Optimizing with new VDI solution for Teams

### Step 1: Confirm prerequisites

1. Make sure you have the new Microsoft Teams version 24124.2311.2896.3219 or higher.
1. Enable the new Teams policy **if necessary** for a specific user group (it's enabled by default at a Global org-wide level).
1. For Citrix, you must configure the **Virtual channel allow list** as described in **Citrix Virtual channel allow list** section of this article.

### Step 2: Plugin installation on the endpoint
