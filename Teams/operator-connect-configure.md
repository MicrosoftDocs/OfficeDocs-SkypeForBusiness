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

You can enable, edit, and remove operators in the Teams Admin Center. In the left navigation pane, go to **Voice > Operators**.

## Enable an operator

1. **Choose an operator.** In the **All operators** tab, filter available operators by region or service to find the right operator for your voice needs. Then select the operator you want to enable.  

2. **Select countries.** Under **Operator settings**, select the countries you want to enable with your selected operator.

3. **Provide contact information.** Operators may want to contact you to share [commercial or business-related information]. To opt in, check the box and provide your contact information.  

4. **Accept the data transfer notice.**

## Set up phone numbers

- If you need to acquire phone numbers for new users, see [Acquire numbers for new Teams users](#acquire-numbers-for-new-teams-users)

- If you're currently using Direct Routing or Calling Plans and want to move existing numbers to Operator Connect, see [Move numbers from other voice solutions to Operator Connect](#move-numbers-from-other-voice-solutions-to-operator-connect)

### Acquire numbers for new Teams users

- **Create emergency addresses** In the Teams admin center, go to **Locations > Emergency addresses** to set up emergency addresses. To learn more, see [Add, change, or remove an emergency location for your organization](https://docs.microsoft.com/MicrosoftTeams/add-change-remove-emergency-location-organization).

- **Acquire numbers.** You'll need to go to your operator's website to acquire phone numbers. See [Operators](#operators) to learn more.  

- **Assign numbers.** View numbers or make changes to assignments from the **Phone numbers** window. To learn how to assign phone numbers to your users, see [Assign, change, or remove a phone number for a user.](https://docs.microsoft.com/microsoftteams/assign-change-or-remove-a-phone-number-for-a-user#assign-a-phone-number-to-a-user)

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
