---
title: "Migrate to Direct Routing"
ms.reviewer: 
ms.date: 06/04/2018
ms.author: crowe
author: CarolynRowe
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: msteams
ms.localizationpriority: medium
ms.custom:
  - has-azure-ad-ps-ref
  - azure-ad-ref-level-one-done
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: "Learn what is needed to migrate to Direct Routing from a Skype for Business Online and Teams configuration perspective."
---

# Migrate to Direct Routing

This article describes what is needed to migrate to Direct Routing from a Skype for Business Online and Microsoft Teams configuration perspective. This article covers migrating from the following:

- Teams Phone with Calling Plans (for Teams and Skype for Business Online)
- Teams Phone with on-premises PSTN Connectivity in Skype for Business Server (for Skype for Business Online)  
- Teams Phone with on-premises PSTN Connectivity by using the Cloud Connector Edition (for Skype for Business Online)

In addition to these configuration steps, configuration is also required on the Session Border Controller (SBC) to route the calls to the new route. That is outside the scope of this document. For more information, see your SBC vendor documentation.  

## User provisioning end-state for various PSTN connectivity options

The following table shows the end-state for a user provisioned for the selected PSTN connectivity options with Teams Phone. Only attributes relevant for voice are shown.

|User object attributes |Teams Phone with Calling Plans|Teams Phone with on-premises PSTN connectivity via Skype for Business Server|Teams Phone with on-premises PSTN connectivity via Cloud Connector|Teams Phone with on-premises PSTN connectivity via Direct Routing|
|---|---|---|---|---|
|Client|Skype for Business or Teams |Skype for Business |Skype for Business |Teams|
|Licenses|Skype Business Online</br>Plan 2</br></br>(MCOProfessional or MCOSTANDARD)</br></br></br>Teams Phone (MCOEV)</br></br></br>Calling Plans</br>Teams|Skype Business Online Plan 2 (MCOProfessional or MCOSTANDARD)</br></br></br>Teams Phone (MCOEV)|Skype Business Online Plan 2 (MCOProfessional or MCOSTANDARD)</br></br></br>Teams Phone (MCOEV)|Skype Business Online Plan 2 (MCOProfessional or MCOSTANDARD)</br></br></br>Teams Phone (MCOEV)</br></br>Teams|
OnPremLineURI |N/A|The phone number  must be synced from the on-premises AD. |The phone number can be managed either in on-premises Active Directory or in Microsoft Entra ID.|The phone number can be managed either in on-premises Active Directory or in Microsoft Entra ID. However, if the organization has on-premises Skype for Business, the number must be synced from the on-premises Active Directory.|
|LineURI|PSTN Calling phone number|Set automatically from the OnPremLineURI parameter|Set automatically from the OnPremLineURI parameter|Set automatically from the OnPremLineURI parameter|
|EnterpriseVoiceEnabled|True|True|True|True|
|HostedVoiceMail |True|True|True|True|
|VoicePolicy|BusinessVoice|HybridVoice|HybridVoice|HybridVoice|
|HostedVoiceMailPolicy |BusinessVoice|BusinessVoice|BusinessVoice|BusinessVoice|
|VoiceRoutingPolicy|Has a value|Has a value|Has a value|N/A|
|OnlineVoiceRoutingPolicy|$Null|$Null|$Null|Has a value|
|TeamsUpgradePolicy<sup>1</sup>|TeamsOnly, SfBOnly|$Null|$Null|TeamsOnly|
|TeamsCallingPolicy</br>AllowPrivateCalling|True|N/A|N/A|True|
|TeamsCallingPolicy</br>AllowGroupCalling|True|N/A|N/A|True|
||||||

<sup>1</sup> Choosing the right mode of the TeamsUpgradePolicy depends on the scenario. Please read about the voice experience in different modes in [Migration and interoperability Guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md).

