---
title: "Assign, change, or remove a phone number for a user"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: davelick, roykuntz, jastark
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
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - Calling Plans
description: "Learn how to assign, change, or remove a work phone number for your Teams users so outside businesses and clients can call in."
---

# Assign, change, or remove a phone number for a user

When you set up Calling Plans, Operator Connect, or Operator Connect Mobile (Public preview release), you assign phone numbers to your users. In Microsoft Teams, the phone number that you assign is listed when a user clicks **Calls**.

This article applies to Calling Plans, Operator Connect, and Operator Connect Mobile (Public preview release). For information about assigning, changing, or removing a phone number from a user in a Direct Routing scenario, see [Enable users for Direct Routing, voice, and voicemail](./direct-routing-enable-users.md).

Before you assign a number for a Calling Plan, Operator Connect, or Operator Connect Mobile user, you must get numbers for your users. For more information, see [Get numbers for Calling Plan users](getting-phone-numbers-for-your-users.md), [Set up numbers for Operator Connect users](operator-connect-configure.md#set-up-phone-numbers), or [Set up numbers for Operator Connect Mobile users](operator-connect-mobile-configure.md).

> [!NOTE]
> One way to see whether a user has a license assigned is by going to the Microsoft Teams admin center > **Users**. If a license is assigned, it will be indicated on the page.  You can also use the Microsoft 365 admin center.

> [!NOTE]
> This note applies to customers who have a hybrid deployment with an on-premises Active Directory. If you want to assign a Calling Plan or Operator Connect phone number to a user or resource account, you must ensure that any phone number stored in the msRTCSIP-Line attribute on the user or resource account object in the on-premises Active Directory has been removed, and the change has been synchronized to Microsoft 365.

## Assign a phone number to a user

When assigning a phone number to a user, make sure the phone number and the usage location of the user are of the same country.

To assign a number by using the Teams admin center:

[!INCLUDE [assign-phone-numbers-to-users-steps](./includes/assign-phone-numbers-to-users-steps.md)]


To assign numbers by using PowerShell, use the [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) cmdlet as follows:

For Calling Plan numbers:

```PowerShell
Set-CsPhoneNumberAssignment -Identity <user> -PhoneNumber <phone number> -PhoneNumberType CallingPlan
```

For Operator Connect numbers:

```PowerShell
Set-CsPhoneNumberAssignment -Identity <user> -PhoneNumber <phone number> -PhoneNumberType OperatorConnect
```

For Operator Connect Mobile numbers:

```PowerShell
Set-CsPhoneNumberAssignment -Identity <user> -PhoneNumber <phone number> -PhoneNumberType OCMobile
```

For example:

```PowerShell
Set-CsPhoneNumberAssignment -Identity john@contoso.com -PhoneNumber "+14255550101" -PhoneNumberType CallingPlan
Set-CsPhoneNumberAssignment -Identity jack@contoso.com -PhoneNumber "+14255550102" -PhoneNumberType OperatorConnect
Set-CsPhoneNumberAssignment -Identity jack@contoso.com -PhoneNumber "+14255550103" -PhoneNumberType OCMobile
```







> [!NOTE]
> Because of the latency between Microsoft 365 and Teams, it can take up to 24 hours for users to be enabled. If the phone number isn't assigned correctly after 24 hours, see [Phone Number Service Center](https://pstnsd.powerappsportals.com/).

## Change a phone number for a user

To change a phone number for a user by using the Teams admin center:

1. In the left navigation, click **Users**, locate and double-click the user you want, click **Account**, and then under **General information**, make a note of the phone number that's assigned to the user.

2. In the left navigation, click **Voice** \> **Phone numbers**.

3. On the **Phone numbers** page, select the number that you identified in step 1, and then click **Edit**.

4. In the **Edit** pane, under **Assigned to**, click the **X** to remove the user.

5. Click **Save**.

6. On the **Phone numbers** page, select an unassigned number in the list, and then click **Edit**.

7. In the **Edit** pane, under **Assigned to**, search for the user by display name or user name, and then click **Assign**.

8. To assign or change the associated emergency location, under **Emergency location**, search for and then select the location.

      > [!NOTE]
      > If you are changing numbers for Operator Connect or Operator Connect Mobile users, you may or may not be able to assign or change the associated emergency location. This functionality will depend on your Operator. Contact your Operator for more information.

9. Click **Save**.

For a PowerShell example, see [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment).

## Remove a phone number from a user

To remove a phone number by using the Teams admin center:

1. In the left navigation, click **Users**, locate and double-click the user you want, click **Account**, and then under **General information**, make a note of the phone number that's assigned to the user.

2. In the left navigation, click **Voice** \> **Phone numbers**.

3. On the **Phone numbers** page, select the number that you identified in step 2, and then click **Edit**.

4. In the **Edit** pane, under **Assigned to**, click the **X** to remove the user.

5. Click **Save**.

For a PowerShell example, see [Remove-CsPhoneNumberAssignment](/powershell/module/teams/remove-csphonenumberassignment).

## Related topics

[What is address validation?](/skypeforbusiness/what-are-calling-plans-in-office-365/what-is-address-validation)

[Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)

[Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)

[Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

[Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment)

[Remove-CsPhoneNumberAssignment](/powershell/module/teams/remove-csphonenumberassignment)
