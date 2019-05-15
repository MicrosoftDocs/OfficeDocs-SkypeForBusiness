---
title: "Manage PIN policies for dial-in conferencing in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 459e80bf-5791-49f8-878d-4a5178b3a210
description: "Summary: Learn how to manage PIN policies for dial-in conferencing in Skype for Business Server."
---

# Manage PIN policies for dial-in conferencing in Skype for Business Server
 
**Summary:** Learn how to manage PIN policies for dial-in conferencing in Skype for Business Server.
  
Skype for Business Server users who have Active Directory Domain Services (AD DS) credentials in your organization can join dial-in conferences as authenticated users by using a personal identification number (PIN). PIN policy defines the rules for how dial-in conferencing PINs work.
  
 If you want to use the same PIN policy for your entire organization, you can use the global PIN policy and modify it as needed. The global PIN policy defines the rules for dial-in conferencing PINs at the forest level. You can modify the global PIN policy, but you cannot delete it.
  
You can create a new PIN policy if you want a specific policy to apply to a site or to a certain group of users.
  
PIN policies apply to users from the narrowest scope to the widest scope. If you assign a user-level PIN policy to a user, those settings take precedence. If you do not assign a user policy, the site-level PIN policy applies, if it exists. If no user or site policies apply, global PIN policy provides the default settings.
  
## View information about PIN policies

You can view information about PIN policies by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
### View information about PIN policies by using Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **PIN Policy**.
    
4. On the **PIN Policy** page, click the PIN policy that you want to view, click **Edit**, and then click **Show details**.
    
### View information about PIN policies by using Skype for Business Server Management Shell

To view information about PIN policies, use the **Get-CsPinPolicy** cmdlet. For example, the following command returns information about a single PIN policy with the Identity site:Redmond:
  
```
Get-CsPinPolicy -Identity "site:Redmond"
```

For more information, including a complete syntax description and list of parameters, see [Get-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/get-cspinpolicy?view=skype-ps).
  
## Modify the global PIN policy

You can modify the global PIN policy by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
### Modify the global dial-in conferencing PIN policy by using Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **PIN Policy**.
    
4. On the **PIN Policy** page, click the **Global** policy, click **Edit**, and then click **Show details**.
    
5. In **Edit PIN Policy**, in **Minimum PIN length**, type or select the minimum PIN length that you want to allow. The default minimum length is five digits.
    
6. To be able to specify the maximum number of logon attempts before a user is locked out, select the **Specify maximum logon attempts** check box. If you do not select this option, the maximum number of allowed attempts is automatically determined based on the PIN length. By default, the maximum number of attempts is automatically determined.
    
7. If you selected the **Specify maximum logon attempts** check box, in **Maximum logon attempts**, type or select the maximum number of logon attempts that you want to allow.
    
8. To have PINs expire, select the **Enable PIN expiration** check box. If you do not select this option, PINs will never expire. By default, PINs never expire.
    
9. If you selected the **Enable PIN expiration** check box, in **PIN expires after (days)**, type or select the number of days after which PINs expire.
    
10. In **PIN history count**, type the number of PINs that a user must create before the user can reuse a PIN. By default, users can reuse their PINs.
    
11. To allow common patterns of digits in PINs, such as sequential numbers and repetitive sets of numbers, select the **Allow common patterns** check box. If you do not select this option, only complex patterns of digits are allowed. By default, only complex patterns of digits are allowed.
    
    > [!IMPORTANT]
    > For security reasons, Microsoft recommends that you do not allow common patterns. 
  
12. Click **Commit**.
    
### Modify the global dial-in conferencing PIN policy by using Skype for Business Server Management Shell

To modify the global dial-in conferencing PIN policy, use the **Set-CsPinPolicy** cmdlet.
  
The following command changes the value of the MinPasswordLength for all the PIN policies configured for use in the organization. To do this, the command first calls the **Get-CsPinPolicy** cmdlet without any parameters in order to retrieve a collection of all the existing PIN policies. That collection is then piped to the **Set-CsPinPolicy** cmdlet, which modifies the value of the MinPasswordLength property for each policy in the collection:
  
```
Get-CsPinPolicy | Set-CsPinPolicy -MinPasswordLength 10
```

For more information, including a complete syntax description and list of parameters, see [Set-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/set-cspinpolicy?view=skype-ps).
  
## Create a user or site PIN policy

