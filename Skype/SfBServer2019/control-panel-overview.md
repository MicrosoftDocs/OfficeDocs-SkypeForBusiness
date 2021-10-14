---
title: "Admin Control Panel - Overview"
ms.reviewer: 
ms.author: v-smandalika
author: v-smandalika
manager: dansimp
ms.date: 10/13/2021
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
description: "This article provides an overview of the Admin Control Panel."
---

# Modern Admin Control Panel

Modern Admin Control Panel (MACP) is a modern version of the existing [Control Panel](../SfbServer/management-tools/install-and-open-administrative-tools.md) that helps manage the configuration of servers, users, clients, and devices in the environment of an organization. The Old Control Panel relies on the Silverlight technology that has reached end of support on October 12, 2021.

> [!NOTE]
> Navigate to the section **Skype for Business Server Control Panel** in the page to which you are redirected by clicking the link for **Control Panel** above.

## Access MACP

To launch MACP in the browser, enter **https://[your pool FQDN]/macp** or **https://admin.[your-domain].com**.

## Retreiving data in functionalities from Old to New Control Panel through cmdlets

The MACP includes commonly used functionalities and covers most of the needs of the organization. There are a few functionalities from Old Control Panel that are unavailable in MACP. However, the MACP provides for access of those functionalities through PowerShell-related cmdlets. For more information on the functionalities that can be access through the cmdlets, see the table in [Client](#client).

## Client

|Sub-tab  |Source of Information for cmdlet  |
|---------|---------|
|Client Version Policy         |    [Client Version Policy](use-powershell-client-tab.md#client-version-policy)     |
|Client Version Configuration      |  [Client Version Configuration](use-powershell-client-tab.md#client-version-configuration)       |
|Test Device     | [Test Device](use-powershell-client-tab.md#test-device)        |
|Device Log Configuration         |    [Device Log Configuration](use-powershell-client-tab.md#device-log-configuration)     |

