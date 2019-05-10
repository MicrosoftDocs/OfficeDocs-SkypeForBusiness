---
title: 'Lync Server 2013: Roll back migrated users'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Roll back migrated users
ms:assetid: bfabaf0b-9a42-4057-b729-a7ab9eee8c72
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205224(v=OCS.15)
ms:contentKeyID: 48185286
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Roll back migrated users in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-07_

If you need to roll back the unified contact store feature, roll back the contacts only if you move the user back to Exchange 2010 or Lync Server 2010. To roll back, disable the policy for the user, and then run the **Invoke-CsUcsRollback** cmdlet. Just running **Invoke-CsUcsRollback** alone is not enough to ensure permanent rollback, because unified contact store migration will be initiated again if the policy is not disabled. For example, if a user is rolled back because Exchange 2013 is rolled back to Exchange 2010, and then the user’s mailbox is moved to Exchange 2013, the unified contact store migration will be initiated again seven days after the rollback, as long as unified contact store is still enabled for the user in the user services policy.

<div>


> [!IMPORTANT]  
> The <STRONG>Move-CsUser</STRONG> cmdlet automatically rolls back the user's contact store from Exchange 2013 to Lync Server 2013 in the following situations: 
> <UL>
> <LI>
> <P>When users are moved from Lync Server 2013 to Lync Server 2010.</P>
> <LI>
> <P>When users are migrated cross premises, such as when a user is moved from Lync Online to Lync Server 2013 on-premises, or vice versa.</P></LI></UL>



</div>

<div>


> [!IMPORTANT]  
> Importing unified contact store data from a backup database can cause unified contact store data and user data to become corrupted if the unified contact store mode changed between the export and the import. For example: 
> <UL>
> <LI>
> <P>If you export contact lists before the users' contacts are migrated to Exchange 2013 and then, after the migration, import the same data, the unified contact store data and contact lists will be corrupted.</P>
> <LI>
> <P>If you export userdata after you migrate users to Exchange 2013, roll back the migration, and then for some reason you import the data from after the migration, the unified contact store data and contact lists will be corrupted.</P></LI></UL>



</div>

<div>


> [!IMPORTANT]  
> Before you move an Exchange mailbox from Exchange 2013 to Exchange 2010, the Exchange administrator must make sure that the Lync Server administrator has first rolled back the Lync Server user contacts from Exchange 2013 to Lync Server. To roll back unified contact store contacts to Lync Server, see procedure "To roll back unified contact store contacts from Exchange 2013 to Lync Server 2013," later in this section.



</div>

The following procedure describes how to roll back user contacts. If you use the **Move-CsUser** cmdlet to move users between Lync Server 2013 and Lync Server 2010, you can skip these steps because the **Move-CsUser** cmdlet automatically rolls back unifed contact store when it moves users from Lync Server 2013 to Lync Server 2010. **Move-CsUser** does not disable unified contact store policy, so the migration to unified contact store will recur if the user is moved back to Lync Server 2013.

<div>

## To roll back user contacts from Lync Server 2013 to Lync Server 2010

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Disable unified contact store for the users to be rolled back so that they will not be remigrated after rollback. (Perform this step only if you want to make sure that users will not remigrate in the future.) To disable unified contact store for individual users, at the command line, type:
    
        Set-CsUserServicesPolicy -Identity "<policy name>" -UcsAllowed $False
    
    For example:
    
        Set-CsUserServicesPolicy -Identity "UCS Enabled Users" -UcsAllowed $False

3.  Before moving a user from Lync Server 2013 to Lync Server 2010, roll back the Buddy List for the specified users on Lync Server.
    
    <div>
    

    > [!IMPORTANT]  
    > If this step is omitted, the Buddy List will be lost.

    
    </div>

4.  Roll back the specified users. At the command line, type:
    
        Invoke-CsUcsRollback -Identity "<user display name>"
    
    For example:
    
        Invoke-CsUcsRollback -Identity "Ken Myer"
    
    <div>
    

    > [!IMPORTANT]  
    > We do not recommend using the –Force option to force the rollback. If you use this option, the users' contacts will be lost.

    
    </div>

</div>

<div>

## To roll back unified contact store contacts from Exchange 2013 to Lync Server 2013

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Disable unified contact store for the users to be rolled back so that they will not be remigrated after rollback. To disable unified contact store for individual users, at the command line, type:
    
        Set-CsUserServicesPolicy -Identity "<policy name>" -UcsAllowed $False
    
    For example:
    
        Set-CsUserServicesPolicy -Identity "UCS Enabled Users" -UcsAllowed $False

3.  Roll back the specified users. At the command line, type:
    
        Invoke-CsUcsRollback -Identity "<user display name>"
    
    For example:
    
        Invoke-CsUcsRollback -Identity "Ken Myer"
    
    <div>
    

    > [!IMPORTANT]  
    > You must first roll back the Lync Server user, and then move the Exchange 2013 mailbox. The Exchange administrator is blocked from rolling back Exchange until the Lync Server rollback is complete. We do not recommend using the –Force option to force the rollback. If you use this option, the users' contacts will be lost.

    
    </div>

4.  After you roll back the user to Lync Server, the Exchange administrator can roll back the Exchange user from Exchange 2013 to Exchange 2010.

</div>

</div>

<span> </span>

</div>

</div>

</div>

