---
title: Configure Operator Connect Mobile
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 09/30/2021
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

You can enable, edit, and remove operators in the Teams admin center. In the left navigation pane, go to **Voice > Operators**.

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

2. Users that will be assigned phone numbers acquired with Operator Connect need to be in TeamsOnly mode. If your organization is in TeamsOnly mode, then all your users are in TeamsOnly mode. To check this, in the Teams admin center, go to **Teams > Teams upgrade settings**. If your organization is in Islands mode, check if specific users are in TeamsOnly mode. Go to **Users** and select a user account. In the **Account** tab, under **Teams upgrade,** the coexistence mode should be set to 'TeamsOnly.'

3. **Acquire numbers.** Go to your operator's website to order and acquire phone numbers. For a list of operator websites, go to the [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory). You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id) for more information.

4. **Assign numbers.** Once your operator completes the order, they'll upload numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. Assign numbers to users from the Teams admin center or by using PowerShell. For more information, see [Assign numbers](#assign-numbers).

> [!NOTE]
> In addition to [getting phone numbers for your users](getting-phone-numbers-for-your-users.md), you can get toll or toll-free phone numbers for services such as Audio Conferencing (for conference bridges), Auto Attendants, and Call Queues (also called service numbers). Service phone numbers have a higher concurrent calling capacity than user or subscriber phone numbers. For example, a service number can handle hundreds of calls simultaneously, whereas a user's phone number can only handle a few calls simultaneously. To get service numbers, contact your operator.

### Emergency addresses

The emergency address is a static location associated with a number. Once you create emergency addresses in the Teams admin center, how you assign the addresses, or change them later, will depend on your operator.

To assign numbers to emergency addresses, your operator will implement one of three scenarios:

- The operator assigns emergency addresses to the phone numbers and allows you to change them later in the Teams admin center.

- The operator doesn't assign addresses and allows you to assign emergency addresses to the phone numbers in the Teams admin center.

- The operator assigns emergency addresses to the phone numbers, and doesn't allow you to change them. In this scenario, you'll need to contact your operator to make changes to phone numbers and their assigned emergency address.

For more information on emergency calling, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md) and [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

### Move numbers from Calling Plans to Operator Connect

1. Contact your operator to port your numbers to Operator Connect. See [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory) to find your operator's website.

2. After your operator completes the porting order, you can unassign your users' Calling Plan phone numbers, and remove the Calling Plan License. Then, your operator can upload the numbers to your tenant.

3. Assign Operator Connect numbers to users by using the Teams admin center or by using PowerShell. For more information, see [Assign numbers](#assign-numbers).

### Move numbers from Direct Routing to Operator Connect

To move numbers from Direct Routing to Operator Connect, the existing Direct Routing number that was uploaded to your tenant by your operator must be removed from the user it's assigned to. Then, after the number is migrated to Operator Connect, you can re-assign the number to the user. To move from Direct Routing to Operator Connect with on-premises or online phone numbers, follow the steps below:

>[!IMPORTANT]
> The phone number will be out of service during the migration, so coordinate with your Operator Connect operator before you begin.

#### Step 1 - Remove existing Direct Routing numbers.

Check that the user is assigned a Direct Routing number by running the Teams PowerShell Module command:

```PowerShell
Get-CsPhoneNumberAssignment -AssignedPstnTargetId <user> 
```

Check that `NumberType` is DirectRouting.

How you remove your existing Direct Routing numbers depends whether the number is assigned on-premises or online. To check, run the following Teams PowerShell Module command:
    
```PowerShell
Get-CsOnlineUser -Identity <user> | fl RegistrarPool, OnPremLineURI, LineURI 
```

If `OnPremLineUri` is populated with an E.164 phone number, the phone number was assigned on-premises and synchronized to Microsoft 365.
    
**To remove Direct Routing numbers assigned on-premises,** run the following Skype for Business Server PowerShell command:
    
```PowerShell
Set-CsUser -Identity <user> -LineURI $null 
```

The amount of time it takes for the removal to take effect depends on your configuration. To check if the on-premises number was removed and the changes have been synced from on-premises to Microsoft 365, run the following Teams PowerShell Module command: 
    
```PowerShell
Get-CsOnlineUser -Identity <user> | fl RegistrarPool, OnPremLineURI, LineURI 
```
       
After the changes have synced to Microsoft 365 online directory, the expected output is: 
       
 ```console
RegistrarPool                        : pool.infra.lync.com
OnPremLineURI                        : 
LineURI                              : 
```

<br> **To remove existing online Direct Routing numbers assigned online,** run the following Teams PowerShell Module command:


```PowerShell
Remove-CsPhoneNumberAssignment -Identity <user> -PhoneNumber <pn> -PhoneNumberType DirectRouting
```

Removing the phone number may take up to 10 minutes. In rare cases, it can take up to 24 hours. To check if the phone number was removed, run the following Teams PowerShell Module command: 


```PowerShell
Get-CsOnlineUser -Identity <user> | fl LineUri
```

#### Step 2 - Remove the online voice routing policy associated with your user

Once the number is unassigned, remove the online voice routing policy associated with your user by running the following Teams PowerShell Module command:

```PowerShell
Grant-CsOnlineVoiceRoutingPolicy -Identity <user> -PolicyName $Null
```

#### Step 3 - Acquire phone numbers

Go to your operator's website to order and acquire phone numbers. To find your operators website, see the [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory). You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id) for more information.

#### Step 4 - Assign phone numbers

Once your operator completes the order, they'll upload numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. Assign Operator Connect numbers to users by using the Teams admin center or by using  PowerShell. For more information, see [Assign numbers](#assign-numbers).

### Assign numbers

For information on how to assign phone numbers to your users, see [Assign, change, or remove a phone number for a user](assign-change-or-remove-a-phone-number-for-a-user.md).

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

## Related topics

- [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md)
