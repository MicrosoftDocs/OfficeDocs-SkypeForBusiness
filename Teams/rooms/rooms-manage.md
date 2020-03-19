---
title: "Manage Microsoft Teams Rooms"
ms.author: dstrome
author: dstrome
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
f1.keywords:
- NOCSH
localization_priority: Normal
ms.assetid: 39d7dc65-22c3-400f-91f1-87ed2fd792b6
ms.collection: 
  - M365-collaboration
description: "Management overview for Microsoft Teams Rooms."
---

# Manage Microsoft Teams Rooms

If you have Microsoft Teams Rooms-certified consoles in your organization, you can manage them from a central location using the Microsoft Teams admin center. You can:

- Perform device management like restarting or blocking devices, downloading device logs, and applying software updates
- Apply Teams-specific settings
- Check the health status of Microsoft Teams Room devices and their peripherals
- Review current and past meeting activity (such as the number of participants and what Teams features were used)
- See peripherals (such as cameras and projectors) connected to a Microsoft Teams Room device

If you have more than one Teams Rooms console, you can do most actions on multiple consoles at the same time. For example, you can set Teams app configuration on all of your consoles at the same time.

To manage Teams Rooms consoles, open the [Microsoft Teams admin center](https://admin.teams.microsoft.com) and go to **Devices** > **Teams Rooms**.

> [!IMPORTANT]
> To manage consoles using the Teams admin center, you need to be assigned the Teams Service Administrator role.

## Change console settings

You can change settings on one or more consoles in your organization. To change console settings, select the console or consoles you want to manage and then select **Settings**. A new pane will open with all of the settings you can change on your consoles. The following table lists the settings you can change using the Teams admin center. Some settings are only available when you select a single console. 

If you select more than one console, settings that support bulk-editing show the two following options.

- **Keep existing value** If you choose this option, no changes will be made to the setting on the consoles you selected.
- **Replace existing value with** If you choose this option, you can update the setting on the consoles you selected with the value you provide.
    > [!CAUTION]
    > Existing values on the settings you choose to update will be replaced with the value you provide. If you want to add to a list of existing values, you need to include the existing values with the value you want to add. For example, if a setting has an existing domain list of `contoso.com, fabrikam.com`, and you want to add `northwindtraders.com`, the value you need to provide would be `contoso.com, fabrikam.com, northwindtraders.com`.
    >
    > If you select multiple consoles, the setting on all of the consoles you select will be changed to the value you provide. If consoles have different values for a setting, they'll all be updated to the same value.

| Setting                                                      | Description | Accepted values                                        | Supports bulk edit |
|--------------------------------------------------------------|-------------|--------------------------------------------------------|--------------------|
| *Account*                                                    |             |                                                        |                    |
| **Email**                                                    |             | Email address                                          | No                 |
| **Password**                                                 |             | Password                                               | No                 |
| **Supported meeting mode**                                   |             | On, Off                                                | Yes                |
| **Modern authentication**                                    |             | On, Off                                                | Yes                |
| **Exchange address**                                         |             | Email address                                          | No                 |
| **Domain\username (optional)**                               |             | Account domain and user name                           | No                 |
| **Configure domain**                                         |             | Comma-separated list                                   | Yes                |
| *Meetings*                                                   |             |                                                        |                    |
| **Automatic screen sharing**                                 |             | On, Off                                                | Yes                |
| **Show meeting names**                                       |             | On, Off                                                | Yes                |
| **Auto-leave if everyone else left meeting**                 |             | On, Off                                                | Yes                |
| **Join third-party meetings**                                |             | Off, Cisco Webex only, Zoom only, Cisco Webex and Zoom | Yes                |
| *Device*                                                     |             |                                                        |                    |
| **Dual monitor mode**                                        |             | On, Off                                                | Yes                |
| **Allow content duplication**                                |             |                                                        | Yes                |
| **Swap screens**                                             |             | N/A                                                    | No                 |
| **Bluetooth beaconing**                                      |             | On, Off                                                | Yes                |
| **Automatically accept proximity-based meeting invitations** |             |                                                        | Yes                |
| **Send logs with feedback**                                  |             | On, Off                                                | Yes                |
| *Peripherals*                                                |             |                                                        |                    |
| **Conferencing microphone**                                  |             |                                                        | No                 |
| **Conferencing speaker**                                     |             |                                                        | No                 |
| **Default volume**                                           |             |                                                        | No                 |
| **Default speaker**                                          |             |                                                        | No                 |
| **Default volume**                                           |             |                                                        | No                 |
| **Content camera**                                           |             |                                                        | No                 |
| *Theming*                                                    |             |                                                        |                    |
| **Select a theme**                                           |             | Default, Upload custom theme image                     | Yes                |

## Console restart options

Some changes to console settings will only take effect after the consoles have been restarted. When you make changes that need a restart, you can choose whether to restart the consoles immediately or schedule a restart. Here are the available restart options:

- **Immediate restart** If you choose this option, all of the consoles you're making changes to will restart as soon as you select this option.
- **Scheduled restart** If you choose this option, you can restart the consoles you're making changes to at a time that's less disruptive to your organization.
  - **Select date and time** - Choose the specific date and time to restart the console. The date and time you choose is local to the console being restarted. 
  - **Leave update for nightly reboot** Consoles are restarted nightly to perform maintenance. Changes you make to consoles will be applied during this restart.
  - **Update as soon as device is not in use** Use this option if you want to apply changes as soon as possible but don't want to interrupt in-progress meetings.

> [!CAUTION]
> Consoles in use at the time of a restart will become unavailable for the duration of the restart process. They'll be disconnected from in-progress meetings and won't be available to join new meetings.