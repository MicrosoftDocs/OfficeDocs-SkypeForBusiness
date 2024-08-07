---
title: Add funds and manage Communications Credits
ms.author: danismith
author: DaniEASmith
manager: pamgreen
ms.reviewer: mikedav
ms.date: 04/19/2023
ms.topic: article
ms.assetid: 691c9301-1f66-41fe-9b2c-ca24ae987463
ms.tgt.pltfrm: cloud
audience: admin
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
 - CSH
ms.custom:
  - Licensing
description: Learn how to pay for Communication credits (PSTN Consumption) for Skype for Business services and see plans to keep your users with continuous phone system access.
---

# Add funds and manage Communications Credits

Communications Credits are a convenient way to pay for Microsoft Teams Calling Plans and Audio Conferencing in Microsoft 365. Communication Credits help ensure that you and your users are never caught without being able to:
  
- Dial in to Audio Conferencing meetings using toll-free dial-in phone numbers.

- Dial out from an Audio Conferencing meeting to add someone else from anywhere in the world.

- Dial out from an Audio Conferencing meeting to your mobile phone with the Skype for Business or Microsoft Teams app installed.

- Dial any international phone number when you have a **Domestic Calling Plan**.

- Dial out and pay per minute after exhausting your monthly minute allotment.

- Dial out and pay per minute for all outgoing calls, if you have a Pay-As-You-Go Calling Plan.

We recommend using automatic recharge so you don't have to remember to add funds manually. When your balance hits the trigger amount, funds are added automatically. If you don't choose to automatically recharge your Communication Credits, you run the risk of your balance falling under zero. At that point, you and your users can't make toll-free calls or international calls.

You can update your payment options at any time. On the **Subscriptions** page in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), select **Communications Credits** and make your updates.

Funds apply only to Communications Credits at Microsoft's published rates when the services are used. Any funds not used within 12 months of the purchase date expire and are forfeited.

> [!TIP]
> We send email notifications when funds are added via automatic recharge, when automatic recharge fails (for example, when a credit card expires), and when your balance reaches zero. 

For more information, see [What are Communications Credits?](what-are-communications-credits.md).

> [!NOTE]
> If you're wondering how much it is and the rates, see the rates table on the [Calling Plans](https://go.microsoft.com/fwlink/p/?LinkId=799523) page.

## For customers with new commerce experience (NCE) calling subscriptions

The new commerce experience (NCE) allows customers to pay for services *after* the services are consumed, also known as post-usage billing.

Because Communication Credits are prepaid to support outgoing minutes, they're not available to purchase for customers with NCE calling subscriptions.

Instead, NCE customers pay for overage outgoing minutes after they use them. There's no need for a pool of Communication Credits.

### Turn off automatic recharge for Communication Credits

Most customers not using the NCE have the **Automatic Top Up** (ATU) flag enabled within their account. The ATU flag automatically refills your Communications Credit balance to the threshold you selected. When switching to NCE, you need to disable this ATU option. Otherwise, the Communications Credit balance will indefinitely refill itself, and the commerce system doesn't switch to the post-usage mechanism under NCE. If you're moving to NCE, turn off automatic recharge by completing the following steps:

1. Sign into the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
1. In the left-side menu, navigate to and select **Your products**.
1. Select **Communication Credits** in your listed products.
1. On the **Communication Credits** page, find the section titled **Billing settings** and select **Edit auto recharge settings**.
1. On the **Auto-recharge settings** page, uncheck the box next to **Auto recharge**.
1. Select the **Save** button.

When the previous process is complete, you can transition to NCE before your Communications Credit balance is empty. Even as an NCE customer, the commerce system consumes your Communications Credit balance prior to changing to post-usage billing. There's no action needed by you to ensure this switch happens other than to turn off **Auto-recharge** for Communications Credits in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).

For more information about the new commerce experience for calling subscriptions, see [Enable pay-as-you-go for your subscription](/microsoft-365/commerce/subscriptions/manage-pay-as-you-go-services) and [New commerce overage for telco pay-as-you-go](/partner-center/new-commerce-telco-payg).

## Learn about calling plans and pricing

You can see the plans and pricing by visiting one of the following links:

- [Calling Plans](https://go.microsoft.com/fwlink/?LinkId=799761)

- [Audio Conferencing plans](https://go.microsoft.com/fwlink/?LinkId=799762)

- [Phone System plans](https://go.microsoft.com/fwlink/?LinkId=799763)

You can also see information by signing in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) and going to **Billing** > **Subscriptions** > **Add subscriptions**.

To see a table with the license or licenses you need for each feature, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).
  
## Related articles

- [Set up Cloud Voicemail - Admin help](set-up-phone-system-voicemail.md)

- [Set up Calling Plans](set-up-calling-plans.md) and [Calling Plans for Microsoft 365 or Office 365](calling-plans-for-office-365.md)
