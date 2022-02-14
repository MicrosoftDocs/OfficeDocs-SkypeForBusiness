---
title: Managing the health of Teams devices
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
ms.reviewer: snchatur
search.appverid: MET150
f1.keywords:
- NOCSH
description: This article will guide you in managing the health of Teams devices, devices that have Microsoft Teams installed on them.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Manage the health of Teams devices

Administrators can monitor the health of devices installed with Microsoft Teams by using health status, which indicates the severity of issues. To check the health of a device, you can go to the device list present under the **Teams Devices** section of the Teams admin center. The health status column in this list indicates the current health status of the device. Selecting that status opens the **Health status panel**, which provides more details about health issues.

Many types of issues can contribute towards device health status, and the Teams admin center system evaluates the severity of these issues as they occur.

The administrator managing the Teams devices for their organization may decide the severity of issues for them isn't the same as the default configuration Teams provides. There's a way for the administrators to customize the severity and the impact on the health of their devices to match their organization's priorities.

Teams Rooms devices have peripherals attached for providing a complete meeting experience, like Speaker, Microphone, Display, Camera. Details about them are available on the device page under the Peripherals and Health tabs. The connectivity of these peripherals impacts the health of the parent device.

## Feature details

When viewing peripheral details on a device page, you'll now see a  **Manage health impact** option. Additionally, administrators can also view the impact each peripheral has on the health of the device.

By default all peripherals are set to have **Critical impact** on the device health. If a peripheral is disconnected, the parent device’s health will become **Critical** and this issue will show up under **Critical issues** in the health status panel.

> [!NOTE]
> The peripheral categories **HDMI ingest** and **Compute** aren't available for customization as they are crucial to the functioning of the parent device.

## How does this work?

1. An administrator can select the peripherals they want to change the health impact for. Then they can select **Manage health impact**. Alternatively they can also find the **Manage health impact** option under the **Peripherals** tab on each peripheral card.
1. The **Health impact** panel will open, and the administrator can select the desired impact level for the selected peripherals and save it.

| Settings Options | Description |
|------------------|-------------|
| **Non-urgent** | When set for a peripheral category (such as a display or a speaker) and the peripheral is disconnected, the health status of the Teams Rooms device will become **Non-urgent** (instead of **Critical**). New issues will be categorized in the **Non-urgent** section of the health status panel.|
| **No Impact** | When set for a peripheral category and the peripheral is disconnected, the health status of the Teams Rooms device will stay **Healthy** (instead of **Critical**). This health issue won't show up in the health status panel.|
| **Critical** | When set for a peripheral category and the peripheral is disconnected, the health status of the Teams Rooms device will become **Critical**. New such issues will be categorized in the **Critical** section of the health status panel.|
| **Reset to default** | When set for a peripheral category, the health impact for that category will be reset to **Critical**. Once this choice is saved, the changes will be applied and health impact will reflect those changes going forward.|

## Applicable device categories

Currently, this feature is available to manage the health impact of peripherals associated with the Microsoft Teams Rooms (Windows) devices.

## Impact on other workflows

If the health impact of the peripherals is reduced in severity, administrators may not notice issues when they happen. You should be mindful of high-priority devices that need close monitoring.

For example if an alert is configured to be triggered for ConfRoom1 if its health becomes **Critical**. The administrator had reduced the health impact of the display and speaker for that meeting room from the default, **Critical**, to **Non-urgent**. Now, if the display is disconnected, the health of ConfRoom1 will become **Non-urgent**. In this case, the alert won't be triggered.
