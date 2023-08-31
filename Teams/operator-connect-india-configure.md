---
title: Configure Operator Connect for India
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 08/15/2023
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
ROBOTS: NOINDEX, NOFOLLOW
---

# Configure Operator Connect for India

> [!NOTE]
> Operator Connect for India is a preview release. Content is subject to change. Check back for updates.

This article describes how to configure Operator Connect for India. Before configuring Operator Connect for India, be sure to read [Plan for Operator Connect for India](operator-connect-india-plan.md) for information about prerequisites and licensing.

## Enable an operator

You can enable, edit, and remove operators in the Teams admin center. In the left navigation pane, go to **Voice > Operators**.

To enable an operator:

1. **Choose an operator.** In the **All operators** tab, filter available operators by choosing **India** from the Country drop-down menu, and choose the best operator for your voice needs. Then select the operator you want to enable.  

2. **Select countries.** Under **Operator settings**, select **India** as the country in which you want to enable with your selected operator. 

3. **Provide contact information** Your contact information, including your full name and email address, will be shared with the operator you select. You can change this information later. Additionally, you'll need to provide company size, and you'll have the option to provide your phone number. Operators will use this information to contact you with more details about Operator Connect for India.

4. Accept the data transfer notice.

5. **Add your operator.** Select **Add as my operator** to save.

## Set up phone numbers

How you set up phone numbers depends on whether you're setting up numbers for new users, or moving existing numbers from Direct Routing.

- If you need to acquire phone numbers for new users in India, see [Acquire numbers for new Teams users](#acquire-numbers-for-new-teams-users).

- If you want to move existing numbers from Direct Routing to Operator Connect, see [Move numbers from Direct Routing to Operator Connect](#move-numbers-from-direct-routing-to-operator-connect-for-india).

### Assign numbers to emergency addresses

The emergency address is a static location associated with a number. Once you create emergency addresses in the Teams admin center, how you assign the addresses, and make changes, will depend on your operator.

To assign numbers to emergency addresses, your operator will implement one of three scenarios:

- The operator assigns emergency addresses to the phone numbers, and allows you to make changes later in the Teams admin center.

- The operator assigns emergency addresses to the phone numbers, and doesn't allow you make changes. In this scenario, you'll need to contact your operator to make changes to phone numbers and their assigned emergency address.

- The operator doesn't assign addresses, and allows you to assign emergency addresses and make changes to the phone numbers in the Teams admin center.



For more information on emergency calling, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md) and [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

### Acquire numbers for new Teams users

To acquire numbers for new Teams users, follow these steps:

1. **Assign an India Teams Phone license to each user.** You'll obtain the license from your Operator Connect for India operator. You can assign licenses to your users from the Microsoft 365 admin center or by using PowerShell. For more information, see [Assign Teams add-on licenses to users](teams-add-on-licensing/assign-teams-add-on-licenses.md).

2. **Teams Only mode.** Users who are assigned phone numbers acquired with Operator Connect for India must be in TeamsOnly mode. If your organization is in TeamsOnly mode, then all your users are in TeamsOnly mode. To check this, in the Teams admin center, go to **Teams > Teams upgrade settings**. If your organization is in Islands mode, check if specific users are in TeamsOnly mode. Go to **Users** and select a user account. In the **Account** tab, under **Teams upgrade,** the coexistence mode should be set to 'TeamsOnly.'

3. **Acquire numbers.** Go to your operator's website to order and acquire phone numbers. To find your operator's website, go to the [Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory). You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id).

4. **Assign numbers.** After your operator completes the number acquisition order, they'll upload numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. You can then assign numbers to users from the Teams admin center or by using PowerShell. For more information, see [Assign numbers](#assign-numbers).

> [!NOTE]
> In addition to [getting phone numbers for your users](getting-phone-numbers-for-your-users.md), you can also get service numbers including toll or toll-free phone numbers for services such as Audio Conferencing (for conference bridges), Auto Attendants, and Call Queues. Service phone numbers have a higher concurrent calling capacity than user or subscriber phone numbers. For example, a service number can handle hundreds of calls simultaneously, whereas a user's phone number can only handle a few calls simultaneously. To get service numbers in India, contact your operator.

### Move numbers from Direct Routing to Operator Connect for India

To move from Direct Routing to Operator Connect for India with on-premises or online phone numbers, follow these steps:

#### Step 1 - Identify if the existing Direct Routing numbers are assigned online or on-premises.

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

- **To migrate existing Direct Routing numbers assigned online to Operator Connect for India**, contact your operator. To find your operator's website, see [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory). On an agreed date and time, your operator will migrate your numbers from Direct Routing to Operator Connect.

- **To migrate Direct Routing numbers assigned on-premises to Operator Connect for India**, run the following Skype for Business Server PowerShell command:

  ```PowerShell
  Set-CsUser -Identity <user> -LineURI $null 
  ```

  >[!IMPORTANT]
  > The phone number will be out of service during the migration, so coordinate with your Operator Connect for India operator before you begin.

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
  
  To remove a number:

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

- [Plan Operator Connect for India](operator-connect-india-plan.md)
