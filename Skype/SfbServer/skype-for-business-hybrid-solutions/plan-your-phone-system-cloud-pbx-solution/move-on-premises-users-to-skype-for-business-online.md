---
title: "Move on-premises users to Skype for Business Online"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 1/27/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- IT_Skype16
- IT_Skype4B_Hybrid
- Strat_SB_Hybrid
ms.custom: 
ms.assetid: 2475674a-f592-4fa8-ae99-f71cbea54dc0
description: "Summary: Information about moving on-premises users to Skype for Business Online."
---

# Move on-premises users to Skype for Business Online
 
**Summary:** Information about moving on-premises users to Skype for Business Online.
  
> [!CAUTION]
> Lync Phone Edition devices MUST be updated to minimum required firmware in your on premises environment PRIOR to moving to Skype for Business Online. 
If you move your users from on-premises to online prior to updating the firmware, users will be unable to connect using their phones. To correct this problem, users must be moved back to the on premises environment to have their phones updated to the minimum firmware. DO NOT ATTEMPT TO UPDATE TO MINIMUM FIRMWARE OR HARD RESET THE PHONE PRIOR TO MOVING THE USER BACK TO YOUR ON PREMISES ENVIRONMENT.
If a hard reset is performed while the device is not at minimum firmware it will default to using PIN Authentication, which is not supported in Skype for Business Online. For more information, please refer to [Getting Phones for Skype for Business Online](https://support.office.com/en-us/article/Getting-phones-for-Skype-for-Business-Online-91f2d947-45fc-4fab-bd8b-2e313531c477?ui=en-US&amp;rs=en-US&amp;ad=US).
  
This is an optional step that is required only if you are moving on-premises users to Skype for Business Online. Before you begin to move users to Skype for Business Online, check that the Skype for Business Online Connector (Windows PowerShell module) is deployed on your Front End Servers. If it isn't, you can download it from [the download center](https://www.microsoft.com/en-us/download/details.aspx?id=39366). Also, to prepare your AD, you'll need to configure Azure AD Connect. The version of AAD Connect you use must be version 1.0.9125.0 or later. If you are using an earlier version of AAD Connect tools or DirSync, please upgrade to the supported version. You can upgrade your current installation and maintain any custom rules you have defined in your environment.
  
You move users using either Skype for Business Server Control Panel or Skype for Business Server Management Shell in your on-premises deployment, but you must have administrator credentials for your Office 365 deployment.
  
## Moving users by using Skype for Business Control Panel

### To move a user to Skype for Business Online

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment that has Skype for Business Server, or at least Skype for Business Server Admin tools installed.
    
2. From the Start menu or desktop shortcut, open the Skype for Business Server Control Panel.
    
    You can also access the Skype for Business Server Control Panel by using the Admin URL if you have configured one.
    
3. In the left navigation bar, click **Users**.
    
4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to enable, and then click **Find**.
    
5. Click the user, then in the **Action** menu, click **Move selected users to Skype for Business Online**.
    
6. On the **Move users to Skype For Business Online** page, read the information and then click **Next**.
    
7. On the next page, if you are not yet signed in to Office 365, click **Sign in to Office 365**, provide your credentials, and click **OK** and **Next**.
    
8. Confirm that the number of users to be moved is correct, and click **Next**.
    
9. On the next page, review the results and click **Close**.
    
## Moving users by using Skype for Business Server Management Shell

To move an on-premises user to your Skype for Business Online tenant, run the following cmdlets in the Skype for Business Server Management Shell, using the administrator credentials for your Microsoft Office 365 tenant. Replace "username@contoso.com" with the information for the user that you want to move.
  
```
$creds=Get-Credential
```

```
Move-CsUser -Identity username@contoso.com -Target sipfed.online.lync.com -Credential $creds -HostedMigrationOverrideUrl <URL>
```

The format of the URL specified for the **HostedMigrationOverrideUrl** parameter must be the URL to the pool where the Hosted Migration service is running, in the following format: _Https://\<Pool FQDN\>/HostedMigration/hostedmigrationService.svc_.
  
You can determine the URL to the Hosted Migration Service by viewing the URL for the Skype for Business Online Admin center for your Office 365 tenant account.
  
> [!NOTE]
> The URL is case sensitive. 
  
### To determine the Hosted Migration Service URL for your Office 365 tenant

1. Login to your Office 365 tenant as an administrator.
    
2. Open the **Skype for Business admin center**.
    
3. With the **Skype for Business admin center** displayed, select and copy the URL in the address bar up to **lync.com**. An example URL looks similar to the following:
    
     `https://webdir0a.online.lync.com/lscp/?language=en-US&amp;tenantID=`
    
4. Replace **webdir** in the URL with **admin**, resulting in the following: 
    
     `https://admin0a.online.lync.com`
    
5. Append the following string to the URL: **/HostedMigration/hostedmigrationService.svc**.
    
    The resulting URL, which is the value of the **HostedMigrationOverrideUrl**, should look like the following:
    
     `https://admin0a.online.lync.com/HostedMigration/hostedmigrationService.svc`
    

