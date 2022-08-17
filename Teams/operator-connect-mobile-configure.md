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

description: Learn more about how to configure Operator Connect Mobile.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Configure Operator Connect Mobile

**Operator Connect Mobile is a public preview release.** For a list of operators participating in the Microsoft Operator Connect Mobile program and the countries or regions where their service is available, see [Microsoft 365 Operator Connect Mobile](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/connect-mobile).

This article describes how to configure Operator Connect Mobile. Before configuring Operator Connect Mobile, be sure to read [Plan for Operator Connect Mobile](operator-connect-mobile-plan.md) for information about benefits, prerequisites, and licensing.

## Enable an operator

You can enable, edit, and remove operators in the Teams admin center. In the left navigation pane, go to **Voice > Operators**.

To enable an operator:

1. Choose an operator that supports Operator Connect Mobile. Under the **All operators** tab, filter available operators by region or service to find the right operator supporting Operator Connect Mobile. Then select the operator you want to enable.

2. Under **Operator settings**, select the countries you want to enable with your selected operator.

3. **Provide contact information.** Your contact information, including your full name and email address, will be shared automatically with your operator. You can change this information later. Additionally, you'll need to provide company size, and you'll have the option to provide your phone number. Operators will use this information to contact you with more details about Operator Connect Mobile.

4. Accept the data transfer notice.

5. Select **Add as my operator** to save.

## Set up phone numbers

If you want to add your existing company paid SIM-enabled phone number to Teams, contact your operator to ensure you have the eligible Operator Connect Mobile subscription and they can upload your numbers to Teams. Once your operator completes the order, you can [assign those numbers to users](assign-change-or-remove-a-phone-number-for-a-user.md). 

To find your operator's website, see the [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory).

You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id.md). You may be porting an existing desk phone number or wireline number to a wireless voice subscription if it's supported in your region and by your operator. 

How you set up phone numbers depends on whether you're setting up numbers for new users, or moving existing numbers from either Microsoft Calling Plans, Operator Connect, or Direct Routing.

