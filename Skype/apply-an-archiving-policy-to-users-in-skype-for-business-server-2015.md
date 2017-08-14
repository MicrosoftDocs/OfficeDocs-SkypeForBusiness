---
title: Apply an archiving policy to users in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: bebd45d1-93c3-4e80-8933-755b699b2209
---


# Apply an archiving policy to users in Skype for Business Server 2015
[] **Summary:** Learn how to assign an archiving policy to users in Skype for Business Server 2015.
If you have created one or more user policies for archiving for users homed on Skype for Business Server 2015, you can implement archiving support for specific users by applying the appropriate policies to those users or user groups. For example, if you create a policy to support archiving of internal communications, you can apply it to at least one user or user group to support archiving of the user's Skype for Business Server 2015 communications.
  
    
    


> [!NOTE]
> If you enabled Microsoft Exchange integration for your deployment, Exchange In-Place Hold policies control whether archiving is enabled for the users who are homed on Exchange and have their mailboxes put on In-Place Hold. For details, see  [Plan for archiving in Skype for Business Server 2015](plan-for-archiving-in-skype-for-business-server-2015.md) and [Configure integration with Exchange storage for Skype for Business Server 2015](configure-integration-with-exchange-storage-for-skype-for-business-server-2015.md). 
  
    
    


## Apply a user policy by using the Control Panel

To apply a user policy by using the Control Panel:
  
    
    

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment. 
    
  
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
  
3. In the left navigation bar, click **Users**, and then search for the user account that you want to configure. 
    
  
4. In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.
    
  
5. In **Edit Lync Server User** under **Archiving policy**, select the archiving user policy that you want to apply.
    
    > [!NOTE]
      > The **<Automatic>** settings apply the default server installation settings. These settings are applied automatically by the server.
6. Click **Commit**.
    
  

## Apply a user policy by using Windows PowerShell

You can also apply a user policy by using the Windows PowerShell **Grant-CsArchivingPolicy** cmdlet.
  
    
    
The following command assigns the per-user archiving policy RedmondArchivingPolicy to the user Ken Myer.
  
    
    



```

Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName "RedmondArchivingPolicy"
```

This command assigns the per-user archiving policy RedmondArchivingPolicy to all users who have accounts homed on the Registrar pool atl-cs-001.contoso.com. For details about the Filter parameter used in this command, see the  [Get-CsUser](get-csuser.md) cmdlet documentation.
  
    
    



```
Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.contoso.com"} | Grant-CsArchivingPolicy -PolicyName "RedmondArchivingPolicy"

```

The following command removes any per-user archiving policy previously assigned to Ken Myer. After the per-user policy is removed, Ken Myer will automatically be managed by using the global policy or, if one exists, his local site policy. A site policy takes precedence over the global policy.
  
    
    



```

Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName $Null
```

For details, see the  [Grant-CsArchivingPolicy](grant-csarchivingpolicy.md) cmdlet documentation.
  
    
    

