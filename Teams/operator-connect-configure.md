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

3. **Provide contact information (optional).** If you want operators to contact you with additional information about Operator Connect, check the box and provide your contact information.  

4. **Accept the data transfer notice.**

5. **Add your operator.** Select **Add as my operator** to save.

## Set up phone numbers

How you set up phone numbers depends on whether you're setting up numbers for new users, or moving existing numbers from either Microsoft Calling Plans or Direct Routing.

- If you need to acquire phone numbers for new users, see [Acquire numbers for new Teams users](#acquire-numbers-for-new-teams-users).

- If you want to move existing numbers from Calling Plans to Operator Connect, see [Move numbers from Calling Plans to Operator Connect](#move-numbers-from-calling-plans-to-operator-connect).

- If you want to move existing numbers from Direct Routing to Operator Connect, see [Move numbers from Direct Routing to Operator Connect](#move-numbers-from-direct-routing-to-operator-connect).

>[!IMPORTANT]
>**Emergency addresses:** Emergency addresses associated with a number acquired from the operator are managed directly with the operator. Please contact the operator to make any changes.

### Acquire numbers for new Teams users

To acquire numbers for new Teams users, follow these steps:

1. **Assign a Phone System license.** You can assign a Phone System license to your users from the Microsoft 365 admin center or using PowerShell. For more information, see [Assign Teams add-on licenses to users](teams-add-on-licensing/assign-teams-add-on-licenses.md).

2. **Make sure you're in TeamsOnly mode.** To check, in the Teams admin center, go to **Org-wide settings > Teams upgrade**. The coexistence mode should be set to Teams only.

3. **Create and validate emergency addresses.** In the Teams admin center, go to **Locations > Emergency addresses** to set up emergency addresses. To learn more, see [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md).

4. **Acquire numbers.** Go to your operator's website to order and acquire phone numbers. For a list of operator websites, see [Operators](#operators). You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id) for more information.

5. **Assign numbers.** Once your operator completes the order, they'll upload test numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. Assign numbers to users by using the Teams admin center or by using PowerShell. For more information, see [Assign numbers](#assign-numbers).
 

### Move numbers from Calling Plans to Operator Connect

1. Contact your operator to port your numbers to Operator Connect. See [Operators](#operators) to find your operator's website.

2. After your operator completes the porting order, you can unassign your users' Calling Plan phone numbers, and remove the Calling Plan License. Then, your operator can upload the numbers to your tenant.

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

2. Remove any PSTNUsage associated with your users, otherwise calls will be routed to the gateway specified in the PSTN Usage. To learn how to remove PSTN usage, see [Set-CsOnlinePstnUsage](/powershell/module/skype/set-csonlinepstnusage?view=skype-ps).

3. Go to your operator's website to order and acquire phone numbers. For a list of operator websites, see [Operators](#operators). You'll need to provide your tenant ID. If you don't know your tenant ID, see [Find your Microsoft 365 tenant ID](/onedrive/find-your-office-365-tenant-id) for more information.

4. Once your operator completes the order, they'll upload test numbers to your tenant. You can view the numbers and the provider in the Teams admin center by going to **Voice > Phone numbers**. Assign Operator Connect numbers to users by using the Teams admin center or by using  PowerShell. For more information, see [Assign numbers](#assign-numbers).

   

### Assign numbers

Whether you're adding new Teams users or moving existing users to Operator Connect, the steps for assigning numbers are as follows:

To assign numbers by using the Teams admin center, go to **Phone numbers**. The steps are the same as assigning numbers for Calling Plans. For more information, see [Assign a phone number to a user](assign-change-or-remove-a-phone-number-for-a-user.md).

To assign numbers by using PowerShell, use the Set-CsOnlineVoiceUser cmdlet as follows:

```
Set-CsOnlineVoiceUser -Identity <user>  -TelephoneNumber <phone number> 
```

For example:

```
Set-CsOnlineVoiceUser -Identity john@contoso.com -TelephoneNumber +14255550101
```

For more information about how to assign phone numbers to your users, see [Assign, change, or remove a phone number for a user](assign-change-or-remove-a-phone-number-for-a-user.md).



## Manage your operators

From the My operators tab, you can view your operators and their status and make the following changes to your selections:  

- Manage operator services by country
- Suspend an operator
- Remove an operator

> [!NOTE]
> Before removing an operator from your organization or from a country, you must remove all phone numbers assigned to users in the organization or country and contact the operator to release the numbers.

## Operators

You can acquire phone numbers from the following operators by going to the websites linked here:


|Operator  |Operator website  |
|---------|---------|
|`BT`     | 	https://www.globalservices.bt.com/en/aboutus/operator-connect        |
|`Deutsche Telekom`     |   https://cloud.telekom.de/de/blog/cloud-software/microsoft-teams-operator-connect      |
|`Intrado`     | https://insight.intrado.com/operator-connect       |
|`NTT`     |  https://www.hello.global.ntt/operator-connect       |
|`NuWave`     |   https://ipilot.io/microsoft-operator-connect/   |
|`Orange Business Services`     | https://www.orange-business.com/en/blogs/operator-connect-orange-and-microsoft-streamline-calling-for-teams-users        |
|`Pure IP`    | https://info.pure-ip.com/operator-connect        |
|`Rogers`    | https://www.rogers.com/business/products-and-solutions/microsoft-365-business-voice        |
|`TATA Communications`     |  https://www.tatacommunications.com/solutions/unified-communications/unified-communications-as-a-service/microsoft-teams-solutions/       |
|`Telenor`     | https://www.telenor.no/bedrift/telefoni/teams/operator-connect        |
|`Verizon`     |  https://www.verizon.com/business/resources/lp/operator-connect       |
