---
title: "Deploy unified contact store in Skype for Business Server "
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d1c9ebd8-af42-42a0-87d9-fc899fbd7c42
description: "Summary: Enable the unified contact store in Skype for Business Server."
---

# Deploy unified contact store in Skype for Business Server
 
**Summary:** Enable the unified contact store in Skype for Business Server.
  
Enabling unified contact store in Skype for Business Server does not require any topology settings. To enable unified contact store for users:
  
- Unified contact store policy is enabled (default is enabled).
    
- Users log in with Skype for Business at least once.
    
After a user's contacts have been migrated, which happens automatically when a user logs in with Skype for Business, the user can access and manage their Skype for Business contacts from Skype for Business, Outlook 2013, or Outlook Web Access. The user does not have to be logged in to Skype for Business to manage their contacts from Outlook or Outlook Web Access.
  
> [!IMPORTANT]
> If a user logs in from Skype for Business after migration, contacts and groups are available and up-to-date, but the user cannot manage (that is, add, delete, move, tag, untag, or modify) those contacts. 
  
## Enable users for unified contact store

When you deploy Skype for Business Server and publish the topology, unified contact store is enabled for all users by default. You do not need to take any additional action to enable unified contact store after you deploy Skype for Business Server. However, you can use the **Set-CsUserServicesPolicy** cmdlet to customize which users have unified contact store available. You can enable this feature globally, by site, by tenant, or by individuals or groups of individuals.
  
### To enable users for unified contact store

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business**, and then click **Skype for Business Server Management Shell**.
    
2. Do any of the following:
    
   - To enable unified contact store globally for all Skype for Business Server users, inter the following cmdlet at the Windows PowerShell command-line interface:
    
   ```
   Set-CsUserServicesPolicy -Identity global -UcsAllowed $True
   ```

   - To enable unified contact store for the users at a specific site, at the prompt, type:
    
   ```
   New-CsUserServicesPolicy -Identity site:<site name> -UcsAllowed $True
   ```

   For example:
    
   ```
   New-CsUserServicesPolicy -Identity site:Redmond -UcsAllowed $True
   ```

   - To enable unified contact store by tenant, at the prompt, type:
    
   ```
   Set-CsUserServicesPolicy -Tenant <tenantId> -UcsAllowed $True
   ```

   For example:
    
   ```
   Set-CsUserServicesPolicy -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308" -UcsAllowed $True
   ```

   - To enable unified contact store for specific users, at the prompt, type:
    
   ```
   New-CsUserServicesPolicy -Identity "<policy name>" -UcsAllowed $True
   Grant-CsUserServicesPolicy -Identity "<user display name>" -PolicyName <"policy name">
   ```

    > [!NOTE]
    > You can also use user alias or SIP URI instead of the user display name. 
  
    For example:
    
   ```
   New-CsUserServicesPolicy -Identity "UCS Enabled Users" -UcsAllowed $True
   Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName "UCS Enabled Users"
   ```

    > [!NOTE]
    > In the preceding example, the first command creates a new per-user policy named UCS Enabled Users with the UcsAllowed flag set to True. The second command assigns the policy to the user with the display name Ken Myer, which means that Ken Myer is now enabled for unified contact store.
  
## Migrate users to unified contact store

A user's contacts are automatically migrated to the Exchange 2013 server when the user:
  
- Has been assigned a user services policy that has UcsAllowed set to True.
    
- Has been provisioned with an Exchange 2013 mailbox and has signed into the mailbox at least once.
    
- Logs in by using a Skype for Business rich client.
    
If the user logs in with a Lync or earlier client, or if the user is not connected to an Exchange 2013 server, the user services policy is ignored and the user's contacts remain in Skype for Business Server.
  
You can determine whether a user's contacts have been migrated by using either of the following methods: 
  
- Check the following registry key on the client computer:
    
    HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\\<SIP URL\>\UCS
    
    If the user's contacts are stored in Exchange 2013, this key contains a value of InUCSMode with a value of 2165.
    
- Run the **Test-CsUnifiedContactStore** cmdlet. At the Skype for Business Server Management Shell command line, type:
    
  ```
  Test-CsUnifiedContactStore -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetFqdn "atl-cs-001.litwareinc.com"
  ```

    If **Test-CsUnifiedContactStore** succeeds, the user's contacts were migrated to unified contact store.
    
## Roll Back Migrated Users

If you need to roll back the unified contact store feature, roll back the contacts only if you move the user back to Exchange 2010 or Lync Server 2010. To roll back, disable the policy for the user, and then run the **Invoke-CsUcsRollback** cmdlet. Just running **Invoke-CsUcsRollback** alone is not enough to ensure permanent rollback, because unified contact store migration will be initiated again if the policy is not disabled. For example, if a user is rolled back because Exchange 2013 is rolled back to Exchange 2010, and then the user's mailbox is moved to Exchange 2013, the unified contact store migration will be initiated again seven days after the rollback, as long as unified contact store is still enabled for the user in the user services policy.
  
The **Move-CsUser** cmdlet automatically rolls back the user's contact store from Exchange 2013 to Skype for Business Server in the following situations:
  
- When users are moved from Skype for Business Server to Microsoft Lync Server 2013 or Lync Server 2010. 
    
- When users are migrated cross premises, such as when a user is moved from Skype for Business Online to Skype for Business Server on-premises, or vice versa.
    
Importing unified contact store data from a backup database can cause unified contact store data and user data to become corrupted if the unified contact store mode changed between the export and the import. For example:
  
- If you export contact lists before the users' contacts are migrated to Exchange 2013 and then, after the migration, import the same data, the unified contact store data and contact lists will be corrupted.
    
- If you export user data after you migrate users to Exchange 2013, roll back the migration, and then for some reason you import the data from after the migration, the unified contact store data and contact lists will be corrupted.
    
> [!IMPORTANT]
> Before you move an Exchange mailbox from Exchange 2013 to Exchange 2010, the Exchange administrator must make sure that the Skype for Business Server administrator has first rolled back the Skype for Business Server user contacts from Exchange 2013 to Skype for Business Server. To roll back unified contact store contacts to Skype for Business Server, see procedure "To roll back unified contact store contacts from Exchange 2013 to Skype for Business Server," later in this section. 
  
 **How to roll back user contacts:** If you use the **Move-CsUser** cmdlet to move users between Skype for Business Server 2015 and Lync Server 2010, you can skip these steps because the **Move-CsUser** cmdlet automatically rolls back unified contact store when it moves users from Skype for Business Server 2015 to Lync Server 2010. **Move-CsUser** does not disable unified contact store policy, so the migration to unified contact store will recur if the user is moved back to Skype for Business Server 2015.
  

