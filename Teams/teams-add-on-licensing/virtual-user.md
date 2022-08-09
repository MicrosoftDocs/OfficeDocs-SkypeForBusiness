---
title: Microsoft Teams Phone Resource Account licenses
ms.author: dstrome
author: dstrome
manager: serdars
ms.reviewer: waseemh
ms.topic: reference
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-collaboration
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.custom: 
  - Licensing
  - LIL_Placement
  - seo-marvel-apr2020
description: Learn about how to assign free Teams Phone Resource Account licenses or a paid Teams Phone Standard user licenses to resource accounts in your organization.
---

# Microsoft Teams Phone Resource Account licenses

Organizations with Teams Phone Standard or Teams Phone with Calling Plan licensed users can assign either a free *Microsoft Teams Phone Resource Account* license or a paid *Teams Phone Standard* user license to resource accounts. A Microsoft calling plan isn't always required (see [Plan for Teams Auto attendant and call queues](../plan-auto-attendant-call-queue.md#prerequisites) for prerequisites when transferring calls to an external phone number).

All auto attendants and call queues require an associated resource account. Resource accounts that require a phone number need either a free *Microsoft Teams Phone Resource Account* license or a paid *Teams Phone Standard* user license before a phone number can be applied to the resource account.

> [!TIP]
> No license is needed for resource accounts that will be used with nested auto attendants or call queues that don't have a phone number assigned.

## Resource Account license allocation

Your organization is allotted *Microsoft Teams Phone Resource Account* licenses depending on its overall size. Any organization that has at least one license with Teams  Phone System features, including Teams Phone Standard and Teams Phone with Calling Plan licenses, has 25 Resource Account licenses available at no cost. When you add 10 Teams Phone Standard or Teams Phone with Calling Plan user licenses in your organization, one more *Microsoft Teams Phone Resource Account* license becomes available.

> [!NOTE]
> Teams Phone Standard and Teams Phone with Calling Plan are add-on licenses available to all Microsoft 365 subscribers. Teams Phone Standard licenses are also included as part of Microsoft 365 E5 plans.

If your organization uses up the free *Microsoft Teams Phone Resource Account* licenses in creating auto attendant or call queue nodes, you can still use the paid *Teams Phone Standard* licenses with a resource account. Most organizations will have enough Resource Account licenses based on the scaling plan.

### License allocation example

Contoso, Inc. purchased 600 licenses that include Phone System (one for each employee). Contoso is allotted an initial 25 plus 60 *Microsoft Teams Phone Resource Account* licenses, 85 in total. Their organization has 90 call queues and auto attendants that have phone numbers. They need to assign all the *Microsoft Teams Phone Resource Account* licenses and obtain five regular-priced *Teams Phone Standard* licenses.

Contoso should consider redesigning the auto attendant and call queue system. If they use fewer phone numbers and more nested nodes that don't need a phone number, they simplify the implementation and reduce costs.

## How to buy Microsoft Teams Phone Resource Account licenses

1. Sign in to the Microsoft 365 admin center.
2. Go to **Billing** > **Purchase services** > **Add-ons**.
3. Scroll to find the **Microsoft Teams Phone Resource Account** license. Select **Buy now**.

   > [!NOTE]
   > Keep in mind you must still **Buy** the license even though it has a cost of zero.

## Change an existing resource account to use a Microsoft Teams Phone Resource Account license

If you decide to switch the license on your resource account from a *Teams Phone Standard* license to a *Microsoft Teams Phone Resource Account* license:

1. Get the new *Microsoft Teams Phone Resource Account* license.
2. Follow the linked steps in the Microsoft 365 admin center to [Move users to a different subscription](/microsoft-365/admin/manage/assign-licenses-to-users#move-users-to-a-different-subscription).

> [!WARNING]
> Always remove a full *Teams Phone Standard* license and assign the *Microsoft Teams Phone Resource Account* license in the same license activity. If you remove the old license, save the account changes, add the new license, and then save the account settings again, the resource account may no longer function as expected. If this happens, we recommend you create a new resource account for the *Microsoft Teams Phone Resource Account* license and remove the broken resource account.

## Related information

[Auto Attendant and Call Queues Service Update](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Auto-Attendant-and-Call-Queues-Service-Update/ba-p/564521)

[Manage resource accounts in Microsoft Teams](../manage-resource-accounts.md)
