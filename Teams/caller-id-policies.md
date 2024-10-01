---
title: Manage caller ID for users
ms.author: crowe
author: CarolynRowe
manager: pamgreen
ms.reviewer: roykuntz
ms.date: 03/26/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
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

This article is for administrators and IT professionals who manage caller ID settings for their users. As an administrator, you can:

- Display an alternate phone number for Teams users in your organization.
- Block the outbound phone number.
- Block an incoming number from being displayed.
- Set the Calling Party Name (CNAM).

Caller ID consists of two user-facing pieces of information:

- **Calling line ID (CLID)** - The phone number that the Public Switched Telephone Network (PSTN) presents as the caller's identity.
- **Calling party name (CNAM)** - The name that appears alongside the phone number (for example, your company's name, a user's name, or Anonymous).

> [!IMPORTANT]
> Emergency calls always send the user's telephone number (caller ID) to a public-safety answering point (PSAP). For more information on emergency calls, see [Plan and manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

For more information, see [More about Calling Line ID and Calling Party Name](more-about-calling-line-ID-and-calling-party-name.md).

## Outbound caller ID options

For the outbound PSTN caller ID, the following options are available:

- The telephone number assigned to the user, which is the default.

- Anonymous, which is available by removing the presentation of the user’s PSTN number.

- A substitute phone number, which can be one of the following:

  - A telephone number through Operator Connect or Direct Routing that is assigned to a resource account used by a Teams Auto attendant or Call queue.

  - A telephone number that is classified as a service and toll-free number in your Calling Plans telephone number inventory. The number is assigned to a resource account used by a Teams Auto attendant or Call queue.
  
  > [!NOTE]
  > The use of CallingIDSubstitute = Service has been deprecated. You're no longer able to create new caller ID policies using CallingIDSubstitute = Service. Existing caller ID policies with CallingIDSubstitute = Service aren't being honored. Use CallingIDSubstitute = Resource instead. For more information, see [Set-CsCallingLineIdentity](/powershell/module/teams/Set-CsCallingLineIdentity).

- The Calling Party Name or CNAM set on the outbound PSTN call.

  - For example, when a user makes a call, you can change the caller ID to display your organization's main phone number and company name instead of the user's phone number.

  - The CNAM can have a maximum of 200 characters, but downstream systems might support fewer characters.
  
  - The CNAM is sent on calls where the caller ID is substituted with LineURI, a resource account or service phone number, and when the caller is a Teams user.

- End user control that overrides the caller ID policy.

  - The parameter EnableUserOverride has precedence over other settings in the [CallingLineIdentity](/powershell/module/teams/set-cscallinglineidentity) policy.

  - For example, assume a policy instance has substitution enabled with a resource account and EnableUserOverride is set and enabled by the user. In this case, the outbound caller ID is blocked and Anonymous is used.

You can't assign the following types of phone numbers for the outbound caller ID:

- Any phone numbers that are classified as a user in your Calling Plan or Operator Connect's telephone number inventory.

- Any on-premises telephone number through Direct Routing that is assigned to a user.

- A Skype for Business Server on-premises telephone number.

For Direct Routing, the phone number substitution and the CNAM are sent in the `From` Session Information Protocol (SIP) header. If the corresponding [OnlinePstnGateway](/powershell/module/teams/set-csonlinepstngateway) policy is configured with `-ForwardPai $true`, the P-Asserted-Identity (PAI) SIP header contains the real calling user.

