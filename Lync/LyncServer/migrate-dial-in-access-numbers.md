---
title: Migrate dial-in access numbers
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migrate dial-in access numbers
ms:assetid: e0dfaed2-64c7-45cb-aaa9-d6117a26625d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721909(v=OCS.15)
ms:contentKeyID: 49733843
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migrate dial-in access numbers

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

Migrating dial-in access numbers from Lync Server 2010 to Lync Server 2013 requires running the **Move-CsApplicationEndpoint** cmdlet to migrate the contact objects. During the Lync Server 2010 and Lync Server 2013 coexistence period, dial-in access numbers that you created in Lync Server 2013 behave similarly to the dial-in access numbers that you create in Lync Server 2010, as described in this section.

Dial-in access numbers that you created in Lync Server 2010 but moved to Lync Server 2013 or that you created in Lync Server 2013 before, during or after migration have the following characteristics:

  - Do not appear on Office Communications Server 2007 R2 meeting invitations and the dial-in access number page.

  - Appear on Lync Server 2010 meeting invitations and the dial-in access number page.

  - Appear on Lync Server 2013 meeting invitations and the dial-in access number page.

  - Cannot be viewed or modified in the Office Communications Server 2007 R2 administrative tool.

  - Can be viewed and modified in the Lync Server 2010 Control Panel and in Lync Server 2010 Management Shell.

  - Can be viewed and modified in the Lync Server 2013 Control Panel and in Lync Server 2013 Management Shell.

  - Can be re-sequenced within the region by using the Set-CsDialinConferencingAccessNumber cmdlet with the Priority parameter.

You must finish migrating dial-in access numbers that point to a Lync Server 2010 pool before you decommission the Lync Server 2010 pool. If you do not complete dial-in access number migration as described in the following procedure, incoming calls to the access numbers will fail.

<div>


> [!IMPORTANT]  
> You must perform this procedure prior to decommissioning the Lync Server 2010 pool.



</div>

<div>


> [!NOTE]  
> We recommend that you move dial-in access numbers when network usage is low, in case there is a short period of service outage.



</div>

**To identify and move dial-in access numbers**

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  To move each dial-in access number to a pool hosted on Lync Server 2013, from the command line run:
    
        Move-CsApplicationEndpoint -Identity <SIP URI of the access number to be moved> -Target <FQDN of the pool to which the access number is moving>

3.  Open Lync Server Control Panel.

4.  In the left navigation bar, click **Conferencing**.

5.  Click the **Dial-in Access Number** tab.

6.  Verify that no dial-in access numbers remain for the Lync Server 2010 pool from which you are migrating.
    
    <div>
    

    > [!NOTE]  
    > When all dial-in access numbers point to the Lync Server 2013 pool, you can then decommission the Lync Server 2010 pool.

    
    </div>

**Verify the dial-in access number migration using Lync Server Control Panel**

1.  From a user account that is assigned to the **CsUserAdministrator** role or the **CsAdministrator** role, log on to any computer in your internal deployment.

2.  Open Lync Server Control Panel.

3.  In the left navigation bar, click **Conferencing**.

4.  Click the **Dial-in Access Number** tab.

5.  Verify all the dial-in access number are migrated to the pool hosted on Lync Server 2013.

**Verify the dial-in access number migration using Lync Server Management Shell**

1.  Open Lync Server Management Shell.

2.  To return all the dial-in conferencing access numbers migrated, from the command line run:
    
        Get-CsDialInConferencingAccessNumber -Filter {Pool -eq "<FQDN of the pool to which the access number is moved>"}

3.  Verify all the dial-in access numbers are migrated to the pool hosted on Lync Server 2013.

</div>

<span> </span>

</div>

</div>

</div>

