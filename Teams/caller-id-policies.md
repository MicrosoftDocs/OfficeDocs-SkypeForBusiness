---
title: Manage caller ID for users
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: jens; roykuntz
ms.date: 04/21/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-voice
  - Tier1
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.voice.callinglineid.overview
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to manage caller ID in Microsoft Teams to change or block the caller ID of Teams users in your organization.
---

# Manage caller ID for users

This article describes how to manage caller ID settings for your users.

Caller ID consists of two user-facing pieces of information:

- **Calling line ID (CLID)** - The phone number that the Public Switched Telephone Network (PSTN) presents as the caller's identity
- **Calling party name (CNAM)** - The name that appears alongside the phone number (i.e. your company's name, a user's name, or Anonymous)

For more specific technical details about these two items and how they work, see [More about Calling Line ID and Calling Party Name](more-about-calling-line-ID-and-calling-party-name.md).

## Outbound caller ID options

For the outbound PSTN caller ID, the following options are:

- The telephone number assigned to the user, which is the default.
- Anonymous, which is available by removing the presentation of the user’s PSTN number.
- A substitute phone number, which can be one of the following:
  - A telephone number through Operator Connect or Direct Routing that is assigned to a resource account used by a Teams Auto Attendant or Call Queue.
  - A telephone number that is classified as a service and toll-free number in your Calling Plans telephone number inventory. It is assigned to a Teams Auto Attendant or Call Queue.
- The Calling Party Name or CNAM set on the outbound PSTN call.
  - For example, when a user makes a call, you can change the caller ID to display your organization's main phone number and company name instead of the user's phone number.
  - The CNAM can have a maximum of 200 characters, but downstream systems might support fewer characters.
  - The CNAM is sent on calls where the caller ID is substituted with LineUri, a resource account or service phone number, and when the caller is a Teams user.
- End user control that overrides the caller ID policy.
  - The parameter `-EnableUserOverride` has precedence over other settings in the [CallingLineIdentity](/powershell/module/skype/set-cscallinglineidentity) policy, unless the parameter `-CallingIDSubstitute` is set to Anonymous. For example, assume a policy instance has substitution enabled with a resource account and `-EnableUserOverride` is set and enabled by the user. In this case, the outbound caller ID will be blocked and Anonymous will be used. If a policy instance has substitution set to Anonymous and `-EnableUserOverride` is enabled, then the outbound caller ID will always be Anonymous, regardless of the end user setting.

For Direct Routing, the phone number substitution and the CNAM is sent in the `From` Session Information Protocol (SIP) header. If the corresponding [OnlinePstnGateway](/powershell/module/skype/set-csonlinepstngateway) policy is configured with `-ForwardPai $true`, the P-Asserted-Identity (PAI) SIP header will contain the real calling user.

