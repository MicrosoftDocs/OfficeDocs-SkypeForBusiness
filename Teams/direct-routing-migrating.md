---
title: "Migrate to Direct Routing"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: msteams
localization_priority: Normal
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- M365-voice
appliesto: Microsoft Teams
description: "Learn what is needed to migrate to Direct Routing from a Skype for Business Online and Teams configuration perspective."
---

# Migrate to Direct Routing

This article describes what is needed to migrate to Direct Routing from a Skype for Business Online and Microsoft Teams configuration perspective. This article covers migrating from the following: 
 
- Office 365 Phone System with Calling Plans (for Teams and Skype for Business Online) 
- Office 365 Phone System with on-premises PSTN Connectivity in Skype for Business Server (for Skype for Business Online)  
- Office 365 Phone System with on-premises PSTN Connectivity by using the Cloud Connector Edition (for Skype for Business Online)

  
In addition to these configuration steps, configuration is also required on the Session Border Controller (SBC) to route the calls to the new route. That is outside the scope of this document. For more information, see your SBC vendor documentation.  

## User provisioning end-state for various PSTN connectivity options 

The following table shows the end-state for a user provisioned for the selected PSTN connectivity options with Office 365 Phone System. Only attributes relevant for voice are shown.

|User object attributes |Phone System with Calling Plans|Phone System with on-premises PSTN connectivity via Skype for Business Server|Phone System with on-premises PSTN connectivity via Cloud Connector|Phone System with on-premises PSTN connectivity via Direct Routing|
|---|---|---|---|---|
|Client|Skype for Business or Teams |Skype for Business |Skype for Business |Teams|
|Licenses|Skype Business Online</br>Plan 2</br></br>MCOProfessional or MCOSTANDARD)</br></br></br>Phone System (MCOEV)</br></br></br>Calling Plans</br>Teams|Skype Business Online Plan 2 (MCOProfessional or MCOSTANDARD)</br></br></br>Phone System (MCOEV)|Skype Business Online Plan 2 (MCOProfessional or MCOSTANDARD)</br></br></br>Phone System (MCOEV)|Skype Business Online Plan 2 (MCOProfessional or MCOSTANDARD</br></br></br>Phone System (MCOEV)</br></br>Teams|
OnPremLineURI |N/A|The phone number  must be synced from the on-premises AD. |The phone number can be managed either in on-premises Active Directory or in Azure Active Directory.|The phone number can be managed either in on-premises Active Directory or in Azure Active Directory. However, if the organization has on-premises Skype for Business, the number must be synced from the on-premises Active Directory.|
|LineURI|PSTN Calling phone number|Set automatically from the OnPremLineURI parameter|Set automatically from the OnPremLineURI parameter|Set automatically from the OnPremLineURI parameter|
|EnterpriseVoiceEnabled|True|True|True|True|
|HostedVoiceMail |True|True|True|True|
|VoicePolicy|BusinessVoice|HybridVoice|HybridVoice|HybridVoice|
|HostedVoiceMailPolicy |BusinessVoice|BusinessVoice|BusinessVoice|BusinessVoice|
|VoiceRoutingPolicy|Has a value|Has a value|Has a value|N/A|
|OnlineVoiceRoutingPolicy|$Null|$Null|$Null|Has a value|
|TeamsUpgradePolicy<sup>1</sup>|TeamsOnly, SfBOnly or Islands|$Null|$Null|Islands or TeamsOnly|
|TeamsInterPolicy<sup>2</sup></br>CallingDefaultClient – please read the note below.|Teams or SfB |SfB|SfB|Teams|
|TeamsCallingPolicy</br>AllowPrivateCalling|True|N/A|N/A|True|
|TeamsCallingPolicy</br>AllowGroupCalling|True|N/A|N/A|True|
||||||

<sup>1</sup>Choosing the right mode of the TeamsUpgradePolicy depends on the scenario. Please read about the voice experience in different modes in [Migration and interoperability Guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md).

<sup>2</sup>As previously announced, TeamsInteropPolicy will be retired (targeted for the end of Q3), and its functionality is being consolidated into TeamsUpgradePolicy. Interop and migration will be managed using “coexistence mode” as determined by TeamsUpgradePolicy, which is now available. Selection of the user’s mode will govern both routing of incoming calls and chats and in which client the user can initiate chats and calls or schedule meetings. While TeamsInteropPolicy will be retired, it still needs to be set in parallel with TeamsUpgradePolicy during the phaseout.  

As part of this effort, Microsoft recently updated the “Microsoft Teams admin center” (also known as Modern Portal) to reflect the new management model based on coexistence modes. In Modern Portal, configuring TeamsUpgradePolicy will now automatically also set TeamsInteropPolicy to consistent value, so TeamsInteropPolicy is no longer exposed in the user interface. However, admins using PowerShell must still set both TeamsUpgradePolicy and TeamsInteropPolicy together to ensure proper routing. After the transition to TeamsUpgradePolicy is complete, it will no longer be necessary to also set TeamsInteropPolicy.

For more information, please refer to [Migration and interoperability Guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md).

## Migrating from Calling Plans

For more information about migrating from Calling Plans, see:

- [Set up Calling Plans](https://docs.microsoft.com/skypeforbusiness/what-are-calling-plans-in-office-365/set-up-calling-plans)
- [Set-CsOnlineVoice User](https://docs.microsoft.com/powershell/module/skype/Set-CsOnlineVoiceUser?view=skype-ps)
- [Get-CsOnlineLisLocation](https://docs.microsoft.com/powershell/module/skype/get-csonlinelislocation?view=skype-ps)  
 
 
It is recommended that you remove previouslycconfigured licensing plan information as follows:
 
```
$companyname = “contoso” 
$lic1 = $companyname + “:MCOPSTN1” 
$lic2 = $companyname + “:MCOPSTN2” 
Set-MsolUserLicense -UserPrincipalName <UPN> -RemoveLicenses $lic1 
Set-MsolUserLicense -UserPrincipalName <UPN> -RemoveLicenses $lic2 
```
## Migrating from Office 365 Phone System with on-premises PSTN connectivity in Skype for Business Server

For more information about migrating from Phone System with on-premises PSTN connectivity in Skype for Business Server, see the following:

- [Planning](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-phone-system-with-on-premises-pstn-connectivity)
- [Deploying](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/enable-users-for-phone-system) 

It is recommended that you remove previously configured voice routing information as follows:

```
Grant-CsVoiceRoutingPolicy -PolicyName $NULL -Identity <UPN> 
```
## Migrating from Office 365 Phone System with on-premises PSTN connectivity via Cloud Connector Edition 

For more information about migrating from Phone System with on-premises PSTN connectivity via Cloud Connector, see the following:

- [Planning](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition)  
- [Deploying](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/enable-users-for-phone-system)
- [User configuration](https://docs.microsoft.com/powershell/module/skype/set-csuserpstnsettings?view=skype-ps) 

It is recommended that you remove previously configured voice routing information as follows:
 
```
Grant-CsVoiceRoutingPolicy -PolicyName $NULL -Identity <UPN> 
Set-CsUserPstnSettings -Identity <UPN> -AllowInternationalCalls $false -HybridPSTNSite $null 
```


## RELATED LINKS

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md)

[Grant-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsupgradepolicy)

[Get-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/Get-CsTeamsUpgradePolicy)

[New-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/New-CsTeamsUpgradePolicy)

[Remove-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/Remove-CsTeamsUpgradePolicy)

[Set-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/Set-CsTeamsUpgradePolicy)

[Get-CsTeamsUpgradeConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsTeamsUpgradeConfiguration)

[Set-CsTeamsUpgradeConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsTeamsUpgradeConfiguration)

