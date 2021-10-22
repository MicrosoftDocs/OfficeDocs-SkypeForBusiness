---
title: "Control Panel - Overview"
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
ms.collection: IT_Skype16
description: "This article provides an overview of the new Control Panel."
---

# Control Panel

The current Control Panel is a new version of the legacy Control Panel, with which it exists in tandem. The new Control Panel came into existence from the Cumulative Update of July 2019. It helps manage the configuration of servers, users, clients, and devices in the environment of an organization.

The switch to the new Control Panel can be attributed to the Silverlight technology's end of support on October 12, 2021. For more information, see [Silverlight End of Support](https://support.microsoft.com/windows/silverlight-end-of-support-0a3be3c7-bead-e203-2dfd-74f0a64f1788).

> [!NOTE]
> For information on the legacy Control Panel, see [Control Panel](../SfbServer/management-tools/install-and-open-administrative-tools.md), and navigate to the section **Skype for Business Server Control Panel**.

## Access Control Panel

To launch the new Control Panel in the browser, enter https://&lt;pool-FQDN&gt;/macp or a configured simple URL.

## Accessing data from menu items unavailable in new Control Panel through cmdlets

The new Control Panel includes commonly used menu items that cover most of the needs of the organization. There are a few menu items from the legacy Control Panel that are unavailable in the new Control Panel. However, there is an option for the user to avail the functionalities in those menu items through PowerShell cmdlets. For more information, see the table below.

> [!NOTE]
> The documentation for other menus items will be made available subsequently in a phased manner.

## Client

|Sub-menu  |Source of Information for cmdlet  |
|---------|---------|
|Client Version Policy         |    [Client Version Policy](use-powershell-client-menu.md#client-version-policy)     |
|Client Version Configuration      |  [Client Version Configuration](use-powershell-client-menu.md#client-version-configuration)       |
|Device Update    | [Device Update](use-powershell-client-menu.md#device-update)        |
|Test Device     | [Test Device](use-powershell-client-menu.md#test-device)        |
|Device Log Configuration         |    [Device Log Configuration](use-powershell-client-menu.md#device-log-configuration)     |
|Device Configuration         |    [Device Configuration](use-powershell-client-menu.md#device-configuration)     |
|Mobility Policy         |    [Mobility Policy](use-powershell-client-menu.md#mobility-policy)     |
|Push Notification Configuration         |    [Push Notification Configuration](use-powershell-client-menu.md#push-notification-configuration)     |