---
title: "Delegating administrative control of Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0f378eff-8ef4-4c60-9fd2-67d7ee259ef8
description: "In Lync Server 2013, administrative tasks are delegated to users by using the new role-based access control (RBAC) feature. When you install Lync Server, a number of RBAC roles are created for you. These roles correspond to universal security groups in Active Directory Domain Services. For example, the RBAC role CsHelpDesk corresponds to the CsHelpDesk group found in the Users container in Active Directory Domain Services. In addition, each RBAC role is associated with a set of Lync Server Windows PowerShell cmdlets. These cmdlets represent the tasks that can be carried out by users who have been assigned the given RBAC role. For example, the CsHelpDesk role has been assigned the Lock-CsClientPin and UnlockCsClientPin cmdlets. That means users who have been assigned the CsHelpDesk role can lock and unlock user PIN numbers. However, the CsHelpDesk role has not been assigned the New-CsVoicePolicy cmdlet. That means that users who have been assigned the CsHelpDesk role cannot create new voice policies."
---

# Delegating administrative control of Lync Server 2013
[]
In Lync Server 2013, administrative tasks are delegated to users by using the new role-based access control (RBAC) feature. When you install Lync Server, a number of RBAC roles are created for you. These roles correspond to universal security groups in Active Directory Domain Services. For example, the RBAC role CsHelpDesk corresponds to the CsHelpDesk group found in the Users container in Active Directory Domain Services. In addition, each RBAC role is associated with a set of Lync Server Windows PowerShell cmdlets. These cmdlets represent the tasks that can be carried out by users who have been assigned the given RBAC role. For example, the CsHelpDesk role has been assigned the Lock-CsClientPin and UnlockCsClientPin cmdlets. That means users who have been assigned the CsHelpDesk role can lock and unlock user PIN numbers. However, the CsHelpDesk role has not been assigned the New-CsVoicePolicy cmdlet. That means that users who have been assigned the CsHelpDesk role cannot create new voice policies.
  
## Viewing Information about RBAC Roles

You can retrieve basic information about your RBAC roles by running the following command from within the Lync Server Management Shell:
  
```
Get-CsAdminRole
```

Keep in mind that the Identity of the RBAC role (for example, CsVoiceAdministrator) has a direct mapping to a security group found in the Users container in Active Directory Domain Services.
  
To view a list of the cmdlets that have been assigned to a role, use a command similar to this:
  
```
Get-CsAdminRole -Identity "CsHelpDesk" | Select-Object -ExpandProperty Cmdlets
```

## Assigning an RBAC Role to a User

To assign an RBAC role to a user, you must add that user to the appropriate Active Directory security group. For example, to assign the CsLocationAdministrator role to a user, you must add that user to the CsLocationAdministrator group. That can be done by carrying out the following procedure:
  
### To assign a user to a security group

1. Using an account that has permission to modify the membership of an Active Directory group, log on to a computer where Active Directory Users and Computers has been installed.
    
2. Click **Start**, click **All Programs**, click **Administrative Tools**, and then click **Active Directory Users and Computers**.
    
3. In Active Directory Users and Computers, expand the name of your domain and click the **Users** container. 
    
4. Right-click the security group **CsLocationAdministrator**, and then click **Properties**.
    
5. In the **Properties** dialog box, on the **Members** tab, click **Add**.
    
6. In the **Select Users, Computers, Contacts, or Groups** dialog box, type the user name or display name of the user to be added to the group (for example, Ken Myer) in the **Enter the object names to select** box and then click **OK**.
    
7. In the **Properties** dialog box, click **OK**.
    
To verify that the RBAC role has been assigned, use the [Get-CsAdminRoleAssignment](get-csadminroleassignment.md) cmdlet, passing the cmdlet the SamAccountName (Active Directory logon name) of the user. For example, run this command from within the Lync Server Management Shell: 
  
```
Get-CsAdminRoleAssignment  -Identity "kenmyer"
```


