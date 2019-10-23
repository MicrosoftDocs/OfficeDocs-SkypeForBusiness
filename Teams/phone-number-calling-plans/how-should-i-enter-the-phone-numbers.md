---
title: "How should I enter the phone numbers?"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.assetid: 28aa24b4-8c81-4327-9752-989ea7540db2
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
f1keywords: ms.lync.lac.PortOrderNumbers
ms.custom:
- Calling Plans
description: "Learn how to set up phone numbers when you port them to Skype for Business. "
---

# How should I enter the phone numbers?

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

  
## Related topics
[Transferring phone numbers common questions](/microsoftteams/transferring-phone-numbers-common-questions)

[Different kinds of phone numbers used for Calling Plans](/microsoftteams/different-kinds-of-phone-numbers-used-for-calling-plans)

[Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)

[Emergency calling terms and conditions](/microsoftteams/emergency-calling-terms-and-conditions)

[Skype for Business Online: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

  
 