---
title: "Phone System–Virtual User licenses "
ms.author: jambirk
author: jambirk
manager: serdars
ms.reviewer: waseemh
ms.topic: reference
ms.service: msteams
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
ms.custom:
- Licensing
- LIL_Placement
description: "Learn about free Virtual User licenses."
---

# Phone System–Virtual User license 

Starting July 2, 2019, an organization with Phone System licensed users can now obtain and assign either a free Phone System–Virtual User license or a paid Phone System user license to resource accounts. A Calling Plan is no longer required. All auto attendants or call queues require an associated resource account. Resource accounts that require a phone number need a free Phone System–Virtual User license or a paid Phone System user license before a phone number can be applied to the resource account.

> [!TIP]
> No license is needed for resource accounts that will be used with nested auto attendants or call queues that don't have a phone number assigned. See the following diagram for reference: 

![Virtual User licenses](../media/resource-account.png)

## Virtual User license allocation

Your organization is allotted Phone System–Virtual User licenses depending on its overall size. Any organization that has at least one license including Phone System or has Phone System added has 25 Virtual User licenses available at no cost. When you add 10 Phone System user licenses in your organization, one more Phone System–Virtual User license becomes available.

> [!NOTE]
> Phone System is an add-on license available with Office 365 F1, E1, E3, and Office Premium licenses. Phone System is also included as part of Office 365 E5 licenses.

If your organization uses up the available free Phone System–Virtual User licenses in creating auto attendant or call queue nodes, you can still use the paid Phone system licenses with a resource account. Most organizations will have enough Virtual User licenses based on the scaling plan. 

### License allocation example

Contoso, Inc. purchased 600 licenses that included Phone System (one for each employee). Contoso is allotted an initial 25 plus 60 Phone System–Virtual User licenses, 85 in total. Their organization has 90 call queues and auto attendants that have phone numbers. They need to assign all the Phone System–Virtual User licenses and obtain five regular-priced Phone System licenses. 

Contoso should consider redesigning the auto attendant and call queue system. If they use fewer phone numbers and more nested nodes that don't need a phone number, they simplify the implementation and reduce costs. 

## How to acquire Phone System–Virtual User licenses 

1. Sign in to the Microsoft 365 admin center.
2. Go to **Billing** > **Purchase services** > **Add-on subscriptions**
3. Scroll to the end to find the **"Phone System–Virtual User"** license. Select **Buy now**.

> [!WARNING]
> Keep in mind you must still  **Buy** the license even though it has a cost of zero. 

## Change an existing resource account to use a Phone System–Virtual User license

If you decide to switch the license on your resource account from a Phone System license to a Phone System–Virtual User license: 

1. Get the new Phone System–Virtual User license. 
2. Follow the linked steps in the Microsoft 365 Admin center to [Move users to a different subscription](https://docs.microsoft.com/en-us/office365/admin/subscriptions-and-billing/assign-licenses-to-users?redirectSourcePath=%252farticle%252f997596b5-4173-4627-b915-36abac6786dc&view=o365-worldwide#move-users-to-a-different-subscription). 

> [!WARNING]
> Always remove a full Phone System License and assign the Phone System–Virtual User license in the same license activity. If you remove the old license, save the account changes, add the new license, and then save the account settings again, the resource account may no longer function as expected. If this happens, we recommend you create a new resource account for the Phone System–Virtual User license and remove the broken resource account. 

## Related information

[Auto Attendant and Call Queues Service Update](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Auto-Attendant-and-Call-Queues-Service-Update/ba-p/564521)

[Manage resource accounts in Microsoft Teams](../manage-resource-accounts.md)
