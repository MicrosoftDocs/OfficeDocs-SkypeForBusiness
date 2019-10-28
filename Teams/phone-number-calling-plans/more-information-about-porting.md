---
title: More information about porting
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: tonysmit,jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
localization_priority: Normal
search.appverid: MET150
ROBOTS: NOINDEX, NOFOLLOW
f1keyword: ms.teamsadmincenter.voice.phonenumbers.porting.moreinfo 
description: Get the guidance you need to port your phone numbers to Microsoft Teams.
---

# More information about porting

Here you'll find more information about porting your phone numbers to Microsoft Teams.

For complete step-by-step instructions, see [Transfer phone numbers to Teams](transfer-phone-numbers-to-teams.md).

If you need help or if you need to get more phone numbers, contact the [PSTN service desk help](../manage-phone-numbers-for-your-organization/contact-pstn-service-desk.md).

## Port order account information

When you're on the **Add account information** page of the porting wizard to submit a port order, you'll  enter almost all the same information that you would provide in the LOA, including:
  
- Account number for the service provider or carrier
    
- Billing Telephone Number (BTN)
    
- PIN - if needed by your current service provider or carrier
    
- Organization name
    
    > [!NOTE]
    > This will only accept 25 characters, including spaces. If the organization name is longer than 25 characters, the first 25 characters of the name will be submitted and the port order will still be processed.
  
- Name of person authorized to make changes to the account
    
    > [!NOTE]
    > This will only accept 15 characters, including spaces. If the authorized person's name is longer than 15 characters, the first 15 characters of the name will be submitted and the port order will still be processed. 
  
- Service address
  
To make submitting the port order easy and avoid errors, make sure you do the following:
  
- Remove any features (such as Hunt Groups) associated with your numbers. Make sure there are no advanced call control features, such as Call Hunt or Distinctive Ring, enabled on these phone numbers.
    
- Ensure that you haven't placed any new service orders or disconnects with your current service provider.
    
- Make sure all numbers are from the same carrier and the same account.
    
- Make sure the account information you give matches exactly what your phone carrier has on record. Mismatched information is the most common cause of errors and can delay your port order.
    
> [!CAUTION]
> Don't disconnect your services with your service provider or carrier. You must keep your previous service active in order to port your phone numbers to Teams. Don't freeze your account with your service provider or carrier. Freezing the account prevents the change of carriers on the account. The authorized user will need to submit an order to the current carrier to remove the freeze. This process can take one to three weeks, depending on the carrier.

## Authorized person on the account

In the porting wizard, you must enter the name of the person who is authorized to make changes to the account with the service provider or carrier. The name isn't used to process the port order, but is used in the case of a dispute, or if something is incorrect when numbers are ported. This person is accountable for the Letter of Authorization (LOA) for a port order.
  
> [!NOTE]
> The box is limited to 15 characters (including spaces). Not having the complete name in the box won't delay or cancel the port order.
  
## What's my billing telephone number?

The billing telephone number (BTN) is the main phone number that's included on your bill and billed by your service provider or carrier. If you're transferring a phone number from an account that has only one phone number, you need to enter this phone number. If you're transferring phone numbers from an account that has more than one, you can look at your bill or contact your service provider or carrier to determine what the BTN is for your account.

## What should I put in for the account number?

Typically, you can find the account number on any bill or invoice you have from your service provider or carrier, or you can log on to your carrier's website. If you still don't know the account number, you can contact your service provider or carrier to get it.
  
> [!CAUTION]
>  It's important that you make sure you don't use spaces, dashes, or hyphens when entering your service provider or carrier account number.

## What should I put in for the organization name?

This is the name of your organization. The organization name is limited to 25 characters, which includes spaces. The name of the company isn't used to process the port order request. It's used in the case of a dispute or if something is incorrect when the phone numbers are being ported over. If you can't fit the entire name of the company in the box, it won't delay or cancel the port order.
  
## What should I put in for the service address?

The service address is different from the billing or emergency address that you have registered with your phone service provider or carrier. If you don't know this, contact your service provider or carrier to find out the service address listed on your account.

## How should I enter the phone numbers?
<a name="bkadding"> </a>

When you submit a port order, you must use a properly formatted CSV file to submit your phone numbers. Here are the requirements for the CSV file:

 - You can give the file any name that you want.
 - The file must only have one column with a header named PhoneNumber.
 - Each phone number must be on a separate row.
 - Phone numbers can be digits only or in E.164 format.
 - The phone number format must match the country or region you selected. For example, if you choose the United Kingdom in the porting wizard, use 44, which is the country code, followed by the phone number with the correct number of digits. For example, 4420812341234.

## How do I see the status of my port order?

See [What's the status of your port orders?](port-order-status.md)

## Related topics

- [What's a port order?](port-order-overview.md)
- [Different kinds of phone numbers used for Calling Plans](../different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Manage phone numbers for your organization](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)
- [Emergency calling terms and conditions](../emergency-calling-terms-and-conditions.md)
- [Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)
