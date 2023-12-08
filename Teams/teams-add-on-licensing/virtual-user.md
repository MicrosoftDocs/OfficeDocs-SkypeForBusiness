---
title: Microsoft Teams Phone Resource Account licenses
author: DaniEASmith
ms.author: danismith
manager: pamgreen
ms.reviewer: roykuntz
ms.date: 02/24/2023
ms.topic: reference
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - tier1
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.custom: 
  - Licensing
  - LIL_Placement
  - admindeeplinkMAC
description: Learn how to assign Microsoft Teams Phone Resource Account licenses to resource accounts for auto attendants and call queues in your organization.
---

# Microsoft Teams Phone Resource Account licenses

In Microsoft Teams, all auto attendants and call queues require an associated resource account. Each resource account must be assigned a **Microsoft Teams Phone Resource Account** license to ensure they're correctly identified by the system and properly function, *regardless of whether the resource account will be assigned a telephone number*.

Organizations with a subscription that includes Teams Phone are allocated a certain amount of **Teams Phone Resource Account** licenses at no extra cost. A Microsoft calling plan isn't required unless you want to be able to dial out using that resource account. For more information, see [Plan for Teams auto attendant and call queues](../plan-auto-attendant-call-queue.md#prerequisites).

The **Teams Phone Resource Account** license should never be assigned to users that aren't resource accounts.

> [!NOTE]
> All resource accounts must be assigned a **Teams Phone Resource Account** license, regardless of whether they'll be assigned a phone number or not.
>
> If you're currently using resource accounts that aren't assigned any license, you should revisit them to ensure they're assigned a **Teams Phone Resource Account** license.
>
> Don't assign a **Teams Phone Standard** license to a resource account. If you currently have resource accounts configured with **Teams Phone Standard** licenses, you must [switch to a **Teams Phone Resource Account** license as described below](#change-an-existing-resource-account-to-use-a-microsoft-teams-phone-resource-account-license).

## Resource Account license allocation

Your organization is allotted **Teams Phone Resource Account** licenses based on its overall size. Any organization that has a subscription with Phone System features, such as **Teams Phone Standard**, **Teams Phone with Calling Plan**, and **Teams Shared Devices** licenses, is allocated 25 **Teams Phone Resource Account** licenses available at no cost.

For every 10 user licenses of **Teams Phone Standard**, **Teams Phone with Calling Plan**, or devices with **Teams Shared Devices** license in your organization, one more **Teams Phone Resource Account** license becomes available.  Most organizations will have enough **Teams Phone Resource Account** licenses based on this scaling plan.

In the event more **Teams Phone Resource Account** licenses are required, you can purchase more **Teams Phone Resource Account** licenses beyond the standard allocation through EA, EAS, EES, CSP, Web Direct, NCE – Customer led, and NCE – Partner led or your Microsoft account representative at a cost.

Your allocation of **Teams Phone Resource Account** licenses is not automatically added to your tenant. You will need to go through the purchasing process for **Teams Phone Resource Account** licenses. Licenses within your allocation of **Teams Phone Resource Account** licenses will be zero cost. Any **Teams Phone Resource Account** license that exceeds your allocation of licenses will have a cost.

### License allocation example

Contoso, Inc. purchased 500 licenses that include Phone System (one for each employee) and has 100 devices licensed with the **Teams Shared Devices** license. Contoso is allotted an initial 25 plus 60 **Teams Phone Resource Account** licenses, 85 in total. Their organization has 90 call queues and auto attendants. They need to assign all the **Teams Phone Resource Account** licenses and purchase five extra **Teams Phone Resource Account** licenses.

## How to obtain Microsoft Teams Phone Resource Account licenses

You obtain Teams Phone Resource Account licenses from the same purchasing channel you purchased the subscription containing Teams Phone. For example, if you purchased Resource Account licenses through an Enterprise Agreement (EA), you need to order through EA.

For Web Direct customers:
1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
1. Go to **Billing** > [**Purchase services**](https://go.microsoft.com/fwlink/p/?linkid=868433) > **Add-ons**.
    > [!NOTE]
    > If **Purchase Services** isn't available, go to **Marketplace** and search for *Resource*. Select **Microsoft Teams Phone Resource Account**.
1. Scroll to find the **Microsoft Teams Phone Resource Account** license.
1. Select the **Details** button.
1. Choose the number of licenses you wish to purchase and your billing frequency.
1. Select the **Buy** button.
1. Fill in the purchasing details.
1. Select the **Place order** button.

   > [!NOTE]
   > Keep in mind, even if you're within your allocation, you must still **Buy** the license even though it has a cost of zero.

## Change an existing resource account to use a Microsoft Teams Phone Resource Account license

If you have existing resource accounts using a **Teams Phone Standard** license, you must switch to using to a **Teams Phone Resource Account** license:

1. Purchase the new **Teams Phone Resource Account** license.
2. Follow the linked steps in the Microsoft 365 admin center to [Move users to a different subscription](/microsoft-365/admin/manage/assign-licenses-to-users#move-users-to-a-different-subscription).

> [!WARNING]
> Always remove a **Teams Phone Standard** license and assign the **Teams Phone Resource Account** license in the same license activity. If you remove the old license, save the account changes, add the new license, and save the account settings again, the resource account may no longer function as expected, like your organization's auto attendants and call queues not working anymore.
>
> If this happens, we recommend you create a new resource account using the **Teams Phone Resource Account** license and remove the broken resource account.

## Related information

[Auto Attendant and Call Queues Service Update](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Auto-Attendant-and-Call-Queues-Service-Update/ba-p/564521)

[Manage resource accounts in Microsoft Teams](../manage-resource-accounts.md)
