---
title: Manage caller ID policies for users
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: roykuntz; jens
ms.date: 04/11/2023
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
description: Learn how to manage caller ID policies in Microsoft Teams to change or block the caller ID of Teams users in your organization.
---

# Manage caller ID policies for users

## Overview

This article describes how to manage caller ID settings for your users. You can:

- Display an alternate phone number for Teams users in your organization.
- Block the outbound phone number.
- Block an incoming number from being displayed.
- Set the Calling Party Name (CNAM). For example, when a user makes a call, you can change the caller ID to display your organization's main phone number and company name instead of the user's phone number.

## Caller ID settings

With settings turned off, the Teams user's phone number is visible when that user makes a call to the Public Switched Telephone Network (PSTN). Likewise, when a PSTN caller makes a call to a Teams user, the PSTN caller's phone number is visible. By default, the following caller ID settings are turned off.

### Outbound PSTN caller ID settings

#### Override the caller ID policy

This setting allows users to override the settings in the policy that decide whether or not they display their number to the callee. This means that users can choose whether to display their caller ID. The default value of `EnableUserOverride` is False.

Your end users can set their caller ID to Anonymous by going to **Settings** > **Calls**, and then under **Caller ID**, select **Hide my phone number and profile information for all calls**. It takes a few minutes for this setting change to reflect on new calls.

If the outbound caller ID is set to **Anonymous** for the **[Block outbound caller ID](#block-outbound-caller-id)** setting, `EnableUserOverride` has no effect, and the caller ID is always set to Anonymous.

#### Set Calling Party Name (CNAM)

This setting sends a CNAM on outbound PSTN calls.

#### Replace outgoing caller ID

This setting replaces a user's caller ID, which by default is their telephone number, with another phone number. For example, you can change the user's caller ID from their phone number to a main phone number for your business or to a main phone number for the legal department. You can set the calling ID number to any Calling Plan, Operator Connect, or Direct Routing phone number assigned to a resource account used by an Auto Attendant or a Call Queue.

#### Block outbound caller ID

This setting blocks the outgoing caller ID from being sent on a user's outgoing PSTN calls. Doing this will block their phone number from being displayed on the phone of a person being called. This means that the call is seen as coming from Anonymous.

> [!NOTE]
> Emergency calls will always send the user's telephone number (caller ID).

### Inbound PSTN caller ID settings

#### Block incoming caller ID

This setting blocks a user from receiving caller ID on any incoming PSTN calls.

## Set up and manage caller ID policies

You can configure caller ID policies by using the Teams admin center or by using PowerShell.

  > [!NOTE]
  > Using the service number calling ID substitute will be deprecated. Use Resource account substitution instead.

### Use the Teams admin center

You can manage caller ID policies by going to **Voice** > **Caller ID policies** in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

#### Create a custom caller ID policy

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies.**

2. Select **Add**.

3. Enter a name and description for the policy.

4. Under **Replace the caller ID with**, set which caller ID is displayed for users by selecting one of the following:
      - **User's number:** Display the user's number.
      - **Service number:** Display the service number. (Note: this option will be deprecated.)
      - **Anonymous:** Display the caller ID as Anonymous.
      - **Resource account:** Set a resource account associated with an Auto Attendant or Call Queue.

    If you choose **Service number** or **Resource account**, you are prompted to specify a service number or a resource account for the next field. Only resource accounts with an assigned phone number will be displayed. If you just assigned a phone number to the resource account, it may take a few minutes before the resource account is available for selection

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

This example modifies the UKAA caller ID policy to set a new description.

```PowerShell
Set-CsCallingLineIdentity -Identity "UKAA" -Description "UK Main office"
```

#### Remove a caller ID policy

This example removes the UKAA caller ID policy.

```PowerShell
Remove-CsCallingLineIdentity -Identity "UKAA"
```

#### Grant a caller ID policy

This example grants the Anonymous caller ID policy to Amos Marble.

```PowerShell
Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName "Anonymous"
```

## Related topics

- [Teams policies reference - Caller ID](settings-policies-reference.md#caller-id-policies)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Set-CsCallingLineIdentity](/powershell/module/skype/set-cscallinglineidentity)
