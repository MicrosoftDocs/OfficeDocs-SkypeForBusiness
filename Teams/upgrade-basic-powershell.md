---
title: Upgrade Basic PowerShell commands - Microsoft Teams
author: dearbeen
ms.author: dearbeen
manager: serdars
ms.date: 06/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: dearbeen
description: Stopgap for upgrading to Teams if the Admin Center hasn't lit up in your tenant 
localization_priority: Priority
ms.custom: Teams-upgrade-guidance
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

# Upgrading your users from Skype for Business Online to Microsoft Teams

The technical migration aspects of your upgrade entail notifying your users that Skype for Business will be upgrading to Teams and then moving them to a **Teams only** mode. These steps can be accomplished via a Skype for Business remote Windows PowerShell session or through the Microsoft Teams & Skype for Business Admin Center. 
 
We're actively rolling out upgrade tooling in the [Microsoft Teams & Skype for Business Admin Center](manage-teams-skypeforbusiness-admin-center.md), and it should be available soon on your tenant. As soon as it's available, you can find information about migrating your users in [Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md). 
 
If you're ready to upgrade today, you can use the [PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) commands listed in the following table. 
 

|Upgrade Basic step # | Mode | PowerShell command |
|-------|--------|------|
| 5 |Islands + Notify the Skype for Business User<br>(Use this command if users are currently in **Islands** mode (default)) | <ul><li>Grant-CsTeamsUpgradePolicy -PolicyName IslandsWithNotify -Identity $SipAddress<br>_(for example, $SipAddress='TestUser@contoso.com')_</li><li>Grant-CsTeamsInteropPolicy -PolicyName DisallowOverrideCallingDefaultChatDefault -Identity $SipAddress</li></ul> |
| 5  | Skype for Business Only + Notify the Skype for Business User <br>(Use this command if users are currently in **Skype for Business only** mode) | <ul><li>Grant-CsTeamsUpgradePolicy -PolicyName SfBOnlyWithNotify -Identity $SipAddress </li><li>Grant-CsTeamsInteropPolicy -PolicyName DisallowOverrideCallingSfBChatSfB -Identity $SipAddress</li></ul> |
| 7 | Teams Only | <ul><li>Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity $SipAddress </li><li>Grant-CsTeamsInteropPolicy -PolicyName DisallowOverrideCallingTeamsChatTeams -Identity $SipAddress</li></ul> |


