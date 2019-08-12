---
title: 'Lync Server 2013: Add a Survivable Branch Appliance to Active Directory'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Add a Survivable Branch Appliance to Active Directory
ms:assetid: 3e63507c-d60b-40ec-8bbe-586b1d707c3e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425906(v=OCS.15)
ms:contentKeyID: 48183938
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Add a Survivable Branch Appliance to Active Directory in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-23_

If you plan to deploy a Survivable Branch Appliance, you must add the Survivable Branch Appliance to Active Directory Domain Services. Perform this procedure at the central site.

<div>


> [!IMPORTANT]  
> Perform this procedure only if you are deploying a Survivable Branch Appliance. Do not perform it if you are deploying a Survivable Branch Server.



</div>

<div>

## To add an Survivable Branch Appliance to Active Directory Domain Services

1.  Log on to a member server as a member of the Enterprise Admins group.

2.  Click **Start**, click **Administrative Tools**, and then click **Active Directory Users and Computers**.

3.  On the **Actions** menu, click **New** and then click **Computer**.

4.  In the **New Object-Computer** dialog box, type in a name for the Survivable Branch Appliance computer object (for example, BranchOffice1), and then click **Change**.

5.  In the **Select User or Group** dialog box, add the RTCUniversalSBATechnicians group and then click **OK**.
    
    <div>
    

    > [!NOTE]  
    > A member of the RTCUniversalSBATechnicians group at the branch site will add this device to the domain later.

    
    </div>

6.  Click **OK** to save the Survivable Branch Appliance computer object.

7.  Click **Start**, click **Administrative Tools**, and then click **ADSI Edit**.

8.  In **ADSI Edit**, right-click the computer object that you created in the previous steps, and then click **Properties**.

9.  In the attribute list, click **servicePrincipalName**, and then click **Edit**.

10. In the **Value to add** field, type HOST/\<SBA FQDN\> where \<SBA FQDN\> is the fully qualified domain name (FQDN) of your Survivable Branch Appliance. For example, type **HOST/BranchOffice1.contoso.com**.

11. Click **OK** to save the **servicePrincipalName** attribute setting, and then click **OK** to save the computer object properties.

12. In **Active Directory Users and Computers**, right-click **Users**, click **New**, and then click **User**.

13. Enter information into the wizard to create a domain user account for a Survivable Branch Appliance technician.

14. In **Active Directory Users and Computers**, click **Users**, right-click the user object, and then click **Add to a group**.

15. In **Enter the object names to select**, type **RTCUniversalSBATechnicians**, and then click **OK**.

16. Repeat Steps 12-15 for each branch site technician.

**Next step**: [Add branch sites to your topology in Lync Server 2013](lync-server-2013-add-branch-sites-to-your-topology.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

