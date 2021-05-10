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

>[!NOTE]
>Operator Connect is currently available only in **public preview**. Public preview allows you to test upcoming features and provide feedback. Features included in public preview may not be complete, may undergo changes, and are not supported in Office 365 Government Clouds.

This article describes how to configure Operator Connect. Before configuring Operator Connect, be sure to read [Plan for Operator Connect](operator-connect-plan.md) for information about prerequisites and licensing.

## Enable an operator

You can enable, edit, and remove operators in the Teams Admin Center. In the left navigation pane, go to **Voice > Operators**.

To enable an operator:

1. **Choose an operator.** In the **All operators** tab, filter available operators by region or service to find the right operator for your voice needs. Then select the operator you want to enable.  

2. **Select countries.** Under **Operator settings**, select the countries you want to enable with your selected operator.

3. **Provide contact information (optional).** Operators may want to contact you to with additional information about Operator Connect. To opt in, check the box and provide your contact information.  

4. **Accept the data transfer notice.**

5. **Add your operator.** Select **Add as my operator** to apply your selections.

## Set up phone numbers

How you set up phone numbers depends on whether you are setting up numbers for new users, or moving existing numbers from either Microsoft Calling Plans or Direct Routing.

- If you need to acquire phone numbers for new users, see [Acquire numbers for new Teams users](#acquire-numbers-for-new-teams-users).

- If you want to move existing numbers from Calling Plans to Operator Connect, see [Move numbers from Calling Plans to Operator Connect](#move-numbers-from-calling-plans-to-operator-connect).

- If you want to move existing numbers from Direct Routing to Operator Connect, see [Move numbers from Direct Routing to Operator Connect](#move-numbers-from-direct-routing-to-operator-connect).

>[!IMPORTANT]
>**Emergency addresses:** Emergency addresses associated with a number acquired from the operator are managed directly with the operator. Please contact the operator to make any changes.

### Acquire numbers for new Teams users

To acquire numbers for new Teams users, follow these steps:

1. **Assign a Phone System license.** You can assign a Phone System license to your users from the Microsoft 365 admin center or using Powershell. For more information, see [Assign Teams add-on licenses to users](https://docs.microsoft.com/microsoftteams/teams-add-on-licensing/assign-teams-add-on-licenses). 

2. **Make sure you're in Teams Only mode.** To check this, in the Teams admin center, go to **Org-wide settings > Teams upgrade**. The coexistence mode should be set to Teams only.

3. **Create and validate emergency addresses.** In the Teams admin center, go to **Locations > Emergency addresses** to set up emergency addresses. To learn more, see [Add, change, or remove an emergency location for your organization](https://docs.microsoft.com/MicrosoftTeams/add-change-remove-emergency-location-organization).

4. **Acquire numbers.** Go to your operator's website to order and acquire phone numbers. For a list of operator websites, see [Operators](#operators). You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](https://docs.microsoft.com/onedrive/find-your-office-365-tenant-id) for more information.

5. Once your operator completes the order, they'll upload test numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**.

6. **Assign numbers.** Assign numbers to users by using the Teams admin center or by using PowerShell. For more information, see [Assign numbers](#assign-numbers).
 

### Move numbers from Calling Plans to Operator Connect

1. How you move existing phone numbers to Operator Connect will depend on your operator. Contact your operator to get started. See [Operators](#operators) to find your operator's website.

2. Once your operator has helped you move your numbers to Operator Connect, unassign the user's Calling Plan phone number, and remove the Calling Plan License. Then, your operator will upload the numbers to your tenant.

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

2. Remove any PSTNUsage associated with the users that you want to use for this private preview, otherwise calls will be routed to the gateway specified in the PSTN Usage. 

3. Your operator will provide new PSTN test numbers and upload these numbers to your tenant. You'll need to go to your operator's website to acquire these phone numbers. See [Operators](#operators) to learn more.

4. Assign Operator Connect numbers to users by using the Teams admin center or by using  PowerShell. For more information, see [Assign numbers](#assign-numbers).

   

### Assign numbers

Whether you are creating new Teams users or moving existing users to Operator Connect, the steps for assigning numbers are as follows:

To assign numbers by using the Teams admin center, go to **Phone numbers**. The steps are the same as assigning numbers for Calling Plans. See [Assign a phone number to a user](https://docs.microsoft.com/microsoftteams/assign-change-or-remove-a-phone-number-for-a-user#assign-a-phone-number-to-a-user) for more information.

To assign numbers by using PowerShell, use the Set-CsOnlineVoiceUser cmdlet as follows:

```
Set-CsOnlineVoiceUser -Identity <user>  -TelephoneNumber <phone number> 
```

For example:

```
Set-CsOnlineVoiceUser -Identity john@contoso.com -TelephoneNumber +14255550101
```

For more information about how to assign phone numbers to your users, see [Assign, change, or remove a phone number for a user](https://docs.microsoft.com/microsoftteams/assign-change-or-remove-a-phone-number-for-a-user#assign-a-phone-number-to-a-user).



## Manage your operators

From the My operators tab, you can view your operators and their status and make the following changes to your selections:  

- Manage operator services by country
- Suspend an operator
- Remove an operator

> [!NOTE]
> Before removing an operator from your organization or from a country, you must remove all phone numbers assigned to users in the organization or country and contact the operator to release the numbers.

## Operators

You can acquire phone numbers from the following operators by going to the websites linked here:

- BT
- Deutshe Telekom
- Intrado
- NTT
- Nuwave
- Orange Business Services
- Pure IP
- Rogers
- TATA
- Telenor
- Verizon
