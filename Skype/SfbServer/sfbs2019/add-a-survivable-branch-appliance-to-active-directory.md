---
title: "Add a Survivable Branch Appliance to Active Directory in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3e63507c-d60b-40ec-8bbe-586b1d707c3e
description: "If you plan to deploy a Survivable Branch Appliance, you must add the Survivable Branch Appliance to Active Directory Domain Services. Perform this procedure at the central site."
---

# Add a Survivable Branch Appliance to Active Directory in Lync Server 2013
[]
If you plan to deploy a Survivable Branch Appliance, you must add the Survivable Branch Appliance to Active Directory Domain Services. Perform this procedure at the central site.
  
> [!IMPORTANT]
> Perform this procedure only if you are deploying a Survivable Branch Appliance. Do not perform it if you are deploying a Survivable Branch Server. 
  
### To add an Survivable Branch Appliance to Active Directory Domain Services

1. Log on to a member server as a member of the Enterprise Admins group.
    
2. Click **Start**, click **Administrative Tools**, and then click **Active Directory Users and Computers**.
    
3. On the **Actions** menu, click **New** and then click **Computer**.
    
4. In the **New Object-Computer** dialog box, type in a name for the Survivable Branch Appliance computer object (for example, BranchOffice1), and then click **Change**.
    
5. In the **Select User or Group** dialog box, add the RTCUniversalSBATechnicians group and then click **OK**.
    
    > [!NOTE]
    > A member of the RTCUniversalSBATechnicians group at the branch site will add this device to the domain later. 
  
6. Click **OK** to save the Survivable Branch Appliance computer object. 
    
7. Click **Start**, click **Administrative Tools**, and then click **ADSI Edit**.
    
8. In **ADSI Edit**, right-click the computer object that you created in the previous steps, and then click **Properties**.
    
9. In the attribute list, click **servicePrincipalName**, and then click **Edit**.
    
10. In the **Value to add** field, type HOST/<SBA FQDN> where <SBA FQDN> is the fully qualified domain name (FQDN) of your Survivable Branch Appliance. For example, type HOST/BranchOffice1.contoso.com.
    
11. Click **OK** to save the **servicePrincipalName** attribute setting, and then click **OK** to save the computer object properties. 
    
12. In **Active Directory Users and Computers**, right-click **Users**, click **New**, and then click **User**.
    
13. Enter information into the wizard to create a domain user account for a Survivable Branch Appliance technician. 
    
14. In **Active Directory Users and Computers**, click **Users**, right-click the user object, and then click **Add to a group**.
    
15. In **Enter the object names to select**, type RTCUniversalSBATechnicians, and then click **OK**.
    
16. Repeat Steps 12-15 for each branch site technician.
    
 **Next step**: [Add branch sites to your topology in Lync Server 2013](add-branch-sites-to-your-topology.md)

