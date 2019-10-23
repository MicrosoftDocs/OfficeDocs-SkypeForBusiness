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
f1keyword: ms.teamsadmincenter.voice.phonenumbers.porting.moreinfo 
description: 
---

# More information about porting

## Authorized person on the account

In the **New Local Number Port Order** wizard, you must enter the name of the person that is authorized to make changes to the account with the service provider or carrier. The name isn't used to process the port order, but is used in the case of a dispute, or if something is incorrect when numbers are ported. This person will be accountable for the Letter of Authorization (LOA) for a port order.
  
> [!NOTE]
> Not having the complete name, because the box is limited to 15 characters (including spaces), won't delay or cancel the port order. 
  
 **For complete step-by-step instructions, see [Transfer phone numbers to Office 365](/microsoftteams/transfer-phone-numbers-to-office-365).**

> [!NOTE]
> If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)

## How should I enter the phone numbers?

When you are porting phone numbers, you must enter them in the correct format. 
  
> [!NOTE]
> Each phone number or range of phone number must be entered separately on each line. 
  
- When you are entering single phone numbers:
    
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
    
- When you are entering a range of phone numbers.
    
  - Only two phone numbers are allowed. The smaller number must be the first number in the range.
    
  - All special characters (except for the dash "-") are treated the same as single numbers. For example, **(425)555 0&amp;\*(123-(1425)5557899nm** will be corrected to **+14255550123 -+13202040659**.
    
  - The "-" is used for only separating the two numbers. It isn't supported to include multiple "-" in the number range. For example, **(425) 555-0649 - (425) 555-1115** should be entered as **(425) 5550649 - (425) 5551115**.
    
  **For complete step-by-step instructions, see [Transfer phone numbers to Office 365](/microsoftteams/transfer-phone-numbers-to-office-365).**

  > [!NOTE]
  > If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)

## Port order account information

When you are using the **Account information** page in the **New Local Number Port Order** wizard to submit a port order, you will need almost all of the same information that you would provide in the LOA, including:
  
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
    
- City, State, and Zip code of the billing address
    
    > [!NOTE]
    > You won't need the authorizing person's signature. 
  
To make submitting the port order easy and avoid errors, make sure you do the following:
  
- Remove any features (such as Hunt Groups) associated with your numbers. Make sure there are no advanced call control features, such as Call Hunt or Distinctive Ring, enabled on these telephone numbers.
    
- Ensure that you haven't placed any new service orders or disconnects with your current service provider.
    
- Make sure all numbers are from the same carrier and the same account.
    
- Make sure the account information you give matches exactly what your phone carrier has on record. Mismatched information is the most common cause of errors and can delay your port order.
    
> [!CAUTION]
> **Don't disconnect your services with your service provider or carrier.**> **You must keep your previous service active in order to port your phone numbers to Skype for Business Online.**> **Don't freeze your account with your service provider or carrier. Freezing the account prevents the change of carriers on the account. The authorized user will need to submit an order to the current carrier to remove the freeze. This process can take 1-3 weeks, depending on the carrier.**> 
  
 **For complete step-by-step instructions, see [Transfer phone numbers to Office 365](/microsoftteams/transfer-phone-numbers-to-office-365).**

## Port order overview

If you currently have a phone service provider or carrier and already have phone numbers for your users, you will need to create what is called a "*port order*" that transfers those phone number to Skype for Business Online. Once the numbers are ported over, you can assign those phone numbers to your users.
  
After you port your phone numbers over to Skype for Business Online in Office 365, Microsoft will become your service provider and you can disconnect your service with you old service provider or carrier.
  
 **For complete step-by-step instructions, see [Transfer phone numbers to Office 365](/microsoftteams/transfer-phone-numbers-to-office-365).**

 > [!NOTE]
> If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)

## What is my billing telephone number?

The billing telephone number (BTN) is the main phone number that is included on your bill and billed by your service provider or carrier. If you are transferring a phone number from an account that has only one phone number, you will need to put this phone number in. If you are transferring phone numbers from an account that has more than one, you can look at your bill or contact your service provider or carrier to determine what the billing telephone number is for your account.
  
 **For complete step-by-step instructions, see [Transfer phone numbers to Office 365](/microsoftteams/transfer-phone-numbers-to-office-365).**

> [!NOTE]
> If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)

## What should I put in for the account number?

Typically, you can find the account number on any bill or invoice you have from your service provider or carrier, or you can log on to your carrier's website. If you still don't know the account number, you can contact your service provider or carrier to get it.
  
> [!CAUTION]
>  It's important that you make sure you don't use spaces, dashes, or hyphens when entering your service provider or carrier account number.
  
 **For complete step-by-step instructions, see [Transfer phone numbers to Office 365](/microsoftteams/transfer-phone-numbers-to-office-365).**

> [!NOTE]
> If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)

## What should I put in for the company name?

This is the name of your company or organization. The name of the company is limited to 25 characters, which includes spaces. The name of the company isn't used to process the port order request; it is used in the case of a dispute or if something is incorrect when the phone numbers are being ported over. If you can't fit the entire name of the company in the box, it won't delay or cancel the port order.
  
 **For complete step-by-step instructions, see [Transfer phone numbers to Office 365](/microsoftteams/transfer-phone-numbers-to-office-365).**
 
> [!NOTE]
> If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
  
## What should I put in for the service address?

The service address is different from the billing or emergency address that you have registered with your phone service provider or carrier. If you don't know this, you can contact your service provider or carrier to find out the service address listed on your account.
  
 **For complete step-by-step instructions, see [Transfer phone numbers to Office 365](/microsoftteams/transfer-phone-numbers-to-office-365).**

> [!NOTE]
> If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)

## What's the status of my port orders?

You can see the status of your port order by going to the **Skype for Business admin center** > **Voice** > **Port orders**. Each port order status will be listed in the **Status** column. If you need help, [contact support for business products - Admin Help](https://docs.microsoft.com/office365/admin/contact-support-for-business-products).

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
   
 **For complete step-by-step instructions, see [Transfer phone numbers to Office 365](/microsoftteams/transfer-phone-numbers-to-office-365).**
 
> [!NOTE]
> If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://docs.microsoft.com/office365/admin/contact-support-for-business-products)

## Related topics

[Transferring phone numbers common questions](/microsoftteams/transferring-phone-numbers-common-questions)

[Different kinds of phone numbers used for Calling Plans](/MicrosoftTeams/different-kinds-of-phone-numbers-used-for-calling-plans)

[Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)

[Emergency calling terms and conditions](/microsoftteams/emergency-calling-terms-and-conditions)

[Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)
