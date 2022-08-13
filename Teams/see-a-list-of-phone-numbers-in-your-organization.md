---
title: "See a list of telephone numbers in your organization"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: davlick, roykuntz, jastark
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
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Calling Plans
  - seo-marvel-mar2020
description: Learn to use the Microsoft Teams admin center to see a list of all telephone numbers in your organization and all numbers that are assigned to users or unassigned.
---

# See a list of telephone numbers 

There are different types of telephone numbers that you can assign to users or voice applications like [Audio Conferencing](deploy-audio-conferencing-teams-landing-page.md) or [Call Queues](plan-auto-attendant-call-queue.md). For more information, see [Manage telephone numbers for your organization](/microsoftteams/manage-phone-numbers-landing-page).

This article applies to Calling Plans, Operator Connect, and Operator Connect Mobile. For information about Direct Routing, see [Configure the telephone number and enable enterprise voice](direct-routing-enable-users.md#configure-the-phone-number-and-enable-enterprise-voice).
  
## To see all telephone numbers in your organization

To see a list of all telephone numbers in your organization:

1. Go to the **Microsoft Teams admin center**.

2. In the left navigation, go to **Voice** > **Phone numbers**.

3. To view the telephone numbers that are assigned, see the **Assignment Status** column, which also shows what type of service the number is assigned to.

4. To filter your view, click the filter icon. On the **Filter** pane, you can use the drop-down list to filter your view by:

   - **Number range** that you set. You can search by lowest number or highest number.

   - Numbers that start with a number that you specify.

   - Number **activation state**.

   - Number **type**.

   - Phone number **status**.

## To see all telephone numbers that are assigned to users

When you are setting up users, you might just want to see the list of the telephone numbers that are already assigned to users and which telephone numbers are available to be assigned to them.

1. Go to the **Microsoft Teams admin center**.

2. In the left navigation, go to **Voice** > **Phone numbers**.

    > [!IMPORTANT]
    > For you to see the **Voice** option in the left navigation in the Microsoft Teams admin center, you must first buy at least one **Enterprise E5 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.

3. To quickly sort the numbers so that you can see which are assigned, click the **Assignment Status** column heading. Or, you can click the filter icon and then filter your view to see telephone numbers that are already assigned to users or unassigned numbers that you can assign to a user. You can filter by:

   - **Assigned to user**
   - **Assigned to conference bridge** 
   - **Assigned to Voice app (Auto Attendant/Call Queue)**
   - **Unassigned**

## To see all telephone numbers that are assigned to voice users

When you are setting up users in your organization to make and receive telephone calls, you must first get the telephone numbers and then assign them to your users. After you've gotten your telephone numbers, you might want to see the activation status of the number assignments.
  
1. Go to the **Microsoft Teams admin center**.

2. In the left navigation, go to **Voice** > **Phone numbers**.

3. Click the filter icon to filter your view by **Activation state**. You can filter by:

   - **Activated**
   - **Assignment pending**
   - **Assignment failed**
   - **Update pending**
   - **Update failed**

## Using the Teams PowerShell module

You can use the Teams PowerShell module to get the same information from the previous sections, but version 1.1.6 or later is required, which includes the integration of the Skype for Business Online connector. For more information about the module, see [Microsoft Teams PowerShell Overview](teams-powershell-overview.md).

To see a list of all telephone numbers that you have for your organization, use the [Get-CsPhoneNumberAssignment](/powershell/module/teams/get-csphonenumberassignment) cmdlet. For example, to see each telephone number, its type and its state, run the following command:

```PowerShell
Get-CsPhoneNumberAssignment | ft TelephoneNumber,ActivationState,NumberType
```

To see all of the telephone numbers that are assigned to users, use the [Get-CsOnlineUser](/powershell/module/skype/get-csonlineuser) cmdlet. For example, to see all users with a telephone number assigned, run the following command:

```PowerShell
Get-CsOnlineUser | Where-Object  { $_.LineURI -notlike $null } | ft DisplayName,UserPrincipalName,LineURI
```

## Related topics

[Manage telephone numbers for your organization](manage-phone-numbers-landing-page.md)

[Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)

[Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

[Get-CsPhoneNumberAssignment](/powershell/module/teams/get-csphonenumberassignment)
  
[Get-CsOnlineUser](/powershell/module/skype/get-csonlineuser)
