---
title: What do I need to buy to use Microsoft 365 Business Voice?
author: dstrome 
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
localization_priority: Priority
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
- Teams_Business_Voice
search.appverid: MET150
description: 
appliesto: 
- Microsoft Teams
no-loc: [Microsoft 365, Microsoft 365 Business Voice, Business Voice, Teams, Microsoft Teams, Office 365]
---

# What do I need to buy to use Microsoft 365 Business Voice?

## Microsoft 365 Business Voice license

If someone in your organization wants to make or receive phone calls to or from external phone numbers in Microsoft Teams, they need a Microsoft 365 Business Voice license. The license gives them access to all the features they need to make or receive phone calls, host audio conferences, and more.

Users who don't need to make or receive phone calls to or from external phone numbers just need Teams. They don't need a Microsoft 365 Business Voice license.

For example, you might have 10 factory employees and 5 office employees. The factory employees may only need to call other employees within your company. The office employees need to call other employees, and they need to make and receive calls to and from suppliers, partners, and customers. In this case, only the 5 office workers would need a Microsoft 365 Business Voice license.

Business Voice includes a domestic calling plan, which gives you a certain amount of minutes per month to make calls within your country or region. You can purchase an international calling plan for if you want to make calls other countries or regions. You can pay for an international calling plan, extra minutes per month for the domestic calling plan, and toll-free numbers by using *communications credits*. You'll learn more about calling plans and communications credits later in this article.

To learn about Business Voice features, see [Microsoft 365 Business Voice Service Description](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-business-voice-service-description).

To buy Microsoft 365 Business Voice licenses, sign in to the [admin center](https://admin.microsoft.com/Adminportal/Home#/homepage) and then go to **Billing** > **Purchase services**.

## Calling plans

Calling plans let users call phone numbers that are outside your organization. The plan include a monthly pool of minutes that's based on the number of assigned Business Voice licenses in a given country or region. When a user makes a phone call, the number of minutes that their call takes is deducted from the total minutes in the calling plan pool. At the beginning of each month, the remaining balance of minutes in the pool is reset.

Calling plan pools are specific to the country or region in which the users are located. Users in a country or region can only use minutes from the calling plan pool in their country or region. And minutes in a calling plan pool in one country or region can't be transferred to a pool in another country or region.

If all the minutes in a calling plan pool are used up, what happens depends on whether you have any communications credits available. (We talk about communications credits later in this article). If you have communications credits, Business Voice will start using them. If you don't have credits available, users won't be able to make phone calls until the calling plan pool is reset at the beginning of the next month.

> [!IMPORTANT]
> The number of minutes in a pool depends on the country or region and thge number of Business Voice licenses that assigned to your users, not the number of Business Voice licenses that you purchased. For example, if you purchased 10 Business Voice licenses in Canada but are only using three licenses, you'll have a total of 9,000 minutes in your pool (3 licenses multiplied by 3,000 minutes per user).

There are two types of calling plans:

**Domestic calling plan:** Lets users call phone numbers in their country or region. Business Voice includes a domestic calling plan for each user who's assigned a Business Voice license. The number of minutes given to each user each month depends on where the user is located. This table that shows the number of minutes for each country or region where Business Voice is supported:

|Where the user is located          |Monthly allotment for domestic calls |
|-----------------------------------|-------------------------------------|
|Canada                             | 3000                                |
|United Kingdom                     | 1200                                |

Calls between the United States and Canada are considered domestic calls. You don't need to add the international calling plan to place calls between these two countries.

**International calling plan:** Lets users call phone numbers outside their country or region. The International calling plan is purchased as an add-on.

When you think about whether to buy the international calling plan for a user, check to see how often they make international calls and how long the calls are. This is important because when you purchase an international calling plan, you pay for a certain number of minutes up front. If a user doesn't use up all of the minutes in a month, the remaining minutes are discarded at the beginning of the next month. If it's likely that a user won't use up all the minutes provided by the international calling plan, don't buy one. Instead use communications credits (see the following section).

## Communications credits

Communications credits are like a digital wallet that's used to pay for calls to or from phone numbers outside your phone system. Communications credits are used in a few situations:

- **A user has run out of minutes in their domestic or international calling plan:** When the minutes in a calling plan are used up, Business Voice automatically starts using your communications credits balance.
- **A user who doesn't have an international calling plan makes international calls:** Business Voice automatically starts using your communications credits balance.
- **You have one or more toll-free numbers:** When someone calls your toll-free number, the cost of the call is deducted from your communications credit balance.

If you still have communication credits left over at the end of the month, they're carried over to the next month.

### Buy communication credits

We strongly recommend that you always keep a minimum balance of communication credits so that your users can always make phone calls. The easiest way to make sure you always have an available balance is to set up automatic recharging. With automatic recharging, Microsoft 365 automatically refills your balance when it falls below a minimum. You can choose the minimum and the amount to buy each time. If you you prefer, you can instead refill your communication credits balance manually.

> [!IMPORTANT]
> Remember that you need communications credits if you run out of minutes in your calling plans or if you receive toll-free calls. If your communications credits balance is empty, you won't be able to receive phone calls on toll-free phone numbers or makes calls after the calling plan balances are used up.

For more information, see [What are communications credits](../what-are-communications-credits.md)?

To see rates for toll-free and international calling, see "Add time with Communication Credits" in [Cloud-based phone system](https://products.office.com/microsoft-teams/voice-calling#ow-download-rates).

## Maximum number of supported users

The Business Voice add-on that's available with small and medium-sized Microsoft 365 subscriptions supports up to 300 licensed users. If you want to license more than 300 users for Business Voice, you need to purchase a Office 365 E3 or E5 subscription.
