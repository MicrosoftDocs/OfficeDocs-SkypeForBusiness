---
title: 'Lync Server 2013: Restoring monitoring or archiving data'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Restoring monitoring or archiving data
ms:assetid: 60118526-13bb-4b03-803e-6ffae219d436
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202175(v=OCS.15)
ms:contentKeyID: 51541483
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Restoring monitoring or archiving data in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-18_

Restoring monitoring and archiving data is not required to get Lync Server up and running after a failure. However, if monitoring and archiving data is critical to your organization, you will want to restore the data after you re-create the databases.

The following procedure describes how to use SQL Server Management Studio to restore archiving or monitoring data.

<div>

## To restore monitoring or archiving data from a backup file

1.  Log on to the server that you are restoring as a member of the Administrators group on the local computer or a group with equivalent user rights.

2.  Open SQL Server Management Studio: click **Start**, click **All Programs**, click **Microsoft SQL Server 2012** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.

3.  In **Connect to Server**, connect to the SQL Server instance by providing at least the name of the server and the authentication information.

4.  In **Object Explorer**, right-click **Databases**, and then click **Restore Database**.

5.  Under **Select a page**, click **General**, and then in **To database** select the database name as follows:
    
      - For an Archiving database, select **LcsLog**.
    
      - For a call detail recording (CDR) database, select **LcsCDR**.
    
      - For a Quality of Experience (QoE) database, select **QoEMetrics**.

6.  Click **From device**.

7.  Under **Select the backup sets to restore**, click the backup file, and then click **Restore**.

8.  Under **Select a page**, click **Options**, verify that the data file path and log path are in the correct folder, and then click **OK**.

</div>

<div>

## To make sure that access control lists (ACLs) are correct

1.  Expand **Databases**, expand the archiving or monitoring database, expand **Security**, and then expand **Users**.

2.  Verify that the domain group RTCComponentUniversalServices exists as a user.

3.  If RTCComponentUniversalServices does not exist under **Users**, do the following:
    
    1.  Right-click **Users**, and then click **New User**.
    
    2.  In **Login name**, type the missing group name, RTCComponentUniversalServices.
    
    3.  Under **Database role membership**, select the **ServerRole** permission, and then click **OK**.
    
    <div>
    

    > [!NOTE]  
    > You do not need to restart the archiving or monitoring service.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

