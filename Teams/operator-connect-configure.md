---
title: Configure Operator Connect
author: cazawideh
ms.author: czawideh
manager: serdars
ms.date: 04/12/2021
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
ms.reviewer: crowe
search.appverid: MET150
f1.keywords:
- NOCSH
- ms.teamsadmincenter.directrouting.overview
description: Learn more about how to configure Operator Connect.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Configure Operator Connect

This article describes how to configure Operator Connect. Before configuring Operator Connect, be sure to read [Plan for Operator Connect](operator-connect-plan.md) for information about prerequisites and licensing.

## Enable an operator

You can enable, edit, and remove operators in the Teams Admin Center. In the left navigation pane, go to **Voice > Operators**.

To enable an operator:

1. **Choose an operator.** In the **All operators** tab, filter available operators by region or service to find the right operator for your voice needs. Then select the operator you want to enable.  

2. **Select countries.** Under **Operator settings**, select the countries you want to enable with your selected operator.

3. **Provide contact information** Your contact information, including your full name and email address, will be shared automatically with your operator. You can change this information later. Additionally, you'll need to provide company size, and you'll have the option to provide your phone number. Operators will use this information to contact you with more details about Operator Connect.

4. Accept the data transfer notice.

5. **Add your operator.** Select **Add as my operator** to save.

## Set up phone numbers

How you set up phone numbers depends on whether you're setting up numbers for new users, or moving existing numbers from either Microsoft Calling Plans or Direct Routing.

- If you need to acquire phone numbers for new users, see [Acquire numbers for new Teams users](#acquire-numbers-for-new-teams-users).

- If you want to move existing numbers from Calling Plans to Operator Connect, see [Move numbers from Calling Plans to Operator Connect](#move-numbers-from-calling-plans-to-operator-connect).

- If you want to move existing numbers from Direct Routing to Operator Connect, see [Move numbers from Direct Routing to Operator Connect](#move-numbers-from-direct-routing-to-operator-connect).

### Acquire numbers for new Teams users

To acquire numbers for new Teams users, follow these steps:

1. **Assign a Phone System license.** You can assign a Phone System license to your users from the Microsoft 365 admin center or using PowerShell. For more information, see [Assign Teams add-on licenses to users](teams-add-on-licensing/assign-teams-add-on-licenses.md).

2. Users that will be assigned phone numbers acquired with Operator Connect need to be in TeamsOnly mode. If your organization is in TeamsOnly mode, then all your users are in TeamsOnly mode. To check this, in the Teams admin center, go to **Org-wide settings > Teams upgrade**. If your organization is in Islands mode, check if specific users are in TeamsOnly mode. Go to **Users** and select a user account. In the **Account** tab, under **Teams upgrade,** the coexistence mode should be set to 'TeamsOnly.'

3. **Acquire numbers.** Go to your operator's website to order and acquire phone numbers. For a list of operator websites, go to the [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory). You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id) for more information.

4. **Assign numbers.** Once your operator completes the order, they'll upload numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. Assign numbers to users from the Teams admin center or by using PowerShell. For more information, see [Assign numbers](#assign-numbers).

> [!NOTE]
> In addition to [getting phone numbers for your users](getting-phone-numbers-for-your-users.md), you can get toll or toll-free phone numbers for services such as Audio Conferencing (for conference bridges), Auto Attendants, and Call Queues (also called service numbers). Service phone numbers have a higher concurrent calling capacity than user or subscriber phone numbers. For example, a service number can handle hundreds of calls simultaneously, whereas a user's phone number can only handle a few calls simultaneously. To get service numbers, contact your operator.

### Emergency addresses

The emergency address is a static location associated with a number. Once you create emergency addresses in the Teams admin center, how you assign the addresses, or change them later, will depend on your operator.

To assign numbers to emergency addresses, your operator will implement one of three scenarios:

- The operator assigns phone numbers to the emergency addresses and allows you to change them later in the Teams admin center.

- The operator doesn't assign numbers and allows you to assign numbers to the emergency addresses in the Teams admin center. 

- The operator assigns phone numbers to the emergency address, and doesn't allow you to change them. In this scenario, you'll need to contact your operator to make changes to emergency addresses and their assigned phone numbers.

For more information on emergency calling, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md) and [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

### Move numbers from Calling Plans to Operator Connect

1. Contact your operator to port your numbers to Operator Connect. See [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory) to find your operator's website.

2. After your operator completes the porting order, you can unassign your users' Calling Plan phone numbers, and remove the Calling Plan License. Then, your operator can upload the numbers to your tenant.

3. Assign Operator Connect numbers to users by using the Teams admin center or by using PowerShell. For more information, see [Assign numbers](#assign-numbers).

### Move numbers from Direct Routing to Operator Connect

1. Remove the existing telephone number from the user as follows:  

   Get the existing On-prem Line URI by running the following PowerShell command:

   ```
   Get-CsOnlineUser -Identity <user> | select OnPremLineURI 
   ```

   Remove the On-prem Line URI by running the following PowerShell command:  

   ```
   Set-CsUser -identity <user> - OnPremLineURI $null 
   ```

2. Remove any PSTNUsage associated with your users, otherwise calls will be routed to the gateway specified in the PSTN Usage. To learn how to remove PSTN usage, see [Set-CsOnlinePstnUsage](/powershell/module/skype/set-csonlinepstnusage?view=skype-ps).

3. Go to your operator's website to order and acquire phone numbers. To find your operators website, see the [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory). You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id) for more information.

4. Once your operator completes the order, they'll upload numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. Assign Operator Connect numbers to users by using the Teams admin center or by using  PowerShell. For more information, see [Assign numbers](#assign-numbers).

### Assign numbers

Whether you're adding new Teams users or moving existing users to Operator Connect, the steps for assigning numbers are as follows:

To assign numbers from the **Phone numbers** page of the Teams admin center, the steps are the same as assigning numbers for Calling Plans. For more information, see [Assign a phone number to a user](assign-change-or-remove-a-phone-number-for-a-user.md).

To assign numbers from the **Users** page of the Teams admin center, go to **Users > Manage users** and select an account. Under **General information**, select **Operator Connect** and choose a number from the dropdown menu.

To assign numbers by using PowerShell, use the Set-CsOnlineVoiceUser cmdlet as follows:

```
Set-CsOnlineVoiceUser -Identity <user>  -TelephoneNumber <phone number> 
```

For example:

```
Set-CsOnlineVoiceUser -Identity john@contoso.com -TelephoneNumber +14255550101
```

For more information about how to assign phone numbers to your users, see [Assign, change, or remove a phone number for a user](assign-change-or-remove-a-phone-number-for-a-user.md).

## Manage your operators

From the **My operators** tab, you can view your operators and their status and make the following changes to your selections:  

- Manage operator services by country
- Suspend an operator
- Remove an operator

> [!NOTE]
> Before removing an operator from your organization or from a country, you must remove all phone numbers assigned to users in the organization or country and contact the operator to release the numbers.

## Release numbers

To release phone numbers from the Teams admin center, go to the **Phone numbers** page and select a number.

- If the phone number isn't assigned to a user, select **Release**.

- If the phone number is assigned to a user, you'll need to unassign the number. Select **Edit**, then **Remove user**. After you save your changes, select **Release**.
