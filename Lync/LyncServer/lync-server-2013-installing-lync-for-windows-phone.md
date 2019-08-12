---
title: 'Lync Server 2013: Installing Lync for Windows Phone'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Installing Lync for Windows Phone
ms:assetid: bf502546-ff69-489f-a92e-a78b58803d53
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690996(v=OCS.15)
ms:contentKeyID: 51541513
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Installing Lync for Windows Phone in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-03_

Lync 2013 for Windows Phone is a user-installable application that is available in the Windows Phone Marketplace.

<div>

## Installing Lync for Windows Mobile

You can instruct your users to install Lync 2013 for Windows Phone on their devices by directing them to the Windows Phone Marketplace at <http://go.microsoft.com/fwlink/p/?linkid=231901>.

</div>

<div>

## If You Use a DNS SRV Record to Publish Exchange Web Services

To enable Exchange integration for Lync clients, some organizations publish the Exchange Web Services URL by using a DNS SRV record. The document "Understanding and Troubleshooting Exchange Integration," available in the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=391095](http://go.microsoft.com/fwlink/?linkid=391095), describes scenarios in which this might be necessary. However, Exchange integration for Windows Phone users will not work in this scenario, because the Windows Phone platform does not support SRV lookups. You will need to instruct Windows Phone users to specify the Exchange Web Services URL instead of allowing the phone to automatically detect the server.

Instruct your users to configure the Lync settings on their Windows Phones as follows:

1.  In Windows Phone, in the Lync settings, select the **Exchange** screen.

2.  Move **Auto-Detect Server** to **Off**.

3.  Tap the empty field and enter the fully qualified domain name (FQDN) or URL for Exchange Web Services.
    
    <div>
    

    > [!NOTE]  
    > You can specify either the fully qualified domain name (FQDN) or the full URL of your Exchange Web Services server. If you specify the FQDN, the protocol (https://) and the Exchange Web Services path (/ews/exchange.asmx) are added automatically. If your Exchange Web Services path is different, you can specify the full URL.

    
    </div>

4.  Close the screen.

</div>

<div>

## Verifying Mobile Client Installation

After you configure the client and sign in successfully, use the following tests to verify that your installation of Lync 2013 is working correctly on your mobile device.

**Search for a contact in the corporate directory**

1.  In the Contacts list, tap **Search** at the bottom.

2.  Search for a contact that exists only in the global address list.

3.  Verify that the contact name appears in the search results.

**Test instant messaging and presence**

1.  In the Contacts list, tap a contact.

2.  In the contact card, tap the **IM** icon.

3.  Verify that an instant messaging (IM) window appears and that you can type and send an IM.

**Test dial-out conferencing**

1.  In Outlook, schedule a Lync meeting.

2.  On the mobile device, open the meeting invitation.

3.  Click the link in the meeting to join.

4.  Answer the call from the conference service and verify that you are connected to meeting audio.

**Test push notifications**

1.  On user A’s mobile device, sign in to Lync with user A’s account.

2.  Open another application on the mobile device.

3.  On a different client, sign in to Lync with user B’s account.

4.  Send an IM from user B to user A.

5.  Verify that the IM notification appears on user A’s mobile device.

</div>

</div>

<span> </span>

</div>

</div>

</div>

