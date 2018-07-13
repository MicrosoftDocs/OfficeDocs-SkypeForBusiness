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

The technical migration aspects of your upgrade entail notifying your users that Skype for Business will be upgrading to Teams and then moving them to a **Teams only** mode. These steps can be accomplished via a Skype for Business remote Windows PowerShell session or through the [Microsoft Teams & Skype for Business Admin Center](manage-teams-skypeforbusiness-admin-center.md). 
 
We're actively rolling out upgrade tooling in the Microsoft Teams & Skype for Business Admin Center, and it should be available soon on your tenant. As soon as it's available, you can find information about migrating your users in [Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md). 
 
If you're ready to upgrade today, you can use the [PowerShell](https://blogs.technet.microsoft.com/shawnt/2007/12/17/how-to-use-the-powershell-1-0-a-beginners-guide/) commands listed in the following table. 
 

|Upgrade Basic step # | Mode | PowerShell command |
|-------|--------|------|
| 5 |Islands + Notify the Skype for Business User<br>(Use this command if users are currently in **Islands** mode (default)) | Grant-CsTeamsUpgradePolicy -PolicyName IslandsWithNotify -Identity $SipAddress<br>Grant-CsTeamsInteropPolicy -PolicyName<br> DisallowOverrideCallingDefaultChatDefault -Identity $SipAddress |
| 5  | Skype for Business Only + Notify the Skype for Business User <br>(Use this command if users are currently in **Skype for Business only** mode) | Grant-CsTeamsUpgradePolicy -PolicyName SfBOnlyWithNotify -Identity $SipAddress <br>Grant-CsTeamsInteropPolicy -PolicyName <br>DisallowOverrideCallingSfBChatSfB -Identity $SipAddress |
| 7 | Teams Only | Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity $SipAddress <br>Grant-CsTeamsInteropPolicy -PolicyName <br> DisallowOverrideCallingTeamsChatTeams -Identity $SipAddress |


