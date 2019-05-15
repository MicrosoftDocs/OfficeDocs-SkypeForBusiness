---
title: 'Lync Server 2013: Defining the location policy'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Defining the location policy
ms:assetid: da3cca7f-f6e5-4b6f-90a1-2008e3dd1ebd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398962(v=OCS.15)
ms:contentKeyID: 48185553
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Defining the location policy for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-29_

Each location policy contains the following information:

  - **Emergency Services Enabled**  
    When this value is **Yes**, the client is enabled for E9-1-1. When a client registers, it attempts to acquire a location from the Location Information service and will include the location information as part of an emergency call.

<!-- end list -->

  - **Location Required**  
    This setting is used only when **Emergence Services Enabled** is set to **Yes**.
    
    You can configure the **Location Required** setting to define the client behavior. Setting the value to **No** means that the user will not be prompted for a location. Setting the value to **Yes** means that the user will be prompted for a location, but can dismiss the prompt. Setting the value to **Disclaimer** means that the user will be prompted for a location and also will be shown a disclaimer if they try to dismiss the prompt. In all cases, the user can continue to use the client.
    
    <div>
    

    > [!NOTE]  
    > The disclaimer text will not appear if a user manually entered a location before being enabled for E9-1-1. Updates to the disclaimer text will not be viewed by users that have already viewed the disclaimer.

    
    </div>

<!-- end list -->

  - **Enhanced Emergency Service Disclaimer**  
    This setting specifies the disclaimer that users see if they dismiss the prompt for a location. In Lync Server 2013, you can use location policy to set different disclaimers for different locales or different sets of users.
    
    <div>
    

    > [!NOTE]  
    > This location policy setting differs from Lync Server 2010, where you used the <STRONG>Set-CsEnhancedEmergencyServiceDisclaimer</STRONG> cmdlet to set a global disclaimer for the entire organization. If a global disclaimer already exists, you need to specify that disclaimer in location policy. That is, Lync Server 2013 uses only disclaimers specified in location policy.

    
    </div>

<!-- end list -->

  - **Emergency Dial String**  
    This dial string (less the leading “+”, but including any normalization done by the Lync user’s Dial Plan) signifies that a call is an emergency call. The **Emergency Dial String** causes the client to include location and callback information with the call.
    
    <div>
    

    > [!NOTE]  
    > If your organization does not use an external line access prefix, you do not need to create a corresponding Dial Plan normalization rule that adds a “+” to the 911 string prior to sending the call to Outbound Routing on a Lync pool server; the “+” will be automatically prepended by the Lync client as a result of the location policy. However, if your site uses an external access prefix, you need to add a normalization rule to the applicable Dial Plan policy that strips the external access prefix and adds the “+”. For example, if your location uses an external access prefix of 9 and a user dials 9&nbsp;911 to place an emergency call, the client will use its Dial Plan policy to normalize this to +911 before the dialed number is evaluated by the routes in the caller’s location profile.

    
    </div>

<!-- end list -->

  - **Emergency Dial String Masks**  
    A semicolon-separated list of dial strings that is translated into the specified **Emergency Dial String**. For example, you may want to add 112, which is the emergency service number for most of Europe. A visiting Lync user from Europe may not know that 911 is the U.S. emergency number, but they can dial 112 and get the same result. As with the Emergency Dial String, do not include a “+” before each number, and if you use external line access codes, be sure there are normalization rules in the user’s Dial Plan policy to strip off the access code digit.

<!-- end list -->

  - **PSTN Usage**  
    The name of the PSTN Usage that contains the routing paths that determine which SIP trunk, PSTN gateway, or ELIN gateway emergency calls will go to.
    
    <div>
    

    > [!NOTE]  
    > Only one usage can be assigned to a location policy. This PSTN Usage overrides the PSTN Usages assigned to the user’s voice policy, but applies only to calls placed to the Emergency Dial String or to one of the Emergency Dial String Masks.

    
    </div>

<!-- end list -->

  - **Notification URI**  
    Specifies one or more SIP URIs of the security personnel who receive an instant messaging (IM) notification when an emergency call is placed. Distribution groups are supported.

<!-- end list -->

  - **Conference URI**  
    Specifies a direct inward dialing (DID) number (typically, a security desk number) that should be conferenced in when an emergency call is placed.

<!-- end list -->

  - **Conference Mode**  
    Specifies if the conference URI will be conferenced into the emergency call by using one-way or two-way communication.

<!-- end list -->

  - **Location Refresh Interval**  
    Specifies the amount of time (in hours) between client requests for a location update from the Location Information service. The value can be set to any value between 1 and 12. The default value is 4.

</div>

<span> </span>

</div>

</div>

</div>

