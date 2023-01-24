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

This article describes how to manage caller ID settings for your users.  You can:

- Display an alternate phone number for Teams users in your organization
- Block the outbound phone number
- Block an incoming number from being displayed
- Set the Calling Party Name (CNAM). For example, when a user makes a call, you can change the caller ID to display your organization's main phone number and company name instead of the user's phone number.

## Which Caller ID settings can administrators manage for Teams?

By default, the following list of caller ID settings are **turned off**. With the settings turned off, the Teams user's phone number is visible when that user makes a call to a Public Switched Telephone Network (PSTN) phone. Likewise, when a PSTN caller makes a call to a Teams user, the PSTN caller's phone number is visible.
**

- **Block incoming caller ID:** Block a user from receiving Caller ID on any incoming PSTN calls.
- **Override the caller ID policy:** Allow users to override the settings in the policy that decide whether or not they display their number to the callee. This means that users can choose whether to display their caller ID. For more information, see [End user control of outbound caller ID.](/microsoftteams/how-can-caller-id-be-used-in-your-organization#end-user-control-of**-outbound-caller-id)
- **Set Calling Party Name (CNAM):** Send a CNAM on outbound PSTN calls.
- **Outgoing caller ID:** Replace a user's Caller ID, which by default is their telephone number, with another phone number. For example, you could change the user's Caller ID from their phone number to a main phone number for your business or to a main phone number for the legal department. You can set the Calling ID number to any Calling Plan, Operator Connect or Direct Routing phone number assigned to a  resource account used by an Auto Attendant or a Call Queue.
- **Block outbound caller ID:** Block the outgoing Caller ID from being sent on a user's outgoing PSTN calls. Doing this will block their phone number from being displayed on the phone of a person being called. This means that the call is seen as coming from Anonymous.
- **Replace the caller ID with:** Set which caller ID that’ll be displayed for users by selecting one of the following:
  - **User's number:** Display the user's number.
  - **Service number:** Display the service number.
  - **Anonymous:** Display the caller ID as Anonymous.
  - **Resource account:** Set a resource account associated to an Auto Attendant or Call Queue.
- **Replace the caller ID with this service number:** Choose a service number to replace the caller ID of users. This option is available if you selected **Service number** in **Replace the caller ID with.**
- **Replace the caller ID with this resource account:** Choose a resource account associated to an Auto Attendant or Call Queue. The phone number assigned to the resource account will replace the caller ID of users. This option is available if you selected **Resource account** in **Replace the caller ID with.**

> [!NOTE]
> Emergency calls will always send the user's telephone number (caller ID).

To learn more about these settings and how you can use them, see [How can caller ID be used in your organization.](how-can-caller-id-be-used-in-your-organization.md)

## Set up and manage caller ID policies

You can configure caller ID policies by using the Teams admin center or by using PowerShell.

### Use the Teams admin center

You can manage caller ID policies by going to **Voice** > **Caller ID policies** in the Microsoft Teams admin center and use the global (Org-wide default) policy or create and assign custom policies. Users in your organization will automatically get the global policy unless you create and assign a custom policy.

Follow the steps below to create a caller ID policy for your users.

#### Create a custom caller ID policy

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies.**
2. Select **Add**
3. Enter a name and description for the policy.
4. From here, choose the settings that you want.
5. Select **Save**.

#### Assign a custom caller ID policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

#### Edit a caller ID policy

You can edit the global policy or any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies**.
2. Select the policy by clicking to the left of the policy name, and then select **Edit**.
3. Change the settings that you want, and then select **Save**.

### Use PowerShell

You can manage caller ID policies through PowerShell.

  > [!NOTE]
  > Using the Service number caller ID substitution will be deprecated. Use Resource account substitution instead.To set the caller ID to a resource account phone number and to set the calling party name, use the PowerShell cmdlets New-CsCallingLineIdentity or Set-CsCallingLineIdentity in the Teams PowerShell module 2.3.1 or later. (These options are not currently available in the Microsoft Teams admin center.)

Open a Windows PowerShell command prompt and run the following commands:

```PowerShell
# When using Teams PowerShell Module

Import-Module MicrosoftTeams
$credential = Get-Credential
Connect-MicrosoftTeams -Credential $credential
```

1. To view all of the caller ID policy settings in your organization, run:

     ```PowerShell
     Get-CsCallingLineIdentity |fl
     ```

   For more information, see [Get-CsCallingLineIdentity](/powershell/module/skype/Get-CsCallingLineIdentity).
2. To create a new caller ID policy for your organization, use the New-CsCallingIdentity cmdlet:

     ```PowerShell
     New-CsCallingLineIdentity  -Identity Anonymous -Description "Anonymous policy" -CallingIDSubstitute Anonymous -EnableUserOverride $false
     ```

    In all cases, the "Service Number" field should not include an initial "+".

   For more information, see [New-CsCallingLineIdentity](/powershell/module/skype/New-CsCallingLineIdentity).
3. Apply the new policy you created by using the Grant-CsCallingIdentity cmdlet. For example, the following example applies the new policy to user Amos Marble.

     ```PowerShell
     Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName Anonymous
     ```

   For more information, see [Grant-CsCallingLineIdentity](/powershell/module/skype/Grant-CsCallingLineIdentity) cmdlet.
4. If you want to block the incoming caller ID, run:

   ```PowerShell
   Set-CsCallingLineIdentity  -Identity "Block Incoming" -BlockIncomingPstnCallerID $true
   ```

   For more information, see [Set-CsCallingLineIdentity](/powershell/module/skype/Set-CsCallingLineIdentity).
5. To apply the policy setting you created to a user in your organization, run:

   ```PowerShell
   Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName "Block Incoming"
   ```

   For more information, see [Grant-CsCallingLineIdentity](/powershell/module/skype/Grant-CsCallingLineIdentity).

6. To create a new Caller ID policy that sets the Caller ID to the phone number of the specified resource account and sets the Calling party name to Contoso:

   ```PowerShell
   $ObjId = (Get-CsOnlineApplicationInstance -Identity dkcq@contoso.com).ObjectId
   New-CsCallingLineIdentity  -Identity DKCQ -CallingIDSubstitute Resource -EnableUserOverride $false -ResourceAccount $ObjId -CompanyName "Contoso"
   ```

If you have already created a policy, you can use the [Set-CsCallingLineIdentity](/powershell/module/skype/Set-CsCallingLineIdentity) cmdlet to make changes to the existing policy, and then use the [Grant-CsCallingLineIdentity](/powershell/module/skype/Grant-CsCallingLineIdentity) cmdlet to apply the settings to your users.

#### Remove a policy setting

To remove a policy from your organization, run:
  
```PowerShell
Remove-CsCallingLineIdentity -Identity "My Caller ID Policy"
```

To remove a policy from a user, run:
  
```PowerShell
Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName $null
```

### Examples

#### New custom call park policy

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

This example modifies the UKOrgAA Caller ID policy to set the Caller ID to a specified service number.

```PowerShell
Set-CsCallingLineIdentity -Identity "UKOrgAA" -CallingIdSubstitute "Service" -ServiceNumber "14258828080"
```

#### Remove a caller ID policy

This example removes the UKOrgAA Caller ID policy.

```PowerShell
Remove-CsCallingLineIdentity -Identity "UKOrgAA"
```

#### Grant a caller ID policy

This example grants the Anonymous Caller ID policy to Amos Marble.

```PowerShell
Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName "Anonymous"
```

For more information on Teams PowerShell Module cmdlets, see the following articles:

- [New-CsCallingLineIdentity](/powershell/module/skype/new-cscallinglineidentity)
- [Set-CsCallingLineIdentity](/powershell/module/skype/set-cscallinglineidentity)
- [Remove-CsCallingLineIdentity](/powershell/module/skype/remove-cscallinglineidentity)
- [Get-CsCallingLineIdentity](/powershell/module/skype/get-cscallinglineidentity)
- [Grant-CsCallingLineIdentity](/powershell/module/skype/grant-cscallinglineidentity)

## Related topics

[New-CsCallingLineIdentity](/powershell/module/skype/new-cscallinglineidentity)

[Set-CsCallingLineIdentity](/powershell/module/skype/set-cscallinglineidentity)

[Assign policies to your users in Teams](policy-assignment-overview.md)
