---
title: "Support for the use of SEFAUtil functionality in Skype PowerShell in Skype for Business Server 2019"
ms.reviewer: rogupta
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.date: 07/22/2019
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro`\n
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: IT_Skype16
description: "Summary: Learn how to use PowerShell to obtain SEFAUtil functionality in Skype for Business Server 2019 after installing Cumulative Update 1."
---

# Using SEFAUtil functionality via PowerShell in Skype for Business Server 2019

SEFAUtil (Secondary Extension Feature Activation) enables Skype for Business Server administrators and help desk agents to configure delegate-ringing, call-forwarding, and Group Call Pickup settings on behalf of Skype for Business Server users. SEFAUtil also allows administrators to query the call-routing settings for a particular user.

After you install the Skype for Business Server 2019 July cumulative update, the following functionality that was available only through SEFAUtil will also be available in Skype PowerShell:

- [Call forwarding settings](#call-forwarding-settings)
- [Delegation settings](#delegation-settings)
- [Team members and related settings](#team-members-and-related-settings)

## Call forwarding settings

Administrators can change call forwarding settings by using the following commands in PowerShell:

```powershell
Get-CsUserCallForwardingSettings -Identity <UserIdParameter>
```

This command returns the specified user's call forwarding settings as an object and displays the same on the screen.

```powershell
Set-CsUserCallForwardingSettings -Identity <UserIdParameter> [Param1 <Value>] [Param2 <Value>]...
```

This command modifies the specified user's call forwarding settings. This command returns the specified user's call forwarding settings as an object, and displays the same on the screen. If the command isn't successful, an appropriate error message will be shown.

```powershell
Set-CsUserCallForwardingSettings [-Identity] <UserIdParameter> -DisableForwarding  [-UnansweredToVoicemail] [-UnansweredWaitTime <TimeSpan>] [-SettingsActiveWorkHours]
```

```powershell
Set-CsUserCallForwardingSettings [-Identity] <UserIdParameter> -DisableForwarding  [-UnansweredToOther <String>] [-UnansweredWaitTime <TimeSpan>] [-SettingsActiveWorkHours]
```

This command disables the user's call forwarding settings (we show two different parameter examples here).

```powershell
Set-CsUserCallForwardingSettings [-Identity] <UserIdParameter> -EnableForwarding <String> [-Delegates <PSListModifier>] [-DelegateRingWaitTime <TimeSpan>] [-SettingsActiveWorkHours]
```

This command modifies the user's call forwarding settings.

```powershell
Set-CsUserCallForwardingSettings [-Identity] <UserIdParameter> -EnableSimulRing <String> [-UnansweredToVoicemail]  [-UnansweredWaitTime <TimeSpan>] [-Delegates <PSListModifier>] [-Team <PSListModifier>] [-TeamDelegateRingWaitTime <TimeSpan>] [-SettingsActiveWorkHours]
```

```powershell
Set-CsUserCallForwardingSettings [-Identity] <UserIdParameter> -EnableSimulRing <String> [-UnansweredToOther <String>] [-UnansweredWaitTime <TimeSpan>] [-Delegates <PSListModifier>]  [-Team <PSListModifier>]  [-TeamDelegateRingWaitTime <TimeSpan>]  [-SettingsActiveWorkHours]
```

This command modifies the simultaneous ring settings (again, with two parameter examples, one for unanswered to voicemail and the second being unanswered to other).

## Delegation settings

Administrators can change delegation settings by using the following command in PowerShell:

```powershell
Get-CsuserDelegates -Identity <UserIdParameter>
```

This command returns an object of delegates list, and displays the specified user's delegate list. If the command isn't successful, an appropriate error message will be shown.

```powershell
Set-CsUserDelegates -Identity <UserIdParameter> [-Delegates <PSListModifier>]
```

This command modifies the specified user's delegation settings, returns an object of delegates list, and displays the list of delegates. If the command isn't successful, an appropriate error message will be shown.

```powershell
Set-CsUserDelegates -Identity <UserIdParameter> [-Delegates @{add=[list]}] [-Delegates @{remove=[list]}]
```

This command adds or removes a delegate.

```powershell
Set-CsUserDelegates -Identity <UserIdParameter> [-Delegates @{replace=[list]}]
```

This command sets a delegate list to specific delegates.

## Team members and related settings

Administrators can change team members and related settings by using the following command in PowerShell:

```powershell
Get-CsUserTeamMembers -Identity <UserIdParameter>
```

This command returns an object that contains list of team members, and displays the object on screen. If the command isn't successful, an appropriate error message will be shown.

```powershell
Set-CsUserTeamMembers -Identity <UserIdParameter> [-Team <PSListModifier>]
```

This command modifies the specified user's team members list, returns an object that contains the team member list and displays the object on the screen. If the command isn't successful, an appropriate error message will be shown.

```powershell
Set-CsUserTeamMembers -Identity <UserIdParameter> [-Team @{add=[list]}] [-Team @{remove=[list]}]
```

This command adds or removes team members.

```powershell
Set-CsUserTeamMembers -Identity <UserIdParameter> [-Team @{replace=[list]}]
```

This command sets a team list to specific members.

## More information

For on-premises deployments, the cmdlets introduced in this feature can only be run by members of the following groups, per the access level specified below:

- CsAdministrator – Get and Set for all cmdlets
- CsVoiceAdministrator - Get and Set for all cmdlets
- CsHelpDesk - Get for all cmdlets

For more information on these administrator roles, see [Create Skype for Business Server Control Panel Administrators](../SfbServer/help-topics/help-depwiz/create-skype-for-business-server-control-panel-administrators.md). The administrator can access these cmdlets by directly or remotely logging on to a server computer.
For a hybrid deployment, Skype for Business administrators should be able to call Get and Set for all cmdlets. For more information about the full list of roles, see [About admin roles](/microsoft-365/admin/add-users/about-admin-roles).

> [!NOTE]
> Server auto-discovery must be enabled. No additional licensing requirements will be introduced for use of the cmdlets.
