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
>Operator Connect is currently available only in **public preview**. Public preview allows you to test upcoming features and provide feedback. Features included in public preview may not be complete, may undergo changes, and are not supported in Office 365 Government Community Cloud (GCC).

This article describes how to configure Operator Connect. Before configuring Operator Connect, be sure to read [Plan for Operator Connect](operator-connect-plan.md) for information about prerequisites and licensing.

You can enable, edit, and remove operators in the Teams Admin Center. In the left navigation pane, go to **Voice > Operators**.

## Enable an operator

To enable an operator:

1. **Choose an operator.** In the **All operators** tab, filter available operators by region or service to find the right operator for your voice needs. Then select the operator you want to enable.  

2. **Select countries.** Under **Operator settings**, select the countries you want to enable with your selected operator.

3. **Provide contact information.** Operators may want to contact you to share [commercial or business-related information]. To opt in, check the box and provide your contact information.  

4. **Accept the data transfer notice.**

## Set up phone numbers

How you set up phone numbers depends on whether you are setting up numbers for new users, or moving existing numbers from either Microsoft Calling Plans or Direct Routing.

- If you need to acquire phone numbers for new users, see [Acquire numbers for new Teams users](#acquire-numbers-for-new-teams-users).

- If you want to move existing numbers from Calling Plans to Operator Connect, see [Move numbers from Calling Plans to Operator Connect](#move-numbers-from-calling-plans-to-operator-connect).

- If you want to move existing numbers from Direct Routing to Operator Connect, see [Move numbers from Direct Routing to Operator Connect](#move-numbers-from-direct-routing-to-operator-connect).

>[!IMPORTANT]
>**Emergency addresses:** Phone numbers acquired with Operator Connect that have been assigned to emergency addresses are managed directly with your operator. Contact them to make any changes to existing phone numbers.

### Acquire numbers for new Teams users

To acquire numbers for new Teams users, follow these steps:

1. **Create the new Teams users in the Teams admin center.** (Do not assign any existing PSTN usage, telephone numbers, or perform any Direct Routing configuration to the newly created users.)  **For more information, see ...**

2. **Create and validate emergency addresses.** In the Teams admin center, go to **Locations > Emergency addresses** to set up emergency addresses. To learn more, see [Add, change, or remove an emergency location for your organization](https://docs.microsoft.com/MicrosoftTeams/add-change-remove-emergency-location-organization).

3. Your operator will provide new PSTN numbers.

4. Provide your Tenant ID to your operator. **Specify how to do this?**

5. **Acquire numbers.** Your operator will upload test numbers to your tenant. You'll need to go to your operator's website to acquire these phone numbers. See [Operators](#operators) to learn more.  

5. **Assign numbers.** Assign numbers to users by using the Teams admin center or by using PowerShell. Or, you can provide the list of users and associated telephone numbers to your operator who can work with Microsoft to do the number assignment.  For more information, see [Assign numbers](#assign-numbers).
 

### Move numbers from Calling Plans to Operator Connect

To move numbers from Calling Plans to Operator Connect, follow these steps:  

1. Provide your tenant ID to your operator.  **Specify how?**

2. Provide the emergency service addresses associated with the new PSTN numbers.

3. Your operator will provide new PSTN test numbers and upload these numbers to your tenant. You'll need to go to your operator's website to acquire these phone numbers. See [Operators](#operators) to learn more.   

To move a user from Calling Plans to Operator Connect, you'll need to:

1. Unassign the user's Calling Plan phone number.

2. Remove the Calling Plan License.

3. Reprocess the licensing from AzureAD portal. 

4. Wait 30 minutes at least  **state why you're waiting**.

5. Assign Operator Connect numbers to users by using the Teams admin center or by using PowerShell. Or, you can provide the list of users and associated telephone numbers to your operator who can work with Microsoft to do the number assignment. For more information, see [Assign numbers](#assign-numbers). 

 
### Move numbers from Direct Routing to Operator Connect

To move numbers from Direct Routing to Operator Connect, follow these steps:  

1. Provide your tenant ID to your operator.   **Specify how?**

2. Provide the existing Direct Routing telephone numbers you want to migrate to your operator  for testing.

3. Provide the emergency service addresses associated with the numbers you wish to migrate.

4. Your operator will provide new PSTN test numbers and upload these numbers to your tenant. You'll need to go to your operator's website to acquire these phone numbers. See [Operators](#operators) to learn more.   

To move a user from Direct Routing to Operator Connect, you will need to:

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

3. Assign Operator Connect numbers to users by using the Teams admin center or by using  PowerShell. Or, you can provide the list of users and associated telephone numbers to your operator who can work with Microsoft to do the number assignment. For more information, see [Assign numbers](#assign-numbers).

   

### Assign numbers

Whether you are creating new Teams users or moving existing users to Operator Connect, the steps for assigning numbers are as follows:

**To assign numbers by using the Teams admin center, ...**

To assign numbers by using PowerShell, use the Set-CsOnlineVoiceUser cmdlet as follows:

```
Set-CsOnlineVoiceUser -Identity <user>  -TelephoneNumber <phone number> 
```

For example:

```
Set-CsOnlineVoiceUser -Identity operatorconnect.teamstest@pure-ip.com -TelephoneNumber +14158000700 
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
