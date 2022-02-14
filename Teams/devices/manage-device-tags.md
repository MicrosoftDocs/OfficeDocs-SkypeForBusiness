---
title: Manage and filter Microsoft Teams device tags
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: kelsawi
ms.collection: 
  - M365-collaboration
f1.keywords:
- CSH
description: Learn how to manage and filter tags on your Microsoft Teams devices.
ms.localizationpriority: medium
search.appverid: MET150
appliesto: 
  - Microsoft Teams
---

# Manage Microsoft Teams device tags

Device tags in Microsoft Teams let you group, organize, and more easily manage the devices you've deployed in your organization. With the Microsoft Teams admin center, you can add one or more tags to devices, use filters to view devices that match the tag you specify, and then perform actions on the devices that have that tag.

You can add a device tag to more than one device type. However, when you open a device pane in the admin center, only the devices of that type are returned. For example, you can assign the "Corporate" tag to both phones and Teams Rooms devices. If you search for the "Corporate" tag while in **Teams Devices** > **Phones**, only phones are returned. Similarly, if you search for the "Corporate" tag in **Teams Devices** > **Teams Rooms**, only Teams Rooms devices are returned.

To manage device tags, you need to be a Global admin, Teams Service admin, or Teams Device admin. For more information about admin roles, see [Use Microsoft Teams administrator roles to manage Teams](../using-admin-roles.md).

> [!IMPORTANT]
> Device tags are assigned to the resource account that's logged into a device. If you sign a resource account out of one device and then use it to sign in to another device, the device tags are applied to the new device.

## Create, remove, or rename device tags

Using the device tag management panel, you can:

- See all your device tags.
- Create multiple device tags easily and then assign them to devices at a later time. Tags can be up to 25 characters.
- Remove device tags that are no longer needed. Before you can remove a device tag, you'll need to remove it from all of the devices it has been added to.
- Rename device tags. When you rename a device tag, that change is reflected on all the devices it's been added to. Tags can be up to 25 characters.

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate to **Teams Devices** and then choose any device pane, such as **Phones**.
3. Select **Actions** in the upper-right corner of the page and select **All device tags**.
4. To create a device tag, select **+ Add**, provide a value for the device tag, and select the **Save** icon.
5. To remove a device tag, select the ellipsis **...** next to the device tag you want to remove, and select **Delete**.
    > [!NOTE]
    > If you try to remove a device tag that's been added to devices, you'll receive a message asking if you want to remove it from all devices. If you want to do this and continue to remove the device tag, select **Untag devices**.
6. To rename a device tag, select the ellipsis **...** next to the device tag you want to rename, and select **Edit**. Provide a new value for the device tag and select the **Save** icon.

## Add or remove tags on a single device

When you add tags to a device, you can either select an existing tag or create a new one. Tags can be up to 25 characters.

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate to **Teams Devices** and then choose the device pane that contains the device you want to add or remove tags on.
3. Place a check mark next to the device you want to add or remove tags on and select **Manage tags**.
4. If you want to add a tag:
    1. Start typing the tag name you want to add.
    2. If the tag already exists, select it from the list of tags that are returned.
    3. If the tag doesn't exist, select **Add "\<tag name>" as a new tag**. Tags can be up to 25 characters.
5. If you want to remove a tag, select **X** next to the tag you want to remove.
6. Repeat the steps above if you want to add or remove more tags.
7. Select **Apply**.

## Add or remove tags on multiple devices

When you add tags to a device, you can either select an existing tag or create a new one. Tags can be up to 25 characters. If you want to remove a tag from multiple devices, you need to select the Teams user that's associated with the device and remove the tag from the user.

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate to **Teams Devices** and then choose the device pane that contains the devices you want to add or remove tags on.
3. Place a check mark next to the devices you want to add or remove tags on and select **Manage tags**.
4. If you want to add a tag:
    1. Start typing the tag name you want to add in **Manage tags for all devices of Teams users**.
    2. If the tag already exists, select it from the list of tags that are returned.
    3. If the tag doesn't exist, select **Add "\<tag name>" as a new tag**.
5. If you want to remove a tag:
    1. Expand **Select Teams users**.
    2. Expand **\<x> tags** under the name of the Teams user you want to remove tags from.
    3. Select **X** next to the tag you want to remove.
6. Repeat the steps above if you want to add or remove more tags.
7. Select **Apply**.

## Use filters to return devices with a specific tag

If you've added device tags to your devices, you can use them to filter the device list to return only the devices that have had a specified tag added to them. This can be helpful if you just want to view all the devices in a specific room, all the devices of a certain type, or any other criteria you used when adding your tags. You can also perform bulk actions on returned devices, such as applying updates in waves, or setting different configuration policies depending on the groups of devices identified using device tags.

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate to **Teams Devices** and then choose the device pane that contains the devices you want to filter.
3. Select the **Filter** icon.
4. If you only want to specify a single tag, or if you want to find devices that have all the tags you specify, select **Match all of these conditions**.
5. If you want to find devices that match one or more device tags, select **Match any one of these conditions**.
6. Select the **Tag** field and then specify a device tag name in the **Enter a value** field.
7. If you want to add more device tags, select **Add more** and repeat step 6 for each tag you want to add.
8. Select **Apply**.

After you've filtered the devices in your device list, you can perform actions on them as you normally would. For example, you can select them and then assign configurations, edit their settings (if they're Teams Rooms devices), and so on. When you're done, you can remove the filter by selecting the **X**  next to the **Tag** filter entry or by selecting **Clear all** on the right side of the list.
