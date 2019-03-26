---
title: 'Lync Server 2013: Configure user account settings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure user account settings
ms:assetid: b7c74ecc-b924-4efc-8a56-3a5f94a9ef13
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412896(v=OCS.15)
ms:contentKeyID: 48185200
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure user account settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-05_

Dial-in users enter their phone number or extension and a PIN to join conferences as authenticated users. The telephony **Line URI** specified on Lync Server user accounts is required for authentication.

The procedure in this topic describes how to assign a **Line URI** for a single user account. If you need to assign a **Line URI** for multiple user accounts, you can create a script that uses the **Set-CsUser** cmdlet. For details about using a sample script to assign **Line URI** to multiple user accounts, see "Assign Line URIs to Multiple Users" at [http://go.microsoft.com/fwlink/p/?linkId=196945](http://go.microsoft.com/fwlink/p/?linkid=196945).

<div>

## To configure user account settings

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **Cs-UserAdministrator** or **CsAdministrator** role.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Users**.

4.  In the search field, type the name of the user you want to configure for dial-in conferencing or click **Add filter** to specify search fields, and then click **Find**.

5.  Double-click the user name to open the **Edit Lync Server User** dialog box.

6.  Under **Telephony**, in the **Line URI** field, type a unique, normalized phone number (for example, tel:+14255550200).
    
    <div>
    

    > [!NOTE]  
    > You can specify <STRONG>Line URI</STRONG> only if <STRONG>Telephony</STRONG> is set to <STRONG>PC-to-PC only</STRONG>, <STRONG>Enterprise Voice</STRONG>, <STRONG>Remote call control</STRONG> or <STRONG>Remote call control only</STRONG>.

    
    </div>

7.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

