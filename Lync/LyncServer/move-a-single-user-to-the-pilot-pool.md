---
title: Move a single user to the pilot pool
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Move a single user to the pilot pool
ms:assetid: e9de81a8-40dd-4446-81e7-a2b810eaea50
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205401(v=OCS.15)
ms:contentKeyID: 48185905
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Move a single user to the pilot pool

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-26_

You can move a user from your Lync Server 2010 pool to your Lync Server 2013 pilot pool using Lync Server 2013 Control Panel or Lync Server 2013 Management Shell. In the example below, in the Registrar pool column, **pool01.contoso.net** is the Lync Server 2010 pool, and all six of these users are connected to this pool. Use the following procedures to move a user to your Lync Server 2013 pool using Lync Server 2013 Control Panel and Lync Server Management Shell.

<div>

## To move a user by using the Lync Server 2013 Control Panel

**List of users in the Lync Server 2013 Control Panel**

![Lync Server Control Panel, Move User dialog](images/JJ721870.a2bce284-0392-4db3-9bb2-9f12699738e7(OCS.15).jpg "Lync Server Control Panel, Move User dialog")

1.  Log on to the Front End Server with an account that is a member of the RTCUniversalServerAdmins group or a member of the CsAdministrator or CsUserAdministrator administrative role.

2.  Open **Lync Server Control Panel**.

3.  Click **Users**, click Search, and then click **Find**.

4.  Select a user that you want to move to the Lync Server 2013 pool. In this example, we will move user Sara Davis.

5.  On the **Action** menu, select **Move selected users to pool**.

6.  From the drop-down list, select the Lync Server 2013 pool.

7.  Click **Action** and then click **Move selected users to pool**. Click **OK**.
    
    ![Move Users, destination registrar pool dialog box](images/JJ205401.8a375003-dc00-4541-b578-4d88f2010601(OCS.15).png "Move Users, destination registrar pool dialog box")  

8.  Verify that the **Registrar pool** column for the user now contains the Lync Server 2013 pool, which indicates that the user has been successfully moved.

</div>

<div>

## To move a user by using the Lync Server 2013 Management Shell

1.  Open the Lync Server Management Shell.

2.  At the command line, type the following:
    
        Move-CsUser -Identity "David Pelton" -Target "pool02.contoso.net"

3.  Next, at the command line, type the following:
    
        Get-CsUser -Identity "David Pelton"

4.  The **RegistrarPool** identity now points to the Lync Server 2013 pool. The presence of this identity confirms that the user has been successfully moved.
    
    ![Output from Get-CsUser cmdlet with Identity filter](images/JJ205401.bc5d4672-8068-4475-b882-dbd305c801a9(OCS.15).jpg "Output from Get-CsUser cmdlet with Identity filter")  
    
    <div>
    

    > [!NOTE]  
    > For details about the <STRONG>Get-CsUser</STRONG> cmdlet, run: <STRONG>Get-Help Get-CsUser –Detailed</STRONG>

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

