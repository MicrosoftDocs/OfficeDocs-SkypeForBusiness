---
title: "Assign, change, or remove a phone number for a user"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.assetid: 91089761-cb87-4119-885b-3713840dd9f7
ms.tgt.pltfrm: cloud
audience: admin
ms.service: msteams
search.appverid: MET150
ms.collection: 
- M365-voice
appliesto: 
  - Microsoft Teams
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: 
  - Calling Plans
description: "Learn how to assign, change, or remove a work phone number for your Teams users so outside businesses and clients can call in."
---

# Assign, change, or remove a phone number for a user (Calling Plans)

When you set up Calling Plans, you assign phone numbers to your users. In Microsoft Teams, the phone number that you assign is listed when a user clicks **Calls**. For instructions about assigning, changing, or removing a phone number from a user in a Direct Routing scenario, see [Enable users for Direct Routing, voice, and voicemail](./direct-routing-enable-users.md).

![User's phone number displayed in Teams.](media/teams-phone-number.png)

When you're setting up users so they can make and receive phone calls, you must first use the Microsoft Teams admin center and assign a phone number. You can change or remove the phone number if you need to.
  
To learn how to get Calling Plans in Teams and how much they cost, see [Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).
  
> [!NOTE]
> One way to see whether a user has a license assigned is by going to the Microsoft Teams admin center > **Users**. If a license is assigned, it will be indicated on the page.  You can also use the Microsoft 365 admin center.
  
## Assign a phone number to a user
 
![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**
    
1. In the left navigation, click **Voice** > **Phone numbers**.
2. On the **Phone numbers** page, select an unassigned number in the list, and then click **Edit**.  
3. In the **Edit** pane, under **Assigned to**, search for the user by display name or user name, and then click **Assign**.
4. To assign or change the associated emergency location, under **Emergency location**, search for and then select the location.
5. Depending on whether you want to send an email to the user with their phone number information, turn off or turn on **Email user with telephone number information**. By default, this is on. 
6. Click **Save**.

For a PowerShell example, see [Set-CsOnlineVoiceUser](/powershell/module/skype/set-csonlinevoiceuser?view=skype-ps).

    > [!NOTE]
    > Because of the latency between Microsoft 365 or Office 365 and Teams, it can take up to 24 hours for users to be enabled. If the phone number isn't assigned correctly after 24 hours, [contact support for business products - Admin Help](/microsoft-365/admin/contact-support-for-business-products). We're here to help!

  
## Change a phone number for a user
 
![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**
    
1. In the left navigation, click **Users**, locate and double-click the user you want, click **Account**, and then under **General information**, make a note of the phone number that's assigned to the user.
2. In the left navigation, click **Voice** > **Phone numbers**.
3. On the **Phone numbers** page, select the number that you identified in step 1, and then click **Edit**.  
4. In the **Edit** pane, under **Assigned to**, click the **X** to remove the user.
5. Click **Save**.
6. On the **Phone numbers** page, select an unassigned number in the list, and then click **Edit**.  
7. In the **Edit** pane, under **Assigned to**, search for the user by display name or user name, and then click **Assign**.
8. To assign or change the associated emergency location, under **Emergency location**, search for and then select the location.
9. Click **Save**.

For a PowerShell example, please see [Set-CsOnlineVoiceUser](/powershell/module/skype/set-csonlinevoiceuser?view=skype-ps).

## Remove a phone number from a user
 
![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. In the left navigation, click **Users**, locate and double-click the user you want, click **Account**, and then under **General information**, make a note of the phone number that's assigned to the user.
2. In the left navigation, click **Voice** > **Phone numbers**.
3. On the **Phone numbers** page, select the number that you identified in step 2, and then click **Edit**.  
4. In the **Edit** pane, under **Assigned to**, click the **X** to remove the user.
5. Click **Save**.

For a PowerShell example, please see [Set-CsOnlineVoiceUser](/powershell/module/skype/set-csonlinevoiceuser?view=skype-ps).

## Related topics

[What is address validation?](/skypeforbusiness/what-are-calling-plans-in-office-365/what-is-address-validation)

[Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)

[Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)

[Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

[Set-CsOnlineVoiceUser](/powershell/module/skype/set-csonlinevoiceuser?view=skype-ps)

[Calling Plans for Microsoft 365](./calling-plans-for-office-365.md)