You can create a user or site PIN policy by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
### Create a user or site PIN policy by using Skype for Business Server Control Panel

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **PIN Policy**.
    
4. On the **PIN Policy** page, click **New**, and then do one of the following:
    
   - To create a user-level policy, click **User policy**. In **New PIN Policy**, in **Name**, type a name that describes the policy.
    
   - To create a site-level policy, click **Site policy**. In the **Select a Site** search field, type all or part of the name of the site for which you want to create a policy. In the list of sites, click the site you want, and then click **OK**.
    
5. In the **Description** field, type a description of the PIN policy.
    
6. In the **Minimum PIN length** field, type or select the minimum PIN length that you want to allow. The default minimum length is five digits.
    
7. To be able to specify the maximum number of logon attempts before a user is locked out, select the **Specify maximum logon attempts** check box. If you do not select this option, the maximum number of allowed attempts is automatically determined based on the PIN length. By default, the maximum number of attempts is automatically determined.
    
8. If you selected the **Specify maximum logon attempts** check box, in **Maximum logon attempts**, type or select the maximum number of logon attempts that you want to allow.
    
9. To have PINs expire, select the **Enable PIN expiration** check box. If you do not select this option, PINs will never expire. By default, PINs never expire.
    
10. If you selected the **Enable PIN expiration** check box, in **PIN expires after (days)**, type or select the number of days after which PINs expire.
    
11. In **PIN history count**, type the number of PINs that a user must create before the user can reuse a PIN. By default, users can reuse their PINs.
    
12. To allow common patterns of digits in PINs, such as sequential numbers and repetitive sets of numbers, select the **Allow common patterns** check box. If you do not select this option, only complex patterns of digits are allowed. By default, only complex patterns of digits are allowed.
    
    > [!IMPORTANT]
    > For security reasons, Microsoft recommends that you do not allow common patterns. 
  
13. Click **Commit**.
    
### Create a user or site PIN policy by using Skype for Business Server Management Shell

To create a user or site PIN policy, use the **New-CsPinPolicy** cmdlet.
  
The following command creates a new PIN policy with the Identity site:Redmond. This command includes just one optional parameter, MinPasswordLength, which is used to set the MinPasswordLength property to 7. All the remaining policy properties will be configured using the default values.
  
```
New-CsPinPolicy -Identity "site:Redmond" -MinPasswordLength 7
```

 For more information, including a complete syntax description and list of parameters, see [New-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/new-cspinpolicy?view=skype-ps).
  
## Modify a user or site PIN policy

You can modify a user or site PIN policy by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
### Modify a user or site PIN policy by using Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **PIN Policy**.
    
4. On the **PIN Policy** page, click the PIN policy that you want to change, click **Edit**, and then click **Show details**.
    
5. In **Edit PIN Policy**, modify any of the policy settings (except for the policy name, which cannot be modified).
    
6. Click **Commit**.
    
### Modify a user or site PIN policy by using Skype for Business Server Management Shell

To modify the dial-in conferencing PIN policy, use the **Set-CsPinPolicy** cmdlet.
  
The following command modifies the PIN policy assigned to the Redmond site. In this case, the command changes the value of the MinPasswordLength property to 10; that means that new PINs will have to contain at least 10 digits:
  
```
Set-CsPinPolicy -Identity site:Redmond -MinPasswordLength 10
```

For more information, including a complete syntax description and list of parameters, see [Set-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/set-cspinpolicy?view=skype-ps).
  
## Delete a user or site PIN policy

You can delete a user or site PIN policy by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
### Delete a user or site PIN policy by using Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **PIN Policy**.
    
4. On the **PIN Policy** page, click the PIN policy that you want to change, click **Edit**, and then click **Delete**.
    
### Delete a user or site PIN policy by using Skype for Business Server Management Shell

To delete a user or site PIN policy, use the **Remove-CsPinPolicy** cmdlet.
  
The following command removes all the PIN policies that have been configured at the site scope. To do this, use the **Get-CsPinPolicy** cmdlet, along with the Filter parameter, to return a collection of all the policies that have an Identity that begins with the characters "site:". This collection is then piped to the **Remove-CsPinPolicy** cmdlet, which deletes each policy in the collection:
  
```
Get-CsPinPolicy -Filter "site:*" | Remove-CsPinPolicy
```

For more information, including a complete syntax description and list of parameters, see [Remove-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/remove-cspinpolicy?view=skype-ps).
  

