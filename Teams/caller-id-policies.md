---
title: Create and manage Caller ID for users
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: roykuntz; jens
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-voice
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.voice.callinglineid.overview
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use and manage caller ID policies in Microsoft Teams to change or block the caller ID of Teams users in your organization.
---

# Create and manage Caller ID for users

## Overview

TEST

This article describes how to manage caller ID settings for your users. You can:

- Display an alternate phone number for Teams users in your organization.

- Block the outbound phone number.

- Block an incoming number from being displayed.

- Set the Calling Party Name (CNAM). For example, when a user makes a call, you can change the caller ID to display your organization's main phone number and company name instead of the user's phone number.

With settings turned off, the Teams user's phone number is visible when that user makes a call to the Public Switched Telephone Network (PSTN). Likewise, when a PSTN caller makes a call to a Teams user, the PSTN caller's phone number is visible. By default, the following caller ID settings are **turned off**.

- **Block incoming caller ID:** Block a user from receiving Caller ID on any incoming PSTN calls.

- **Override the caller ID policy:** Allow users to override the settings in the policy that decide whether or not they display their number to the callee. This means that users can choose whether to display their caller ID. For more information, see [End user control of outbound caller ID.](/microsoftteams/how-can-caller-id-be-used-in-your-organization#end-user-control-of**-outbound-caller-id).

- **Set Calling Party Name (CNAM):** Send a CNAM on outbound PSTN calls.

- **Replace outgoing caller ID:** Replace a user's Caller ID, which by default is their telephone number, with another phone number. For example, you can change the user's Caller ID from their phone number to a main phone number for your business or to a main phone number for the legal department. You can set the Calling ID number to any Calling Plan, Operator Connect, or Direct Routing phone number assigned to a resource account used by an Auto Attendant or a Call Queue.

- **Block outbound caller ID:** Block the outgoing Caller ID from being sent on a user's outgoing PSTN calls. Doing this will block their phone number from being displayed on the phone of a person being called. This means that the call is seen as coming from Anonymous.


> [!NOTE]
> Emergency calls will always send the user's telephone number (caller ID).

To learn more about these settings and how you can use them, see [How can caller ID be used in your organization](how-can-caller-id-be-used-in-your-organization.md).

## Set up and manage caller ID policies

You can configure caller ID policies by using the Teams admin center or by using PowerShell.

  > [!NOTE]
  > Using the service number calling ID substitute will be deprecated. Use Resource account substitution instead. 

### Use the Teams admin center

You can manage caller ID policies by going to **Voice** > **Caller ID policies** in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

Follow the steps below to create a caller ID policy for your users.

#### Create a custom caller ID policy

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies.**

2. Select **Add**.

3. Enter a name and description for the policy.

4. Choose the settings that you want.

    **Replace the caller ID with:** Set which caller ID will be displayed for users by selecting one of the following:
      - **User's number:** Display the user's number.
      - **Service number:** Display the service number. (Note: will be deprecated.)
      - **Anonymous:** Display the caller ID as Anonymous.
      - **Resource account:** Set a resource account associated to an Auto Attendant or Call Queue.<br><br>

    
    Depending on which option you choose, you can now specify a service number or a resource account associated to an Auto Attendant or Call Queue.

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


#### New custom Caller ID policy

This example creates a new Caller ID policy that sets the Caller ID to the phone number of the specified resource account and sets the Calling party name to Contoso:

```PowerShell
$ObjId = (Get-CsOnlineApplicationInstance -Identity dkcq@contoso.com).ObjectId
```

```PowerShell
New-CsCallingLineIdentity -Identity DKCQ -CallingIDSubstitute Resource -EnableUserOverride $false -ResourceAccount $ObjId -CompanyName "Contoso"
```

This example creates a new Caller ID policy that sets the Caller ID to Anonymous:

```PowerShell
New-CsCallingLineIdentity -Identity Anonymous -Description "anonymous policy" -CallingIDSubstitute Anonymous -EnableUserOverride $false
```

#### Change a caller ID policy

This example modifies the UKAA Caller ID policy to set a new description.

```PowerShell
Set-CsCallingLineIdentity -Identity "UKAA" -Description "UK Main office"
```

#### Remove a caller ID policy

This example removes the UKAA Caller ID policy.

```PowerShell
Remove-CsCallingLineIdentity -Identity "UKAA"
```

#### Grant a caller ID policy

This example grants the Anonymous Caller ID policy to Amos Marble.

```PowerShell
Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName "Anonymous"
```

## Related topics

[How can caller ID be used in your organization](how-can-caller-id-be-used-in-your-organization.md)

[New-CsCallingLineIdentity](/powershell/module/skype/new-cscallinglineidentity)

[Set-CsCallingLineIdentity](/powershell/module/skype/set-cscallinglineidentity)

[Assign policies to your users in Teams](policy-assignment-overview.md)
