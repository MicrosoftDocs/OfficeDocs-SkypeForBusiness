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
description: Learn about how to develop and execute ongoing maintenance and operations to ensure that your Microsoft Teams Rooms systems are available for your users.
ms.custom: seo-marvel-apr2020
---

# Manage Microsoft Teams Rooms

If you have Microsoft Teams Rooms-certified consoles in your organization, you can manage them from a central location using the Microsoft Teams admin center. You can:

- Perform device management like restarting or blocking devices, downloading device logs, and applying software updates
- Apply Teams-specific settings
- Check the health status of Microsoft Teams Room devices and their peripherals
- Review current and past meeting activity (such as the number of participants and what Teams features were used)
- See peripherals (such as cameras and projectors) connected to a Microsoft Teams Room device

To manage Teams Rooms consoles, open the [Microsoft Teams admin center](https://admin.teams.microsoft.com) and go to **Devices** > **Teams Rooms**.

> [!IMPORTANT]
> To manage consoles using the Teams admin center, you need to be assigned the Teams Service Administrator role.

## Making changes to consoles

If you have more than one Teams Rooms console, you can do most actions on multiple consoles at the same time. For example, you can set Teams app configuration on all of your consoles at the same time.

### Console settings

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
| **Supported meeting mode**                                   | | Skype for Business (default) and Microsoft Teams<br>Skype for Business and Microsoft Teams (default)<br>Skype for Business Only|Yes|
| **Modern authentication**                                    |             | On<br>Off                                              | Yes                |
| **Exchange address**                                         |             | Email address                                          | No                 |
| **Domain\username (optional)**                               |             | Account domain and user name                           | No                 |
| **Configure domain**                                         |             | Comma-separated list                                   | Yes                |
| *Meetings*                                                   |             |                                                        |                    |
| **Automatic screen sharing**                                 |             | On<br>Off                                              | Yes                |
| **Show meeting names**                                       |             | On<br>Off                                              | Yes                |
| **Auto-leave if everyone else left meeting**                 |             | On<br>Off                                              | Yes                |
| **Join third-party meetings**                                |             | Off<br>Cisco Webex only<br>Zoom only<br>Cisco Webex and Zoom | Yes                |
| *Device*                                                     |             |                                                        |                    |
| **Dual monitor mode**                                        |             | On<br>Off                                              | Yes                |
| **Allow content duplication**                                |             |                                                        | Yes                |
| **Swap screens**                                             |             | N/A                                                    | No                 |
| **Bluetooth beaconing**                                      |             | On<br>Off                                              | Yes                |
| **Automatically accept proximity-based meeting invitations** |             |                                                        | Yes                |
| **Send logs with feedback**                                  |             | On<br>Off                                              | Yes                |
| *Peripherals*                                                |             |                                                        |                    |
| **Conferencing microphone**                                  |             |                                                        | No                 |
| **Conferencing speaker**                                     |             |                                                        | No                 |
| **Default volume**                                           |             | 0-100                                                  | No                 |
| **Default speaker**                                          |             |                                                        | No                 |
| **Default volume**                                           |             | 0-100                                                  | No                 |
| **Content camera**                                           |             |                                                        | No                 |
| *Theming*                                                    |             |                                                        |                    |
| **Select a theme**                                           |             | Default<br>Upload custom theme image                   | Yes                |

### Console updates

You can apply updates to one or more consoles at the same time. Updates you can apply include updates to the Teams Room app, Teams agent, Windows 10, console firmware, and so on. By default, all available updates for a console are selected when you choose to update your consoles. If you don't want to apply an update to a specific console, you can deselect that update. 

To apply updates to one or more consoles, do the following:

1. In **Devices** > **Teams Rooms**, select the consoles you want to update and then select **Update**.
2. In the **Available updates** pane that appears, you can open each console's details to see which updates will be applied to that console.
3. If you don't want to apply an update to a console, deselect the update for that console. If you want to deselect an update on multiple consoles, you need to open each console individually and deselect the update.
4. After you've selected the updates you want to apply, choose your restart option (see [Console restart options](#console-restart-options) for more information). The selected consoles will be updated at the time you specify.

### Console restart options

Some changes to console settings will only take effect after the consoles have been restarted. When you make changes that need a restart, you can choose whether to restart the consoles immediately or schedule a restart. Here are the available restart options:

- **Immediate restart** If you choose this option, all of the consoles you're making changes to will restart as soon as you select this option.
- **Scheduled restart** If you choose this option, you can restart the consoles you're making changes to at a time that's less disruptive to your organization.
  - **Select date and time** - Choose the specific date and time to restart the console. The date and time you choose is local to the console being restarted. 
  - **Leave update for nightly reboot** Consoles are restarted nightly to perform maintenance. Changes you make to consoles will be applied during this restart.
  - **Update as soon as device is not in use** Use this option if you want to apply changes as soon as possible but don't want to interrupt in-progress meetings.

> [!CAUTION]
> Consoles in use at the time of a restart will become unavailable for the duration of the restart process. They'll be disconnected from in-progress meetings and won't be available to join new meetings.

## View console information

From the Teams admin center, you an view the overall status of all consoles in your organization and view details of each console individually.

### Teams Rooms system dashboard

The Teams Rooms system dashboard shows you the status and health of all of your consoles at a glance.

### Console details view

To view detailed information about a console, select its name from the console list.

#### Peripherals

#### Health

#### Details

#### Meetings

#### History


