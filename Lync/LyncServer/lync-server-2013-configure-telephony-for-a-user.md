---
title: 'Lync Server 2013: Configure telephony for a user'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure telephony for a user
ms:assetid: 4546432e-c839-4517-a2c5-bc0d4d8c6a03
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520988(v=OCS.15)
ms:contentKeyID: 48183987
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure telephony for a user in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

Telephony settings are some of the individual settings of a user account that can be configured in Lync Server Control Panel for the user (that is, if the individual user has been enabled for Lync Server 2013 and the organization supports telephony).

Lync Server user telephony options include the following:

  - **Audio/video disabled**   The user cannot make calls with audio and video.

  - **PC-to-PC only**   The user can make only PC-to-PC audio or video calls.

  - **Enterprise Voice**   The user can use the Lync Server 2013 infrastructure to route all incoming and outgoing calls. The user can also make PC-to-PC calls.

  - **Remote call control**   The user can use Lync Server 2013 to control the desktop phone, and can also make PC-to-PC calls.

For details about configuring telephony for an organization, see [Configure telephony for a user in Lync Server 2013](lync-server-2013-configure-telephony-for-a-user.md) and [Deploying Enterprise Voice in Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md) in the Deployment documentation.

<div>

## To configure telephony for a specific user account

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Users**.

4.  In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want, and then click **Find**.

5.  In the table, click the user account that you want to modify.

6.  On the **Edit** menu, click **Modify**.

7.  In **Telephony**, do the following:
    
      - To disable audio and video calls for the user, click **Audio/video disabled**.
    
      - To enable PC-to-PC audio communications for the user, but not remote call control or Enterprise Voice, click **PC-to-PC only**. Specify a value for **Line URI** for the telephone that the user uses for PC-to-PC audio communications.
    
      - To route the user's phone calls by using the Lync Server 2010 infrastructure in accordance with the class of service policy, including PC-to-PC audio communication, click **Enterprise Voice**. In **Line URI**, specify the telephone number for Enterprise Voice. In **Dial plan policy** and **Voice policy**, specify the appropriate policies for the user. To specify the normalization rules for translating phone numbers dialed by the user to the E.164 format, select the appropriate location profile in **Location policy**.
    
      - To enable remote call control, which enables users to control their desktop phone line from Lync Server 2013 to make PC-to-PC calls and PC-to-phone calls, click **Remote call control**. In **Line URI**, specify the telephone number for remote call control. The user must have a desktop phone and private branch exchange (PBX) connection for call routing.

</div>

<div>

## See Also


[Modifying user account properties in Lync Server 2013](lync-server-2013-modifying-user-account-properties.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

