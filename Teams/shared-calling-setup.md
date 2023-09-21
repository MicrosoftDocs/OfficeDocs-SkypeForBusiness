---
title: "Configure Shared Calling"
ms.reviewer: jenstr
ms.date: 09/20/2023
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom: 
  - Phone System
description: "In this article, you'll learn how to configure Teams Phone Shared Calling policies."
---

# Configure Shared Calling

Before reading this article, be sure you've read [Plan for Shared Calling](shared-calling-plan.md). It describes licensing and other requirements needed to set up Shared Calling.

This article describes the following steps to configure Shared Calling:

1. [Assign Teams Phone licenses and enable users for voice.](#step-1-assign-teams-phone-licenses-and-enable-users-for-voice)
1. [Assign number to resource account for inbound and outbound calling.](#step-2-assign-number-to-resource-account-for-inbound-and-outbound-calling)
1. [Associate resource account with Auto attendant for inbound calling.](#step-3-associate-resource-account-with-auto-attendant-for-inbound-calling)
1. [Assign a location to the resource account for emergency calling](#step-4-assign-a-location-to-the-resource-account-for-emergency-calling)
1. [Assign Pay-As-You-Go Calling Plan to resource account with Calling Plan service number.](#step-5-assign-pay-as-you-go-calling-plan-to-resource-account-with-calling-plan-service-number)
1. [Assign and fund a Communication credits license.](#step-6-assign-and-fund-a-communication-credits-license)
1. [Create voice routing policy without PSTN usages.](#step-7-create-voice-routing-policy-without-pstn-usages)
1. [Enable emergency calling for users.](#step-8-enable-emergency-calling-for-users)
1. [Create your Shared Calling policy.](#step-9-create-the-shared-calling-policy)
1. [Assign the Shared Calling policy to users](#step-10-assign-the-shared-calling-policy-to-users)

For a step-by-step example on how to configure Shared Calling with PowerShell, see [Shared Calling scenario](shared-calling-scenario.md).

Keep the following in mind:

- You can use the same resource account in multiple Shared Calling policies.

- All numbers within a given policy must be of the same number type and country (resource and emergency calling numbers).

- When you add a resource account to a policy, you must ensure that the number has a location/emergency address assigned to it.

- If you remove, reassign, or port a number of the resource account used in a Shared Calling policy, the policy remains intact, but outbound calls will fail for any users still configured to make calls from that number.

- In some Calling Plan markets, you aren't allowed to set the location on service numbers. For these markets, please contact the [Telephone Number Services service desk](/microsoftteams/phone-reference/manage-numbers/contact-tns-service-desk.md).

- If you are attempting to use a resource account with an Operator Connect phone number assigned, you should confirm support for Shared Calling with your operator.

- Shared Calling isn't supported for Calling Plan service phone numbers in Romania, the Czech Republic, Hungary, Singapore, New Zealand, Australia, and Japan. A limited number of existing Calling Plan service phone numbers in other countries are also not supported for Shared Calling. For information about these service phone numbers, please contact the [Telephone Number Services service desk](/microsoftteams/phone-reference/manage-numbers/contact-tns-service-desk.md).

## Step 1: Assign Teams Phone licenses and enable users for voice

Each user must have a Teams Phone license assigned, and each user must be "voice enabled."

- To assign the Teams Phone license, do the following:
  1. Use the Microsoft 365 admin center and go to **Billing** > **Licenses**.
  1. Select your Teams Phone license. On the product details page, select **Assign licenses** and assign the license to your users.
  1. Select **Assign** once you're finished.

- To enable users for voice, use the [Set-CsPhoneNumberAssignment cmdlet](/powershell/module/teams/set-csphonenumberassignment) and set the -EnterpriseVoiceEnabled parameter to $true.

For more information about licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md) and [assigning licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users.md).

## Step 2: Assign number to resource account for inbound and outbound calling

You must create or reuse an existing resource account and assign a Calling Plan service number, Operator Connect number, or Direct Routing number to this account to be used for inbound and outbound calling. For more information about creating resource accounts, see [Manage resource accounts](manage-resource-accounts.md).

## Step 3: Associate resource account with Auto attendant for inbound calling

If inbound calling is required, you must associate this resource account with a configured Auto attendant that is scoped to the users it needs to reach. For more information, see [Manage resource accounts](manage-resource-accounts.md) and [Set up Auto attendants](create-a-phone-system-auto-attendant.md).

## Step 4: Assign a location to the resource account for emergency calling

You need the location id to assign the location to a resource account. You can get the location id by using the [Get-CsOnlineLisLocation](/powershell/module/skype/get-csonlinelislocation) PowerShell cmdlet.

To assign a location to a resource account number for Calling Plan, Operator Connect, and Direct Routing, use the [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) PowerShell cmdlet.

For information on the configuration of emergency locations, see [Manage emergency locations](add-change-remove-emergency-location-organization).

## Step 5: Assign Pay-As-You-Go Calling Plan to resource account with Calling Plan service number

If the resource account is using a Calling Plan service number, you must have a [Pay-As-You-Go Calling Plan](calling-plans-for-office-365.md#pay-as-you-go-calling-plan), and assign it to the resource account.

## Step 6: Assign and fund a Communication credits license

If the resource account is using a Calling Plan service number, assign a Communications credits license to the resource account and fund it to support outbound Shared Calling calls via the Pay-As-You-Go Calling Plan.

For more information, see [How to fund a Pay-As-You-Go Calling Plan](calling-plans-for-office-365.md#how-to-fund-a-pay-as-you-go-calling-plan), [Enable pay-as-you-go for your subscription](/microsoft-365/commerce/subscriptions/manage-pay-as-you-go-services.md), [Customers with new commerce experience calling subscriptions](what-are-communications-credits.md#customers-with-new-commerce-experience-calling-subscriptions) and [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md).

## Step 7: Create voice routing policy without PSTN usages

Shared Calling users must not have an assigned voice routing policy (also known as a call routing policy) with valid PSTN usages. If you are using global voice routing policies in your tenant with valid PSTN usages, then you must create a new voice routing policy with empty PSTN usages and assign this policy to Shared Calling users.

## Step 8: Enable emergency calling for users

You must ensure that users enabled for Shared Calling are able to make emergency calls to emergency services--and that emergency services are able to call back Shared Calling users who've made emergency calls. How you enable emergency calling is described in detail in [Emergency calling](#emergency-calling-for-shared-calling-users).

You aren't required to define emergency numbers for a Shared Calling policy. If you don't define emergency numbers, when an emergency call is made, the number associated with the resource account in the Shared Calling policy is used.

## Step 9: Create the Shared Calling policy

Once you've created your emergency call routing policy, you'll create your Shared Calling policy.

Currently, Shared Calling can only be configured with PowerShell.

To configure and manage Shared Calling policies, you'll use the following Teams PowerShell cmdlets:

- [New-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/new-csteamssharedcallingroutingpolicy)
- [Get-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/get-csteamssharedcallingroutingpolicy)
- [Remove-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/remove-csteamssharedcallingroutingpolicy)
- [Set-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/set-csteamssharedcallingroutingpolicy)
- [Grant-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/grant-csteamssharedcallingroutingpolicy)

For example, the following command creates a new Shared Calling policy, called Seattle, and configures the policy with the resource account main-aa@contoso.com. The command also identifies the emergency callback numbers associated with the resource account:

```powershell
$ecbn1 = '+14255556789'
$ecbn2 = '+14255554321'
$ra = Get-CsOnlineUser -Identity main-aa@contoso.com
New-CsTeamsSharedCallingRoutingPolicy -Identity Seattle -ResourceAccount $ra.Identity -EmergencyNumbers @{add=$ecbn1,$ecbn2}
```

The next command removes one of the emergency callback numbers, +14255554321, from the policy (required before that number can be deleted or reassigned):

```powershell
Set-CsTeamsSharedCallingRoutingPolicy -Identity Seattle -EmergencyNumbers @{remove='+14255554321'}
```

The next command adds a new emergency callback number, 1425555433, to the policy:

```powershell
Set-CsTeamsSharedCallingRoutingPolicy -Identity Seattle -EmergencyNumbers @{add='+1425555433'} 
```

## Step 10: Assign the Shared Calling policy to users

Once you've [created your Shared Calling policy](#step-9-create-the-shared-calling-policy), you need to assign it to users with [Grant-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/grant-csteamssharedcallingroutingpolicy).

The following cmdlet assigns the Shared Calling policy to a user:

```powershell
Grant-CsTeamsSharedCallingRoutingPolicy -PolicyName Seattle -Identity user@contoso.com
```

## Emergency calling for Shared Calling users

To enable emergency calling for Shared Calling users, you must configure emergency numbers and location of the user.

- **[Emergency calling number](#configure-emergency-calling-numbers)**: The Teams client used by the Shared Calling user needs to recognize that a given phone number called is an emergency calling number like 911.

- **[Emergency callback number](#emergency-callback-number)**: The emergency services must be able to call back a user that has dialed the emergency services. Since a Shared Calling user does not have a dedicated phone number assigned, either the phone number of the resource account or configured emergency numbers is used.

- **[Emergency location](#emergency-location)**: The emergency services need to know the location or emergency address of the Shared Calling user making the emergency call.

Emergency calling for Shared Calling is available globally. There are configuration requirements for customers outside of North America. You need to ensure that the emergency addresses assigned to the phone numbers used for the resource accounts in the Shared Calling policy instances are uploaded to their carrier’s emergency calling database. You must contact individual carriers to perform this process.

### Configure emergency calling numbers

Emergency calling numbers are defined in the [emergency call routing policy](manage-emergency-call-routing-policies.md). If you've not already done so, you must create and assign an emergency call routing policy for each user enabled for Shared Calling--regardless of the type of number used for the resource account: Calling Plan, Operator Connect, or Direct Routing.

### Routing of emergency calls

The routing of the emergency call is based on how the resource account is configured. If the resource account used in the Shared Calling policy uses a Calling Plan or Operator Connect number, the emergency call routing policy assigned to the Shared Calling user shouldn't have online PSTN usages configured. If the emergency call routing policy used for the emergency call has online PSTN usages configured, the routing of the emergency call will be based on the online PSTN usages. For more information, see [Manage emergency call routing policies](manage-emergency-call-routing-policies.md) and [Set-CsOnlinePstnUsage](/powershell/module/skype/set-csonlinepstnusage).

### Emergency callback number

Emergency services must be able to call back the originator of an emergency call through the *emergency callback number*. The callback number serves as the caller ID or calling number used when an emergency call is made.

You define a list of emergency callback numbers in the Shared Calling policy by using the -EmergencyNumbers parameter. Each Shared Calling policy must have a unique emergency calling number. That is, you can't use the same emergency number in more than one Shared Calling policy.

When an emergency call is made, the next free number in the emergency number list will be used as the caller ID and this number will be reserved for the next 60 minutes.

- If there are no free numbers available in the list, we will reuse a phone number from the list.

- If this list is empty, the phone number of the resource account is used as the emergency callback number--however, this isn't supported if your resource account is assigned a Calling Plan toll free service number.

When emergency numbers are added to a policy:

- The emergency numbers must be routable for inbound PSTN calls. For Calling Plan & Operator Connect, the callback numbers must be available within the tenant.

- The emergency numbers specified must all be of the same phone number type as the phone number assigned to the specified resource account--that is Calling Plan, Operator Connect, or Direct Routing.

- The emergency numbers can’t be assigned to any user or resource account.

- You can't delete or reassign an emergency number used in any Shared Calling policy. You must first remove the number from the Shared Calling policy before you delete or reassign the number.

You can view all Calling Plan and Operator Connect emergency numbers by country, number sequence, or policy group by using the Teams admin center. For assigned Direct Routing numbers, you can use [Get-CsPhoneNumberAssignment](/powershell/module/teams/get-csphonenumberassignment) -NumberType DirectRouting.

### Calling Plan service numbers

- If the resource account has assigned a Calling Plan service number, then the emergency callback number must be a Calling Plan subscriber number--not a Calling Plan service number.

- If your resource account is assigned a Calling Plan toll-free service number, you need to add Calling Plan subscriber numbers to emergency numbers in the Shared Calling policy.

### Emergency location

The emergency location provided to the emergency services through the emergency call is determined in the following order:

1. Actual location of user -- dynamically obtained by the Teams client.

2. Location assigned to the phone number assigned to the resource account specified in the Shared Calling policy -- statically obtained.

For more information about emergency calling and how location is determined, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md) and [Configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

## Related topics

- [Plan for Shared Calling](shared-calling-plan.md)
- [Shared Calling scenario](shared-calling-scenario.md)
- [Set-CsTeamsSharedCallingRoutingPolicy](/powershell/module/teams/set-csteamssharedcallingroutingpolicy)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment)
