---
title: Move users to Skype for Business Online
ms.prod: SKYPEFORBUSINESS
ms.assetid: 6a523c86-2eac-4fa4-973a-4406872c9a7d
---


# Move users to Skype for Business Online
[] **Summary:** Learn how to migrate user settings and move users to Skype for Business Online.
Before actually moving the user to Office 365, you should first confirm that the user accounts are synchronized to the cloud, and assign them a license. To do this, you use the Office 365 Admin Center.
  
    
    


### To confirm that an on-premises user account has been synchronized with Office 365


1. Using an tenant admin account, open the  [Office 365 admin center](https://portal.office.com/) for your tenant.
    
  
2. On the left navigation pane, click **Users** and then **Active Users**.
    
  
3. Click **Search for a User**, and type the name of the user.
    
  
4. Confirm that you see the user, and that their status is **Synched with Active Directory**.
    
    If the user is not yet synchronized, the next automatic synchronization should happen within three hours. You can also force a synchronization sooner. For more information, see  [Force Directory Synchronization](https://msdn.microsoft.com/en-us/library/azure/jj151771.aspx).
    
  
To assign the license in Office 365, see  [Assign licenses for Office 365 for Business](https://support.office.com/en-us/article/Assign-or-unassign-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).
## Migrate User Settings to Skype for Business Online

Before you start migrating users to Skype for Business Online, you should backup the user data associated with the accounts to be moved. Not all user data is moved with the user account. For information, see  [Backup and Restoration Requirements: Data](http://technet.microsoft.com/library/ecfb8e4d-cb4f-476d-9772-4486bd683c04.aspx).
  
    
    
User settings are moved with the user account. Some on-premises settings are not moved with the user account.
  
    
    

## Moving Pilot Users to Skype for Business Online

Before you begin to move users to Skype for Business Online, you may want to move a few pilot users to confirm that your environment is correctly configured. You can then verify that the features and services function as expected before attempting to move additional users.
  
    
    
To move an on-premises user to your Skype for Business Online tenant, run the following cmdlets in the Skype for Business Server Management Shell, using the administrator credentials for your Microsoft Office 365 tenant. Replace "username@contoso.com" with the information for the user that you want to move.
  
    
    



```

$creds=Get-Credential
```




```
Move-CsUser -Identity username@contoso.com -Target sipfed.online.lync.com -Credential $creds -HostedMigrationOverrideUrl <URL>
```

The format of the URL specified for the **HostedMigrationOverrideUrl** parameter must be the URL to the pool where the Hosted Migration service is running, in the following format: _Https://<Pool FQDN>/HostedMigration/hostedmigrationService.svc_.
  
    
    
You can determine the URL to the Hosted Migration Service by viewing the URL for the Online Control Panel for your Office 365 tenant account.
  
    
    

### To determine the Hosted Migration Service URL for your Office 365 tenant


1. Login to your Office 365 tenant as an administrator.
    
  
2. Open the **Skype for Business admin center**.
    
  
3. With the **Skype for Business admin center** displayed, select and copy the URL in the address bar up to **lync.com**. An example URL looks similar to the following:
    
     `https://webdir0a.online.lync.com/lscp/?language=en-US&amp;tenantID=`
    
  
4. Replace **webdir** in the URL with **admin**, resulting in the following: 
    
     `https://admin0a.online.lync.com`
    
  
5. Append the following string to the URL: **/HostedMigration/hostedmigrationservice.svc**.
    
    The resulting URL, which is the value of the **HostedMigrationOverrideUrl**, should look like the following:
    
     `https://admin0a.online.lync.com/HostedMigration/hostedmigrationservice.svc`
    
  

## Move users to Skype for Business Online

You can move multiple users by using the  [Get-CsUser](get-csuser.md)cmdlet with the -Filter parameter to select the users with a specific property assigned to the user accounts, such as RegistrarPool. You can then pipe the returned users to the  [Move-CsUser](move-csuser.md) cmdlet, as shown in the following example.
  
    
    

```
Get-CsUser -Filter {UserProperty -eq "UserPropertyValue"} | Move-CsUser -Target sipfed.online.lync.com -Credential $creds -HostedMigrationOverrideUrl <URL>
```

You can also use the -OU parameter to retrieve all users in the specified OU, as shown in the following example.
  
    
    



```
Get-CsUser -OU "cn=hybridusers,cn=contoso.." | Move-CsUser -Target sipfed.online.lync.com -Credentials $creds -HostedMigrationOverrideUrl <URL>
```


## Verify online user settings and features

You can verify that the user was moved successfully in the following ways:
  
    
    

- View the status of the user in the Skype for Business Online Control Panel. The visual indicator for on-premises users and online users is different.
    
  
- Run the following cmdlet:
    
  ```
  Get-CsUser -Identity
  ```


