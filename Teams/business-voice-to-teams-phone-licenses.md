---
title: Move from Business Voice to Teams Phone licenses
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to change your Business Voice licenses to Teams Phone licenses.
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-voice
---

# Move from Business Voice to Teams Phone licenses

By the end of June 2022, Business Voice will be retired, so we [recommend businesses to switch to Microsoft Teams Phone with Calling Plan bundle licenses](https://techcommunity.microsoft.com/t5/small-and-medium-business-blog/teams-phone-with-calling-plan-available-in-33-markets-on-january/ba-p/2967643).

Business Voice bundled the following three Teams add-on licenses:

- **Microsoft Teams Phone** for a cloud-based Phone System in Microsoft Teams.
- **Audio Conferencing** for dial-in and dial-out conferencing for meetings.
- **Microsoft Calling Plans** for domestic calls to Public Switched Telephone Network (PSTN) connectivity.

Existing Business Voice customers won't be automatically transitioned to the new licensing model.

This article is for IT admins who need to change their Business Voice licenses to Microsoft Teams Phone and Audio Conferencing licenses while maintaining the same capabilities.

> [!WARNING]
> Closely follow this article's instructions. If the instructions tell you to NOT select the **Save** button, don't select the **Save** button.
>
> Saving prematurely may result in losing phone number assignments, dial plans, auto attendants, and call queues.

## Acquire new licenses

Before replacing Business Voice licenses, you first need to purchase replacement licenses for your users.

You'll need licenses to provide these features:

- Audio conferencing
- Cloud-based Phone System
- PSTN connectivity

Use the following table to determine which licenses to purchase based on your needs:

| Old license plan | Recommended license plan | Description |
| ---------------- | ------------------------ | ----------- |
| Business Voice with Calling Plan | Teams Phone with Calling Plan and Microsoft Teams Audio Conferencing with dial-out to USA/CAN | Provides cloud-based Phone System capabilities, a Domestic Calling Plan with Microsoft as your PSTN provider, and dial-in and dial-out capabilities to meeting attendees organized by a licensed user. |
| Business Voice without Calling Plan | Teams Phone Standard and Microsoft Teams Audio Conferencing with dial-out to USA/CAN | Provides cloud-based Phone System capabilities that can be combined with [a third-party calling plan with a PSTN provider using Operator Connect or Direct Routing](pstn-connectivity.md) and dial-in and dial-out capabilities to meeting attendees organized by a licensed user. |

## How to update licenses

You have four ways to update your licenses:

- Single user license update via Microsoft 365 admin center
- Bulk user license update via Microsoft 365 admin center
- Bulk user license update using a PowerShell script
- Bulk user license update using Azure group-based licensing

# [Option 1: Single user in admin center](#tab/single-user)

### Option 1: Single user license update via Microsoft 365 admin center

To update a single user, you can use the Microsoft 365 admin center.

1. Go to [admin.microsoft.com](https://admin.microsoft.com/) and sign in with the tenant admin credentials.
1. Navigate to **Users** > **Active Users** and select the desired user.
1. Select **Manage product licenses** on the list toolbar.
1. On the **Licenses and apps** screen, deselect the Business Voice license.
    > [!IMPORTANT]
    > DON'T save changes yet. If you save changes without adding the new licenses, the user account will be deprovisioned and the phone number unassigned.
1. After deselecting Business Voice, check the new Teams Phone and Audio Conferencing licenses.
1. Now you can safely save your changes by selecting **Save change**.

The user's licenses will be updated and shouldn't impact service availability.

# [Option 2: Bulk users in admin center](#tab/bulk-users-admin-center)

### Option 2: Bulk user license update via Microsoft 365 admin center

To update multiple users' licenses in bulk, you can use the Microsoft 365 admin center. The selected users will have the same license plan assignment.

1. Go to [admin.microsoft.com](https://admin.microsoft.com/) and sign in with the tenant admin credentials.
1. Navigate to **Users** > **Active Users** and select all the desired users.  
1. Select **Manage product licenses** on the list toolbar.
1. At the **What would you like to do with the licenses for these users?** prompt, select the **Replace: Unassign existing licenses and assign new ones** option.
    > [!IMPORTANT]
    > The **Replace** option will remove all existing licenses for the selected users.  As a result, you’ll have to select the desired licensing state for users, including any other licenses in use, like Microsoft 365 Business Premium.
    >
    > Also, if the selected users have different base license configurations, they will be overwritten with your selected licenses, which may affect other areas of Microsoft 365.
    >
    > For tenants with a mixed license setup, we recommend using the [bulk update option with a PowerShell script](#option-3-bulk-user-license-update-using-a-powershell-script).
1. On the **Licenses and apps** screen, deselect the Business Voice license.
    > [!IMPORTANT]
    > DON'T save changes yet. If you save changes without adding the new licenses, the accounts for the selected users will be deprovisioned and the phone number unassigned.
1. After deselecting Business Voice, check the new Teams Phone and Audio Conferencing licenses.
1. Now you can safely save your changes by selecting **Save change**.
  The users' licenses will be updated and shouldn't impact service availability.

# [Option 3: Bulk users via PowerShell](#tab/powershell)

### Option 3: Bulk user license update using a PowerShell script

Replacing the Business Voice license plan using a PowerShell script is an efficient solution for most scenarios.  

To use this method, you'll follow these general steps:

1. Get the tenant-specific license plan identifiers of your current Business Voice licenses.
1. Get the tenant-specific identifiers of your new Teams Phone and Audio Conferencing license plans.
1. Validate if the new license plans have the same service plans as the current Business Voice license.
1. Find tenant users who are licensed for Business Voice (or modify the script to include a filter to select a subset of users, if desired).
1. Update users' license configuration with Teams Phone and Audio Conferencing plans.

> [!IMPORTANT]
> The script provided is a code sample. The script shouldn't be copied as-is and run in a production tenant without testing, validation, and customization for your specific environment.

### How to bulk update licenses using PowerShell

1. Install and import the AzureAD PowerShell module.

    ```powershell
    Install-Module AzureAD
    Import-Module AzureAD
    ```

1. Connect to your Microsoft 365 tenant and provide the tenant admin credentials.

    ```powershell
    Connect-AzureAD
    ```

1. Use the following commandlet to list all license packages in the tenant.

    ```powershell
    Get-AzureADSubscribedSku
    ```

1. Use the following table to identify the Business Voice add-on license plan that will be replaced.

    | SKU Code | License type |
    | -------- | ------------ |
    | BUSINESS_VOICE_MED | Business Voice with Calling Plan - Canada |
    | BUSINESS_VOICE | Business Voice with Calling Plan - UK |
    | BUSINESS_VOICE_MED2_TELCO | Business Voice with Calling Plan - US |
    | BUSINESS_VOICE_DIRECTROUTING | Business Voice without Calling Plan |
    | BUSINESS_VOICE_DIRECTROUTING_MED | Business Voice without Calling Plan - US |

    > [!NOTE]
    > The script provided in this document assumes that you have a single SKU Code for Business Voice in your tenant.  
    >
    > If you have multiple Business Voice SKUs, you'll need to adjust the script or run it multiple times, one time for each SKU Code.

1. Create a PowerShell variable named `$skuSourceBV`.
    1. Make sure to replace the `SkuPartNumber` label with your tenant's Business Voice SKU Code.
    1. In this example, we're using the `BUSINESS_VOICE_MED2_TELCO` SKU Code.

    ```powershell
    $skuSourceBV = Get-AzureADSubscribedSku  | where {$_.SkuPartNumber -eq "BUSINESS_VOICE_MED2_TELCO"}
    ```

1. Use the following table to identify your new Teams Phone and Audio Conferencing license SKU Codes.

    | SKU Code | License type |
    | -------- | ------------ |
    | MCOTEAMS_ESSENTIALS | Teams Phone with Calling Plan |
    | MCOEV | Teams Phone Standard (No Calling Plan) |
    | MCOMEETADV | Audio Conferencing |
    | Microsoft_Teams_Audio_Conferencing_select_dial_out | Microsoft Teams Audio Conferencing Select Dial-Out |

1. Create PowerShell variables to store the unique Teams Phone and Audio Conferencing SKU Codes.
    1. Make sure you replace the `SkuPartNumber` label with the SKU Codes you have available in your tenant.
    1. In this example, we're using the `MCOTEAM_ESSENTIALS` and `MCOMEETADV` SKU Codes.

        ```powershell
        $skuTargetTPCP = Get-AzureADSubscribedSku | where {$_.SkuPartNumber -eq "MCOTEAMS_ESSENTIALS"}
        $skuTargetAC = Get-AzureADSubscribedSku | where {$_.SkuPartNumber -eq "MCOMEETADV"} 
        ```

1. Run this script to collect the required Service Plan data from the source SKU into unique objects.

     ```powershell
     $servicePlan_Phone = $skuSourceBV.ServicePlans | where {$_.ServicePlanName.ToString() -like "*EV*"}
    $servicePlan_AC = $skuSourceBV.ServicePlans | where {$_.ServicePlanName.ToString() -like "*MEET*"}
    $servicePlan_CP = $skuSourceBV.ServicePlans | where {$_.ServicePlanName.ToString() -like "*PSTN*"}
    ```

1. Before moving on, validate if the source SKU (Business Voice) and the target SKUs (Teams Phone and Audio Conferencing) have the same Service Plans included.
    1. A mismatch can trigger a license change that could disrupt users' voice and audio conferencing services.
    2. Create variables to validate if all Service Plans in the source SKU will be replaced with the same target service plan.

        ```powershell
        $validated_TP = $false
        $validated_AC = $false
        $validated_CP = $false
        ```

    3. If the source Business Voice license has no Calling Plan included, don't check for it.

        ```powershell
        if($skuSourceBV.ServicePlans.Count -eq 2) { $validated_CP = $true }
        ```

    4. Verify if all service plans in source SKU have a matching service plan in target SKU.

        ```powershell
        For ($i=0; $i -le $skuSourceBV.ServicePlans.Count ; $i++) {
        if($validated_TP -eq $false) { if($skuTargetTP.ServicePlans.Contains($servicePlan_Phone)) { $validated_TP = $true } }
        if($validated_AC -eq $false) { if($skuTargetAC.ServicePlans.Contains($servicePlan_AC)) { $validated_AC = $true } }
        if($validated_CP -eq $false) { if($skuTargetTP.ServicePlans.Contains($servicePlan_CP)) { $validated_CP = $true } }
        }
        ```

    5. If there's a missing service plan in the target SKU, you could disrupt service availability for users, and your script should stop processing.

        ```powershell
        if($validated_TP -eq $false ) { Write-Host "Stop updating users because target SKU does not have the same Service Plan for Teams Phone." ; exit }
        if($validated_AC -eq $false ) { Write-Host "Stop updating users because target SKU does not have the same Service Plan for Audio Conferencing." ; exit }
        if($validated_CP -eq $false ) { Write-Host "Stop updating users because target SKU does not have the same Service Plan for Calling Plan." ; exit }
        ```

1. If everything looks good, prepare PowerShell Objects to perform the update operations on user objects. Use the `AssignedLicenses` object for this.

    ```powershell
    $LicenseAddTPCP = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
    $LicenseAddTPCP.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $skuTargetTPCP.SkuPartNumber -EQ).SkuID
    $LicenseAddAC = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
    $LicenseAddAC.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $skuTargetAC.SkuPartNumber -EQ).SkuID
    
    $LicensesToUpdate = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
    $LicensesToUpdate.AddLicenses += ($LicenseAddTPCP)
    $LicensesToUpdate.AddLicenses += ($LicenseAddAC)
    $LicensesToUpdate.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $skuSourceBV.SkuPartNumber -EQ).SkuID
    ```

1. Next, get the list of users who have the Business Voice licenses assigned and store it in a list named `$usersLicensedOldSKU`.

    ```powershell
    $usersLicensedOldSKU = New-Object System.Collections.Generic.List[Microsoft.Open.AzureAD.Model.User]
    
    Get-AzureAdUser | ForEach { $BVlicensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If($_.AssignedLicenses[$i].SkuId -eq $skuSourceBV.SkuId) { $BVlicensed=$true } } ; If( $BVlicensed -eq $true) { $usersLicensedOldSKU.Add($_)} }
    ```

1. Now, using the new list of users, perform an update activity to remove the Business Voice licenses and add the Teams Phone and Audio Conferencing licenses, using the ``$LicensesToUpdate`` object you created earlier.

    ```powershell
    $usersLicensedOldSKU | ForEach { Set-AzureADUserLicense -ObjectId $_.ObjectId -AssignedLicenses $LicensesToUpdate; Write-Host "Completed Update of user " $_.UserPrincipalName;  }
    ```

> [!NOTE]
> If you don't have enough available Teams Phone and/or Audio Conferencing licenses to replace Business Voice, you’ll get the error **Subscription with SKU guid does not have any available license** during user assignment as soon as the pool of licenses is depleted.

### Full script

```powershell
#Install the AzureAD module when required
Install-Module AzureAD
#Import the AzureAD module so you can use the commandlets
Import-Module AzureAD

#Connect to your tenant
Connect-AzureAD

#When necessary, uncomment and use this commandlet to list all the licenses in the tenant and identify which license packages are required
#Get-AzureADSubscribedSku

##Replace the SKU codes below to match your desired scenario
$skuSourceBV = Get-AzureADSubscribedSku | where {$_.SkuPartNumber -eq "BUSINESS_VOICE_MED2_TELCO"}
$skuTargetTP = Get-AzureADSubscribedSku | where {$_.SkuPartNumber -eq "MCOTEAMS_ESSENTIALS"}
$skuTargetAC = Get-AzureADSubscribedSku | where {$_.SkuPartNumber -eq "MCOMEETADV"}

##Replace the SKU codes below to match your desired scenario
$servicePlan_Phone = $skuSourceBV.ServicePlans | where {$_.ServicePlanName.ToString() -like "*EV*"}
$servicePlan_AC = $skuSourceBV.ServicePlans | where {$_.ServicePlanName.ToString() -like "*MEET*"}
$servicePlan_CP = $skuSourceBV.ServicePlans | where {$_.ServicePlanName.ToString() -like "*PSTN*"}

##Create variables to validate if all Service Plans in the source SKU will be replaced with the same target service plan
$validated_TP = $false
$validated_AC = $false
$validated_CP = $false

##If source Business Voice has no Calling Plan included, do not check
if($skuSourceBV.ServicePlans.Count -eq 2) { $validated_CP = $true }

##Verify if all service plans in source SKU have a matching service plan in target SKU
For ($i=0; $i -le $skuSourceBV.ServicePlans.Count ; $i++) { 
    if($validated_TP -eq $false) { if($skuTargetTP.ServicePlans.Contains($servicePlan_Phone)) { $validated_TP = $true } }
    if($validated_AC -eq $false) { if($skuTargetAC.ServicePlans.Contains($servicePlan_AC)) { $validated_AC = $true } }
    if($validated_CP -eq $false) { if($skuTargetTP.ServicePlans.Contains($servicePlan_CP)) { $validated_CP = $true } }
}

##If there's a missing service plan in the target sku, we might impact service availability for a user and therefore stop processing
if($validated_TP -eq $false ) { Write-Host "Stop updating users because target SKU does not have the same Service Plan for Teams Phone." ; exit } 
if($validated_AC -eq $false ) { Write-Host "Stop updating users because target SKU does not have the same Service Plan for Audio Conferencing." ; exit } 
if($validated_CP -eq $false ) { Write-Host "Stop updating users because target SKU does not have the same Service Plan for Calling Plan." ; exit } 


##Prepare variables and update
$LicenseAddTP = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$LicenseAddTP.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $skuTargetTP.SkuPartNumber -EQ).SkuID
$LicenseAddAC = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$LicenseAddAC.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $skuTargetAC.SkuPartNumber -EQ).SkuID
$LicensesToUpdate = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToUpdate.AddLicenses += ($LicenseAddTP)
$LicensesToUpdate.AddLicenses += ($LicenseAddAC)
$LicensesToUpdate.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $skuSourceBV.SkuPartNumber -EQ).SkuID

$usersLicensedOldSKU = New-Object System.Collections.Generic.List[Microsoft.Open.AzureAD.Model.User]
Get-AzureAdUser | ForEach { $BVlicensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If($_.AssignedLicenses[$i].SkuId -eq $skuSourceBV.SkuId) { $BVlicensed=$true } } ; If( $BVlicensed -eq $true) { $usersLicensedOldSKU.Add($_)} }

$usersLicensedOldSKU | ForEach { Set-AzureADUserLicense -ObjectId $_.ObjectId -AssignedLicenses $LicensesToUpdate; Write-Host "Completed Update of user " $_.UserPrincipalName;  }
```

# [Option 4: Bulk users with Azure group-based licensing](#tab/azure-licensing)

### Option 4: Bulk user license update using Azure group-based licensing

Azure group-based license management allows you to assign subscriptions and service plans to a group.

This method ensures that:

- Licenses are assigned to all members of the group.
- Any new members who join the group are assigned the appropriate licenses.
- When members are removed from the group, those licenses are removed too.

You’ll have to validate [license requirements for group-based licensing](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

> [!NOTE]
> For this method, the license updates must be processed in a single step.
>
> We recommend that you compile a list of existing groups that have Business Voice licenses assigned, select a small test user group first, and replace the license plan assignment with the preferred new license plans.

### How to bulk update licenses using group-based licensing

1. Go to [portal.azure.com](https://portal.azure.com) and sign in with admin credentials.
1. Go to **Azure Active Directory** and on the left menu, select **Licenses**.
1. To verify which groups have Business Voice licenses assigned, choose **All Products** and select the Business Voice plan.
1. Select **Licensed Groups** or **Licensed users**. You’ll find the list of licensed groups in the right-hand pane.
1. Select the group name to open the group assignment details.
1. Select **Assignments** to modify the licenses assigned to this group.
1. Check the boxes in front of the license plans you acquired to replace Business Voice.
1. Uncheck the box in front of the Microsoft 365 Business Voice license plan.
1. Select **Save**.
1. Return to the group by selecting the group name. You’ll see a banner stating **License changes are pending**.
1. Select **Reprocess** to force the license assignment to update.

---

## Validate user license updates

After you've completed your chosen method, validate if the user licenses were properly updated.

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com) and sign in with admin credentials.
1. Navigate to **Users** > **Active Users** and select a test user.
1. Select **Manage product licenses** on the toolbar.
1. On the **Licenses and apps** screen, review which licenses they have assigned to them.

If all the targeted users have the correct licenses assigned, you've completed updating your Business Voice licenses to Teams Phone and Audio Conferencing licenses.
