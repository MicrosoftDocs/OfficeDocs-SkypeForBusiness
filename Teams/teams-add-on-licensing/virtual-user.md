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
appliesto: Because 
- Microsoft Teams
localization_priority: Normal
ms.custom:
- Licensing
- LIL_Placement
description: "Learn about free virtual user licenses."
---

# Virtual User license

Resouce accounts are used for call routing for auto attendants and call queues twith an external phone number that people can call.

Starting July 2nd, 2019, for resource accounts with an external phone number, an organization with auto attendants and call queues can now use a free Phone System - Virtual user license instead of having to assign a Phone System license that was purchased.

## Free Virtual license scaling

Each organization is given a number of Phone System - Virtual user licenses depending on the number of Phone System licenses that have been already purchased. Each organization will be given 25 Phone System - Virtual user licenses that has one Office 365 license with Phone System or other Office 365 licenses have added Phone System. Then for every 10 Phone System licenses that have been purchased for users an additional Phone System - Virtual user license is added. So, if you have purchased 600 Phone System licenses, you will get an additional 60 Phone System - Virtual user licenses plus the 25 licenses will give you a total of 85 Phone System - Virtual user licenses.

If your organization uses up the number of Phone System - Virtual user licenses when creating resouce accounts used with auto attendants or call queue, you can still assign a Phone system license you bought to a resource account. This means that if you organization exceeds the 85 Phone System - Virtual user licenses that were given, you will need to purchase additional Phone System licenses.

## How to aquire Virtual User licenses 

1. Sign in to the Microsoft 365 admin center.
2. Go to **Billing** > **Purchase services** > **Add-on subscriptions**
3. Scroll to the end - you will see a **Phone System - Virtual User** license. Select **Buy now**.

> [!WARNING]
> Keep in mind you still need to **Buy** the license even though it has a cost of zero. 

## Change an existing resource account to use a Virtual User license

If you decide to switch the licenses on your existing resource account from a Phone system license to a Phone System - Virtual user license, you'll need first get the Phone System - Virtual user license, then follow the linked steps in the Microsoft 365 Admin center to [Move users to a different subscription](https://docs.microsoft.com/en-us/office365/admin/subscriptions-and-billing/assign-licenses-to-users?redirectSourcePath=%252farticle%252f997596b5-4173-4627-b915-36abac6786dc&view=o365-worldwide#move-users-to-a-different-subscription). 

> [!WARNING]
> Always remove a Phone System license and assign the Phone System - Virtual user license in the same license activity. If you remove the Phone System license, save the account changes, add the new Phone System - Virtual user license, and then save the account settings again, the resource account may no longer function as expected. 

> You need to get the Phone System - Virtual user license first before you remove and replace the licenses. Then you must remove the Phone System license from the resource account, assign the new Phone System - Virtual user license, and then save the account settings.

> If this happens by accident, we recommend you create a new resource account for the Phone System - Virtual user license and remove the broken resource account.  

## Related information

[Auto Attendant and Call Queues Service Update](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Auto-Attendant-and-Call-Queues-Service-Update/ba-p/564521)
