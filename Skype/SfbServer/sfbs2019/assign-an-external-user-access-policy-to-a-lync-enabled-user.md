---
title: "Assign an external user access policy to a Lync enabled user in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 736fcaad-9f95-4896-b767-e199d86a00a4
description: "If a user has been enabled for Lync Server, you can configure SIP federation, XMPP federation, remote user access, and public instant messaging (IM) connectivity in the Lync Server Control Panel by applying the appropriate policies to specific users. For example, if you created a policy to support remote user access, you must apply it to the user before the user can connect to Lync Server from a remote location and collaborate with internal users from the remote location."
---

# Assign an external user access policy to a Lync enabled user in Lync Server 2013
[]
If a user has been enabled for Lync Server, you can configure SIP federation, XMPP federation, remote user access, and public instant messaging (IM) connectivity in the Lync Server Control Panel by applying the appropriate policies to specific users. For example, if you created a policy to support remote user access, you must apply it to the user before the user can connect to Lync Server from a remote location and collaborate with internal users from the remote location.
  
> [!NOTE]
> To support external user access, you must enable support for each type of external user access you want to support, and configure the appropriate policies and other options to control its use. For details, see [Configuring support for external user access in Lync Server 2013](configuring-support-for-external-user-access.md) in the Deployment documentation or [Managing federation and external access to Lync Server 2013](managing-federation-and-external-access-to-lync-server-2013.md) in the Operations documentation. 
  
Use the procedure in this topic to apply a previously created external user access policy to one or more user accounts.
  
### To apply an external user policy to a user account

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Users**, and then search on the user account that you want to configure. 
    
4. In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.
    
5. In **Edit Lync Server User** under **External access policy**, select the user policy that you want to apply. 
    
    > [!NOTE]
    > The **\<Automatic\>** settings apply the default server or global policy settings. 
  
## Assigning Per-User External Access Policies by Using Windows PowerShell Cmdlets

Per-user external access policies can be assigned by using Windows PowerShell and the Grant-CsExternalAccessPolicy cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To assign a per-user external access policy to a single user

- This command assigns the per-user external access policy RedmondExternalAccessPolicy to the user Ken Myer.
    
  ```
  Grant-CsExternalAccessPolicy -Identity "Ken Myer" -PolicyName "RedmondExternalAccessPolicy"
  ```

### To assign a per-user external access policy to multiple users

- This command assigns the per-user external access policy USAExternalAccessPolicy to all the users who have accounts in the UnitedStates OU in Active Directory. For more information on the OU parameter used in this command, see the documentation for the [Get-CsUser](get-csuser.md) cmdlet. 
    
  ```
  Get-CsUser -OU "ou=UnitedStates,dc=litwareinc,dc=com" | Grant-CsExternalAccessPolicy -PolicyName "USAExternalAccessPolicy"
  
  ```

### To unassign a per-user external access policy

- This command unassigns any per-user external access policy previously assigned to Ken Myer. After the per-user policy is unassigned, Ken Myer will automatically be managed by using the global policy or, if one exists, his local site policy. A site policy takes precedence over the global policy.
    
  ```
  Grant-CsExternalAccessPolicy -Identity "Ken Myer" -PolicyName $Null
  ```

For more information, see the help topic for the [Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md) cmdlet. 
  

