---
title: "Support for the use of SEFAUtil functionality in PowerShell in Skype for Business Server 2019"
ms.reviewer: rogupta
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.date: 07/22/2019
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
description: "Summary: Learn how to use PowerShell to obtain SEFAUtil functionality in Skype for Business Server 2019 after installing Cumulative Update 1."
---

# Using SEFAUtil functionality via PowerShell in Skype for Business Server 2019

SEFAUtil (Secondary Extension Feature Activation) enables Skype for Business Server administrators and helpdesk agents to configure delegate-ringing, call-forwarding, and Group Call Pickup settings on behalf of a Skype for Business Server user. This tool also allows administrators to query the call-routing settings that are published for a particular user. After you install this update, the following functionality that can currently be managed only through SEFAUtil will be also manageable through PowerShell:

- [Call forwarding settings](#call-forwarding-settings)
- [Delegation settings](#delegation-settings)
- [Team members and related settings](#team-members-and-related-settings)

## Call forwarding settings

Administrators can change call forwarding settings by using the following cmdlet in PowerShell:

- `Get-CsUserForwardingSettings -Identity <String>`

This cmdlet returns the specified user’s call forwarding settings as an object and displays the same on the screen.

- `Set-CsUserForwardingSettings -Identity <String> [Param1 <Value>] [Param2 <Value>]…`

This cmdlet modifies the specified user’s call forwarding settings. This cmdlet returns the specified user’s call forwarding settings as an object, and displays the same on the screen, in case of success. In case of failure, an appropriate error message will be shown.

- `Set-CsUserForwardingSettings -DisableForwarding -Identity <String> [-UnansweredToVoicemail] [-UnansweredToOther <Destination>] [-UnansweredWaitTime <Value>] [-SettingsActiveWorkHours]`

This cmdlet disables the user’s call forwarding settings.

- `Set-CsUserForwardingSettings -Identity <String> -EnableForwarding <ForwardDestination> [-Delegates @{add=[list]}] [-Delegates @{remove=[list]}] [-Delegates @{replace=[list]}] [-DelegateRingWaitTime] [-SettingsActiveWorkHours]`

This cmdlet modifies the user’s call forwarding settings.

- `Set-CsUserForwardingSettings -Identity <String> -EnableSimulRing <SimulRingDestination> [-UnansweredToVoicemail] [-UnansweredToOther <Destination>] [-UnansweredWaitTime <Value>] [-Delegates @{add=[list]}] [-Delegates @{remove=[list]}] [-Delegates @{replace=[list]}] [-Team @{add=[list]}] [-Team @{remove=[list]}] [-Team @{replace=[list]}] [-TeamDelegateRingWaitTime <Value>] [-SettingsActiveWorkHours]`

This cmdlet modifies the SimulRing settings.

## Delegation settings

Administrators can change delegation settings by using the following cmdlet in PowerShell:

- `Get-CsuserDelegates -Identity <String>`

This cmdlet returns an object of delegates list, and displays the specified user’s delegate list, in case of success. In case of failure, an appropriate error message will be shown.

- `Set-CsUserDelegates -Identity <String> [-Delegates @{add=[list]}] [-Delegates @{remove=[list]}] [-Delegates @{replace=[list]}]`

This cmdlet modifies the specified user’s delegation settings, returns an object of delegates list and displays the list of delegates, in case of success. In case of failure, an appropriate error message will be shown. 

- `Set-CsUserDelegates -Identity <String> [-Delegates @{add=[list]}] [-Delegates @{remove=[list]}]`

This cmdlet adds or removes a delegate.

- `Set-CsUserDelegates -Identity <String> [-Delegates @{replace=[list]}]`

This cmdlet sets a delegate list to specific delegates.

## Team members and related settings

Administrators can change team members and related settings by using the following cmdlet in PowerShell:

- `Get-CsUserTeamMembers -Identity <String>`

This cmdlet returns an object that contains list of team members, and displays the object on screen, in case of success. In case of failure, an appropriate error message will be shown.

- `Set-CsUserTeamMembers -Identity <String> [-Team @{add=[list]};@{remove=[list]};@{replace=[list]}]`

This cmdlet modifies the specified user’s team members list, returns an object that contains the team member list and displays the object on the screen, in case of success. In case of failure, an appropriate error message will be shown.

- `Set-CsUserTeamMembers -Identity <String> [-Team @{add=[list]}] [-Team @{remove=[list]}]`

This cmdlet adds or removes team members.

- `Set-CsUserTeamMembers -Identity <String> [-Team @{replace=[list]}]`

This cmdlet sets a team list to specific members.

## More information

For on-premises deployments, the cmdlets introduced in this feature can only be run by members of the following groups, per the access level specified below:

- CsAdministrator – Get and Set for all cmdlets
- CsVoiceAdministrator - Get and Set for all cmdlets
- CsHelpDesk - Get for all cmdlets

For more information on these administrator roles, see [Create Skype for Business Server Control Panel Administrators](../SfbServer/help-topics/help-depwiz/create-skype-for-business-server-control-panel-administrators.md). The administrator can access these cmdlets by directly or remotely logging on to a server computer.
For a hybrid deployment, Skype for Business administrators should be able to call Get and Set for all cmdlets. For more information about the full list of roles, see [About Office 365 admin roles](https://docs.microsoft.com/en-us/office365/admin/add-users/about-admin-roles)

> [!NOTE]
> Server auto-discovery must be enabled. No additional licensing requirements will be introduced for use of the cmdlets.
