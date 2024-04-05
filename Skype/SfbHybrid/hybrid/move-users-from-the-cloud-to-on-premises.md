---
ms.date: 11/16/2018
title: "Move users from the cloud to on-premises"
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: bjwhalen
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.collection: 
- Hybrid 
- M365-voice
- m365initiative-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
ms.custom:
description: "Learn how to move users from Teams to on-premises."
---

# Move users from the cloud to on-premises

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

If needed, you can move a user who was previously migrated from on-premises to Teams back to on-premises. To move users from TeamsOnly mode back to an on-premises deployment of Skype for Business Server, use either the Move-CsUser cmdlet or the Skype for Business Server Control Panel, both of which are on-premises tools. When you move a user back to an on-premises deployment, you must decide which pool to move the user to.

> [!IMPORTANT]
> If the user was previously in TeamsOnly mode, and you are using an earlier version than Skype for Business Server 2015 with CU8, then you must also remove the TeamsOnly mode assignment of TeamsUpgradePolicy for that user. On-premises users must not have mode= TeamsOnly.  Subsequent versions of Skype for Business Server automatically remove this assignment. For more information, see [Grant-CsTeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy).

## Prerequisites

- The organization must have Microsoft Entra Connect properly configured and be syncing all relevant attributes for the user, as described in [Configure Microsoft Entra Connect](configure-azure-ad-connect.md).
- The user being moved from online back to on-premises must already exist in the on-premises Active Directory.
- Skype for Business hybrid must be configured, as described in [Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md).

## Moving users back to on-premises

Once you move a user from the cloud back to on-premises:

- The user interacts with your Skype for Business Server deployment for its functionality.
- Any contacts that existed in Teams are migrated to Skype for Business Server. The two sets of contacts are merged and then migrated back to on-premises.  In addition, contacts that are pre-existing in Teams remain in Teams.
- If the user also uses Teams, they won't have the ability to interoperate with Skype for Business users, nor will they be able to communicate with users in federated organizations.

### Move users with Move-CsUser

Move-CsUser is available from an on-premises Skype for Business Management Shell PowerShell window. You must have sufficient privileges in both the on-premises environment as well as the cloud service organization (Microsoft 365), as described in [Required administrative credentials](move-users-between-on-premises-and-cloud.md#required-administrative-credentials). You can either use a single account that has privileges in both environments, or you can start an on-premises Skype for Business Server Management Shell window with on-premises credentials, and use the `-Credential` parameter to specify credentials for a Microsoft 365  account with the necessary administrative role.

To move a user to on-premises using Move-CsUser:

- Specify the user to move using the Identity parameter.
- Specify the -Target parameter with the fully qualified domain name of the desired on-premises pool that will host the user.
- If you don't have one account with sufficient permissions in both on-premises and the cloud service (Microsoft 365), use the -credential parameter to supply an account with sufficient permissions in Microsoft 365.
- You must have sufficient privileges in both the on-premises environment and the cloud service (Microsoft 365), as described in [Required administrative credentials](move-users-between-on-premises-and-cloud.md#required-administrative-credentials).

The following cmdlet sequence can be used to move a user to Skype for Business Server, and assumes the Microsoft 365 credential is a separate account and supplied as input for the Get-Credential prompt.

```PowerShell
$cred=Get-Credential
Move-CsUser -Identity username@contoso.com -Target pool.corp.contoso.com -Credential $cred
```

### Move users with the Skype for Business Server Control Panel

1. Open the Skype for Business Server Control Panel app.
2. In the left navigation, choose **Users**.
3. Use **Find** to locate the user(s) you would like to move back to on-premises.
4. Select the user(s), and then from the **Action** dropdown above the list, choose **Move selected users to on-premises**.
5. In the wizard, select the user pool that will host the user and select **Next**.
6. If prompted, sign in to Microsoft 365 with an account that ends in .onmicrosoft.com and has sufficient permissions.
7. Select **Next**, and then **Next** one more time to move the user.
8. Note that status messages regarding success or failure are provided at the top of the main Control Panel app, not in the wizard.

### Removing TeamsOnly mode

If you're using a version earlier than Skype for Business 2015 with CU8 and the user is being moved back to on-premises in TeamsOnly mode, you must remove the UpgradeToTeams instance of `TeamsUpgradePolicy` before you move the user on-premises. You can either explicitly grant a policy with a different mode or remove the existing policy assignment for that user to use the global policy (as long as your tenant’s global policy is not UpgradeToTeams).

To remove the user’s assignment of TeamsUpgradePolicy, run the following cmdlet from a Teams PowerShell window:

`Grant-CsTeamsUpgradePolicy -Identity $user -PolicyName $null`

Alternatively, to assign another instance of TeamsUpgradePolicy that doesn't have mode=TeamsOnly, you can specify the name of the desired instance as the value of PolicyName parameter in the cmdlet. To see a list of available instances of TeamsUpgradePolicy, run Get-CsTeamsUpgradePolicy.

## See also

[Move-CsUser](/powershell/module/skype/move-csuser)