For more information, see [Configure caller ID policies](#configure-caller-id-policies).

## Inbound caller ID options

Teams Phone shows the incoming external phone number as the caller ID. If the number is associated with a user or contact in Microsoft Entra ID or a personal contact, the Skype for Business and Teams clients show the caller ID based on that information. If the phone number isn't in Microsoft Entra ID or a personal contact, the telco-provided display name is shown if it's available.

The **Block incoming caller ID** setting allows for blocking the caller ID on incoming PSTN calls. You can turn on this setting, but it isn't available to your end users on the user settings page. When this setting is turned on, the incoming PSTN caller is shown as coming from Anonymous.

For more information, see [configure caller ID policies](#configure-caller-id-policies).

## Configure caller ID policies

You can control caller ID for both inbound and outbound calls. With caller ID settings turned off, the Teams user's phone number is visible when that user makes a call to the PSTN. Likewise, when a PSTN caller makes a call to a Teams user, the PSTN caller's phone number is visible.

By default, the following caller ID settings are **turned off**.

|Setting|Default|Description|
|-------|--------|---------|
|Block incoming caller ID|Off|This setting blocks a user from receiving caller ID on any incoming PSTN calls.|
|Override the caller ID policy|Off|This setting allows users to override the settings in the policy that decide whether or not they display their number to the callee. By turning on this setting, users can choose whether to display their caller ID.</br></br>Your end users can set their caller ID to Anonymous by going to **Settings** > **Calls**, and then under **Caller ID**, select **Hide my phone number and profile information for all calls**. It takes a few minutes for this setting change to reflect on new calls.</br>|
|Calling Party Name|(empty)|This setting sends a CNAM on outbound PSTN calls.|
|Replace the caller ID with Users's number|User's number|This setting replaces a user's caller ID with another phone number. For example, you can change the user's caller ID from their phone number to a main phone number for your business or to a main phone number for the legal department. You can set the calling ID number to any Calling Plan, Operator Connect, or Direct Routing phone number assigned to a resource account used by an Auto attendant or a Call queue.|
|Replace the caller ID with Anonymous|(empty)|This setting lets you block the outgoing caller ID from being sent on a user's outgoing PSTN calls. Turning on this setting blocks the outgoing caller's phone number from being displayed on the phone of a person being called and that call is displayed as coming from Anonymous. If Override the caller ID is On, then the user can toggle off the option to hide their caller ID in the Teams client.  |
|Replace the caller ID with Resource account|(empty)|This setting lets you choose a resource account which is used to replace the caller ID of users.|

You can configure caller ID policies by using the [Teams admin center](#use-the-teams-admin-center) or by using [PowerShell](#use-powershell).

### Use the Teams admin center

You manage caller ID policies by going to **Voice** > **Caller ID policies** in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization automatically get the global policy unless you create and assign a custom policy.

For more information on each policy, see [configure caller ID policies](#configure-caller-id-policies).

#### Create a custom caller ID policy

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies.**

2. Select **Add**.

3. Enter a name and description for the policy.

4. Turn on or off **Block incoming caller ID** and **Override the caller ID policy**.

5. Enter a **Calling Party Name**.

6. Under **Replace the caller ID with**, set which caller ID is displayed for users by selecting one of the following:

      - **User's number:** Display the user's number.

      - **Anonymous:** Display the caller ID as Anonymous.

      - **Resource account:** Set a resource account associated with an Auto Attendant or Call Queue.

    If you choose **Resource account**, you're prompted to specify a resource account for the next field, called **Replace the caller ID with this resource account**. Only resource accounts with an assigned phone number will be displayed. If you just assigned a phone number to the resource account, it might take a few minutes before the resource account is available for selection.

7. Select **Save**.

#### Assign a custom caller ID policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

#### Edit a caller ID policy

You can edit the global policy or any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies**.

2. Select the policy by clicking to the left of the policy name, and then select **Edit**.

3. Change the settings that you want, and then select **Save**.

### Use PowerShell

You can manage caller ID policies by using the following PowerShell cmdlets in Teams PowerShell module 2.3.1 or later:

- [New-CsCallingLineIdentity](/powershell/module/teams/new-cscallinglineidentity)
- [Set-CsCallingLineIdentity](/powershell/module/teams/set-cscallinglineidentity)
- [Remove-CsCallingLineIdentity](/powershell/module/teams/remove-cscallinglineidentity)
- [Get-CsCallingLineIdentity](/powershell/module/teams/get-cscallinglineidentity)
- [Grant-CsCallingLineIdentity](/powershell/module/teams/grant-cscallinglineidentity)

#### New custom caller ID policy

The following example creates a new caller ID policy that sets the caller ID to the phone number of the specified resource account, and sets the Calling party name to Contoso:

```PowerShell
$ObjId = (Get-CsOnlineApplicationInstance -Identity dkcq@contoso.com).ObjectId
```

```PowerShell
New-CsCallingLineIdentity -Identity DKCQ -CallingIDSubstitute Resource -EnableUserOverride $false -ResourceAccount $ObjId -CompanyName "Contoso"
```

The next example creates a new caller ID policy that sets the caller ID to Anonymous:

```PowerShell
New-CsCallingLineIdentity -Identity Anonymous -Description "anonymous policy" -CallingIDSubstitute Anonymous -EnableUserOverride $false
```

#### Change a caller ID policy

The following example modifies the UKAA caller ID policy to set a new description:

```PowerShell
Set-CsCallingLineIdentity -Identity "UKAA" -Description "UK Main office"
```

#### Remove a caller ID policy

The following example removes the UKAA caller ID policy:

```PowerShell
Remove-CsCallingLineIdentity -Identity "UKAA"
```

#### Grant a caller ID policy

The following example grants the Anonymous caller ID policy to Amos Marble:

```PowerShell
Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName "Anonymous"
```

## Related articles

- [Teams policies reference - Caller ID](settings-policies-reference.md#caller-id-policies)
- [More about Calling Line ID and Calling Party Name](more-about-calling-line-ID-and-calling-party-name.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Set-CsCallingLineIdentity](/powershell/module/teams/set-cscallinglineidentity)
