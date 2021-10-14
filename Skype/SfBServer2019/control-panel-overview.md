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

Modern Admin Control Panel (MACP) is a component of Skype for Business Server that helps manage the configuration of servers, users, clients, and devices in the environment of an organization.

The MACP had the following releases:

1. **Phase 1 (July 2019)** - Introduced the following features as tabs:

    - **Home**
    - **Users**

2. **Phase 2 (March 2020)** - Introduced the following features as tabs, in addition to the features of **Phase 1**:

    - **Conferencing** 

      > [!NOTE]
      > This tab was introduced in this release, with a few of its sub-tabs - such as **Dial-In-Access Number** - being introduced in subsequent releases.

    - **Federation and External Access**

3. **Cumulative Update (March 2021)** - Introduced the following features as tabs, in addition to the features of **Phase 1** and **Phase 2**: 

    - **Voice Routing**
    - **Voice Features**
    - **Response Group**

## Accessing information of tabs not in New Control Panel

The New Control Panel doesn't have a few tabs present in the Old Control Panel. However, the users can access the information pertaining to those tabs through PowerShell-related cmdlets. For information on the tabs not there in the New Control Panel, see [Tabs not available in New Control Panel](#tabs-not-available-in-new-control-panel).

## Tabs not available in New Control Panel

This section describes the tabs missing in the New Control Panel. For information about the missing tabs, its subtabs, and the data embedded in it, see the table below.

## Client

The **Client** tab is one of the tabs that is not available on the New Control Panel. This tab comprises sub-tabs that facilitate various functionalities, which are described in the table below.

|Sub-tab  |Source of Information for cmdlet  |
|---------|---------|
|Client Version Policy         |    [Client Version Policy](use-powershell-client-tab.md#client-version-policy)     |
|Client Version Configuration      |  [Client Version Configuration](use-powershell-client-tab.md#client-version-configuration)       |
|Test Device     | [Test Device](use-powershell-client-tab.md#test-device)        |
|Device Log Configuration         |    [Device Log Configuration](use-powershell-client-tab.md#device-log-configuration)     |




  



