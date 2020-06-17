---
title: What do I need to buy to use Microsoft 365 Business Voice with Calling Plan?
author: dstrome 
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
f1.keywords:
- NOCSH
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

## Microsoft 365 Business Voice licenses

To make or receive phone calls to or from *external* phone numbers in Microsoft Teams, users need a Microsoft 365 Business Voice license. The license gives them access to all the features that they need to make or receive phone calls, host audio conferences, and more.

Users who don't need to make or receive phone calls to or from external phone numbers just need Teams. They don't need a Microsoft 365 Business Voice license.

For example, you might have 10 factory employees and 5 office employees. The factory employees may only need to call other employees within your company. In addition to calling other employees, office workers also need to make and receive phone calls to and from suppliers, partners, and customers. In this case, only the 5 office workers would need a Microsoft 365 Business Voice license.

### Business Voice license types

There are two types of Business Voice licenses: Business Voice **with** Calling Plan and Business Voice **without** Calling Plan. The type of Business Voice license available to you depends on the location of your Microsoft 365 tenant. The license type determines whether you can set up Business Voice on your own, if you need help from a Microsoft partner or reseller, who manages your phone numbers, and so on.

- **Business Voice with Calling Plan** You can buy Business Voice from Microsoft, use the Getting Started Wizard to set up Business Voice, and then set up or transfer your existing phone numbers to Microsoft. The article [Use the Getting Started wizard to set up Business Voice](use-getting-started-wizard.md) shows you how to set up Business Voice for your tenant.

  See [Business Voice with Calling Plan](#business-voice-with-calling-plan) later in this article for more information about buying Business Voice with Calling Plan licenses.
- **Business Voice without Calling Plan** You need to buy Business Voice from a Microsoft partner or reseller who will help you set up Business Voice. Your existing phone numbers remain with your current third-party telephone provider. The article [Get help from a Microsoft reseller or partner](reseller-partner-support.md) gives you an overview of process needed to set up Business Voice in your tenant.

To see whether your country or region supports Calling Plan, check out [Country and region availability for Business Voice](country-region-availability.md).

To learn about Business Voice features, see [Microsoft 365 Business Voice service description](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-business-voice-service-description).

## Business Voice with Calling Plan

Business Voice with Calling Plan includes a Domestic Calling Plan, which gives you a certain number of minutes per month to make calls within your country or region. You can purchase an International Calling Plan if you want to make calls to other countries or regions. You use *Communications Credits* to pay for an International Calling Plan, extra minutes per month for a Domestic Calling Plan, and toll-free numbers. You'll learn more about Calling Plans and Communications Credits later in this article.

To buy Microsoft 365 Business Voice with Calling Plan licenses, sign in to the [admin center](https://admin.microsoft.com/Adminportal/Home#/homepage), and then go to **Billing** > **Purchase services**.

### Calling Plans

Calling Plans let your users call phone numbers that are outside your organization. Calling Plans include a monthly pool of minutes that's based on the number of assigned Business Voice licenses in a given country or region. When a user makes a phone call, the number of minutes used for that call is deducted from the monthly pool. At the beginning of each month, the balance of minutes in the pool is reset.

Calling Plan pools are specific to the country or region in which the users are located. Users in a country or region can only use minutes from the Calling Plan pool in their country or region. Minutes in a Calling Plan pool in one country or region can't be transferred to a pool in another country or region.

What happens when all the minutes in a Calling Plan pool are used up depends on whether you have Communications Credits available. (We talk about Communications Credits later in this article.) If you have Communications Credits, Business Voice will start using them. If you don't have Credits, users won't be able to make phone call outside your organization until the Calling Plan pool is reset at the beginning of the next month.

> [!IMPORTANT]
> The number of minutes in a pool depends on the country or region and the number of Business Voice licenses that are assigned to your users, not the number of Business Voice licenses that you purchased. For example, if you purchased 10 Business Voice licenses in Canada but are only using three licenses, you'll have a total of 9,000 minutes in your pool (3 licenses multiplied by 3,000 minutes per user).

There are two types of Calling Plans:

#### Domestic Calling Plan

The Domestic Calling Plan lets users call phone numbers in their country or region. Business Voice includes a Domestic Calling Plan for each user who's assigned a Business Voice license. The number of minutes that are available for each user each month depends on country or region the user is located. This table shows the number of minutes for each country or region where Calling Plan is included with Business Voice:

|Where the user is located          |Monthly allotment for domestic calls  |
|-----------------------------------|--------------------------------------|
|Canada                             | 3,000                                |
|United Kingdom                     | 1,200                                |
|United States                      | 3,000                                |

Calling Plan isn't included with Business Voice in countries or regions not listed in the preceding table. For a list of all countries and regions in which Business Voice is available, see [Business Voice availability](country-region-availability.md).

Calls between the United States and Canada are considered domestic calls. You don't need to add the International Calling Plan to place calls between these two countries.

#### International Calling Plan

The International Calling Plan lets users call phone numbers outside their country or region. The International Calling Plan is purchased as an add-on.

When you consider whether to buy the International Calling Plan for a user, determine how often they make international calls and how long the calls are. This is important because when you purchase an International Calling Plan, you pay for a certain number of minutes up front. If a user doesn't use up all of the minutes in a month, the remaining minutes are discarded at the beginning of the next month. If it's likely that a user won't use up all the minutes in the International Calling Plan, don't buy one. Instead use Communications Credits (see the following section).

### Communications Credits

Communications Credits are like a digital wallet that's used to pay for calls to or from phone numbers outside your phone system. Communications Credits are used in a few situations.

- **A user has run out of minutes in their Domestic or International Calling Plan:** If a user doesn't have an International Calling Plan, Business Voice automatically starts using your Communications Credits balance.
- **A user who doesn't have an International Calling Plan makes international calls:** Business Voice automatically starts using your Communications Credits balance.
- **You have toll-free numbers:** When someone calls your toll-free number, the cost of the call is deducted from your Communications Credit balance.

If you still have Communication Credits left over at the end of the month, they're carried over to the next month.

#### Buy Communication Credits

We strongly recommend that you always have a minimum balance of Communication Credits so that your users can always make phone calls. The easiest way to make sure you always have an available balance is to set up automatic recharging. With automatic recharging, Microsoft 365 automatically refills your balance when it falls below a minimum. You can choose the minimum and the amount to buy each time. If you'd rather refill your Communication Credits balance manually, you can do that too.

> [!IMPORTANT]
> Remember that you need Communications Credits if you run out of minutes in your Calling Plans or if you receive toll-free calls. If your Communications Credits balance is empty, you won't be able to receive phone calls on toll-free phone numbers or make calls after the Calling Plan balances are used up.

To learn more about Communication Credits, take a look at [What are Communications Credits?](../what-are-communications-credits.md)

To see rates for toll-free and international calling, scroll down to "Add time with Communication Credits" in [Cloud-based Phone System](https://products.office.com/microsoft-teams/voice-calling#ow-download-rates).
