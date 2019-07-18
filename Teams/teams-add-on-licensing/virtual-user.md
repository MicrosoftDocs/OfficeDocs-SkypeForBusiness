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

Starting July 2nd, 2020, licensed users will no longer need to assign a full Phone System user License to Resource Accounts that are used with Call Queues or Auto Attendants. 

You must either buy a Phone System license or use a Phone System - virtual user license for resource accounts that will have an assigned service phone number, as well as a Calling Plan. You need three licenses to be assigned to a resource account: Phone System (either regular or Virtual User), Calling Plan, and Communication Credits.

## Free Virtual License scaling

The number of free licenses your organization has to assign phone numbers to call queues or auto attendants depends on the overall size. There are 25 free licenses available to any organization that has a license that includes Phone System or has Phone System added to its licensing. For every 10 Phone System users in your organization, an additional free Virtual User license is available.

If your organization uses up its free licenses in creating auto attendant or call queue nodes, you'll have to use the paid licenses.  

You can also add Phone System and a Calling Plan to a Small Business Essentials license.

## Virtual User License customers: How to  buy

1. Sign in to the Microsoft 365 admin center.
2. Go to **Billing** > **Purchase services** > **Add-on subscriptions**
3. Scroll to the end - you will see a "Phone System - Virtual User" license. Select **Buy now**.

Keep in mind you still need to **Buy** the license even though it has a cost of zero. If you don't see the license, it may not be available to your tenant yet.

## Changing an existing resource account to use a Virtual User License

If you decide to switch the licenses on your existing resource account from a Phone system license to a Virtual User license, you'll need to  buy the free Virtual User License, then follow the linked steps in the Microsoft 365 Admin center to [Move users to a different subscription](https://docs.microsoft.com/en-us/office365/admin/subscriptions-and-billing/assign-licenses-to-users?redirectSourcePath=%252farticle%252f997596b5-4173-4627-b915-36abac6786dc&view=o365-worldwide#move-users-to-a-different-subscription). 

> [!WARNING]
> Remove a full Phone System License and assign the Virtual Phone System license in the same license activity. If you remove the old license, save the account changes, add the new license, and then save the account settings again, the resource account may no longer function as expected.  


## Related information

[Auto Attendant and Call Queues Service Update](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Auto-Attendant-and-Call-Queues-Service-Update/ba-p/564521)