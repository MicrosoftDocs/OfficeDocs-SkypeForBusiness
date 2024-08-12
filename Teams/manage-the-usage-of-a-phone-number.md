---
title: "Manage the usage of a phone number"
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: garciadaniel
ms.date: 01/29/2024
ms.topic: article
ms.assetid: 
ms.tgt.pltfrm: cloud
audience: admin
ms.service: msteams
search.appverid: 
ms.collection: 
- M365-voice
- m365initiative-voice
- Tier1
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - Calling Plans
description: "Learn how to change the usage of a phone number to be used as either a service number or a user number."
---

# Manage the usage of a phone number

You might want to change the usage of a phone number after it was acquired or ported into your organization. You can change the usage of user and service numbers by using the Teams admin center.

There are three types of usages:

- User number assigned directly to a user.
- Service number assigned to an Auto attendant or Call queue.
- Service number assigned to an Audio conferencing bridge.

For more information about types of phone numbers, see [Manage phone numbers for your oranization](manage-phone-numbers-landing-page.md).

Before changing the usage of a number:

- Be sure you have the right licenses for the target type of number usage. For more information, see [How many numbers can you get](how-many-phone-numbers-can-you-get.md). 

- Be aware that you can only assign toll-free numbers to voice apps (Auto attendants and Call queues) and Audio conferencing bridges.

## How to manage the usage of a phone number

To change the usage of a phone number by using the Teams admin center:

1. Open the Microsoft Teams admin center and log in with a Teams Telephony Administrator or higher account. 

2. In the left navigation, select **Voice** \> **Phone numbers**.

3. On the **Phone numbers** page, choose an unassigned number in the list, and then select **Change usage**.

   If you don't see a **Change usage** option, check the following:

   - Make sure you're selecting an unassigned number before trying to change its usage. The value of the **Assignment status** column should be **Unassigned.** Otherwise, the option isn't visible. 
   - If the number is currently assigned, you need to [remove the phone number from a user](/MicrosoftTeams/assign-change-or-remove-a-phone-number-for-a-user#remove-a-phone-number-from-a-user) or resource account first. To unassign a number from a conference bridge, see [Change numbers on your Audio Conferencing bridge](change-the-phone-numbers-on-your-audio-conferencing-bridge.md#steps-when-youre-unassigning-a-service-phone-number-for-a-conferencing-bridge).
   - You must have more than one type of usage in the **Available usages** column. Otherwise, you can't change the number type through the Teams admin center.

4. In the **Change usage** pane, open the list of available usages for the phone number, and then select the intended option.

   The list only displays usages that are available for the telephone number, depending on its number type (geographic, non-geographic, or toll-free) and supplier. You can quickly review the available usages for each phone number by setting the **Available usages** column in the Phone numbers table to visible.

5. Select **Apply** to set the Licensed usage.

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. To learn more, see [About administrator roles in the Microsoft 365 admin center](/microsoft-365/admin/add-users/about-admin-roles) and [Teams administrator roles](using-admin-roles.md).

## Still need assistance?

If you still need assistance, contact the [TNS Service Desk](/MicrosoftTeams/manage-phone-numbers-for-your-organization/contact-tns-service-desk).

## Related articles

[Manage phone numbers for your organization](manage-phone-numbers-landing-page.md)

[Manage phone numbers for users](assign-change-or-remove-a-phone-number-for-a-user.md)


