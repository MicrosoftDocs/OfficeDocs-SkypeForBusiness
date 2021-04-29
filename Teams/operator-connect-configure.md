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

1. **Choose an operator.** In the **All operators** tab, filter available operators by region or service to find the right operator for your voice needs. Then select the operator you want to enable.  

2. **Select countries.** Under **Operator settings**, select the countries you want to enable with your selected operator.

3. **Provide contact information.** Operators may want to contact you to share [commercial or business-related information]. To opt in, check the box and provide your contact information.  

4. **Accept the data transfer notice.**

## Set up phone numbers

- If you need to acquire phone numbers for new users, see [Acquire numbers for new Teams users](#acquire-numbers-for-new-teams-users).

- If you're currently using Direct Routing or Calling Plans and want to move existing numbers to Operator Connect, see [Move numbers from other voice solutions to Operator Connect](#move-numbers-from-other-voice-solutions-to-operator-connect).

### Acquire numbers for new Teams users

To acquire numbers for new Teams users, follow these steps:

1. **Create and validate emergency addresses** In the Teams admin center, go to **Locations > Emergency addresses** to set up emergency addresses. To learn more, see [Add, change, or remove an emergency location for your organization](https://docs.microsoft.com/MicrosoftTeams/add-change-remove-emergency-location-organization).

2. **WHAT ABOUT PROVIDING THE TENANT ID TO THE OPERATOR?** This seems to be an important step listed in the Pure IP doc.

3. **Acquire numbers.** You'll need to go to your operator's website to acquire phone numbers. See [Operators](#operators) to learn more.  

4. **Assign numbers.** View numbers or make changes to assignments from the **Phone numbers** window. To learn how to assign phone numbers to your users, see [Assign, change, or remove a phone number for a user.](https://docs.microsoft.com/microsoftteams/assign-change-or-remove-a-phone-number-for-a-user#assign-a-phone-number-to-a-user)

>[!IMPORTANT]
>**Emergency addresses:** Phone numbers acquired with Operator Connect that have been assigned to emergency addresses are managed directly with your operator. Contact them to make any changes to existing phone numbers.

### Move numbers from other voice solutions to Operator Connect

If you use Direct Routing or Calling Plans for your Teams voice solution and want to move existing phone numbers to Operator Connect, you'll need to deconfigure your current solution and remove all assigned phone numbers.

Then, you can assign Operator Connect numbers to your users in one of two ways:

- Provide a list of users and their numbers to your Operator Connect operator, who will assign the phone numbers for you.

- Or, use Powershell and run the following command for each user:

```PowerShell

Set-CsOnlineVoiceUser -Identity <user>  -TelephoneNumber <phone number> 

```

### Move numbers from Calling Plans to Operator Connect

To move numbers from Calling Plans to Operator Connect, your opeartor will provide and reserve new PSTN numbers. You'll need to provide your operator with your tenant ID and with the  emergency service addresses associated with the new PSTN numbers.

To move a user from Calling Plans to Operator Connect:

1. Unassign the user their Calling Plan Phone Number.

2. Remove the Calling Plan License.

3. Reprocess the licensing from AzureAD portal. 

4. Wait 30 minutes at least  (state why you're waiting).

You can now start assigning Operator Connect numbers to the test user(s) by using the following PowerShell cmdlet:

```
Set-CsOnlineVoiceUser -Identity <user>  -TelephoneNumber <phone number> 
```
For example:

```
Set-CsOnlineVoiceUser -Identity operatorconnect.teamstest@pure-ip.com -TelephoneNumber +14158000700 
```

Alternatively, you can provide the list of users and associated telephone numbers to your operator so that your operator can to do the number assignment.  

### Move numbers from Direct Routing to Operator Connect

To move numbers from Direct Routing to Operator Connect, you'll need to provide your operator with the following:

- Your tenant ID.

- The existing Direct Routing telephone numbers you want to migrate to Operator Connect for testing.

- The emergency service addresses associated with the numbers you wish to migrate.

To move a user from Direct Routing to Operator Connect, you will need  to first remove the existing telephone number from the user.  

To get the existing On-prem Line URI for an existing user, run the following command:

```
Get-CsOnlineUser -Identity <user> | select OnPremLineURI 
```

To remove the On-prem Line URI for an existing user,  run the PowerShell command below :  

```
Set-CsUser -identity <user> - OnPremLineURI $null 
```

Then you will need to remove any PSTNUsage associated with the users that you want to use for this private preview, otherwise calls will be routed to the gateway specified in the PSTN Usage. 

You can now start assigning Operator Connect numbers to the test user(s) as follows:

```
Set-CsOnlineVoiceUser -Identity <user>  -TelephoneNumber <phone number> 
```

For example:

```
Set-CsOnlineVoiceUser -Identity operatorconnect.teamstest@pure-ip.com -TelephoneNumber +14158000700 
```

Alternatively, you can provide the list of users and associated telephone numbers to your operator who can work with Microsoft to do the number assignment.  

## Manage your operators

From the My operators tab, you can view your operators and their status and make the following changes to your selections:  

- Manage operator services by country
- Suspend an operator
- Remove an operator

>[!NOTE]
>Before removing an operator from your organization or from a country, you must remove all phone numbers assigned to users in the organization or country and contact the operator to release the numbers.

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
