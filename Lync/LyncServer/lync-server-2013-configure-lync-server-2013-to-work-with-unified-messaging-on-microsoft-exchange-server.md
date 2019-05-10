---
title: 'Lync Server 2013: Configure Lync Server 2013 to work with Unified Messaging on Microsoft Exchange Server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure Lync Server 2013 to work with Unified Messaging on Microsoft Exchange Server
ms:assetid: 1098ae4d-f57f-44f3-804e-39889d9fc14e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398193(v=OCS.15)
ms:contentKeyID: 48183430
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure Lync Server 2013 to work with Unified Messaging on Microsoft Exchange Server

</div>

<div id="mainSection">

<div id="mainBody">

_**Topic Last Modified:** 2013-04-03_

This step requires the Exchange UM Integration Utility (OcsUmUtil.exe). This tool is located on the Lync Server 2013 server in the ..\\Program Files\\Common Files\\Microsoft Lync Server 2013\\Support folder.

<div>

## Running the Exchange UM Integration Utility

The Exchange UM Integration Utility must be run from a user account with the following characteristics:

  - Membership in the RTCUniversalServerAdmins and RtcUniversalUserAdmins groups (which includes permission to read Exchange Server Unified Messaging settings).

  - User rights within the domain to create contact objects in the specified organizational unit (OU) container.

When you run the Exchange UM Integration Utility, it performs the following tasks:

  - Creates contact objects for each auto-attendant and subscriber access number to be used by Enterprise Voice users.

  - Verifies that the name of each Enterprise Voice dial plan matches its corresponding unified messaging (UM) dial plan phone context. This matching is necessary only if the UM dial plan is running on a version of Exchange *earlier* than Exchange 2010 Service Pack 1 (SP1).

> [!IMPORTANT]
> Before running the Exchange UM Integration Utility, be sure that you have done the following:
> <ul>
> <li><p>Create one or more Exchange UM dial plans, as described in the Exchange product documentation.</p>
> <p>For Microsoft Exchange Server 2010, see &quot;Create a UM Dial Plan&quot; at <a href="http://go.microsoft.com/fwlink/p/?linkid=186177">http://go.microsoft.com/fwlink/p/?linkId=186177</a>.</p>
> <p>For Microsoft Exchange Server 2007 Service Pack 1 (SP1), see &quot;How to Create a Unified Messaging SIP URI Dial Plan&quot; at <a href="http://go.microsoft.com/fwlink/p/?linkid=185771">http://go.microsoft.com/fwlink/p/?linkId=185771</a>.</p></li>
> <li><p>Create one or more corresponding Lync Server dial plans, as described in <a href="lync-server-2013-create-a-dial-plan.md">Create a dial plan in Lync Server 2013</a>.</p></li>
> <ul><li>If you are using a version of Exchange that is earlier than Microsoft Exchange Server 2010 SP1, you must enter the fully qualified domain name (FQDN) of the corresponding Exchange Unified Messaging (UM) SIP dial plan in the Lync Server 2013 dial plan <STRONG>Simple name</STRONG> field. If you are using Microsoft Exchange Server 2010 SP1 or latest service pack, this dial plan name matching is not necessary.</li></ul>
> <li>Create an auto-attendant and make sure that both the subscriber access number and auto-attendant number are in E.164 format.</li></ul>


<div>

## To run the Exchange UM Integration Utility

1.  On a Front End Server, open a command prompt and type **cd %CommonProgramFiles%\\Microsoft Lync Server 2013\\Support**, and then press ENTER.

2.  Type **OcsUmUtil.exe**, and then press ENTER.

3.  Click **Load Data** to find all trusted Exchange forests.

4.  In the **SIP Dial Plans** list, select a UM SIP dial plan for which you want to create contact objects, and then click **Add**.

5.  In the **Contact** box, accept the default organizational unit, or click **Browse** to start the **OU Picker**. In the **OU Picker** box, you can select an OU and click **OK**, or you can click **Make New OU** to create a new organizational unit under the root or any other OU in the domain (for example, "OU=RTC Special Accounts,DC=fourthcoffee,DC=com"), and then click **OK**.
    
    <div>
    

    > [!NOTE]  
    > The distinguished name (DN) of the OU that you have selected or created is now displayed in the <STRONG>Organizational Unit</STRONG> box.

    
    </div>

6.  In the **Name** box, either accept the default dial plan name or type a new display name for the contact object that you are creating.
    
    <div>
    

    > [!NOTE]  
    > For example, if you are creating a subscriber access contact object, you might simply name it Subscriber Access.

    
    </div>

7.  In the **SIP Address** box, either accept the default SIP address or type a new SIP address.
    
    <div>
    

    > [!NOTE]  
    > If you type a new SIP address, it must begin with <STRONG>SIP:</STRONG> (that is, "SIP:" including the colon).

    
    </div>

8.  In the **Server or Pool** list, select the Standard Edition server or Front End pool in which the contact object is to be enabled.
    
    <div>
    

    > [!NOTE]  
    > Preferably, the pool you select is the same one pool where users enabled for Enterprise Voice and Exchange UM are deployed.

    
    </div>

9.  In the **Phone Number** list, select either **Enter phone number** or **Use this pilot number from Exchange UM** and then enter a phone number.

10. In the **Contact Type** list, select the contact type that you want to create, and then click **OK**.

11. Repeat steps 1 through 10 for additional contact objects that you want to create.
    
    <div>
    

    > [!NOTE]  
    > You should create at least one contact for each auto attendant. If you want external access, you also need a Subscriber Access contact and to specify Direct Inward Dial (DID) numbers.

    
    </div>

</div>

To verify that the contact objects have been created, open Active Directory Users and Computers and select the OU in which the objects were created. The contact objects should appear in the details pane.

</div>

</div>

<span> </span>

</div>

</div>

</div>

