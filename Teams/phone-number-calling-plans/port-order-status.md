---
title: "What's the status of your port orders?"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords:
ms.custom:
- Calling Plans
description: "Learn how to get the status of your port orders, and what the different actions you can take on them. "
---

# What's the status of your port orders?

To see the status of your port order, in the left navigation of the Microsoft Teams admin center, go to  > **Voice** > **Port orders**, and then click **Order history**. Each port order status will be listed in the **Status** column.

The following table lists port order statuses, as well as actions you can take if needed.

|**Status**|**Can you view the order?**|**Can you edit the order?**|**Can you cancel the order?**|**Can you delete the order?**|**Description**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|**Processing** <br/> |Yes  <br/> |No  <br/> |Yes  <br/> |No  <br/> |The admin has created the order, and it's been received by Microsoft.  <br/> |
|**Contacting carrier** <br/> |Yes  <br/> |No  <br/> |Yes  <br/> |No  <br/> |The order has been received and approved by Microsoft, and we are working with the losing carrier to get it approved.  <br/> |
|**Transfer approved** <br/> |Yes  <br/> |Firm Order Commitment(FOC)  <br/> |Yes  <br/> |No  <br/> |The order has been accepted by the losing carrier, and the FOC date has been set.  <br/> |
|**Transfer pending** <br/> |Yes  <br/> |No  <br/> |No  <br/> |No  <br/> |The transfer is less than 24 hours away, so the order can no longer be edited or cancelled.  <br/> |
|**Error** <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |Yes (at this time, you can't delete the port order if there is an error. The port order needs to be re-created, or you need to [Contact support for business products - Admin Help](https://docs.microsoft.com/office365/admin/contact-support-for-business-products).  <br/> |The losing carrier has rejected the order.  <br/> |
|**Completed** <br/> |Yes  <br/> |No  <br/> |No  <br/> |No  <br/> |The numbers have been successfully transferred.  <br/> |
|**Cancelled** <br/> |No  <br/> |Yes  <br/> |No  <br/> |No  <br/> |The admin has canceled the order.  <br/> |

For complete step-by-step instructions, see [Transfer phone numbers to Teams](transfer-phone-numbers-to-teams.md).

If you need help or to get more telephone numbers than this, contact the [PSTN service desk help](../manage-phone-numbers-for-your-organization/contact-pstn-service-desk.md).

## Related topics

- [What's a port order?](port-order-overview.md)
- [Different kinds of phone numbers used for Calling Plans](../different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Manage phone numbers for your organization](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)
- [Emergency calling terms and conditions](../emergency-calling-terms-and-conditions.md)
- [Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)