As part of this effort, Microsoft recently updated the “Microsoft Teams admin center” (also known as Modern Portal) to reflect the new management model based on coexistence modes. In Modern Portal, configuring TeamsUpgradePolicy will now automatically also set TeamsInteropPolicy to consistent value, so TeamsInteropPolicy is no longer exposed in the user interface. However, admins using PowerShell must still set both TeamsUpgradePolicy and TeamsInteropPolicy together to ensure proper routing. After the transition to TeamsUpgradePolicy is complete, it will no longer be necessary to also set TeamsInteropPolicy.

For more information, please refer to [Migration and interoperability Guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md).

## Migrating from Calling Plans

For more information about migrating from Calling Plans, see:

- [Set up Calling Plans](/skypeforbusiness/what-are-calling-plans-in-office-365/set-up-calling-plans)
- [Set-CsOnlineVoice User](/powershell/module/teams/Set-CsOnlineVoiceUser)
- [Get-CsOnlineLisLocation](/powershell/module/teams/get-csonlinelislocation)  

It's recommended that you remove previously configured licensing plan information as follows:

```powershell
$companyname = “contoso” 
$lic1 = $companyname + “:MCOPSTN1” 
$lic2 = $companyname + “:MCOPSTN2” 
Set-MgUserLicense -UserId '11111111-0000-aaaa-bbbb-222222222222' -RemoveLicenses @($lic1) 
Set-MgUserLicense -UserId '11111111-0000-aaaa-bbbb-222222222222' -RemoveLicenses @($lic2) 
```

## Migrating from Office 365 Teams Phone with on-premises PSTN connectivity in Skype for Business Server

For more information about migrating from Teams Phone with on-premises PSTN connectivity in Skype for Business Server, see the following:

- [Planning](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-phone-system-with-on-premises-pstn-connectivity)
- [Deploying](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/enable-users-for-phone-system)

It's recommended that you remove previously configured voice routing information as follows:

```PowerShell
Grant-CsVoiceRoutingPolicy -PolicyName $NULL -Identity <UPN> 
```

> [!NOTE]
> If a global CsVoiceRoutingPolicy is configured, it's recommended that you remove any PSTN usages associated with this global policy.

## Migrating from Office 365 Teams Phone with on-premises PSTN connectivity via Cloud Connector Edition

> [!IMPORTANT]
> Cloud Connector Edition will retire July 31, 2021 along with Skype for Business Online. Once your organization has upgraded to Teams, learn how to connect your on-premises telephony network to Teams using [Direct Routing](direct-routing-landing-page.md).

For more information about migrating from Teams Phone with on-premises PSTN connectivity via Cloud Connector, see the following:

- [Planning](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition)  
- [Deploying](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/enable-users-for-phone-system)
- [User configuration](/powershell/module/skype/set-csuserpstnsettings)

It's recommended that you remove previously configured voice routing information as follows:

```PowerShell
Grant-CsVoiceRoutingPolicy -PolicyName $NULL -Identity <UPN> 
Set-CsUserPstnSettings -Identity <UPN> -AllowInternationalCalls $false -HybridPSTNSite $null 
```

## Related links

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md)

[Grant-CsTeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy)

[Get-CsTeamsUpgradePolicy](/powershell/module/skype/Get-CsTeamsUpgradePolicy)

[New-CsTeamsUpgradePolicy](/powershell/module/skype/New-CsTeamsUpgradePolicy)

[Remove-CsTeamsUpgradePolicy](/powershell/module/skype/Remove-CsTeamsUpgradePolicy)

[Set-CsTeamsUpgradePolicy](/powershell/module/skype/Set-CsTeamsUpgradePolicy)

[Get-CsTeamsUpgradeConfiguration](/powershell/module/skype/Get-CsTeamsUpgradeConfiguration)

[Set-CsTeamsUpgradeConfiguration](/powershell/module/skype/Set-CsTeamsUpgradeConfiguration)
