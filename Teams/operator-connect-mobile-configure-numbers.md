---
title: Manage phone numbers for Teams Phone Mobile
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.date: 07/08/2024
ms.topic: article
ms.service: msteams 
audience: admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
ms.reviewer: crowe
search.appverid: MET150

description: Learn how to manage phone numbers for Teams Phone Mobile.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Manage phone numbers for Teams Phone Mobile

This is step 3 in how to configure Teams Phone Mobile. Before reading this article, be sure you've read [Configure Teams Phone Mobile](operator-connect-mobile-configure.md).

How you manage phone numbers depends on whether you're setting up numbers for new users, or moving existing numbers from Microsoft Calling Plans, Operator Connect, or Direct Routing.  This article describes the following scenarios:

- [Acquire numbers for new Teams users](#acquire-numbers-for-new-teams-users).  

- [Move numbers from Calling Plans to Teams Phone Mobile](#move-numbers-from-calling-plans-to-teams-phone-mobile).  

- [Move numbers from Operator Connect to Teams Phone Mobile](#move-numbers-from-operator-connect-to-teams-phone-mobile).  

- [Move numbers from Direct Routing to Teams Phone Mobile](#move-numbers-from-direct-routing-to-teams-phone-mobile).  


## Acquire numbers for new Teams users

To acquire numbers for new Teams users, follow these steps:

1. **Assign a Teams Phone license** to users by using the Microsoft 365 admin center or by using PowerShell. For more information, see [Assign Teams add-on licenses to users](teams-add-on-licensing/assign-teams-add-on-licenses.md).

2. **Ensure users who are assigned phone numbers acquired with Teams Phone Mobile are in TeamsOnly mode.** If your organization is in TeamsOnly mode, then all your users are in TeamsOnly mode. 

   To check, in the Teams admin center, go to **Teams > Teams upgrade settings**. If your organization is in Islands mode, check if specific users are in TeamsOnly mode. Go to **Users** and select a user account. In the **Account** tab, under **Teams upgrade,** the coexistence mode should be set to TeamsOnly.

3. **Acquire numbers.** Go to your operator's website or contact them to order and acquire mobile SIM-enabled phone numbers with the Teams Phone Mobile service enabled. 

   After your operator completes the order, they'll upload SIM-enabled mobile numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. 

4. **Assign numbers** to users by using the Teams admin center or by using PowerShell. For more information, see [Assign numbers](assign-change-or-remove-a-phone-number-for-a-user.md).


## Move numbers from Calling Plans to Teams Phone Mobile

1. Ensure you have eligible Microsoft 365 subscriptions for Teams Phone Mobile. 

2. [Remove the phone number to be moved for respective users](assign-change-or-remove-a-phone-number-for-a-user.md#remove-a-phone-number-from-a-user). 

3. Contact your operator to port your numbers to Teams Phone Mobile on an eligible wireless voice plan which is SIM-enabled. 

4. After your operator completes the porting order, your operator will upload the numbers to your tenant.  You can view the numbers and the operator in the Teams admin center by going to **Voice > Phone numbers**. 

5. **Assign numbers** to users by using the Teams admin center or by using PowerShell. For more information, see [Assign numbers](assign-change-or-remove-a-phone-number-for-a-user.md).

## Move numbers from Operator Connect to Teams Phone Mobile

1. Ensure you have eligible Microsoft 365 subscriptions for Teams Phone Mobile. 

2. [Remove the phone number to be moved for respective users](assign-change-or-remove-a-phone-number-for-a-user.md#remove-a-phone-number-from-a-user). 

3. Contact your existing Operator Connect provider to remove the phone numbers from your tenant.

4. Contact your operator to port your numbers to Teams Phone Mobile on an eligible wireless voice plan which is SIM-enabled. 

5. After your operator completes the porting order, your operator will upload the numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. 

6. You can assign numbers to users by using the Teams admin center or by using PowerShell. For more information, see [Assign numbers](assign-change-or-remove-a-phone-number-for-a-user.md).

## Move numbers from Direct Routing to Teams Phone Mobile   

To move numbers from Direct Routing to Teams Phone Mobile, you'll need to complete the following steps:

1. [Determine if the existing Direct Routing numbers are assigned online or on-premises](#determine-if-the-existing-direct-routing-numbers-are-assigned-online-or-on-premises).

2. [Migrate the numbers from Direct Routing to Teams Phone Mobile](#migrate-the-numbers-from-direct-routing-to-teams-phone-mobile).

3. [Remove the Direct Routing online voice routing policy associated with your user](#remove-the-direct-routing-online-voice-routing-policy-associated-with-your-user).

4. [Acquire phone numbers](#acquire-phone-numbers).

5. [Assign phone numbers](#assign-phone-numbers).

These steps are described in greater detail in the following sections.

### Determine if the existing Direct Routing numbers are assigned online or on-premises.

How you remove your existing Direct Routing numbers depends on whether the number is assigned on-premises or online.

1. First, check that the user is assigned a Direct Routing number by running the following Teams PowerShell command. NumberType should be DirectRouting:

   ```PowerShell
   Get-CsPhoneNumberAssignment -AssignedPstnTargetId <user> 
   ```

2. Determine if the number is assigned online or on-premises by running the following Teams PowerShell command:

   ```PowerShell
   Get-CsOnlineUser -Identity <user> | fl RegistrarPool, OnPremLineURI, LineURI 
   ```

   If OnPremLineUri is populated with an E.164 phone number, the phone number was assigned on-premises and synchronized to Microsoft 365.

### Migrate the numbers from Direct Routing to Teams Phone Mobile

To migrate numbers, follow the steps below.  

> [!Important]
> During migration, the phone number will be out of service. Coordinate with your Teams Phone Mobile operator before you begin the migration.

- **To migrate existing Direct Routing numbers assigned online to Teams Phone Mobile**, contact your operator. To find your operator's website, see [Microsoft 365 Teams Phone Mobile directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory). On the agreed date and time, your operator will migrate your numbers from Direct Routing to Teams Phone Mobile. This may involve removing the phone number being migrated from your tenant and add it again as a new phone number associated with Teams Phone Mobile.

- **To migrate Direct Routing numbers assigned on-premises to Teams Phone Mobile**, run the following Skype for Business Server PowerShell command:

   ```PowerShell
   Set-CsUser -Identity <user> -LineURI $null 
   ```
  To check if the on-premises number was removed and the changes have been synced from on-premises to Microsoft 365, run the following Teams PowerShell command:

   ```PowerShell
   Get-CsOnlineUser -Identity <user> | fl RegistrarPool, OnPremLineURI, LineURI 
   ```

After the changes have synced to Microsoft 365 online directory, the expected output is:

```
ConsoleCopy
RegistrarPool                        : pool.infra.lync.com
OnPremLineURI                        : 
LineURI                              
```

To check if the phone number was removed, run the following Teams PowerShell command:

```PowerShell
Get-CsOnlineUser -Identity <user> | fl LineUri
```

> [!NOTE]
> The amount of time it takes for the removal to take effect depends on your configuration. Removing the phone number may take up to 10 minutes, in rare cases, it can take up to 24 hours. 

### Remove the Direct Routing online voice routing policy associated with your user

After the number is unassigned, remove the online voice routing policy associated with your user by running the following Teams PowerShell command:

```PowerShell
Grant-CsOnlineVoiceRoutingPolicy -Identity <user> -PolicyName $Null
```

### Assign Teams Phone Mobile licenses to your users

For more information, see [Assign Teams add-on licenses](teams-add-on-licensing/assign-teams-add-on-licenses.md).

### Acquire phone numbers

Contact your operator to port your numbers to Teams Phone Mobile on an eligible wireless voice plan which is SIM-enabled.

After your operator completes the order, they'll upload numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. 

### Assign phone numbers

You can assign Teams Phone Mobile numbers to users by using the Teams admin center or by using PowerShell. For more information, see [Assign numbers](assign-change-or-remove-a-phone-number-for-a-user.md).











