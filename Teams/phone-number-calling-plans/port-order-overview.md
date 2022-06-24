---
title: What's a port order?
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
audience: Admin
appliesto:
- Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
- CSH
ms.custom:
- ms.teamsadmincenter.voice.phonenumbers.porting.overview
- Calling Plans
description: Get an overview of what port orders are and how to transfer phone numbers from your service provider to Teams. 
---

# What's a port order?

If you currently have a phone service provider or carrier and already have phone numbers for your users or services, you need to create a "*port order*" to transfer those phone numbers to Microsoft Teams. When the numbers are ported over, you can assign those phone numbers to your users and services such as audio conferencing (for conference bridges), auto attendants, and call queues.
  
After you port your phone numbers over to Teams, Microsoft becomes your service provider and you can disconnect your service with your old service provider or carrier.

Review the information in this article to get familiar with number porting. After that, you should be ready to create a port order and transfer your phone numbers. See [Transfer phone numbers to Teams](transfer-phone-numbers-to-teams.md) for step-by-step instructions.
  
## What countries or regions support number porting?

You can port or transfer phone numbers in all the supported countries or regions, but how you submit a port order request depend on the country or region where the phone numbers come from. For a list of  countries and regions that support number porting, see [Manage phone numbers for your organization](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).  

Currently, [the porting wizard](transfer-phone-numbers-to-teams.md) in the Microsoft Teams admin center supports getting phone numbers for the United Kingdom, United States, and Canada. To get phone numbers for other countries and regions, you can [manually submit a port order](manually-submit-port-order.md).
  
## What numbers can be transferred?

 **You can transfer**
  
In general, you can transfer any phone number that's from a supported provider, including:
  
- Land line phone numbers.

- Mobile device phone numbers such as those used for cell phone and tablets.

    > [!NOTE]
    > Transferring mobile numbers is only available in the United States and Puerto Rico.
  
- Toll phone numbers.

- Toll-free phone numbers.

    > [!NOTE]
    > Universal International Freephone Number (UIFN) can't be transferred to us.
    > Porting availability for Toll-free phone numbers may vary by country and region. To find our more, please refer to your country or region specific documents to see available support for porting service. 
  
- Service phone numbers such as those used for conference bridges, auto attendants, etc.

- Fax phone numbers, but they can't be used for faxing. They have to be assigned to a user.

- VoIP phone numbers from a phone provider such as Vonage or RingCentral.

- If you are porting hybrid phone numbers (migrating from Direct Routing or Operator Connect to Calling Plans) please contact the [Telephone Number Services Team](../manage-phone-numbers-for-your-organization/contact-tns-service-desk.md), make sure you include a note stating those are hybrid phone numbers.

**You can't transfer:**
  
