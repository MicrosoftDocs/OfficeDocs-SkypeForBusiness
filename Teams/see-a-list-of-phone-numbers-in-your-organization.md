---
title: "See a list of phone numbers in your organization"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.assetid: 93098bc5-df63-4a1f-8734-0b72a6280a69
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
  - M365-voice
  - M365-collaboration
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: 
  - Calling Plans
  - seo-marvel-mar2020
description: Learn to use the Microsoft Teams admin center to see a list of all phone numbers in your organization and all numbers that are assigned to users or unassigned.
---

# See a list of phone numbers in your organization

There are different types of phone numbers that you can assign to users or other services (service numbers), such as for Audio Conferencing in Microsoft 365 or Office 365.
  
## To see a list of all phone numbers that you have for your organization

![An icon showing the Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. Go to the **Microsoft Teams admin center**.

2. In the left navigation, go to **Voice** > **Phone numbers**.

    > [!IMPORTANT]
    > For you to see the **Voice** option in the left navigation in the Skype for Business admin center, you must first buy at least one **Enterprise E5 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.

3. To view the phone numbers that are assigned, see the **Status** column.

4. To filter your view, click the filter icon. On the **Filter** pane, you can use the drop-down list to filter your view by:

   - **Number range** that you set. You can search by lowest number or highest number.

   - Numbers that start with a number that you specify.

   - Number **activation state**.

   - Number **type**.

   - Phone number **status**.

## To see all of the phone numbers that are assigned to users

When you are setting up users, you might just want to see the list of the phone numbers that are already assigned to users and which phone numbers are available to be assigned to them.
  
![An icon showing the Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. Go to the **Microsoft Teams admin center**.

2. In the left navigation, go to **Voice** > **Phone numbers**.

    > [!IMPORTANT]
    > For you to see the **Voice** option in the left navigation in the Microsoft Teams admin center, you must first buy at least one **Enterprise E5 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.

3. To quickly sort the numbers so that you can see which are assigned, click the **Status** column heading. Or, you can click the filter icon and then filter your view to see phone numbers that are already assigned to users or unassigned numbers that you can assign to a user. You can filter by:

   - **Assigned to user**

   - **Assigned to conference bridge** 

   - **Unassigned**

## To see the phone numbers that are assigned to voice users

When you are setting up users in your organization to make and receive phone calls, you must first get the phone numbers and then assign them to your users. After you've gotten your phone numbers, you might just want to see the activation status of the number assignments.

![An icon showing the Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center** !
  
1. Go to the **Microsoft Teams admin center**.

2. In the left navigation, go to **Voice** > **Phone numbers**.

    > [!IMPORTANT]
    > For you to see the **Voice** option in the left navigation in the Microsoft Teams admin center, you must first buy at least one **Enterprise E5 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.

3. Click the filter icon to filter your view by **Activation state** You can filter by:

   - **Activated**

   - **Assignment pending**

   - **Assignment failed**

   - **Update pending**

   - **Update failed**

## Using the Teams PowerShell module

You can use the Teams PowerShell module to get the same information from the previous sections, but version 1.1.6 or later is required, which includes the integration of the Skype for Business Online connector. For more information about the module, see [Microsoft Teams PowerShell Overview](teams-powershell-overview.md).

You can see a list of all phone numbers that you have for your organization by using the [Get-CsOnlineTelephoneNumber](https://docs.microsoft.com/powershell/module/skype/get-csonlinetelephonenumber) cmdlet. For example, you can run the following command to see each phone number and their state:

```PowerShell
Get-CsOnlineTelephoneNumber | ft Id,ActivationState
```

You can see all of the phone numbers that are assigned to users by using the [Get-CsOnlineUser](https://docs.microsoft.com/powershell/module/skype/get-csonlineuser) cmdlet. For example, you can run the following command to see all the users with a phone number assigned:

```PowerShell
Get-CsOnlineUser | Where-Object  { $_.LineURI -notlike $null } | ft DisplayName,UserPrincipalName,LineURI
```

## Related topics
[Transferring phone numbers common questions](/microsoftteams/transferring-phone-numbers-common-questions)

[Different kinds of phone numbers used for Calling Plans](/microsoftteams/different-kinds-of-phone-numbers-used-for-calling-plans)

[Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)

[Emergency calling terms and conditions](/microsoftteams/emergency-calling-terms-and-conditions)

[Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

[Get-CsOnlineTelephoneNumber](https://docs.microsoft.com/powershell/module/skype/get-csonlinetelephonenumber)
  
[Get-CsOnlineUser](https://docs.microsoft.com/powershell/module/skype/get-csonlineuser)
