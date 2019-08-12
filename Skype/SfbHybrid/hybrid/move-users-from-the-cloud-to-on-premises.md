---
title: "Move users from the cloud to on premises"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
ms.custom:
description: "Learn how to move users from Skype for Business Online to on premises."
---

# Move users from the cloud to on premises 

If needed, you can move a user who was previously migrated from on premises to the cloud (whether using Skype for Business Online or Teams Only) back to on premises. To move users from either Skype for Business Online or TeamsOnly mode back to an on-premises deployment of Skype for Business Server, use either the Move-CsUser cmdlet or the Skype for Business Server Control Panel, both of which are on-premises tools. When you move a user back to an on-premises deployment, you must decide which pool to move the user to.

> [!Important]
> If the user was previously in TeamsOnly mode, and you are using an earlier version than Skype for Business Server 2015 with CU8, then you must also remove the TeamsOnly mode assignment of TeamsUpgradePolicy for that user. On-premises users must not have mode= TeamsOnly.  Subsequent versions of Skype for Business Server automatically remove this assignment. For more details, see [Grant-CsTeamsUpgradePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/grant-csteamsupgradepolicy).

## Prerequisites

- The organization must have Azure AD Connect properly configured and be syncing all relevant attributes for the user, as described in [Configure Azure AD Connect](configure-azure-ad-connect.md).
- The user being moved from online back to on premises must already exist in the on-premises Active Directory.
- Skype for Business hybrid must be configured, as described in [Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md).

## Moving users back to on premises

Once you move a user from the cloud back to on-premises:

- The user interacts with your Skype for Business Server deployment for its functionality. 
- Any contacts that existed in either Skype for Business Online or Teams are migrated  to Skype for Business Server. The two sets of contacts are merged and then migrated back to on premises.  In addition, contacts that are pre-existing in Teams remain in Teams.
- If the user also uses Teams, they will not have the ability to interoperate with Skype for Business users, nor will they be able to communicate with users in federated organizations.
- Meetings in Skype for Business Online are *not* automatically migrated back to on premises. Users should either reschedule their meetings or, if desired, use the [Meeting Migration Tool](https://support.office.com/en-us/article/2b525fe6-ed0f-4331-b533-c31546fcf4d4).

### Move users with Move-CsUser

Move-CsUser is available from an on-premises Skype for Business Management Shell PowerShell window. You must have sufficient privileges in both the on-premises environment as well as the Office 365 tenant, as described in [Required administrative credentials](move-users-between-on-premises-and-cloud.md#required-administrative-credentials). You can either use a single account that has privileges in both environments, or you can start an on-premise Skype for Business Server Management Shell window with on-premise credentials, and use the `-Credential` parameter to specify credentials for an Office 365 account with the necessary Office 365 administrative role.

To move a user to on premises using Move-CsUser:

- Specify the user to move using the Identity parameter.
- Specify the -Target parameter with the fully qualified domain name of the desired on-premises pool that will host the user.
- If you do not have one account with sufficient permissions in both on premises and Office 365, use the -credential parameter to supply an account with sufficient permissions in Office 365.
- If the account with permissions in Office 365 does not end in “on.microsoft.com”, you must specify the -HostedMigrationOverrideUrl parameter, with the correct value as described in [Required administrative credentials](move-users-between-on-premises-and-cloud.md#required-administrative-credentials).

The following cmdlet sequence can be used to move a user to Skype for Business Server, and assumes the Office 365 credential is a separate account and supplied as input for the Get-Credential prompt.

```
$cred=Get-Credential
$url="https://admin1a.online.lync.com/HostedMigration/hostedmigrationService.svc"
Move-CsUser -Identity username@contoso.com -Target pool.corp.contoso.com -Credential $cred -HostedMigrationOverrideUrl $url
```

### Move users with the Skype for Business Server Control Panel

1. Open the Skype for Business Server Control Panel app.
2. In the left navigation, choose **Users**.
3. Use **Find** to locate the user(s) you would like to move back to on premises.
4. Select the user(s), and then from the **Action** dropdown above the list, choose **Move selected users to on-premises**.
5. In the wizard, select the user pool that will host the user and click **Next**.
6. If prompted, sign in to Office 365, with an account that ends in .onmicrosoft.com and has sufficient permissions.
7. Click **Next**, and then **Next** one more time to move the user.
8. Note that status messages regarding success or failure are provided at the top of the main Control Panel app, not in the wizard.

### Removing TeamsOnly mode

If you are using a version earlier than Skype for Business 2015 with CU8 and the user is being moved back to on premises in TeamsOnly mode, you must remove the UpgradeToTeams instance of `TeamsUpgradePolicy` before you move the user on premises. You can either explicitly grant a policy with a different mode or simply remove the existing policy assignment for that user to use the global policy (as long as your tenant’s global policy is not UpgradeToTeams).

To remove the user’s assignment of TeamsUpgradePolicy, run the following cmdlet from a Skype for Business Online PowerShell window:

`Grant-CsTeamsUpgradePolicy -Identity $user -PolicyName $null`

Alternatively, to assign another instance of TeamsUpgradePolicy that does not have mode=TeamsOnly, you can specify the name of the desired instance as the value of PolicyName parameter in the cmdlet. To see a list of available instances of TeamsUpgradePolicy, run Get-CsTeamsUpgradePolicy.


## See also

[Move-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/move-csuser)
