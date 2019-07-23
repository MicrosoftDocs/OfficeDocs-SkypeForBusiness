---
title: "Virtual user licenses "
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

# Virtual User license  

Starting July 2nd, 2019, an organization with Phone System licensed users can now assign a free Virtual User license or a full Phone System user license to resource accounts that are used with Call Queues or Auto Attendants that require a phone number.  A Calling Plan is no longer required. 

> [!TIP]
> A Virtual User license is not needed for resource accounts that will be used with nested auto attendants or call queues that don't have a phone number assigned. 

## Free Virtual license scaling

Your organization is alotted a number of free Virtual User licenses depending on its overall size. There are 25 free licenses available to any organization that has at least one license that includes Phone System or has Phone System added. For every additional 10 Phone System user licenses in your organization, an additional free Virtual User license is made available.

If your organization uses up its free licenses in creating auto attendant or call queue nodes, you can still use the regular Phone system licenses with a resource account, but most organizations will have enough free Virtual User licenses.  

## How to aquire Virtual User licenses 

1. Sign in to the Microsoft 365 admin center.
2. Go to **Billing** > **Purchase services** > **Add-on subscriptions**
3. Scroll to the end - you will see a "Phone System - Virtual User" license. Select **Buy now**.

Keep in mind you still need to **Buy** the license even though it has a cost of zero. 

## Change an existing resource account to use a Virtual User license

If you decide to switch the licenses on your existing resource account from a Phone system license to a Virtual User license, you'll need to  aquire the free Virtual User license, then follow the linked steps in the Microsoft 365 Admin center to [Move users to a different subscription](https://docs.microsoft.com/en-us/office365/admin/subscriptions-and-billing/assign-licenses-to-users?redirectSourcePath=%252farticle%252f997596b5-4173-4627-b915-36abac6786dc&view=o365-worldwide#move-users-to-a-different-subscription). 

> [!WARNING]
> Always remove a full Phone System License and assign the Virtual User license in the same license activity. If you remove the old license, save the account changes, add the new license, and then save the account settings again, the resource account may no longer function as expected. If this happens, we recommend you create a new resource account for the Virtual User license and remove the broken resource account.  

## Related information

[Auto Attendant and Call Queues Service Update](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Auto-Attendant-and-Call-Queues-Service-Update/ba-p/564521)

[Manage resource accounts in Microsoft Teams](../manage-resource-accounts.md)
