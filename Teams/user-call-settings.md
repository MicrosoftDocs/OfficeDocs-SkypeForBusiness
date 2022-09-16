---
title: Configure call settings for users
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: jenstr
ms.topic: article
ms.assetid: 67ccda94-1210-43fb-a25b-7b9785f8a061
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview
  - Phone System
  - seo-marvel-apr2020
description: Learn how to configure user settings for call forwarding and delegation.
---
# Configure call settings for your users

This article describes how you, the administrator, can change call forwarding and delegation settings for your users. You might want to change these settings, for example, if:

- A user is out on sick leave, and you need to ensure that incoming calls to the user are forwarded to a colleague.
- You need to inspect the call forward settings for all users in a department and potentially correct them as appropriate.
- A new assistant has been employed and you need to add the assistant as a delegate for a group of employees.

You can use the Teams admin center or Teams PowerShell cmdlets to view and change call settings for users.

To set call settings for a user, the user must have an assigned Microsoft Phone System license.

## Use the Teams admin center

You can use the Teams admin center to configure call forward and unanswered settings, group call pickup, and call delegation for your users.

To configure immediate call forward settings:

1. In the Teams admin center, go to **Users** > **Manage users** and select a user.

2. On the user details page, go to the **Voice** tab.

3. Under **Call answering rules**, select **Be immediately forwarded**, and select the appropriate call forward type and destination.

To configure simultaneous ringing, on the same page select **Ring the user's devices**. In the **Also allow** drop-down, select the appropriate simultaneous ringing setting.

To configure unanswered settings, on the same page select the appropriate setting in the **If unanswered** drop-down. In the **Ring for this many seconds before redirecting** drop-down, specify the number of seconds to wait.

The configuration of call delegation and group call pickup are integrated into the call forward and unanswered settings by selecting the appropriate type. For example, to configure that calls should also ring the user's delegates, on the same page select **Call delegation** under **Also allow**. Then add the appropriate delegates by selecting **Add people** and clicking **Save**.

This video shows the steps to view and edit the voice settings for a user.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE546F7?autoplay=false]

## Use PowerShell

You can use PowerShell to configure call forward and delegation settings for your users.  You'll use the following cmdlets, which are available in Teams PowerShell module version 4.0 or later:

- [Get-CsUserCallingSettings](/powershell/module/teams/get-csusercallingsettings) - shows call forwarding settings, delegates, and delegator information for a user.
- [Set-CsUserCallingSettings](/powershell/module/teams/set-csusercallingsettings) - sets call forwarding settings for a user.
- [New-CsUserCallingDelegate](/powershell/module/teams/new-csusercallingdelegate) - adds a new delegate with permissions for a user.
- [Set-CsUserCallingDelegate](/powershell/module/teams/set-csusercallingdelegate) - changes permissions for an existing delegate.
- [Remove-CsUserCallingDelegate](/powershell/module/teams/remove-csusercallingdelegate) - removes a delegate from a user.

### Display call forward and delegation settings for a user

To display the current call forward and delegation settings for a user, use the  Get-CsUserCallingSettings cmdlet, as shown in the following example:

```PowerShell
Get-CsUserCallingSettings -Identity user1@contoso.com
SipUri                    : sip:opr1@contoso.com
IsForwardingEnabled       : True
ForwardingType            : Simultaneous
ForwardingTarget          :
ForwardingTargetType      : MyDelegates
IsUnansweredEnabled       : True
UnansweredTarget          :
UnansweredTargetType      : Voicemail
UnansweredDelay           : 00:00:20
Delegates                 : Id:sip:user2@contoso.com
Delegators                :
CallGroupOrder            : InOrder
CallGroupTargets          : {}
GroupMembershipDetails    :
GroupNotificationOverride : Ring

(Get-CsUserCallingSettings -Identity user1@contoso.com).Delegates

Id             : sip:user2@contoso.com
MakeCalls      : True
ManageSettings : True
ReceiveCalls   : True
```

The output shows that user1 has simultaneous ringing to delegates configured. Unanswered calls are sent to voicemail after 20 seconds. User2 is defined as the delegate with all delegate permissions.

### Set call forward settings for a user

To forward all calls for user1 to user2, use the Set-CsUserCallingSettings cmdlet, as shown in the following example:

```PowerShell
Set-CsUserCallingSettings -Identity user1@contoso.com -IsForwardingEnabled $true -ForwardingType Immediate -ForwardingTargetType SingleTarget -ForwardingTarget user2@contoso.com
```

To simultaneously ring all delegates for user3, use the Set-CsUserCallingSettings cmdlet, as shown in the following example:

```PowerShell
Set-CsUserCallingSettings -Identity user3@contoso.com -IsForwardingEnabled $true -ForwardingType Simultaneous -ForwardingTargetType MyDelegates
```

The following example uses the Set-CsUserCallingSettings cmdlet to configure a call group for user4 with user5 and user6 as members. All calls to members of the group are forwarded in the order they are defined:

```PowerShell
$cgm = @("user5@contoso.com","user6@contoso.com")

Set-CsUserCallingSettings -Identity user4@contoso.com -CallGroupOrder InOrder -CallGroupTargets $cgm

Set-CsUserCallingSettings -Identity user4@contoso.com -IsForwardingEnabled $true -ForwardingType Immediate -ForwardingTargetType Group
```

For more examples, see [Set-CsUserCallingSettings](/powershell/module/teams/get-csusercallingsettings).

### Add a calling delegate for a user

To add user2 as a delegate for user1 with all permissions allowed, use the New-CsUserCallingDelegate cmdlet, as shown in the following example:

```PowerShell
New-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com -MakeCalls $true -ReceiveCalls $true -ManageSettings $true
```

### Change calling delegate permissions

To change delegate permissions--for example to not allow user2 to make calls for user1--use the Set-CsUserCallingDelegate cmdlet as shown in the following example:

```PowerShell
Set-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com -MakeCalls $false
```

### Remove a calling delegate for a user

To remove user2 as a delegate for user1, use the Remove-CsUserCallingDelegate cmdlet, as shown in the following example:

```PowerShell
Remove-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com
```

## Related topics

- [Get-CsUserCallingSettings](/powershell/module/teams/get-csusercallingsettings)
- [Set-CsUserCallingSettings](/powershell/module/teams/set-csusercallingsettings)
- [New-CsUserCallingDelegate](/powershell/module/teams/new-csusercallingdelegate)
- [Set-CsUserCallingDelegate](/powershell/module/teams/set-csusercallingdelegate)
- [Remove-CsUserCallingDelegate](/powershell/module/teams/remove-csusercallingdelegate)
