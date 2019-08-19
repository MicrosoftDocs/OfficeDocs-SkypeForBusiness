---
title: Move users from Skype for Business Server 2019 to Teams
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
description: "Summary: Learn how to migrate user settings and move users to Teams."
---

# Move users from on-premises to Teams

When a user is moved from on premises to Teams Only, the user’s Skype for Business home is moved from on premises to online and the user is assigned TeamsUpgradePolicy with mode=TeamsOnly.  After a user is moved from on-premises to TeamsOnly mode:

- All incoming calls and chats from other users (whether sent from Skype for Business or Teams), will land in the user’s Teams client.
- The user will be able to interoperate with other users who use Skype for Business (whether online or on premises).
- The user will be able to communicate with users in federated organizations.
- New meetings scheduled by that user are Teams meetings.
- User can still join any Skype for Business meetings.
- The user’s pre-existing meetings scheduled for the future will be migrated from on-premises to Teams.
- Contacts that existed on premises are available in Teams shortly after the user logs on for the first time.
- Users cannot initiate calls or chats from Skype for Business, nor can they schedule new meetings in Skype for Business. If they attempt to open the Skype for Business client, they will be redirected to use Teams as shown below. If the Teams client is not installed, they will be directed to the web version of Teams using their browser.<br><br>
    ![Message redirecting a user to Teams](../media/go-to-teams-page.png)

Before moving any users, be sure to review the [prerequisites](move-users-between-on-premises-and-cloud.md#prerequisites) to move users to the cloud. Also be sure to review [Migration and interoperability guidance for organizations using Teams together with Skype for Business](/microsoftteams/migration-interop-guidance-for-teams-with-skype).

There are two methods to move a user from on premises to Teams:

- If you are using a version earlier than Skype for Business Server 2015 CU8, the move requires two steps (which can be scripted to be done together as a single step, if desired):
  - [Move the user from Skype for Business Server (on premises) to Skype for Business Online](move-users-from-on-premises-to-skype-for-business-online.md).
  - Once the user is homed in Skype for Business Online, assign the user TeamsUpgradePolicy with mode= TeamsOnly. To grant TeamsOnly mode, run the following cmdlet from a Skype for Business Online PowerShell window:
        `Grant-CsTeamsUpgradePolicy -Identity $user -PolicyName UpgradeToTeams`
- If you have admin tools from Skype for Business Server 2015 CU8 or later, you can use the method above, or you can do this move in one step as described below. In addition, you can optionally provide a notification within the Skype for Business client prior to moving them to Teams Only as well as optionally have the Teams client silently downloaded by the Skype for Business client.

## Move a user directly from Skype for Business on premises to Teams Only

The on-premises admin tools in Skype for Business Server 2015 with CU8, as well as in Skype for Business Server 2019, enable you to move users from on premises to Teams Only mode in a single step using either the Move-CsUser cmdlet in PowerShell or the Skype for Business Server Control Panel, as described below.

### Move to Teams using Move-CsUser

Move-CsUser is available from an on-premises Skype for Business Management Shell PowerShell window. The steps below and permissions required are the same as moving a user to Skype for Business Online, except that you must also specify the MoveToTeams switch and you must ensure that the user has also been granted a license for Teams (in addition to Skype for Business Online).

You must have sufficient privileges in both the on-premises environment and the Office 365 tenant, as described in [Required administrative credentials](move-users-between-on-premises-and-cloud.md#required-administrative-credentials). You can either use a single account that has privileges in both environments, or you can start an on-premises Skype for Business Server Management Shell window with on-premises credentials, and use the `-Credential` parameter to specify credentials for an Office 365 account with the necessary Office 365 administrative role.

To move a user to Teams Only mode using Move-CsUser:

- Specify the user to move using the `Identity` parameter.
- Specify the     -Target     parameter with the value “sipfed.online.lync.<span>com”.
- Specify the `MoveToTeams` switch.
- If you do not have one account with sufficient permissions in both on premises and Office 365, use the `-credential` parameter to supply an account with sufficient permissions in Office 365.
- If the account with permissions in Office 365 does not end in “on.microsoft.<span>com”, you must specify the `-HostedMigrationOverrideUrl` parameter, with the correct value as described in [Required administrative credentials](move-users-between-on-premises-and-cloud.md#required-administrative-credentials).

The following cmdlet sequence can be used to move a user to TeamsOnly, and assumes the Office 365 credential is a separate account and supplied as input for the Get-Credential prompt.

    ```
    $cred=Get-Credential
    $url="https://admin1a.online.lync.com/HostedMigration/hostedmigrationService.svc"
    Move-CsUser -Identity username@contoso.com -Target sipfed.online.lync.com -MoveToTeams -Credential $cred -HostedMigrationOverrideUrl $url
    ```

### Move to Teams using Skype for Business Server Control Panel

1. Open the Skype for Business Server Control Panel app.
2. In the left navigation, choose **Users**.
3. Use **Find** to locate the user(s) you would like to move to Teams.
4. Select the user(s), and then, from the **Action** dropdown above the list, choose **Move selected users to Teams**.
5. In the wizard, click **Next**.
6. If prompted, sign in to Office 365, with an account that ends in .onmicrosoft.com and has sufficient permissions.
7. Click **Next**, and then **Next** one more time to move the user.
8. Note that status messages regarding success or failure are provided at the top of the main Control Panel app, not in the wizard.

## Notify your Skype for Business on-premises users of the upcoming move to Teams

The on-premises admin tools in Skype for Business Server 2015 with CU8, as well as in Skype for Business Server 2019, enable you to notify on-premises Skype for Business users of their upcoming move to Teams. When you enable these notifications, users will see a notification in their Skype for Business client (Win32, Mac, web, and mobile) as shown below. If users click the **Try it** button, the Teams client will be launched if it is installed; otherwise, users will be navigated to the web version of Teams in their browser. By default, when notifications are enabled, Win32 Skype for Business clients silently download the Teams client so that the rich client is available prior to moving the user to Teams Only mode; however, you can also disable this behavior.  Notifications are configured using the on-premises version of `TeamsUpgradePolicy`, and silent download for Win32 clients is controlled via the on-premises `TeamsUpgradeConfiguration` cmdlet.

> [!TIP]
> Some servers may need to reboot for this to work in Skype for Business 2015 with CU8.

![Notification of upcoming move to Teams](../media/teams-upgrade-notification.png)

To notify on-premises users that they will soon be upgraded to Teams, create a new instance of TeamsUpgradePolicy with NotifySfBUsers=true. Then assign that policy to the users who you want to notify, either by assigning the policy directly to the user or by setting the policy at the site, pool, or global level. The following cmdlets create and grant a user-level policy:

```
New-CsTeamsUpgradePolicy -Identity EnableNotifications -NotifySfbUser $true
Grant-CsTeamsUpgradePolicy -Identity username@contoso.com -PolicyName EnableNotifications
```

Automatic download of Teams via the Skype for Business Win32 client is controlled via the on-premises TeamsUpgradeConfiguration cmdlet with the DownloadTeams parameter. You create this configuration on a global, site, and pool level. For example, the following command creates the configuration for the site Redmond1:

`New-CsTeamsUpgradeConfiguration -Identity “site:redmond1”`

By default, the value of DownloadTeams is True; however, it is *only* honored if NotifySfbUser = True for a given user.

## See also

[Move-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/move-csuser)

[Grant-CsTeamsUpgradePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/grant-csteamsupgradepolicy
)

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](/microsoftteams/migration-interop-guidance-for-teams-with-skype)

[Coexistence with Skype for Business](/microsoftteams/coexistence-chat-calls-presence)
