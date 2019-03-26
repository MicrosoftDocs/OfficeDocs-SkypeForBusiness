---
title: 'Lync Server 2013: Caller ID presentation'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Caller ID presentation
ms:assetid: 6a643961-a0a1-41d1-96ba-6c428a89d82e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204980(v=OCS.15)
ms:contentKeyID: 48184425
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Caller ID presentation in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

With Lync Server 2010, the called party’s phone number (that is, the phone number called) can be translated from E.164 format to the local dialing format that is required by the trunk peer (that is, the associated gateway, private branch exchange (PBX), or SIP trunk). To do this, you must define one or more translation rules to translate the Request URI before routing it to the trunk peer.

Lync Server 2013 introduces the option to also translate the calling party’s phone number (that is, the phone number that the caller is calling from) from E.164 format to the local dialing format that is required by the trunk peer. For example, you can write a translation rule to remove +44 from the beginning of a dial string and replace it with 0144.

<div id="sectionSection0" class="section">

**To configure Caller ID by using Lync Server Control Panel**

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Voice Routing**, and then click **Trunk Configuration**.

4.  On the **Trunk Configuration** page, double-click an existing trunk (for example, the **Global** trunk) to display the **Edit Trunk Configuration** dialog box.

5.  To configure caller ID presentation:
    
      - To choose one or more rules from a list of all translation rules available in your Enterprise Voice deployment, click **Select**. In **Calling number translation rules**, click the rules that you want to associate with the trunk, and then click **OK**.
    
      - To define a new translation rule and associate it with the trunk, click **New**. For details about defining a new rule, see [Defining translation rules in Lync Server 2013](lync-server-2013-defining-translation-rules.md) in the Deployment documentation.
    
      - To edit a translation rule that is already associated with the trunk, click the rule name, and then click **Show details**. For details, see [Defining translation rules in Lync Server 2013](lync-server-2013-defining-translation-rules.md) in the Deployment documentation.
    
      - To copy an existing translation rule to use as a starting point for defining a new rule, click the rule name and click **Copy**, and then click **Paste**. For details, see [Defining translation rules in Lync Server 2013](lync-server-2013-defining-translation-rules.md).
    
      - To remove a translation rule from the trunk, highlight the rule name and click **Remove**.
    
    <div>
    

    > [!WARNING]  
    > Do not associate translation rules with a trunk if you have configured translation rules on the associated trunk peer, because the two rules might conflict.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