> [!NOTE]
> At this time, you can't transfer any phone number or numbers that aren't from a supported country or region, including phone numbers from a VoIP phone provider. For a list of supported countries/regions, see [Country and region availability for Audio Conferencing and Calling Plans](../country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
  
- Phone numbers used for data connections like for DSL lines or broadband Internet connections.

- Phone numbers dedicated to faxing.

    If you have existing dedicated phone numbers that are being used for faxing, you  *can*  transfer these numbers over to Teams but your fax services won't continue to work as expected. Faxing services aren't available to Teams customers, even if you have licenses for Phone System, Domestic Calling Plan, or International Calling Plan.

    If you port the phone number to Teams, you can assign this phone number to a user in your organization instead of using it for faxing.

> [!NOTE]
> At this time in the United Kingdom, we currently don't support transferring UK non-geographic numbers including shared cost numbers for area codes 0843, 0844, 0845, 0870, 0871, 0872.
  
## What information do I need to provide?

You need to have all the account information for your current carrier. The information that you enter in the port order is mostly found on the most recent bill or invoice from your current service provider. You also need to know whose name is on the account and what numbers you want to port.
  
## What are full-port and partial-port transfers?

When you're porting phone numbers to Teams, you have the option to transfer all your numbers or some of them.
  
- **Full-port** This is when you transfer all of your numbers from your current service provider to Teams. When you're asked for the phone numbers you want to transfer, you *must include* the billing telephone number (BTN) along with all of the other phone numbers on your account.

    For example, let's say your BTN is  *+1 425-555-1234*  and you want to port all of your 25 phone numbers (*+1 425-555-1235 through 1259*). When you follow the instructions below to transfer your numbers, you would enter: **+14255551234 - +14255551259**.

- **Partial-port** This is when you're only transferring some of your phone numbers from your current service provider to Teams. When you want to port some of the phone numbers tied to the same BTN, you ** *must not include* ** the BTN along with all of the other phone numbers on your account.

    For example, let's say your BTN is  *+1 425-555-1234*  and you want to port only 5 of your 25 phone numbers (*+1 425-555-1235 through 1259*). When you follow the instructions below to transfer your numbers, you would enter: **+1 425 555 1235 - +1 425 555 1239**.
    
## Can I submit a single number porting request for all of my numbers at one time?
<a name="bkmk_type_1"> </a>

A unique request is needed for each carrier and type of number being ported.
  
For example, you need to submit a unique number porting request for each of the following types of numbers:
  
- Local toll numbers, also known as subscriber numbers or geographic numbers

- Toll Free numbers with area codes such as: 800, 844, 855, 866, 877 and 888

- Mobile numbers

- Service numbers that can be used for Audio Conferencing in Microsoft 365 or Office 365.

Here's more information about how to submit number porting requests for each of these types of numbers:
  
- **Phone numbers** provided by different carriers require a unique porting request for numbers with each carrier.

- **Toll-free numbers** with area codes such as: 800, 844, 855, 866, 877 and 888 can't be included in a number porting request with other types of numbers. To port these toll-free numbers, you must [manually submit a port order](manually-submit-port-order.md). You can't port these numbers in the Microsoft Teams admin center. For more information, see [Manage phone numbers for your organization](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).

    It's important to use the correct Letter of Authorization (LOA) for the country and type of phone numbers that you want to port. You can [download the LOA that you need here](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).

- **Mobile numbers** require a PIN code to authorize the transfer. Therefore, they need separate number porting request.

- **Service number** porting requests need to be submitted by themselves. They can't be submitted with other types of numbers.

## How long does it take to port numbers?
<a name="bkmk_type_1"> </a>

After you've completed the port order request, it takes between 7-14 days to be processed. However, depending on your service provider it may take up to 30 days. After the phone numbers are ported over, you'll get an email from us to let you know that you're good to go.
  
To check the status of your port order, in the left navigation of the Microsoft Teams admin center, go to **Voice** > **Phone numbers**, and then click **Order history**. Each port order status is listed in the **Status** column.
  
## Can user (subscriber) phone numbers be converted to service numbers?
<a name="bkmk_type_1"> </a>

Yes they can. All you need to do is submit a service request that includes your organization's tenant GUID and the phone numbers you want converted. To do this, see [Manage phone numbers for your organization](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)

## Can I port out my numbers from Teams to a different phone service provider or carrier?

To port out your numbers from Teams to a different carrier, you must submit a request with the new carrier. You'll also need to set a porting PIN in the Microsoft Teams admin center.

To define your porting PIN, in the left navigation of the Microsoft Teams admin center, go to **Voice** > **Phone numbers**, on the upper-right corner of the page, select **Manage porting PIN**, and then enter a 10-digit PIN.

When your new carrier contacts us with the porting request, we'll ask them to provide the PIN you defined.

If you need further assitance setting up a PIN please contact the [Telephone Number Services Team](../manage-phone-numbers-for-your-organization/contact-tns-service-desk.md)

## Common mistakes to watch out for
<a name="bkmk_type_1"> </a>

Number porting is easy to do. Your order can get messed up, however, if there's a problem with the phone service provider, the order is incomplete and missing information, or there are typos.
  
Here are the most common mistakes we see customers make when they port numbers. Save yourself a call to customer support and double-check for these errors.
  
- Make sure the account information you give matches exactly what your phone carrier has on record. Mismatched information is the most common cause of errors and delay your port order. Verify the following is true:

  - Name or person authorized to make changes to the account is correct.

  - Address is correct.

  - Account number is correct.

  - BTN is correct.

- Make sure there are no advanced call control features, for example, Call Hunt, Distinctive Ring, that are enabled on these phone numbers.

- Make sure you haven't placed any new service orders or disconnects with your current service provider.

- Make sure all numbers are from the same carrier and the same account.

- Make sure your service is active. Freezing the account prevents the change of carriers on the account. The person authorized to make changes to the account must submit an order to the current carrier to remove the freeze. This process can take one to three weeks depending on the carrier.

## Related topics

- [What's the status of your port orders?](port-order-status.md)
- [Different kinds of phone numbers used for Calling Plans](../different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Manage phone numbers for your organization](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)
- [Emergency calling terms and conditions](../emergency-calling-terms-and-conditions.md)
- [Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)