- [Acquire numbers for new Teams users](#acquire-numbers-for-new-teams-users).  

- [Move numbers from Calling Plans to Operator Connect Mobile](#move-numbers-from-calling-plans-to-operator-connect-mobile).  

- [Move numbers from Operator Connect to Operator Connect Mobile](#move-numbers-from-operator-connect-to-operator-connect-mobile).  

- [Move numbers from Direct Routing to Operator Connect Mobile](#move-numbers-from-direct-routing-to-operator-connect-mobile).  


### Assign numbers to emergency addresses

The emergency address is a static location associated with a number when accessible through Microsoft Teams endpoints/clients. Once you create emergency addresses in the Teams admin center, how you assign the addresses, or change them later, will depend on your operator.

To assign numbers to emergency addresses being used by Microsoft Teams endpoints, your operator will implement one of three scenarios:

- The operator assigns emergency addresses to the phone numbers and allows you to change them later in the Teams admin center.

- The operator doesn't assign addresses and allows you to assign emergency addresses to the phone numbers in the Teams admin center.

- The operator assigns emergency addresses to the phone numbers, and doesn't allow you to change them. In this scenario, you'll need to contact your operator to make changes to phone numbers and their assigned emergency address.

When calls are made through the native dialer of the SIM-enabled smartphone, your operator may use the geographic coordinates or cell tower handling the call to approximate emergency location for assistance.

For more information on emergency calling, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md) and [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

### Acquire numbers for new Teams users

To acquire numbers for new Teams users, follow these steps:

1. **Assign a Phone System license and an Operator Connect Mobile add-on license.** You can assign a Phone System license and an Operator Connect Mobile add-on license to your users from the Microsoft 365 admin center or by using PowerShell. For more information, see [Assign Teams add-on licenses to users](teams-add-on-licensing/assign-teams-add-on-licenses.md).

2. **Users who will be assigned phone numbers acquired with Operator Connect Mobile need to be in TeamsOnly mode.** If your organization is in TeamsOnly mode, then all your users are in TeamsOnly mode. 

   To check, in the Teams admin center, go to **Teams > Teams upgrade settings**. If your organization is in Islands mode, check if specific users are in TeamsOnly mode. Go to **Users** and select a user account. In the **Account** tab, under **Teams upgrade,** the coexistence mode should be set to 'TeamsOnly.'

3. **Acquire numbers.** Go to your operator's website or contact them to order and acquire mobile SIM-enabled phone numbers with the Operator Connect Mobile service enabled. 

   After your operator completes the order, they'll upload SIM-enabled mobile numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. 

4. **Assign numbers.** You can assign numbers to users from the Teams admin center or by using PowerShell. For more information, see [Assign numbers](assign-change-or-remove-a-phone-number-for-a-user.md).

### Move numbers from Calling Plans to Operator Connect Mobile

1. Ensure you have eligible Microsoft 365 subscriptions for Operator Connect Mobile and the Operator Connect Mobile add-on license. You need to [remove the phone number to be moved for respective users](assign-change-or-remove-a-phone-number-for-a-user.md#remove-a-phone-number-from-a-user). 

2. Contact your operator to port your numbers to Operator Connect Mobile on an eligible wireless voice plan which is SIM-enabled. 

3. After your operator completes the porting order, your operator will upload the numbers to your tenant.  You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. 

4. You can assign numbers to users by using the Teams admin center or by using PowerShell. For more information, see [Assign numbers](assign-change-or-remove-a-phone-number-for-a-user.md).

### Move numbers from Operator Connect to Operator Connect Mobile

1. Ensure you have eligible Microsoft 365 subscriptions for Operator Connect Mobile and the Operator Connect add-on license. You need to [remove the phone number to be moved for respective users](assign-change-or-remove-a-phone-number-for-a-user.md#remove-a-phone-number-from-a-user). Contact your existing Operator Connect provider to remove the phone numbers from your tenant.

2. Contact your operator to port your numbers to Operator Connect Mobile on an eligible wireless voice plan which is SIM-enabled. 

3. After your operator completes the porting order, your operator will upload the numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. 

4. You can assign numbers to users by using the Teams admin center or by using PowerShell. For more information, see [Assign numbers](assign-change-or-remove-a-phone-number-for-a-user.md).

### Move numbers from Direct Routing to Operator Connect Mobile   

To move numbers from Direct Routing to Operator Connect Mobile, you'll need to complete the following steps:

1. [Determine if the existing Direct Routing numbers are assigned online or on-premises](#determine-if-the-existing-direct-routing-numbers-are-assigned-online-or-on-premises).

2. [Migrate the numbers from Direct Routing to Operator Connect Mobile](#migrate-the-numbers-from-direct-routing-to-operator-connect-mobile).

2. [Remove the online voice routing policy associated with your user](#remove-the-online-voice-routing-policy-associated-with-your-user).

3. [Acquire phone numbers](#acquire-phone-numbers).

4. [Assign phone numbers](#assign-phone-numbers).

These steps are described in greater detail in the following sections.

#### Determine if the existing Direct Routing numbers are assigned online or on-premises.

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

#### Migrate the numbers from Direct Routing to Operator Connect Mobile

To migrate numbers, follow the steps below.  

> [!Important]
> During migration, the phone number will be out of service. Coordinate with your Operator Connect operator before you begin the migration.

- **To migrate existing Direct Routing numbers assigned online to Operator Connect Mobile**, contact your operator. To find your operator's website, see [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory). On the agreed date and time, your operator will migrate your numbers from Direct Routing to Operator Connect Mobile. This may involve removing the phone number being migrated from your tenant and add it again as a new phone number associated with Operator Connect Mobile.

- **To migrate Direct Routing numbers assigned on-premises to Operator Connect Mobile**, run the following Skype for Business Server PowerShell command:

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

#### Remove the online voice routing policy associated with your user

After the number is unassigned, remove the online voice routing policy associated with your user by running the following Teams PowerShell command:

```PowerShell
Grant-CsOnlineVoiceRoutingPolicy -Identity <user> -PolicyName $Null
```

#### Acquire phone numbers

Contact your operator to port your numbers to Operator Connect Mobile on an eligible wireless voice plan which is SIM-enabled.

After your operator completes the order, they'll upload numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. 

#### Assign phone numbers

You can assign Operator Connect numbers to users by using the Teams admin center or by using PowerShell. For more information, see [Assign numbers](assign-change-or-remove-a-phone-number-for-a-user.md).


## Manage your operators

From the **My operators** tab, you can view your operators and their status, and make the following changes to your selections:  

- Manage operator services by country
- Suspend an operator
- Remove an operator

> [!NOTE]
> Before removing an operator from your organization or from a country, you must remove all phone numbers assigned to users in the organization or country and contact the operator to release the numbers.

## Release numbers

To release phone numbers from the Teams admin center, go to the **Phone numbers** page and select a number.

- If the phone number isn't assigned to a user, select **Release**.

- If the phone number is assigned to a user, you'll need to unassign the number. Select **Edit**, then **Remove user**. After you save your changes, select **Release**.

## Manage user incoming calling policies

You can manage a user's incoming calling policies by using the Teams admin center or by using PowerShell. By default, incoming calls for Operator Connect Mobile users will ring the Teams app first on the user's SIM-enabled mobile device. 

- If a user's incoming calling preference is set to the Teams app, all incoming calls will ring the Teams app on the SIM-enabled smartphone and any other Teams endpoints on other devices simultaneously. 

- If a user's incoming calling preference is set to the native dialer, all incoming calls ring the native dialer on the SIM-enabled smartphone and simultaneously rings all other Teams endpoints on other devices. 

### Use the Teams admin center

To manage a user's incoming calling policies by using the Teams admin center:

1. Under the voice tab, select **Mobility Policies**. 

2. To add a new mobile policy, click **Add**.

3. Select a name, add a description of the policy, and choose one of the following from the **Select a mobile dialer** dropdown option:

   -  **Microsoft Teams** to ring the Teams app on the SIM-enabled smartphone first. 

   - **Native Dialer** to ring the Native Dialer on the SIM-enabled smartphone first.

4. Assign the policies to users. See [Assign policies](assign-policies-users-and-groups.md).


### Use PowerShell

1. Connect to your tenant: Connect-MicrosoftTeams.
 
2. Create policies for incoming calls to ring either the Native dialer or the Teams app first. (You can choose the policy name; this example uses TeamsFirst and NativeFirst.) 

   ```PowerShell
   New-CsTeamsMobilityPolicy -identity TeamsFirst -MobileDialerPreference Teams 
   New-CsTeamsMobilityPolicy -identity NativeFirst -MobileDialerPreference Native 
   ```

3. Grant policies to users (Either Native or Mobile): 

   ```PowerShell
   Grant-CsTeamsMobilityPolicy NativeFirst -Identity user@xyz.onmicrosoft.com
   Grant-CsTeamsMobilityPolicy TeamsFirst -Identity user@xyz.onmicrosoft.com
   ```

4. Check user policies: 

   ```PowerShell
   get-CsUserpolicyassignment -identity user@xyz.onmicrosoft.com
   ```
 
 5.	Check all mobility policy options: 
    
    ```PowerShell
    Get-CsTeamsMobilityPolicy
    ```  

 








