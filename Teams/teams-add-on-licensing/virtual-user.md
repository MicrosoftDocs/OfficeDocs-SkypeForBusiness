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
description: Learn about how to assign Teams Phone Resource Account licenses to resource accounts in your organization.
---

# Microsoft Teams Phone Resource Account licenses

In Microsoft Teams, all auto attendants and call queues require an associated resource account. Each resource account must be assigned a *Microsoft Teams Phone Resource Account* license to ensure they are correctly identified by the system and proper functionality, *regardless of whether the resource account will be assigned a telephone number*. Organizations with a subscription that includes Teams Phone are automatically allocated a certain amount of Phone Resource accounts licenses at no additional cost.  A Microsoft calling plan is not required unless you want to be able to dial out using that resource account (see [Plan for Teams Auto attendant and call queues](../plan-auto-attendant-call-queue.md#prerequisites) ).

> [!NOTE]
> Previously, a Phone Resource Account license (also known as a virtual user license) was only required in order to assign a phone number to a resource account. Going forward, however, all resource accounts, regardless of whether they will be assigned a phone number, must be assigned a Phone Resource Account license. In addition, do not assign a regular Phone System license to a resource account. If you currently have resource accounts configured with regular Phone System license, you must switch to a resource account, as described below
 

## Resource Account license allocation

Your organization is allotted *Microsoft Teams Phone Resource Account* licenses depending on its overall size. Any organization that has a subscription with Teams Phone features, such as Teams Phone Standard and Teams Phone with Calling Plan licenses, has 25 Resource Account licenses available at no cost. For every 10 user licenses of Teams Phone Standard or Teams Phone with Calling Plan in your organization, one more *Microsoft Teams Phone Resource Account* license becomes available.  Most organizations will have enough Resource Account licenses based on this scaling plan. In the event more *Microsoft Teams Phone Resource Account* licenses are required, customers have the option to purchase additional *Microsoft Teams Phone Resource Account* licenses beyond the standard allocation through their Microsoft account representative.


### License allocation example

Contoso, Inc. purchased 600 licenses that include Phone System (one for each employee). Contoso is allotted an initial 25 plus 60 *Microsoft Teams Phone Resource Account* licenses, 85 in total. Their organization has 90 call queues and auto attendants that have phone numbers. They need to assign all the *Microsoft Teams Phone Resource Account* licenses and purchase five additional *Microsoft Teams Phone Resource Account* licenses. 

## How to obtain Microsoft Teams Phone Resource Account licenses

1. Sign in to the Microsoft 365 admin center.
2. Go to **Billing** > **Purchase services** > **Add-ons**.
3. Scroll to find the **Microsoft Teams Phone Resource Account** license. Select **Buy now**.

   > [!NOTE]
   > Keep in mind, even if you are within your allocation, you must still **Buy** the license even though it has a cost of zero.

## Change an existing resource account to use a Microsoft Teams Phone Resource Account license

If you have exisitng resource accounts using a *Teams Phone Standard* license, you must switch to using to a *Microsoft Teams Phone Resource Account* license:

1. Get the new *Microsoft Teams Phone Resource Account* license.
2. Follow the linked steps in the Microsoft 365 admin center to [Move users to a different subscription](/microsoft-365/admin/manage/assign-licenses-to-users#move-users-to-a-different-subscription).

> [!WARNING]
> Always remove a full *Teams Phone Standard* license and assign the *Microsoft Teams Phone Resource Account* license in the same license activity. If you remove the old license, save the account changes, add the new license, and then save the account settings again, the resource account may no longer function as expected. If this happens, we recommend you create a new resource account for the *Microsoft Teams Phone Resource Account* license and remove the broken resource account.

## Related information

[Auto Attendant and Call Queues Service Update](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Auto-Attendant-and-Call-Queues-Service-Update/ba-p/564521)

[Manage resource accounts in Microsoft Teams](../manage-resource-accounts.md)
