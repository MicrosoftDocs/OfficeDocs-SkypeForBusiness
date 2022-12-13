---
title: Basic Upgrade PowerShell| Microsoft Teams| Grant Upgrade Interop Policy
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: landerl
description: Learn about a stopgap for upgrading to Microsoft Teams if the Admin Center hasn't lit up in your tenant. 
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
 - Teams-upgrade-guidance
 - seo-marvel-apr2020
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Upgrading your users from Skype for Business Online to Microsoft Teams

> [!Note]
> The commands described in this article are designed to be used as part of the [Upgrade Basic](./upgrade-start-here.md) checklist.

The technical migration aspects of your upgrade entail notifying your users that Skype for Business will be upgrading to Teams and then moving them to a **Teams only** mode. These steps can be accomplished via a Skype for Business remote Windows PowerShell session or through the Microsoft Teams admin center.

We're actively rolling out upgrade tooling in the [Microsoft Teams admin center](manage-teams-skypeforbusiness-admin-center.md), and it should be available soon on your tenant. As soon as it's available, you can find information about migrating your users in [Setting your coexistence and upgrade settings](./setting-your-coexistence-and-upgrade-settings.md).

If you're ready to upgrade today, you can use the [PowerShell](/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) commands listed in the following table.

| Upgrade Basic step # | Mode | PowerShell command |
|---|---|---|
| [5](upgrade-basic.md#step-5) | Islands + Notify the Skype for Business User<br>(Use this command if users are currently in **Islands** mode (default)) | ```Grant-CsTeamsUpgradePolicy -PolicyName IslandsWithNotify -Identity $SipAddress```<br>*(for example, $SipAddress='TestUser@contoso.com')* |
| [5](upgrade-basic.md#step-5) | Skype for Business Only + Notify the Skype for Business User <br>(Use this command if users are currently in **Skype for Business only** mode) | ```Grant-CsTeamsUpgradePolicy -PolicyName SfBOnlyWithNotify -Identity $SipAddress```  |
| [7](upgrade-basic.md#step-7) | Teams Only | ```Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity $SipAddress```  |