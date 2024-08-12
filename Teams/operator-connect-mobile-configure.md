---
title: Configure Teams Phone Mobile
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

description: Learn how to configure Teams Phone Mobile.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Configure Teams Phone Mobile

This article is for administrators and IT professionals who are configuring Microsoft Teams Phone Mobile. Before configuring Teams Phone Mobile, be sure to read [Plan for Teams Phone Mobile](operator-connect-mobile-plan.md) for information about benefits, requirements, and licensing.

For a list of operators participating in the Teams Phone Mobile program, and the countries or regions where their service is available, see [Microsoft 365 Teams Phone Mobile](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/teams-phone-mobile).

This article describes the following steps to configure Teams Phone Mobile:

- [Step 1: Enable an operator](#step-1-enable-an-operator)
- [Step 2: Manage phone numbers and assign licenses](#step-2-manage-phone-numbers-and-assign-licenses)
- [Step 3: Assign numbers to emergency addresses](#step-3-assign-numbers-to-emergency-addresses)
- [Step 4: Manage your operators](#step-4-manage-your-operators)
- [Step 5: Release numbers](#step-5-release-numbers)
- [Step 6: Manage user incoming calling policies](#step-6-manage-user-incoming-calling-policies)

## Step 1: Enable an operator

You can enable an operator by using the Teams admin center. 

1. In the left navigation pane, go to **Voice > Operators**.

2. Choose an operator that supports Teams Phone Mobile. Under the **All operators** tab, filter available operators by region or service, and then select the operator you want to enable.

3. Under **Operator settings**, select the countries/regions you want to enable with your selected operator.

4. **Provide contact information.** Your contact information, including your full name and email address, will be shared automatically with your operator. You can change this information later. Additionally, you'll need to provide company size, and you'll have the option to provide your phone number. Operators will use this information to contact you with more details about Teams Phone Mobile.

5. Accept the data transfer notice.

6. Select **Add as my operator** to save.

You can also edit and remove operators by using the Teams admin center and navigating to **Voice > Operators**.

## Step 2: Manage phone numbers and assign licenses

If you want to add your existing company paid SIM-enabled phone numbers to Teams, contact your operator to ensure you have the eligible Teams Phone Mobile subscription. Your operator can upload your numbers to Teams. After your operator completes the order, you can assign those numbers to users. 

To find your operator's website, see the [Microsoft 365 Teams Phone Mobile directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory).

You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id). You may be porting an existing desk phone number or wireline number to a wireless voice subscription if it's supported in your region and by your operator. 

How you manage phone numbers depends on whether you're setting up numbers for new users, or moving existing numbers from Microsoft Calling Plans, Operator Connect, or Direct Routing. The various scenarios are described in detail in [Manage phone numbers for Teams Phone Mobile](operator-connect-mobile-configure-numbers.md). You can navigate to the section that pertains to your scenario:

- [Acquire numbers for new Teams users](operator-connect-mobile-configure-numbers.md#acquire-numbers-for-new-teams-users).  

- [Move numbers from Calling Plans to Teams Phone Mobile](operator-connect-mobile-configure-numbers.md#move-numbers-from-calling-plans-to-teams-phone-mobile).  

- [Move numbers from Operator Connect to Teams Phone Mobile](operator-connect-mobile-configure-numbers.md#move-numbers-from-operator-connect-to-teams-phone-mobile).  

- [Move numbers from Direct Routing to Teams Phone Mobile](operator-connect-mobile-configure-numbers.md#move-numbers-from-direct-routing-to-teams-phone-mobile).  


## Step 3: Assign numbers to emergency addresses

The emergency address is a static location associated with a number when accessible through Microsoft Teams endpoints/clients. Once you create emergency addresses in the Teams admin center, how you assign the addresses, or change them later, will depend on your operator.

To assign numbers to emergency addresses being used by Microsoft Teams endpoints, your operator will implement one of three scenarios:

- The operator assigns emergency addresses to the phone numbers and allows you to change them later in the Teams admin center.

- The operator doesn't assign addresses and allows you to assign emergency addresses to the phone numbers in the Teams admin center.

- The operator assigns emergency addresses to the phone numbers, and doesn't allow you to change them. In this scenario, you'll need to contact your operator to make changes to phone numbers and their assigned emergency address.

When calls are made through the native dialer of the SIM-enabled smartphone, your operator may use the geographic coordinates or cell tower handling the call to approximate emergency location for assistance.

For more information on emergency calling, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md) and [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).


## Step 4: Manage your operators

From the **My operators** tab, you can view your operators and their status, and make the following changes to your selections:  

- Manage operator services by country/region
- Suspend an operator
- Remove an operator

> [!NOTE]
> Before removing an operator from your organization or from a country/region, you must remove all phone numbers assigned to users in the organization or country/region and contact the operator to release the numbers.

## Step 5: Release numbers

To release phone numbers from the Teams admin center, go to the **Phone numbers** page and select a number.

- If the phone number isn't assigned to a user, select **Release**.

- If the phone number is assigned to a user, you'll need to unassign the number. Select **Edit**, then **Remove user**. After you save your changes, select **Release**.

## Step 6: Manage user incoming calling policies

You can manage a user's incoming calling policies by using the Teams admin center or by using PowerShell. By default, incoming calls for Teams Phone Mobile users will ring the Teams app first on the user's SIM-enabled mobile device. 

- If a user's incoming calling preference is set to the Teams app, all incoming calls will ring the Teams app on the SIM-enabled smartphone and any other Teams endpoints on other devices simultaneously. 

- If a user's incoming calling preference is set to the native dialer, all incoming calls ring the native dialer on the SIM-enabled smartphone and simultaneously rings all other Teams endpoints on other devices. 

### Use the Teams admin center

To manage a user's incoming calling policies by using the Teams admin center:

1. Under the voice tab, select **Mobility Policies**. 

2. To add a new mobile policy, click **Add**.

3. Select a name, add a description of the policy, and choose one of the following from the **Select a mobile dialer** dropdown option:

   -  **Microsoft Teams** to ring the Teams app on the SIM-enabled smartphone first. 

   - **Native Dialer** to ring the Native Dialer on the SIM-enabled smartphone first.

   - **User Controlled** allows end users to select their mobility policy from the Teams iOS or Android apps.

4. Assign the policies to users. See [Assign policies](assign-policies-users-and-groups.md).


### Use PowerShell

To manage a user's incoming calling policies by using PowerShell:

1. Connect to your tenant: Connect-MicrosoftTeams.
 
2. Create policies for incoming calls to ring either the Native dialer or the Teams app first. (You can choose the policy name; this example uses TeamsFirst and NativeFirst.) 

   ```PowerShell
   New-CsTeamsMobilityPolicy -identity TeamsFirst -MobileDialerPreference Teams 
   New-CsTeamsMobilityPolicy -identity NativeFirst -MobileDialerPreference Native 
   New-CsTeamsMobilityPolicy -identity UserSelected -MobileDialerPreference UserOverride 
   ```

3. Grant policies to users: 

   ```PowerShell
   Grant-CsTeamsMobilityPolicy NativeFirst -Identity user@xyz.onmicrosoft.com
   Grant-CsTeamsMobilityPolicy TeamsFirst -Identity user@xyz.onmicrosoft.com
   Grant-CsTeamsMobilityPolicy UserSelected -Identity user@xyz.onmicrosoft.com 
   ```

4. Check user policies: 

   ```PowerShell
   get-CsUserpolicyassignment -identity user@xyz.onmicrosoft.com
   ```
 
 5. Check all mobility policy options: 
    
    ```PowerShell
    Get-CsTeamsMobilityPolicy
    ```  

6. You can change the Global Mobility policy to Teams, Native, or UserOverride. To update the default Global Mobility policy for all users, use the following command:  
 
   ```PowerShell
   Set-CsTeamsMobilityPolicy -identity <Policy name> -MobileDialerPreference <Dialer preference> 
   ``` 

## Related articles

For administrators:

- [Plan Teams Phone Mobile](operator-connect-mobile-plan.md)
- [Manage phone numbers for Teams Phone Mobile](operator-connect-mobile-configure-numbers.md)

For users in your organization:

- [Get started with Teams Phone Mobile](https://prod.support.services.microsoft.com/en-us/office/getting-started-with-teams-phone-mobile-c37a6764-6c4f-4685-a26f-b84c12a71697)
- [Manage call settings in Teams Phone Mobile](https://prod.support.services.microsoft.com/en-us/office/manage-call-settings-in-microsoft-teams-phone-mobile-dbe4098a-198f-4101-b769-ecf0da9b33e2)









