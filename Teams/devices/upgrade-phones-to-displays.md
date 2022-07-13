---
title: "Upgrade Teams phones to Teams displays"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: weizxue
ms.topic: reference
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-voice
search.appverid: MET150
ms.localizationpriority: medium
description: "Learn how to upgrade Teams phones to Teams displays in the Microsoft Teams admin center."
---

# Upgrade Teams phones to Teams displays

> [!IMPORTANT]
> Upgrading to Teams displays is available only on Lenovo ThinkSmart View devices. The information in this article applies only to this device model.  

This article gives you an overview of how to upgrade your Teams phones to Teams display devices in the Microsoft Teams admin center. Doing this allows the devices to provide a rich experience for your users as Teams display devices.

Teams displays are a category of all-in-one dedicated Teams devices with an ambient touchscreen and a hands-free experience powered by Cortana. Teams displays are the evolution of Teams phones. In addition to [features supported by Teams phones](phones-for-teams.md#features-supported-by-teams-phones), Teams displays include features such as an always-on display in which all Teams activity and collaboration options are always available. To learn more about features unique to Teams displays, see [Microsoft Teams displays](teams-displays.md).

## What you need to know about upgrading to Teams displays

### Which Teams phones can be upgraded?

Lenovo ThinkSmart View devices can be upgraded to Teams displays.

### How can I prepare users?

To get your users ready, share [Get started with Teams displays](https://support.microsoft.com/office/get-started-with-teams-displays-ff299825-7f13-4528-96c2-1d3437e6d4e6) with your users to help them get familiar with using Teams displays. We recommend you do this well in advance of the upgrade.

Let them know that there's no changes to their data or preferences after the upgrade. For example, users can access all their meetings, missed calls, and voicemails in Teams displays. 

### What happens after the upgrade?

After you upgrade a Teams phone to a Teams display device, the device is listed on the **Teams displays** page in the **Teams Devices** section of the Microsoft Teams admin center. You manage it in the same way that you manage any other Teams device. To learn more, see [Manage your devices in Teams](device-management.md).

Keep in mind that after you upgrade a Teams phone to a Teams display device, the action can't be reversed. We recommend you first run a pilot with a group of early adopters before you upgrade your entire organization. 

## Upgrade your Teams phones to Teams displays

1. In the left navigation of the Microsoft Teams admin center, go to **Teams Devices** > **Phones**.
2. Select the Teams phones you want to upgrade, and then select **Upgrade**.

    :::image type="content" source="../media/upgrade-phones-to-displays-select-new.png" alt-text="Screenshot showing Teams phones selected for upgrade to Teams displays." lightbox="../media/upgrade-phones-to-displays-select-new.png":::

3. In the **Upgrade to Teams display** dialogue box, select **Schedule upgrade** to set a date and time for the upgrade or **Upgrade now**.

    :::image type="content" source="../media/upgrade-phones-to-displays-upgrade.png" alt-text="Screenshot showing Upgrade to Teams display dialogue box.":::

> [!NOTE]
> If you receive a message that says your selected phones can't be upgraded, check to make sure that you select [phones that support the upgrade](#which-teams-phones-can-be-upgraded), and then try again.

During the upgrade process, the device's firmware is updated to a Teams display device, the device restarts, and is ready for use. When the upgrade is completed, you'll see the device listed on the **Teams displays** page in the Microsoft Teams admin center.

It can take up to an hour for the upgrade to complete. If the process hasn't completed after an hour, retry the upgrade. You can also go to the **History** tab of the device details page to see the status.

## Known issues

### Teams displays have the Default theme instead of the Dark theme

Dark theme support on Teams displays will be available in a future update. Teams phones that use the Dark theme will get the Default theme after the upgrade to Teams displays.

### Some apps are missing from the Home screen

If certain apps are missing from the Home screen after the upgrade, sign out and sign in again. The fix for this will be available in a future update.

## See also

[Introducing Microsoft Teams displays](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/introducing-microsoft-teams-displays/ba-p/1505437)

[Teams displays](teams-displays.md)

[Teams Marketplace](https://office.com/teamsdevices)

[Phones for Teams](phones-for-teams.md)

[IP Phones certified for Microsoft Teams](teams-ip-phones.md)

[Cortana voice assistance in Teams](../cortana-in-teams.md)
