---
title: 'Lync Server 2013: Verifying schema replication'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Verifying schema replication
ms:assetid: ad01a7cf-aa79-4648-ba5a-a7a09172db36
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412822(v=OCS.15)
ms:contentKeyID: 48185124
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Verifying Active Directory schema replication in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-29_

Before you run forest preparation, manually verify that the schema partition has been replicated.

<div>

## To manually verify schema replication

1.  Log on to a domain controller as a member of the Enterprise Admins group.

2.  Open ADSI Edit by clicking **Start**, clicking **Administrative Tools**, and then clicking **ADSI Edit**.
    
    <div>
    

    > [!TIP]  
    > Alternatively, you can run <STRONG>adsiedit.msc</STRONG> from the command line.

    
    </div>

3.  In the Microsoft Management Console (MMC) tree, if it is not already selected, click **ADSI Edit**.

4.  On the **Action** menu, click **Connect to**.

5.  In the **Connection Settings** dialog box under **Select a well known Naming Context**, select **Schema**, and then click **OK**.

6.  Under the schema container, search for CN=ms-RTC-SIP-SchemaVersion. If this object exists, and the value of the **rangeUpper** attribute is 1150 and the value of the **rangeLower** attribute is 3, then the schema was successfully updated and replicated. If this object does not exist or the values of the **rangeUpper** and **rangeLower** attributes are not as specified, then the schema was not modified or has not replicated.

</div>

<div>

## See Also


[Running Active Directory schema preparation in Lync Server 2013](lync-server-2013-running-schema-preparation.md)  


[Preparing the Active Directory schema in Lync Server 2013](lync-server-2013-preparing-the-active-directory-schema.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

