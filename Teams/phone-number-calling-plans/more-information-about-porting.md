---
title: More information about porting
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: tonysmit
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

## Authorized person on the account

In the porting wizard, you must enter the name of the person who is  authorized to make changes to the account with the service provider or carrier. The name isn't used to process the port order, but is used in the case of a dispute, or if something is incorrect when numbers are ported. This person is accountable for the Letter of Authorization (LOA) for a port order.
  
> [!NOTE]
> The box is limited to 15 characters (including spaces). Not having the complete name in the box won't delay or cancel the port order.

## Port order account information

When you're on the **Account information** page of the porting wizard to submit a port order, you'll  enter almost all the same information that you would provide in the LOA, including:
  
- Account number for the service provider or carrier
    
- Billing Telephone Number (BTN)
    
- PIN - if needed by your current service provider or carrier
    
- Company name
    
    > [!NOTE]
    > This will only accept 25 characters, including spaces. If the company's name is longer than 25 characters, the first 25 characters of the name will be submitted and the port order will still be processed. 
  
- Authorized user's name
    
    > [!NOTE]
    > This will only accept 15 characters, including spaces. If the authorized person's name is longer than 15 characters, the first 15 characters of the name will be submitted and the port order will still be processed. 
  
- Service address
    
- City, state, and zip code of the billing address
    
    > [!NOTE]
    > You won't need the authorizing person's signature.
  
To make submitting the port order easy and avoid errors, make sure you do the following:
  
- Remove any features (such as Hunt Groups) associated with your numbers. Make sure there are no advanced call control features, such as Call Hunt or Distinctive Ring, enabled on these phone numbers.
    
- Ensure that you haven't placed any new service orders or disconnects with your current service provider.
    
- Make sure all numbers are from the same carrier and the same account.
    
- Make sure the account information you give matches exactly what your phone carrier has on record. Mismatched information is the most common cause of errors and can delay your port order.
    
> [!CAUTION]
> **Don't disconnect your services with your service provider or carrier.** **You must keep your previous service active in order to port your phone numbers to Teams.** **Don't freeze your account with your service provider or carrier. Freezing the account prevents the change of carriers on the account. The authorized user will need to submit an order to the current carrier to remove the freeze. This process can take one to three weeks, depending on the carrier.**
  
## What is my billing telephone number?

The billing telephone number (BTN) is the main phone number that's included on your bill and billed by your service provider or carrier. If you're transferring a phone number from an account that has only one phone number, you need to enter this phone number. If you're transferring phone numbers from an account that has more than one, you can look at your bill or contact your service provider or carrier to determine what the billing telephone number is for your account.

## What should I put in for the account number?

Typically, you can find the account number on any bill or invoice you have from your service provider or carrier, or you can log on to your carrier's website. If you still don't know the account number, you can contact your service provider or carrier to get it.
  
> [!CAUTION]
>  It's important that you make sure you don't use spaces, dashes, or hyphens when entering your service provider or carrier account number.

## What should I put in for the company name?

This is the name of your company or organization. The name of the company is limited to 25 characters, which includes spaces. The name of the company isn't used to process the port order request. It's used in the case of a dispute or if something is incorrect when the phone numbers are being ported over. If you can't fit the entire name of the company in the box, it won't delay or cancel the port order.
  
## What should I put in for the service address?

The service address is different from the billing or emergency address that you have registered with your phone service provider or carrier. If you don't know this, you can contact your service provider or carrier to find out the service address listed on your account.

## How should I enter the phone numbers?

When you're porting phone numbers, you must enter them in the correct format.
  
> [!NOTE]
> Each phone number or range of phone number must be entered separately on each line.
  
- When you enter single phone numbers:
    
  - All special characters will be ignored (including dash "-"). For example:
    
  - For a 10-digit number: **&amp;\*(425\*()(\*&amp;4&amp;\*())(\*250649** will be corrected to **+14255550649**.
    
  - For an 11-digit number: **1\*()(\*&amp;42&amp;\*()(\*&amp;55550649** will be corrected to **+14255550649**.
    
  - All tags will be ignored if there are 10 or 11 digits. For example, **\<div> 4255551234\</div>** will be **+14255551234**.
    
  - "-", space, and parenthesis will be ignored. For example:
    
  - For a 10-digit number: **(425) 555-6776** will be corrected to **+14255556776**.
    
  - For an 11-digit number: **1(425) 555-6776** will be corrected to **+14255556776**.
    
  - All letters will be treated as special characters and ignored if there is a 10-digit or 11-digit phone number. For example:
    
  - For a 10-digit number: **14jaosia2reoij05jof55506ajfoj49isdjf** will be corrected to **+14255550649**.
    
  - For an 11-digit number: **1ade4jaoda2rfoij05ojof55506dsfoj49if** will be corrected to **+14255550649**.
    
  - Any combination of special characters, even in other languages, will be corrected. For example: 
    
  - For a 10-digit number: **中文4中文2ajj5\*（）（\*（5()...551345** will be corrected to **+14555551345**.
    
  - For an 11-digit number: **中文4中文2$a5\*（）（\*（5()...55(.1345** will be corrected to **+14555551345**.
    
  - If any numbers contain fewer than 10 digits or more than 11 digits, they will be highlighted for the user to correct:
    
  - \*\*5551245\*\* will be highlighted and need to be corrected.
    
  - **1234567891011** will be highlighted and need to be corrected.
    
  - Any numbers that are fewer than 10 digits or more than 11 digits, with any special characters, will be highlighted without being automatically corrected.
    
  - For a 7-digit number without special characters that is entered: **123456abcdefg7** will be highlighted and need to be corrected, but the letters won't be ignored.
    
  - For a 7-digit number with special characters that is entered: **12345!@#$%^&amp;\*()--@#$%^&amp;\*()7** will be highlighted to be corrected. The special characters won't be ignored.
    
- When you enter a range of phone numbers.
    
  - Only two phone numbers are allowed. The smaller number must be the first number in the range.
    
  - All special characters (except for the dash "-") are treated the same as single numbers. For example, **(425)555 0&amp;\*(123-(1425)5557899nm** will be corrected to **+14255550123 -+13202040659**.
    
  - The "-" is used for only separating the two numbers. It isn't supported to include multiple "-" in the number range. For example, **(425) 555-0649 - (425) 555-1115** should be entered as **(425) 5550649 - (425) 5551115**.

  ## How do I see the status of my port order?

  See [What's the status of your port orders?](port-order-status.md)

## Related topics

- [What's a port order?](port-order-overview.md)
- [Different kinds of phone numbers used for Calling Plans](../different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Manage phone numbers for your organization](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)
- [Emergency calling terms and conditions](../emergency-calling-terms-and-conditions.md)
- [Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)
