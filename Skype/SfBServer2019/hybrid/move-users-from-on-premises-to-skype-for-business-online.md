---
title: "Move users from on premises to Skype for Business Online"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
ms.custom:
description: "Summary: Learn how to migrate user settings and move users to Skype for Business Online."
---

# Move users from on premises to Skype for Business Online

**Summary:** Learn how to migrate user settings and move users to Skype for Business Online.

Before actually moving a user to Office 365, you should first confirm that the user accounts are synchronized to the cloud, and assign them a license. To do this, you use the Office 365 Admin Center.

### To confirm that an on-premises user account has been synchronized with Office 365

1. Using a tenant admin account, open the Office 365 admin center for your tenant.  Tenant admin accounts should be granted both the Skype for Business Admin Role and the User Management Role (or the Global Admin role) to perform this function in Office 365.

2. On the left navigation pane, click **Users**, and then click **Active Users**.

3. Click **Search for a User**, and type the name of the user.

4. Confirm that you see the user and that their status is **Synched with Active Directory**.

    If the user is not yet synchronized, the next automatic synchronization should happen within three hours. You can also force a synchronization sooner. For more information, see [Force Directory Synchronization](https://msdn.microsoft.com/en-us/library/azure/jj151771.aspx).

To assign the license in Office 365, see [Assign licenses to users in Office 365 for Business](https://support.office.com/en-us/article/Assign-or-unassign-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

## Migrate user settings to Skype for Business Online

Before you migrate users to Skype for Business Online, you should back up the user data associated with the accounts to be moved. Not all user data is moved with the user account. For information, see [Backup and Restoration Requirements: Data](https://technet.microsoft.com/library/ecfb8e4d-cb4f-476d-9772-4486bd683c04.aspx).

User settings are moved with the user account. Some on-premises settings are not moved with the user account.

## Move pilot users to Skype for Business Online

Before you move users to Skype for Business Online, you may want to move a few pilot users to confirm that your environment is correctly configured. You can then verify that the features and services function as expected before attempting to move additional users.

To move an on-premises user to your Skype for Business Online tenant, run the following cmdlets in the Skype for Business Server Management Shell, using the administrator credentials for your Microsoft Office 365 tenant. Replace "username@contoso.com" with the information for the user you want to move.

```
$creds=Get-Credential
```

```
Move-CsUser -Identity username@contoso.com -Target sipfed.online.lync.com -Credential $creds
```

## Move users to Skype for Business Online

You can move multiple users by using the [Get-CsUser](https://docs.microsoft.com/powershell/module/skype/get-csuser?view=skype-ps) cmdlet with the -Filter parameter to select the users with a specific property assigned to the user accounts, such as RegistrarPool. You can then pipe the returned users to the [Move-CsUser](https://docs.microsoft.com/powershell/module/skype/move-csuser?view=skype-ps) cmdlet, as shown in the following example:

```
Get-CsUser -Filter {UserProperty -eq "UserPropertyValue"} | Move-CsUser -Target sipfed.online.lync.com -Credential $creds
```

You can also use the -OU parameter to retrieve all users in the specified OU, as shown in the following example:

```
Get-CsUser -OU "cn=hybridusers,cn=contoso.." | Move-CsUser -Target sipfed.online.lync.com -Credentials $creds
```

## Verify online user settings and features

You can verify that the user was moved successfully in the following ways:

- View the status of the user in the Skype for Business Online Control Panel. The visual indicator for on-premises users and online users is different.

- Run the following cmdlet:

  ```
  Get-CsUser -Identity
  ```


