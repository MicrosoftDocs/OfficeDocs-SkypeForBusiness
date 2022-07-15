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

The legacy Control Panel may not work as Silverlight technology has reached the "end-of-support" stage on October 12, 2021. For more information, see [Silverlight End of Support](https://support.microsoft.com/windows/silverlight-end-of-support-0a3be3c7-bead-e203-2dfd-74f0a64f1788).

> [!NOTE]
> For information on the legacy Control Panel, see [Control Panel](../SfbServer/management-tools/install-and-open-administrative-tools.md), and navigate to the section **Skype for Business Server Control Panel**.

## Access Control Panel

To launch the new Control Panel in the browser, enter https://&lt;pool-FQDN&gt;/macp or a configured simple URL.

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

## Security

|Sub-menu  |Source of Information for cmdlet  |
|---------|---------|
|Registrar         |    [Registrar](use-powershell-security-menu.md#registrar)     |
|Web Service      |  [Web Service](use-powershell-security-menu.md#web-service)       |
|PIN Policy    | [PIN Policy](use-powershell-security-menu.md#pin-policy)        |

## IM and Presence

|Sub-menu  |Source of Information for cmdlet  |
|---------|---------|
|File Filter         |    [File Filter](use-powershell-im-and-presence-menu.md#file-filter)     |
|URL Filter      |  [URL Filter](use-powershell-im-and-presence-menu.md#url-filter)       |

## Monitoring and Archiving

|Sub-menu  |Source of Information for cmdlet  |
|---------|---------|
|Call Detail Recording       |    [Call Detail Recording](use-powershell-monitoring-and-archiving-menu.md#call-detail-recording)     |
|Quality of Experience Data      |  [Quality of Experience Data](use-powershell-monitoring-and-archiving-menu.md#quality-of-experience-data)       |
|Archiving Policy       |    [Archiving Policy](use-powershell-monitoring-and-archiving-menu.md#archiving-policy)     |
|Archiving Configuration      |  [Archiving Configuration](use-powershell-monitoring-and-archiving-menu.md#archiving-configuration)       |

## Network Configuration

|Sub-menu  |Source of Information for cmdlet  |
|---------|---------|
|Location Policy       |    [Location Policy](use-powershell-network-configuration-menu.md#location-policy)     |
|Bandwidth Policy      |  [Bandwidth Policy](use-powershell-network-configuration-menu.md#bandwidth-policy)       |
|Region       |    [Region](use-powershell-network-configuration-menu.md#region)     |
|Site      |  [Site](use-powershell-network-configuration-menu.md#site)       |
|Subnet      |  [Subnet](use-powershell-network-configuration-menu.md#subnet)       |
|Region Link       |    [Region Link](use-powershell-network-configuration-menu.md#region-link)     |
|Region Route      |  [Region Route](use-powershell-network-configuration-menu.md#region-route)       |

## Topology

|Sub-menu  |Source of Information for cmdlet  |
|---------|---------|
|Status       |    [Status](use-powershell-topology-menu.md#status)     |
|Server Application      |  [Server Application](use-powershell-topology-menu.md#server-application)       |
|Simple URL       |    [Simple URL](use-powershell-topology-menu.md#simple-url)     |
|Trusted Application       |    [Trusted Application](use-powershell-topology-menu.md#trusted-application)     |
