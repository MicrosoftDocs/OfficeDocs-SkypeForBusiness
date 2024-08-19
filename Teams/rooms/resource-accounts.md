---
title: Microsoft Teams Rooms Resource Accounts
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: sohailta
ms.date: 08/08/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords: 
  - NOCSH
ms.custom: 
  - Licensing
  - LIL_Placement
  - seo-marvel-apr2020
description: Learn how to see the status of your resource accounts information; and the information pertaining to mailbox settings, location, and license.
---

# Resource accounts

Resource accounts is a feature that enables you to see the status of your resource accounts for Teams Rooms; and the information pertaining to mailbox settings, location, and license.

> [!IMPORTANT]
> If you're setting up your Pro Management Portal for the first time, you need to open Planning > Inventory and select the **Get Data** button to connect the Pro Management Portal to your resource accounts in Microsoft 365. Allow 15 minutes for replication once you select the **Get Data** button to see your resource accounts in the portal.

> [!IMPORTANT]
> The option of managing resource accounts isn't available for GCC tenants.

## View resource accounts

The **Resource Accounts** page shows you all the resource accounts that your organization created for your Teams Rooms. You can see the account name, UPN, and location in different columns for each resource account.

The **Resource Accounts** page also has a **Refresh** option on the command bar to fetch newly created resource accounts from Entra.

### View settings for each resource account

Select a resource account; you're taken to the page showing its settings and other details. In this page, you can see the settings of the account and its mailbox; and information pertaining to the resource account's location and license.

:::image type="content" source="../media/account-configuration-tab.png" alt-text="Screenshot that shows the Account Configuration tab." lightbox="../media/account-configuration-tab.png":::

To know more about the settings of the account or its mailbox, hover over the setting with the cursor, as shown in the following screenshot:

:::image type="content" source="../media/viewing-information-of-setting-by-mouse-hover.png" alt-text="Screenshot that shows the information of a setting displayed on a mouse-hover over the setting." lightbox="../media/viewing-information-of-setting-by-mouse-hover.png":::

On the same page, that is, the page containing the settings and other details, you can also see the status of the resource account. The **Status** label at the top shows whether a resource account is correctly set up to be used with Teams Rooms.

:::image type="content" source="../media/status-of-resource-account.png" alt-text="Screenshot that shows the status of a resource account." lightbox="../media/status-of-resource-account.png":::

The following statuses are supported for resource account settings:

- **No Action Needed**: This status implies that the account and mailbox settings have been configured as required for Teams rooms.
- **Needs Action**: This status implies that the account hasn't been configured correctly, and that we must review our account information.
- **N/A**: This status implies that the account information isn't available.

## Configure resource accounts

To configure the settings of a resource account and its mailbox, perform the following steps:

1. Select a resource account to navigate to the page containing the resource account's settings and other details.
1. Enable the settings under the **Account settings** and **Mailbox settings** panes.

Once you've configured the settings of the account and its other associated settings, you can navigate to the page displaying the settings and other details to verify the status. You can see that the status has been updated (to **No action needed**), under the **Status** label.

:::image type="content" source="../media/status-updated-on-configuration-completion.png" alt-text="Screenshot that shows the updated status of a resource account whose settings and that of its mailbox has just been configured." lightbox="../media/status-updated-on-configuration-completion.png":::

### View licenses

To view the licenses assigned to a resource account, perform the following steps:

1. Select a resource account and navigate to the page displaying its settings and other details.
1. Select **Licenses** tab. You can view the Teams Rooms licenses that have been assigned to the chosen resource account.

   :::image type="content" source="../media/licenses-assigned-to-resource-account.png" alt-text="Screenshot that shows the page displaying details of licenses assigned to a resource account." lightbox="../media/licenses-assigned-to-resource-account.png":::

### Other information

This section lists crucial alert messages and their descriptions:


|Message  |Description  |
|---------|---------|
|Mailbox settings are not available. You need to be a global admin to get this information. Contact your administrator to get access.     |  This message appears if the users don't have permissions.  Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.|
|An error occurred while loading resource account(s). If the problem persists please contact support.     |   This message appears when an error has occurred while loading accounts.      |
|An error occurred while loading summary, please try again later. If the problem persists please contact support.     | This message appears when an error has occurred while loading stats.       |
|An error occurred while exporting file, please try again later. If the problem persists, please contact support.     | This message appears when an error has occurred while exporting resource accounts.         |
|An error occurred while saving your request, please try again later. If the problem persists, please contact support.     | This message appears when an error has occurred while saving mailbox settings.    |
|Your changes have been saved successfully     |    This message appears when the mailbox settings have been saved successfully.     |
|An error occurred while applying recommended config. Please try again later. If the problem persists, please contact support.     | This message appears when an error has occurred while applying recommended configuration to resource accounts.     |
