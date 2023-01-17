---
title: "Assign a Voice Routing Policy"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 2/15/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
- Ent_O365_Hybrid
- IT_Skype16
- IT_Skype4B_Hybrid
- Strat_SB_Hybrid
ms.custom: 
ms.assetid: c7f78f23-b74f-402f-bedb-4cc308718f5b
description: "Summary: Read this topic to learn how to assign a voice policy for users using Phone System with on-premises PSTN connectivity."
---

# Assign a Voice Routing Policy
 
> [!Important]
> Skype for Business Online was retired on July 31, 2021 and PSTN connectivity between your on-premises environment, whether through Skype for Business Server or Cloud Connector Edition and Skype for Business Online, is no longer supported.  Learn how to connect your on-premises telephony network to Teams using [Direct Routing](/MicrosoftTeams/direct-routing-landing-page).

**Summary:** Read this topic to learn how to assign a voice policy for users using Phone System with on-premises PSTN connectivity. 
  
Once a user is on Skype for Business Online and using Phone System with on-premises PSTN connectivity, two voice policies will apply to them. One is an on-premises voice routing policy that you will assign on premises. This policy can be global or user-specific and defines what PSTN usage records are associated with the user. This topic explains how to assign this policy.
  
The other voice policy defines what calling features are available to the user; this voice policy is defined by Microsoft and is identical for all Phone System with on-premises PSTN connectivity users. It is automatically assigned to Phone System users.
  
|&nbsp;|On-premises user|Phone System with on-premises PSTN connectivity user|
|:-----|:-----|:-----|
|Calling features defined in   |Voice policy   |Pre-defined voice policy, assigned automatically when the user is licensed for Phone System.   |
|PSTN usage records associated with   |Voice policy   |Voice routing policy, assigned while the user is still homed on-premises.   |
   
You perform the following steps using your on-premises deployment, while the user is still homed in the on-premises deployment.
  
## Using a global voice routing policy

Before using a global voice routing policy for your Phone System with on-premises PSTN connectivity users, you must add PSTN usage records to the policy.
  
### To assign PSTN usage records to the global voice routing policy

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Add the PSTN usage records to the policy:
    
   ```powershell
   Set-CSVoiceRoutingPolicy -Identity Global -PSTNUsages <PSTNUsagesId> 
   ```

    For example:
    
   ```powershell
   Set-CSVoiceRoutingPolicy -Identity Global -PSTNUsages "Local", "Long Distance" 
   ```

## Creating a new voice routing policy

### To create a new voice routing policy

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Create a new voice routing policy:
    
   ```powershell
   New-CSVoiceRoutingPolicy -Identity <String> -Name <String> -PSTNUsages <PSTNUsagesId>
   ```

    For example:
    
   ```powershell
   New-CSVoiceRoutingPolicy -Identity HybridVoice -Name Hybrid -PSTNUsages "Local", "Long Distance"
   ```

This example creates a new voice routing policy called HybridVoice, which has two PSTN usages associated with it.
  
## Assigning a voice routing policy

No matter whether you use the global voice routing policy, or user-specific ones, use the following steps to assign the policy to a user.
  
### To assign the voice routing policy

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Assign an existing voice policy to a user:
    
   ```powershell
   Grant-CsVoiceRoutingPolicy -Identity <UserIdParameter> -PolicyName <String>
   ```

    For example:
    
   ```powershell
   Grant-CsVoiceRoutingPolicy -Identity "Bob Kelly" -PolicyName HybridVoice
   ```

In this example, the user with the display name Bob Kelly is assigned to the previously created voice policy with the name HybridVoice.
  
For more details about voice routing policies, see [Create or modify a voice policy and configure PSTN usage records in Skype for Business 2015](../../deploy/deploy-enterprise-voice/voice-policy-and-pstn-usage-records.md), [New-CsVoiceRoutingPolicy](/powershell/module/skype/new-csvoiceroutingpolicy), and [Grant-CsVoicePolicy](/powershell/module/skype/grant-csvoicepolicy).
