---
title: "Create and manage dial plans"
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: mikedav, roykuntz, jastark
ms.date: 02/22/2024
ms.topic: article
ms.assetid: 7af17c94-5f8f-4452-ae1d-01f495b4dc94
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
audience: Admin
appliesto:
- Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Calling Plans
- seo-marvel-apr2020
description: Learn how to use the Microsoft Teams admin center or Windows PowerShell to create and manage dial plans (PSTN Calling dial plans).
---

# Create and manage dial plans

After you plan the dial plans for your organization and figured out all the normalization rules that need to be created for voice routing, you're ready to create the dial plans. With an administrator account that has a valid Teams license, you can use the Microsoft Teams admin center or Windows PowerShell to create and manage dial plans.  

## Using the Microsoft Teams admin center

### Create a dial plan

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Dial plans**.
1. Select **Add**, and then enter a name and description for the dial plan.
1. Under **Normalization rules**, configure and associate one or more [normalization rules](what-are-dial-plans.md#normalization-rules) for the dial plan. Each dial plan must have at least one normalization rule associated with it. To do this, do one or more of the following:
    - To create a new normalization rule and associate it with the dial plan, select **Add**, and then define the rule.
    - To edit a normalization rule that's already associated with the dial plan, select the rule by clicking to the left of the rule name, and then select **Edit**. Make the changes you want, and then select **Save**.
    - To remove a normalization rule from the dial plan, select the rule by clicking to the left of the rule name, and then select **Delete**.
1. Arrange the normalization rules in the order that you want. Select **Move up** or **Move down** to change the position of rules in the list.

    > [!NOTE]
    > Teams traverses the list of normalization rules from the top down and uses the first rule that matches the dialed number. If you set up a dial plan so that a dialed number can match more than one normalization rule, make sure the more restrictive rules are sorted above the less restrictive ones. If you set up a dial plan that normalizes a dialed number without a "+", the calling service will attempt to normalize the number again using Tenant and regional dial plan rules. To avoid double normalization, it's recommended that all normalization rules result in numbers starting with a "+". Direct Routing customers can use [trunk translation](direct-routing-translate-numbers.md) rules to remove the "+" if required.

1. Select **Save**.
1. If you want to test the dial plan, under **Test dial plan**, enter a phone number, and then select **Test**.

### Edit a dial plan

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Dial plans**.
2. Select the dial plan by clicking to the left of the dial plan name, and then select **Edit**.
3. Make the changes that you want, and then select **Save**.

### Assign a dial plan to users

You assign a dial plan in the same way you assign policies. [!INCLUDE [assign-policy](includes/assign-policy.md)]

## Using PowerShell
  
### Start PowerShell

Open a Windows PowerShell command prompt and run the following commands:

```powershell
  # When using Teams PowerShell Module

   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
```
  
### Create and manage your dial plans

You can either use a single cmdlet or a PowerShell script to create and manage tenant dial plans.
  
#### Using single cmdlets

- To create a new dial plan, run the following script:

  ```PowerShell
  New-CsTenantDialPlan -Identity RedmondDialPlan -Description "Dial Plan for Redmond" -NormalizationRules <pslistmodifier> -SimpleName "Dial-Plan-for-Redmond"
  ```

    For other examples and parameters, see [New-CsTenantDialPlan](/powershell/module/teams/new-cstenantdialplan).

- To edit the settings of an existing dial plan, run the following script:

  ```PowerShell
  Set-CsTenantDialPlan -Identity RedmondDialPlan  -NormalizationRules <pslistmodifier> -SimpleName "Dial-Plan-for-Redmond"
  ```

    For other examples and parameters, see [Set-CsTenantDialPlan](/powershell/module/teams/set-cstenantdialplan).

- To add users to a dial plan, run the following script:

  ```PowerShell
  Grant-CsTenantDialPlan -Identity amos.marble@contoso.com -PolicyName RedmondDialPlan
  ```

    For other examples and parameters, see [Grant-CsTenantDialPlan](/powershell/module/teams/grant-cstenantdialplan).

- To view the settings on a dial plan, run the following script:

  ```PowerShell
  Get-CsTenantDialPlan -Identity RedmondDialPlan
  ```

    For other examples and parameters, see [Get-CsTenantDialPlan](/powershell/module/teams/get-cstenantdialplan).

- To delete a dial plan, run the following script:

  ```PowerShell
  Remove-CsTenantDialPlan -Identity RedmondDialPlan -force
  ```

    For other examples and parameters, see [Remove-CsTenantDialPlan](/powershell/module/teams/remove-cstenantdialplan).

- To see the settings of the effective dial plan, run the following script:

  ```PowerShell
  Get-CsEffectiveTenantDialPlan -Identity amos.marble@contoso.com
  ```

    For other examples and parameters, see [Get-CsEffectiveTenantDialPlan](/powershell/module/teams/get-cseffectivetenantdialplan).

- To test the effective settings of a dial plan, run:

  ```PowerShell
  Test-CsEffectiveTenantDialPlan -DialedNumber 14255550199 -Identity amos.marble@contoso.com
  ```

    For other examples and parameters, see [Test-CsEffectiveTenantDialPlan](/powershell/module/teams/test-cseffectivetenantdialplan).

#### Using a PowerShell script

Run this script to delete a normalization rule that's associated with a tenant dial plan without needing to delete the tenant dial plan first:

```PowerShell
$b1=New-CsVoiceNormalizationRule -Identity Global/NR4 -InMemory
Set-CsTenantDialPlan -Identity RedmondDialPlan -NormalizationRules @{add=$b1}
(Get-CsTenantDialPlan -Identity RedmondDialPlan).NormalizationRules
$b2=New-CsVoiceNormalizationRule -Identity Global/NR4 -InMemory
Set-CsTenantDialPlan -Identity RedmondDialPlan -NormalizationRules @{remove=$b2}
```

Run this script to add the following normalization rule to the existing tenant dial plan named RedmondDialPlan:

```PowerShell
$nr1=New-CsVoiceNormalizationRule -Parent Global -Description 'Organization extension dialing' -Pattern '^(\\d{3})$' -Translation '+14255551$1' -Name NR1 -IsInternalExtension $false -InMemory
Set-CsTenantDialPlan -Identity RedmondDialPlan -NormalizationRules @{add=$nr1}
```

Run this script to remove the following normalization rule from the existing tenant dial plan named RedmondDialPlan:

```PowerShell
$nr1=New-CsVoiceNormalizationRule -Identity Global/NR1 -InMemory
Set-CsTenantDialPlan -Identity RedmondDialPlan -NormalizationRules @{remove=$nr1}
```

Run the following script when you want to also examine the existing normalization rules, determine which one you want to delete, and then use its index to remove it. The array of normalization rules starts with index 0. We would like to remove the 3-digit normalization rule, so that is index 1.
  
```PowerShell
(Get-CsTenantDialPlan RedmondDialPlan).NormalizationRules
Description         : 4-digit
Pattern             : ^(\\d{4})$
Translation         : +1426666$1
Name                : NR2
IsInternalExtension : False

Description         : 3-digit
Pattern             : ^(\\d{3})$
Translation         : +14255551$1
Name                : NR12
IsInternalExtension : False

$nr1=(Get-CsTenantDialPlan RedmondDialPlan).NormalizationRules[1]
Set-CsTenantDialPlan -Identity RedmondDialPlan -NormalizationRules @{remove=$nr1}
```

Run this script to find all users who have been granted the RedmondDialPlan tenant dial plan.
  
```PowerShell
Get-CsOnlineUser | Where-Object {$_.TenantDialPlan -eq "RedmondDialPlan"}
```

Run this script to remove any assigned TenantDialPlan from all users who have a HostingProvider of sipfed.online.lync.com.

```PowerShell
Get-CsOnlineUser -Filter {HostingProvider -eq "sipfed.online.lync.com"} | Grant-CsTenantDialPlan -policyname $null
```

Run these to add the existing on-premises dial plan named OPDP1 as a tenant dial plan for your organization. You need to first save the on-premises dial plan to an .xml file, and then use it to create the new tenant dial plan.
  
- Run this script in Skype for Business Server Management Shell on-premises to save the on-premises dial plan to the .xml file.
  
    ```PowerShell
    $DPName = "OPDP1"
    $DPFileName = "dialplan.xml"
    Get-CsDialplan $DPName | Export-Clixml $DPFileName
    ```

- Run this script in Teams PowerShell Module online to create the new tenant dial plan.
  
    ```PowerShell
    $DPFileName = "dialplan.xml"
    $dp = Import-Clixml $DPFileName
    $NormRules = @()
    ForEach($nr in $dp.NormalizationRules)
    {
     $id1 = "Global/" + $nr.Name
     $nr2 = New-CsVoiceNormalizationRule -Identity $id1 -Description $nr.Description -Pattern $nr.Pattern -Translation $nr.Translation -IsInternalExtension $nr.IsInternalExtension -InMemory
     $NormRules += $nr2
    }
    New-CsTenantDialPlan -Identity $dp.SimpleName -Description $dp.Description -SimpleName $dp.SimpleName -NormalizationRules $NormRules
    ```

## Related articles

- [What are dial plans?](what-are-dial-plans.md)
- [Transferring phone numbers common questions](./phone-number-calling-plans/port-order-overview.md)
- [Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)
- [Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)
- [Emergency calling disclaimer label](https://download.microsoft.com/download/9/9/0/990e24c1-eb49-4b52-9306-dbd4c864ed91/emergency-calling-label-(en-us)-(v.1.0).zip)
- [Teams PowerShell overview](teams-powershell-overview.md)
