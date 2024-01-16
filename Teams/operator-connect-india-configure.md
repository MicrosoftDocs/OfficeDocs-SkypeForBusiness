---
title: Configure Operator Connect for India
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.date: 09/01/2023
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
f1.keywords:
- NOCSH
description: Learn more about how to configure Operator Connect for India.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Configure Operator Connect for India

This article describes how to configure Operator Connect for India. Before configuring Operator Connect for India, be sure to read [Plan for Operator Connect for India](operator-connect-india-plan.md) for information about prerequisites and licensing. You'll need to acquire the appropriate Teams license from a licensed telecom operator in India (that is, your carrier). This requirement must be met whether or not you have an existing Teams Phone license.

## Enable an Operator Connect for India operator

You can enable, edit, and remove operators in the Teams admin center. In the left navigation pane, go to **Voice > Operators**.

To enable an operator:

1. **Choose an operator.** In the **All operators** tab, filter available operators by choosing **India** from the Country drop-down menu, and choose the best operator for your voice needs. Then select the operator you want to enable.  

2. **Select countries.** Under **Operator settings**, select **India** as the country in which you want to enable with your selected operator. 

3. **Provide contact information.** Your contact information, including your full name and email address, is shared with the operator you select. You can change this information later. Additionally, you'll need to provide company size, and you have the option to provide your phone number. Operators use this information to contact you with more details about Operator Connect for India.

4. Accept the data transfer notice.

5. **Add your operator.** Select **Add as my operator** to save.

## Set up phone numbers for Operator Connect for India

How you set up phone numbers for Operator Connect for India depends on whether you're:

- Setting up numbers for new Operator Connect for India users.
- Moving existing numbers from Direct Routing to Operator Connect for India.

**If you're setting up phone numbers for new Operator Connect for India users**, see [Set up numbers for new Operator Connect for India users](#set-up-phone-numbers-for-new-operator-connect-for-india-users).

**If you're moving existing numbers from Direct Routing to Operator Connect for India**, see [Move numbers from Direct Routing to Operator Connect for India](#move-phone-numbers-from-direct-routing-to-operator-connect-for-india).


### Set up phone numbers for new Operator Connect for India users

**NOTE: Read this section only if you're setting up phone numbers for new Operator Connect for India users.** If you're moving existing numbers from Direct Routing to Operator Connect for India, see [Move numbers from Direct Routing to Operator Connect for India](#move-phone-numbers-from-direct-routing-to-operator-connect-for-india).

To acquire numbers for new Operator Connect for India users, follow these steps:

1. **Assign an Operator Connect for India Teams Phone license to each user.** You obtain the license from your Operator Connect for India operator. You can assign licenses to your users from the Microsoft 365 admin center or by using PowerShell. For more information, see [Assign Teams add-on licenses to users](teams-add-on-licensing/assign-teams-add-on-licenses.md).

2. **Teams Only mode.** Users who are assigned phone numbers acquired with Operator Connect for India must be in TeamsOnly mode. If your organization is in TeamsOnly mode, then all your users are in TeamsOnly mode. To check what mode your users are in, in the Teams admin center, go to **Teams > Teams upgrade settings**. If your organization is in Islands mode, check if specific users are in TeamsOnly mode. Go to **Users** and select a user account. In the **Account** tab, under **Teams upgrade,** the coexistence mode should be set to 'TeamsOnly.'

3. **Acquire numbers.** Go to your operator's website to order and acquire phone numbers.  You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id).

4. **Assign numbers.** After your operator completes the number acquisition order, they'll upload numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. You can then assign numbers to users from the Teams admin center or by using PowerShell. For information on how to assign phone numbers to your users, see [Manage phone numbers for users](assign-change-or-remove-a-phone-number-for-a-user.md).



### Move phone numbers from Direct Routing to Operator Connect for India

**NOTE: Read this section only if you're moving numbers from Direct Routing to Operator Connect for India.**  If you're setting up numbers for new Operator Connect for India users, see [Set up numbers for new Operator Connect for India users](#set-up-phone-numbers-for-new-operator-connect-for-india-users).

To move phone numbers from Direct Routing to Operator Connect for India, follow these steps.  You'll need to coordinate with your operator to port your existing Direct Routing numbers to Operator Connect for India numbers.

>[!IMPORTANT]
> The phone number will be out of service during the migration, so coordinate with your Operator Connect for India operator before you begin.

1. **Create a list** of all the Direct Routing numbers you want to move.

2. **Acquire Operator Connect for India Teams Phone user licenses and phone numbers** from your Operator Connect for India operator. Go to your operator's website to order and acquire phone numbers. You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id).

3. **Assign Operator Connect for India Teams Phone licenses to your users** by using the Microsoft 365 admin center or by using PowerShell. For more information, see [Assign Teams add-on licenses to users](teams-add-on-licensing/assign-teams-add-on-licenses.md).

   > [!Important]
   > Assigning the Operator Connect for India license to a user will remove the user's Direct Routing number. Be sure you have the new licenses and numbers ready to go before you complete this step.

4. **After the Direct Routing number is unassigned, remove the online voice routing policy** associated with your user by running the following Teams PowerShell Module command:

   ```PowerShell
   Grant-CsOnlineVoiceRoutingPolicy -Identity <user> -PolicyName $Null
   ```

5. **Assign the Operator Connect for India numbers to your users.** After your operator completes the number acquisition order, they'll upload numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. You can then assign numbers to users from the Teams admin center or by using PowerShell. For information on how to assign phone numbers to your users, see [Manage phone numbers for users](assign-change-or-remove-a-phone-number-for-a-user.md).


### Service numbers

In addition to getting phone numbers for your users, you can also get service numbers including toll or toll-free phone numbers for services such as Auto attendants and Call queues. Service phone numbers have a higher concurrent calling capacity than user or subscriber phone numbers. For example, a service number can handle hundreds of calls simultaneously, whereas a user's phone number can only handle a few calls simultaneously. To get service numbers in India, contact your operator.

## Manage your operators

From the **My operators** tab, you can view your operators and their status, and make the following changes to your selections:  

- Manage operator services by country
- Suspend an operator
- Remove an operator

> [!NOTE]
> Before removing an operator from your organization or from a country, you must remove all phone numbers assigned to users in the organization or country, and contact the operator to release the numbers.

## Release numbers

To release phone numbers from the Teams admin center, go to the **Phone numbers** page and select a number.

- If the phone number isn't assigned to a user, select **Release**.

- If the phone number is assigned to a user, unassign the number. Select **Edit**, then **Remove user**. After you save your changes, select **Release**.

## Related articles

- [Plan Operator Connect for India](operator-connect-india-plan.md)
- [Plan and configure Location-Based Routing for Operator Connect for India](location-based-routing-india-plan.md)
- [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md)

