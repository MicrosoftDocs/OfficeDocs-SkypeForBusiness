---
title: 'Lync Server 2013: Defining your mobility requirements'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Defining your mobility requirements
ms:assetid: b7608335-cdeb-4aae-8e4b-d80c55f0d62b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690039(v=OCS.15)
ms:contentKeyID: 48185226
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Defining your mobility requirements for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-14_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

During the planning phase for the Lync Server 2013 mobility feature, when you are using Lync 2010 Mobile and Lync 2013 Mobile clients, you make decisions that determine your deployment steps.

Here are the decisions that you must consider:

  - **Do you want to use automatic discovery for Lync mobile clients?**
    
    If you want to support automatic discovery, you need to create new internal and external Domain Name System (DNS) records, add subject alternative names to certificates on the Front End Servers, Directors, and reverse proxy, and modify the existing publishing rules on the reverse proxy. For details, see [Technical requirements for mobility in Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md). With automatic discovery, users can automatically locate Lync Server 2013 Web Services from anywhere inside or outside the corporate network, without entering URLs in their mobile device settings.
    
    If you use manual settings instead of automatic discovery, mobile users need to manually enter the following URLs in their mobile devices:
    
      - https://\<ExtPoolFQDN\>/Autodiscover/autodiscoverservice.svc/Root for external access
    
      - https://\<IntPoolFQDN\>/AutoDiscover/ autodiscoverservice.svc/Root for internal access
    
    We strongly recommend using automatic discovery. The primary use of manual settings is for troubleshooting.

  - **If you decide to support automatic discovery, are you willing to update certificates on the reverse proxy with subject alternative names for each SIP domain?**
    
    If you have many SIP domains, updating public certificates on the reverse proxy can become very expensive. If this is the case, you can choose to implement automatic discovery so that the initial Autodiscover Service request uses HTTP on port 80, instead of using HTTPS on port 443. However, this is not the recommended approach. If you decide to choose this alternative, you do not need to update the certificates on the reverse proxy, but you need to create a web publishing rule for HTTP on port 80. For more details, see [Technical requirements for mobility in Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md).

  - **Do you want to support Lync mobile clients both internal and external to the corporate network, or support clients only inside the corporate network?**
    
    If you want to support mobile clients internal and external to your network, mobile devices can access mobility features from any location. The default configuration is to support clients both internal and external to the corporate network.
    
    Although the default configuration enables mobile client traffic to go through the external site, you can restrict mobile client traffic to the internal corporate network. When you restrict the traffic to the internal network, users can use Lync mobile applications on their mobile devices only when they are inside the network.
    
    For deployments that support mobility using the Mcx mobility service and Lync 2010 Mobile, you run the **Set-CsMcxConfiguration** cmdlet. To set mobility for internal use only, you would use a command similar to the following:
    
        Set-CsMcxConfiguration -Identity site:Redmond -ExposedWebURL Internal
    
    <div>
    

    > [!NOTE]  
    > There are no additional configurations required for UCWA. UCWA does not have an equivalent internal-only configuration.

    
    </div>
    
    <div>
    

    > [!IMPORTANT]  
    > If you are using a Lync Server 2013&nbsp;Front End Server or Front End pools and <STRONG>you do not have</STRONG> any Lync Server 2010&nbsp;Front End Servers or Front End pools, <STRONG>there is no requirement for cookie-based persistence</STRONG>. If you need to retain any Lync Server 2010&nbsp;Front End Servers or Front End pools, the same rules still apply as in Lync Server 2010 for cookie-based persistence.

    
    </div>

  - **Do you want to support push notifications for Apple iOS devices and Windows Phones?**
    
    If you support push notifications, supported Apple iOS devices and Windows Phones receive a notification of events that occur when the mobile application is inactive. You must configure your Edge Server to have a federation relationship with the cloud-based Lync Server Push Notification Service, which is located in the Lync Online datacenter, and run a cmdlet to enable push notifications.
    
    If you want to support push notifications over your Wi-Fi network, in addition to supporting push notifications over the mobile device providers' 3G or data networks, you must open port 5223 outbound on your enterprise Wi-Fi network. Supporting push notifications over the Wi-Fi network supports mobile devices that use only Wi-Fi and mobile devices that have poor indoor reception.
    
    <div>
    

    > [!IMPORTANT]  
    > Opening port TCP 5223 is required only when supporting Apple devices running the Lync 2010 Mobile client.

    
    </div>
    
    If you do not support push notifications, users of Apple mobile devices and Windows Phones will not find out about events—such as instant message invitations or missed messages—that occur when the mobile application is inactive.
    
    <div>
    

    > [!NOTE]  
    > Lync 2013 Mobile clients on Apple devices do not require push notification. The Lync 2013 Mobile clients on Windows Phone use push notification. Planning for push notification and the push notification clearinghouse remain the same for Lync Mobile on Windows Phone and Apple devices that are not able to run the Lync 2013 Mobile client.

    
    </div>

  - **Do you want all users to have access to mobility features, or do you want to be able to specify which users have access to these features?**
    
    The table describes features available to users in Lync Server 2013. The defaults allow Call via Work, allow Voice over IP (VoIP), and enable Mobility. Here is the full set of available options:
    
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Feature/Parameter Name/Scope (Policy parameter names may not be the same)</th>
    <th>Description</th>
    <th>Introduced</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Enable Mobility</p>
    <p>Parameter Name : <code>EnableMobility</code></p>
    <p>Scope: Global/Site/User</p></td>
    <td><p>Administrative setting to control users in a given scope that have the Lync Mobile installed, If the policy is set to False, the user would not be able to sign into the client.</p>
    <p>The default setting is True.</p></td>
    <td><p>Cumulative Update for Lync Server 2010: November 2011</p></td>
    </tr>
    <tr class="even">
    <td><p>Enable Outside Voice</p>
    <p>Parameter Name : <code>EnableOutsideVoice</code></p>
    <p>Scope: Global/Site/User</p></td>
    <td><p>Controls a user’s ability to use Call Via Work, a feature that enables users to make and receive calls by using their work number instead of their mobile number. If set to False, the user will not be able to make or receive calls by using their work number from their mobile device.</p>
    <p>The default setting is True</p></td>
    <td><p>Cumulative Update for Lync Server 2010: November 2011</p></td>
    </tr>
    <tr class="odd">
    <td><p>Enable IP Audio and Video</p>
    <p>Parameter Name : <code>EnableIPAudioVideo</code></p>
    <p>Scope: Global/Site/User</p></td>
    <td><p>Controls whether a user can use VoIP to make or receive voice or video calls on their mobile device. If set to False, the user will not be able to make or receive VoIP or video calls on their device.</p>
    <p>The default setting is True.</p></td>
    <td><p>Microsoft Lync Server 2013</p></td>
    </tr>
    <tr class="even">
    <td><p>Require WiFi for IP Audio</p>
    <p>Parameter Name : <code>RequireWiFiForIPAudio</code></p>
    <p>Scope: Global/Site/User</p></td>
    <td><p>This setting defines whether the client will be required to make and receive calls over VoIP on WiFi instead of the cellular data network. If set to True, the user can make and receive VoIP calls only when connected to a WiFi network.</p>
    <p>The default setting is False.</p></td>
    <td><p>Microsoft Lync Server 2013</p></td>
    </tr>
    <tr class="odd">
    <td><p>Require WiFi for IP Video</p>
    <p>Parameter Name : <code>RequireWiFiForIPVideo</code></p>
    <p>Scope: Global/Site/User</p></td>
    <td><p>This setting defines whether the client will be required to make and receive video calls on Wi-Fi instead of on the cellular data network. If set to True, the user can make and receive video calls only when connected to a Wi-Fi network.</p>
    <p>The default setting is False.</p></td>
    <td><p>Microsoft Lync Server 2013</p></td>
    </tr>
    </tbody>
    </table>
    
    For a description of the policy settings that you can configure, and how to manage the policies, see [New-CsMobilityPolicy](https://docs.microsoft.com/powershell/module/skype/New-CsMobilityPolicy), [Set-CsMobilityPolicy](https://docs.microsoft.com/powershell/module/skype/Set-CsMobilityPolicy), [Get-CsMobilityPolicy](https://docs.microsoft.com/powershell/module/skype/Get-CsMobilityPolicy), [Grant-CsMobilityPolicy](https://docs.microsoft.com/powershell/module/skype/Grant-CsMobilityPolicy) and [Remove-CsMobilityPolicy](https://docs.microsoft.com/powershell/module/skype/Remove-CsMobilityPolicy).

  - **Do you want users who are not enabled for Enterprise Voice to be able to use Click to Join to join conferences?**
    
    For users to have access to mobility features and Call via Work, they must be enabled for Enterprise Voice. However, users who are not enabled for Enterprise Voice can join conferences by clicking the link on their mobile device, if they have an appropriate voice policy assigned to them. You can either assign a specific voice policy to these users or make sure that a global policy or site-level policy exists that applies to them. The voice policy that you assign must have public switched telephone network (PSTN) usage records and routes that define the areas to which users can dial out to join a conference. For details about setting voice policy, PSTN usage records, and routes, see [Configuring voice policies, PSTN usage records, and voice routes in Lync Server 2013](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md).
    
    <div>
    

    > [!NOTE]  
    > Mobile users who want to use Click to Join require a voice policy, along with the related PSTN usage records and voice routes, because clicking the link on the mobile device results in an outbound call from Lync Server 2013.

    
    </div>

<div>

## See Also


[Technical requirements for mobility in Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md)  


[Configuring voice policies, PSTN usage records, and voice routes in Lync Server 2013](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

