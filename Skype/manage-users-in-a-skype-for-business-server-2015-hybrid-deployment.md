---
title: Manage users in a Skype for Business Server 2015 hybrid deployment
ms.prod: SKYPEFORBUSINESS
ms.assetid: 6924ed7b-30a9-4be7-b952-90655625f2c8
---


# Manage users in a Skype for Business Server 2015 hybrid deployment
[] **Summary:** Learn how to manage user settings and policies for users migrated to Skype for Business Online.
You can manage user settings and policies for users migrated to Skype for Business Online by using the User Management features available in the Microsoft Office 365 online portal. You must sign in by using your tenant administrator account to perform administration tasks.
  
    
    


## Move users back to on-premises


> [!IMPORTANT]
> This section applies only to users that were created and enabled for an on-premises deployment and then moved from an on-premises deployment to online. If you want to move users that were created online (and not ever enabled for an on-premises deployment) see,  [Configure hybrid from online to on-premises in Skype for Business Server 2015](configure-hybrid-from-online-to-on-premises-in-skype-for-business-server-2015.md). 
  
    
    


- Run the following cmdlets to move a user from Skype for Business Online back to on-premises, replacing the value for the **Identity** and **Target** parameters to correct values for your environment:
    
  ```
  
$cred=Get-Credential
  ```


  ```
  Move-CsUser -Identity username@contoso.com -Target localpool.contoso.com -Credential $cred -HostedMigrationOverrideUrl <URL>
  ```

The format of the URL specified for the **HostedMigrationOverrideUrl** parameter must be the URL to the pool where the Hosted Migration service is running, in the following format:
  
    
    
 _Https://<Pool FQDN>/HostedMigration/hostedmigrationService.svc_. You can determine the URL to the Hosted Migration Service by viewing the URL for the Lync Online Control Panel for your Office 365 tenant account.
  
    
    

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
    
  

