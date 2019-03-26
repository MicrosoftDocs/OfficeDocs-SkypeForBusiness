---
title: "Assign a per-user PIN policy in Skype for Business Server"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: d8211c64-0b63-4193-a074-673da7d14287
description: "Summary: Stage AV and OAuth certificates for Skype for Business Server."
---

# Assign a per-user PIN policy in Skype for Business Server

**Summary:** Stage AV and OAuth certificates for Skype for Business Server.
  
The dial-in conferencing personal identification number (PIN) policy is one of the individual settings of a user account that can be configured in the Skype for Business Server Control Panel.
  
Deploying one or more per-user PIN policies is optional. You can also deploy only a global-level PIN policy or site-level PIN policy. If you do deploy per-user policies, you must explicitly assign them to users, groups, or contact object. User rights and permissions regarding the use of PINs for dial-in conferencing automatically default to those defined in the global-level PIN policy when no specific site-level or per-user policy is assigned.
  
After creating at least one per-user PIN policy, use the procedures in this topic to assign the policy that specifies the constraints you want the server to impose on the PINs created by and used by a particular user.
  
### To assign a per-user PIN policy

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Users**.
    
4. Use one of the following methods to locate a user:
    
   - In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account, and then click **Find**.
    
   - If you have a saved query, click the **Open query** icon, use the **Open** dialog box to retrieve the query (a .usf file), and then click **Find**.
    
5. (Optional) Specify additional search criteria to narrow the results:
    
   a. Click **Add Filter**.
    
   b. Enter the user property by typing it or by clicking the arrow in the drop-down list to select the property.
    
   c. In the **Equal to** drop-down list, click the operator (for example, **Equal to** or **Not equal to**).
    
   d. Depending on the user property you selected, enter the criteria you want to use to filter the search results by typing it or by clicking the arrow in the drop-down list.
    
    > [!TIP]
    > To add additional search clauses to your query, click **Add Filter**. 
  
   e. Click **Find**.
    
6. Click a user in the search results, click **Action**, and then click **Assign policies**.
    
    > [!TIP]
    > If you want the same per-user PIN policy to apply to multiple users, select multiple users in the search results, then click **Actions**, and then click **Assign policies**. 
  
7. In **Assign Policies**, under **PIN policy**, do one of the following:
    
    > [!NOTE]
    > Because there are multiple policies that you can configure by using the **Assign Policies** dialog box, **\<Keep as is\>** is selected by default for every policy in the dialog box. Continue using the policy previously assigned to the user by making no changes to this setting.
  
   - Allow Skype for Business Server to automatically choose either the global-level policy or, if defined, the site-level policy.
    
   - Click the name of a per-user PIN policy you previously defined on the **PIN Policy** page.
    
     > [!TIP]
     > To help you decide the policy you want to assign, after you click a policy name, click **View** to view the user rights and permissions defined in the policy.
  
8. When you are finished, click **OK**.
    
## Assigning a Per-User PIN Policy by Using Windows PowerShell Cmdlets

You can assign per-user PIN policies by using Windows PowerShell and the **Grant-CsPinPolicy** cmdlet. You can run this cmdlet from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To assign a per-user PIN policy to a single user

- The following command assigns the per-user PIN policy RedmondPinPolicy to the user Ken Myer.
    
  ```
  Grant-CsPinPolicy -Identity "Ken Myer" -PolicyName "RedmondPinPolicy"
  ```

### To assign a per-user PIN policy to multiple users

- The following command assigns the per-user PIN policy RedmondUsersPinPolicy to all the users who work in the city of Redmond. For details about the LdapFilter parameter used in this command, see [Get-CsUser](https://docs.microsoft.com/powershell/module/skype/get-csuser?view=skype-ps).
    
  ```
  Get-CsUser -LdapFilter "l=Redmond" | Grant-CsPinPolicy -PolicyName "RedmondUsersPinPolicy"
  ```

### To unassign a per-user PIN policy

- The following command unassigns any per-user PIN policy previously assigned to Ken Myer. After the per-user policy is unassigned, Ken Myer will automatically be managed by using the global policy or, if one exists, his local site policy. A site policy takes precedence over the global policy.
    
  ```
  Grant-CsPinPolicy -Identity "Ken Myer" -PolicyName $Null
  ```

For details, see [Grant-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/grant-cspinpolicy?view=skype-ps).
  
## See also

[Create a new PIN policy in Skype for Business Server](create-a-new-pin-policy.md)
