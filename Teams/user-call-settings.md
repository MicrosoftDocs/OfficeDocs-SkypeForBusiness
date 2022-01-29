---
title: "Configure call settings for users"
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
  - m365initiative-voice
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview"
  - Phone System
    - seo-marvel-apr2020
description: Learn how to configure user settings for call forwarding and delegation.
---
# Configure call settings for your users

This article describes how you, the administrator, can change call forwarding and delegation settings for your users. You might want to change these settings, for example, if:

- A user is out on sick leave, and you need to ensure that incoming calls to the user are forwarded to a colleague.

- You need to inspect the call forward settings for all users in a department and potentially correct them as appropriate.

- A new assistant has been employed and you need to add the assistant as a delegate for a group of employees.

You can use Teams admin center or Teams PowerShell cmdlets to view and change call settings for users.

To set call settings for a user, the user must have an assigned Microsoft Phone System license.

## Use the Teams admin center

You can use the Teams admin center to configure group call pickup and call delegation for your users. 

> [!NOTE]
> The option for configuring call forward settings is not currently available in the Teams admin center.

To configure group call pickup:

1. In the Teams admin center, go to **Users** > **Voice**.

2. Under **Group call pickup** and select **Add people**. 

3. Specify settings for **Call delay and order**.

To configure delegation, on the same page:

1. Go to **Call delegation** and select **Add people**.

## Use PowerShell

You can user PowerShell to configure call forward and delegation settings for your users.  You'll use the following cmdlets, which are available in Teams PowerShell module version 3.0.1-preview:

- [Get-CsUserCallingSettings](/powershell/module/teams/get-csusercallingsettings?view=teams-ps) shows call forwarding settings, delegates, and delegator information for a user.

- [Set-CsUserCallingSettings](/powershell/module/teams/set-csusercallingsettings?view=teams-ps) sets call forwarding settings for a user.

- [New-CsUserCallingDelegate](/powershell/module/teams/new-csusercallingdelegate?view=teams-ps) adds a new delegate with permissions for a user.

-	[Set-CsUserCallingDelegate](/powershell/module/teams/set-csusercallingdelegate?view=teams-ps) changes permissions for an existing delegate.

-	[Remove-CsUserCallingDelegate](/powershell/module/teams/remove-csusercallingdelegate?view=teams-ps) removes a delegate from a user.


### Display call forward and delegation settings for a user

To display the current call forward and delegation settings for a user, use the  Get-CsUserCallingSettings cmdlet as shown in the following example:

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
Delegates                 : Id:user2@contoso.com
Delegators                : 
CallGroupOrder            : InOrder
CallGroupTargets          : {}
GroupMembershipDetails    :
GroupNotificationOverride : Ring

(Get-CsUserCallingSettings -Identity user1@contoso.com).Delegates

Id             : user2@contoso.com
MakeCalls      : True
ManageSettings : True
ReceiveCalls   : True
```

The output shows that user1 has simultaneous ringing to delegates configured. Unanswered calls are sent to voicemail after 20 seconds. User2 is defined as the delegate with all delegate permissions.


### Set call forward settings for a user

To forward all calls for user1 to user2, use the Set-CsUserCallingSettings cmdlet as shown in the following example: 

```PowerShell
Set-CsUserCallingSettings -Identity user1@contoso.com -IsForwardingEnabled $true -ForwardingType Immediate -ForwardingTargetType SingleTarget -ForwardingTarget user2@contoso.com
```

To simultaneously ring all delegates for user3, use the Set-CsUserCallingSettings cmdlet as shown in the following example: 

```PowerShell
Set-CsUserCallingSettings -Identity user3@contoso.com -IsForwardingEnabled $true -ForwardingType Simultaneous -ForwardingTargetType MyDelegates
```

The following example uses the Set-CsUserCallingSettings cmdlet to configure a call group for user4 with user5 and user6 as members. All calls to members of the group are forwarded in the order they are defined: 

```PowerShell
$cgm = @("user5@contoso.com","user6@contoso.com")

Set-CsUserCallingSettings -Identity user4@contoso.com -CallGroupOrder InOrder -CallGroupTargets $cgm

Set-CsUserCallingSettings -Identity user4@contoso.com -IsForwardingEnabled $true -ForwardingType Immediate -ForwardingTargetType Group
```

For more examples, see [Set-CsUserCallingSettings](powershell/module/teams/get-csusercallingsettings?view=teams-ps).
Call queues provide:

### Add a calling delegate for a user

To add user2 as a delegate for user1 with all permissions allowed, use the New-CsUserCallingDelegate cmdlet as shown in the following example: 

```PowerShell
New-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com -MakeCalls $true -ReceiveCalls $true -ManageSettings $true
```

### Change calling delegate permissions

To change delegate permissions--for example to not allow user2 to make calls for user1--use the Set-CsUserCallingDelegate cmdlet as shown in the following example: 

```PowerShell
Set-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com -MakeCalls $false
```

### Remove a calling delegate for a user

To remove user2 as a delegate for user1, use the Remove-CsUserCallingDelegate cmdlet as shown in the following example: 

```PowerShell
Remove-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com
```


## Related topics