For more information, see [caller ID policies](#caller-id-policies).

## Inbound caller ID options

Phone System shows the incoming external phone number as the caller ID. If the number is associated with a user or contact in Azure AD or a personal contact, the Skype for Business and Teams clients will show the caller ID based on that information. If the phone number is not in Azure AD or a personal contact, the telco-provided display name will be shown if it is available.

The **Block incoming caller ID** setting allows for blocking the caller ID on incoming PSTN calls. You can turn on this setting, but it isn't available to your end users on the user settings page. When this setting is turned on, the incoming PSTN caller is displayed as coming from Anonymous.

> [!IMPORTANT]
> Emergency calls will always send the user's telephone number (caller ID) to a public-safety answering point (PSAP). For more information on emergency calls, read [Plan and manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

For more information, see [caller ID policies](#caller-id-policies).

## Caller ID policies

As an admin, you can control caller ID for both inbound and outbound calls by using PowerShell with the CallingLineIdentity policy or by using the Teams admin center under **Voice** > **Caller ID policies**. For more information, see [Configure caller ID policies](#configure-caller-id-policies).

With settings turned off, the Teams user's phone number is visible when that user makes a call to the PSTN. Likewise, when a PSTN caller makes a call to a Teams user, the PSTN caller's phone number is visible.

By default, the following caller ID settings are turned off.

|Setting|Default|Description|
|-------|--------|---------|
|Block incoming caller ID|Off|This setting blocks a user from receiving caller ID on any incoming PSTN calls.|
|Override the caller ID policy|Off|This setting allows users to override the settings in the policy that decide whether or not they display their number to the callee. This means that users can choose whether to display their caller ID.</br></br>Your end users can set their caller ID to Anonymous by going to **Settings** > **Calls**, and then under **Caller ID**, select **Hide my phone number and profile information for all calls**. It takes a few minutes for this setting change to reflect on new calls.</br>|
|Calling Party Name|(empty)|This setting sends a CNAM on outbound PSTN calls.|
|Replace the caller ID with|User's number|This setting replaces a user's caller ID with another phone number. For example, you can change the user's caller ID from their phone number to a main phone number for your business or to a main phone number for the legal department. You can set the calling ID number to any Calling Plan, Operator Connect, or Direct Routing phone number assigned to a resource account used by an Auto Attendant or a Call Queue.</br></br>If this is set to **Anonymous**, the outgoing caller ID is blocked from being sent on a user's outgoing PSTN calls. Doing this will block their phone number from being displayed on the phone of a person being called. This means that the call is seen as coming from Anonymous. If the outbound caller ID is set to **Anonymous**, **Override the caller ID policy** will have no effect, and the caller ID will still show as Anonymous.|
|Replace the caller ID with this resource account/service number|(Choose a resource account/service number)|This setting lets you choose a resource account or service number to replace the caller ID of users.|

> [!NOTE]
> The use of `-CallingIDSubstitute Service` will be deprecated. You are no longer able to create new caller ID policies using `-CallingIDSubstitute Service`. You should use `-CallingIDSubstitute Resource` instead. See [Set-CsCallingLineIdentity](/powershell/module/skype/Set-CsCallingLineIdentity) for more details and examples.

## Configure caller ID policies

You can configure caller ID policies with the [Teams admin center](#use-the-teams-admin-center) or with [PowerShell](#use-powershell).

### Use the Teams admin center

You can manage caller ID policies by going to **Voice** > **Caller ID policies** in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

#### Create a custom caller ID policy

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies.**

2. Select **Add**.

3. Enter a name and description for the policy.

4. Under **Replace the caller ID with**, set which caller ID is displayed for users by selecting one of the following:
      - **User's number:** Display the user's number.
      - **Service number:** Display the service number. (Note: this option will be deprecated. Newly created caller ID policies must use **Resource account**)
      - **Anonymous:** Display the caller ID as Anonymous.
      - **Resource account:** Set a resource account associated with an Auto Attendant or Call Queue.

    If you choose **Service number** or **Resource account**, you are prompted to specify a service number or a resource account for the next field, called **Replace the caller ID with this resource account/service number**. Only resource accounts with an assigned phone number will be displayed. If you just assigned a phone number to the resource account, it may take a few minutes before the resource account is available for selection.

5. Select **Save**.

#### Assign a custom caller ID policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

#### Edit a caller ID policy

You can edit the global policy or any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies**.
2. Select the policy by clicking to the left of the policy name, and then select **Edit**.
3. Change the settings that you want, and then select **Save**.

### Use PowerShell

You can manage caller ID policies by using the following PowerShell cmdlets in Teams PowerShell module 2.3.1 or later:

- [New-CsCallingLineIdentity](/powershell/module/skype/new-cscallinglineidentity)
- [Set-CsCallingLineIdentity](/powershell/module/skype/set-cscallinglineidentity)
- [Remove-CsCallingLineIdentity](/powershell/module/skype/remove-cscallinglineidentity)
- [Get-CsCallingLineIdentity](/powershell/module/skype/get-cscallinglineidentity)
- [Grant-CsCallingLineIdentity](/powershell/module/skype/grant-cscallinglineidentity)

#### New custom caller ID policy

This example creates a new caller ID policy that sets the caller ID to the phone number of the specified resource account and sets the Calling party name to Contoso:

```PowerShell
$ObjId = (Get-CsOnlineApplicationInstance -Identity dkcq@contoso.com).ObjectId
```

```PowerShell
New-CsCallingLineIdentity -Identity DKCQ -CallingIDSubstitute Resource -EnableUserOverride $false -ResourceAccount $ObjId -CompanyName "Contoso"
```

This example creates a new caller ID policy that sets the caller ID to Anonymous:

```PowerShell
New-CsCallingLineIdentity -Identity Anonymous -Description "anonymous policy" -CallingIDSubstitute Anonymous -EnableUserOverride $false
```

#### Change a caller ID policy

This example modifies the UKAA caller ID policy to set a new description:

```PowerShell
Set-CsCallingLineIdentity -Identity "UKAA" -Description "UK Main office"
```

#### Remove a caller ID policy

This example removes the UKAA caller ID policy:

```PowerShell
Remove-CsCallingLineIdentity -Identity "UKAA"
```

#### Grant a caller ID policy

This example grants the Anonymous caller ID policy to Amos Marble:

```PowerShell
Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName "Anonymous"
```

## Related topics

- [Teams policies reference - Caller ID](settings-policies-reference.md#caller-id-policies)
- [More about Calling Line ID and Calling Party Name](more-about-calling-line-ID-and-calling-party-name.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Set-CsCallingLineIdentity](/powershell/module/skype/set-cscallinglineidentity)
