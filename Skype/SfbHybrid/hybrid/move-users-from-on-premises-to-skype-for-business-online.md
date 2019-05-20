---
title: "Move users from on premises to Skype for Business Online"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
ms.audience: ITPro
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
description: "Learn how to move users to Skype for Business Online."
---

# Move users from on premises to Skype for Business Online

After you move a user from on-premises to Skype for Business Online, the user interacts with Skype for Business Online for its functionality. Any contacts that existed on-premises will be available in Skype for Business Online, and any existing meetings the user organized for the future are updated to so the links point to Skype for Business Online. If the user is enabled for Audio Conferencing, the meetings will also include dial-in coordinates.  To move users from an on-premises environment to Skype for Business Online, use either the Move-CsUser cmdlet or the Skype for Business Server Control Panel, both of which are on-premises tools. 

Before moving any users, be sure to review the [prerequisites](move-users-between-on-premises-and-cloud.md#prerequisites) to move users to the cloud.
 
## Move users with Move-CsUser 

Move-CsUser is available from an on-premises Skype for Business Management Shell PowerShell window. You must have sufficient privileges in both the on-premises environment as well as in the Office 365 tenant as described in [Required administrative credentials](move-users-between-on-premises-and-cloud.md#required-administrative-credentials). You can either use a single account that has privileges in both environments, or you can start an on-premise Skype for Business Server Management Shell window with on-premise credentials, and use the `-Credential` parameter to specify credentials for an Office 365 account with the necessary Office 365 administrative role.

To move a user to online using Move-CsUser:

- Specify the user to move using the Identity parameter.
- Specify the -Target parameter with the value “sipfed.online.lync.<span>com”.
- If you do not have one account with sufficient permissions in both on premises and Office 365, use the -credential parameter to supply an account with sufficient permissions in Office 365.
- If the account with permissions in Office 365 does not end in “on.microsoft.<span>com”, then you must specify the -HostedMigrationOverrideUrl parameter, with  the correct value as described in [Required administrative credentials](move-users-between-on-premises-and-cloud.md#required-administrative-credentials).

 > [!NOTE]
 > You must determine the correct HostedMigrationOverrideUrl value for your tenant. this can be easily done by navigating to the Legacy Skype for Business admin center. determine the prefix - XXXXXXX.online.lync.com and append /HostedMigration/hostedmigrationservice.svc. for example: https://admin1a.online.lync.com/HostedMigration/hostedmigrationService.svc
 > Once you identified the value, use it for the $url variable as shown below.

The following cmdlet sequence can be used to move a user to Skype for Business Online, and assumes the Office 365 credential is a separate account and supplied as input for the Get-Credential prompt.

```
$cred=Get-Credential
$url="https://admin1a.online.lync.com/HostedMigration/hostedmigrationService.svc"
 
Move-CsUser -Identity username@contoso.com -Target sipfed.online.lync.com -Credential $cred -HostedMigrationOverrideUrl $url
```

If the administrator account is MFA (Multi-Factor Authentication) enabled, do not specify the -Credential parameter. The administrator will be prompted for credentials.

## Move users with Skype for Business Server Control Panel 

1. Open the Skype for Business Server Control Panel app.
2. In the left navigation, choose **Users**.
3. Use **Find** to locate the user(s) you would like to move to Skype for Business Online.
4. Select the user(s), and then, from the **Action** dropdown above the list, choose **Move selected users to Skype for Business Online**.
5. In the wizard, click **Next**.
6. If prompted, sign in to Office 365, with an account that ends in .onmicrosoft.com and has sufficient permissions.
7. Click **Next**, and then **Next** one more time to move the user.
8. Note that status messages regarding success or failure are provided at the top of the main Control Panel app, not in the wizard.

## See also

[Move-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/move-csuser)
