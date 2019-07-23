---
title: "Phone System -  Virtual User licenses "
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
description: "Learn about free virtual user licenses."
---

# Phone System - Virtual User license  

Starting July 2nd, 2019, an organization with Phone System licensed users can now obtain and assign either a free Phone System - Virtual User license or a paid Phone System user license to resource accounts.  A Calling Plan is no longer required.  All auto attendants or call queues require an associated  resource account, but only those resource accounts that will be assigned a phone number need a free Phone System - Virtual User license or a paid Phone System user license.

> [!TIP]
> A Phone System - Virtual User license is not needed for resource accounts that will be used with nested auto attendants or call queues that don't have a phone number assigned. See the following diagram for reference: 

![virtual user licenses](../media/resource-account.png)

## Virtual User license scaling

Your organization is alotted a certain number of Phone System - Virtual User licenses depending on its overall size. There are 25 Virtual User licenses available to any organization that has at least one license that includes Phone System or has Phone System added. For every additional 10 Phone System user licenses in your organization, an additional Phone System - Virtual User license is made available.

If your organization uses up its Phone System - Virtual User licenses in creating auto attendant or call queue nodes, you can still use the paid Phone system licenses with a resource account, but most organizations will have enough Virtual User licenses.  

### License scaling example

Contoso, Inc. purchased 600 Phone System licenses, so they are alotted an initial 25 and an aditional 60 Phone System - Virtual User licenses, for a total of 85 Phone System - Virtual User licenses.  Their organization has a total of 150 call queues and auto attendants that have phone numbers, so they will need to assign all the Phone System - Virtual User licenses and purchase 65 Phone System licenses and assign them to the resource accounts linked to the remaining call queues and auto attendants.  

Contoso may want to redesign the auto attendant and call queue system to use fewer phone numbers and more nested nodes that don't need a phone number or any license. An auto attendant node or call queue that an organization's callers only access from a main auto attendant or another nested auto attendant won't need a phone number, and this will simplify the implementation and reduce costs. 


## How to acquire Phone System - Virtual User licenses 

1. Sign in to the Microsoft 365 admin center.
2. Go to **Billing** > **Purchase services** > **Add-on subscriptions**
3. Scroll to the end - you will see a "Phone System - Virtual User" license. Select **Buy now**.

> [!WARNING]
> Keep in mind you still need to **Buy** the license even though it has a cost of zero. 

## Change an existing resource account to use a Phone System - Virtual User license

If you decide to switch the licenses on your existing resource account from a Phone System license to a Phone System - Virtual User license, first you'll need to get the Phone System - Virtual User license, then follow the linked steps in the Microsoft 365 Admin center to [Move users to a different subscription](https://docs.microsoft.com/en-us/office365/admin/subscriptions-and-billing/assign-licenses-to-users?redirectSourcePath=%252farticle%252f997596b5-4173-4627-b915-36abac6786dc&view=o365-worldwide#move-users-to-a-different-subscription). 

> [!WARNING]
> Always remove a full Phone System License and assign the Phone System - Virtual User license in the same license activity. If you remove the old license, save the account changes, add the new license, and then save the account settings again, the resource account may no longer function as expected. If this happens, we recommend you create a new resource account for the Phone System - Virtual User license and remove the broken resource account.  

## Related information

[Auto Attendant and Call Queues Service Update](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Auto-Attendant-and-Call-Queues-Service-Update/ba-p/564521)

[Manage resource accounts in Microsoft Teams](../manage-resource-accounts.md)
