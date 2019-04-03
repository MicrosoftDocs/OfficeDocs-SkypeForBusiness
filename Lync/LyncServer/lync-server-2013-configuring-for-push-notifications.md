---
title: 'Lync Server 2013: Configuring for push notifications'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring for push notifications
ms:assetid: d77f2c06-0fe6-45d5-8f08-808ab871b3e0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690047(v=OCS.15)
ms:contentKeyID: 48185574
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring for push notifications in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-12_

Push notifications, in the form of badges, icons, or alerts, can be sent to a mobile device even when the mobile application is inactive. Push notifications notify a user of events such as a new or missed IM invitation and voice mail. The Lync Server 2013 Mobility Service sends the notifications to the cloud-based Lync Server Push Notification Service, which then sends the notifications to the Apple Push Notification Service (APNS) (for an Apple device running the Lync 2010 Mobile client) or the Microsoft Push Notification Service (MPNS) (for a Windows Phone device running the Lync 2010 Mobile or the Lync 2013 Mobile client).

<div>


> [!IMPORTANT]  
> If you use Windows Phone with Lync 2010 Mobile or Lync 2013 Mobile client, push notification is an important consideration.<BR>If you use Lync 2010 Mobile on Apple devices, push notification is an important consideration.<BR>If you use Lync 2013 Mobile on Apple devices, you no longer need push notification.



</div>

Configure your topology to support push notifications by doing the following:

  - If your environment has a Lync Server 2010 or Lync Server 2013 Edge Server, you need to add a new hosting provider, Microsoft Lync Online, and then set up hosting provider federation between your organization and Lync Online.

  - If your environment has a Office Communications Server 2007 R2 Edge Server, you need to set up direct SIP federation with push.lync.com.
    
    <div>
    

    > [!NOTE]  
    > Push.lync.com is a Microsoft Office 365 domain for Push Notification Service.

    
    </div>

  - To enable push notifications, you need to run the **Set-CsPushNotificationConfiguration** cmdlet. By default, push notifications are turned off.

  - Test the federation configuration and push notifications.

<div>

## To configure for push notifications with Lync Server 2013 or Lync Server 2010 Edge Server

1.  Log on to a computer where Lync Server Management Shell and Ocscore are installed as a member of the RtcUniversalServerAdmins group.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Add a Lync Server online hosting provider. At the command line, type:
    
        New-CsHostingProvider -Identity <unique identifier for Lync Online hosting provider> -Enabled $True -ProxyFqdn <FQDN for the Access Server used by the hosting provider> -VerificationLevel UseSourceVerification
    
    For example:
    
        New-CsHostingProvider -Identity "LyncOnline" -Enabled $True -ProxyFqdn "sipfed.online.lync.com" -VerificationLevel UseSourceVerification
    
    <div>
    

    > [!NOTE]  
    > You cannot have more than one federation relationship with a single hosting provider. That is, if you have already set up a hosting provider that has a federation relationship with sipfed.online.lync.com, do not add another hosting provider for it, even if the identity of the hosting provider is something other than LyncOnline.

    
    </div>

4.  Set up hosting provider federation between your organization and the Push Notification Service at Lync Online. At the command line, type:
    
        New-CsAllowedDomain -Identity "push.lync.com"

</div>

<div>

## To configure for push notifications with Office Communications Server 2007 R2 Edge Server

1.  Log on to the Edge Server as a member of the RtcUniversalServerAdmins group.

2.  Click **Start**, click **All Programs**, click **Administrative Tools**, and then click **Computer Management**.

3.  In the console tree, expand **Services and Applications**, right-click **Microsoft Office Communications Server 2007 R2**, and then click **Properties**.

4.  On the **Allow** tab, click **Add**.

5.  In the **Add Federated Partner** dialog box, do the following:
    
      - In **Federated partner domain name**, type **push.lync.com**.
    
      - In **Federated partner Access Edge Server**, type **sipfed.online.lync.com**.
    
      - Click **OK**.

</div>

<div>

## To enable push notifications

1.  Log on to a computer where Lync Server Management Shell and Ocscore are installed as a member of the CsAdministrator role.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Enable push notifications. At the command line, type:
    
        Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $True -EnableMicrosoftPushNotificationService $True

4.  Enable federation. At the command line, type:
    
        Set-CsAccessEdgeConfiguration -AllowFederatedUsers $True

</div>

<div>

## To test federation and push notifications

1.  Log on to a computer where Lync Server Management Shell and Ocscore are installed as a member of the CsAdministrator role.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Test the federation configuration. At the command line, type:
    
        Test-CsFederatedPartner -TargetFqdn <FQDN of Access Edge server used for federated SIP traffic> -Domain <FQDN of federated domain> -ProxyFqdn <FQDN of the Access Edge server used by the federated organization>
    
    For example:
    
        Test-CsFederatedPartner -TargetFqdn accessproxy.contoso.com -Domain push.lync.com -ProxyFqdn sipfed.online.lync.com

4.  Test push notifications. At the command line, type:
    
        Test-CsMcxPushNotification -AccessEdgeFqdn <Access Edge service FQDN>
    
    For example:
    
        Test-CsMcxPushNotification -AccessEdgeFqdn accessproxy.contoso.com

</div>

<div>

## See Also


[Test-CsFederatedPartner](https://docs.microsoft.com/powershell/module/skype/Test-CsFederatedPartner)  
[Test-CsMcxPushNotification](https://docs.microsoft.com/powershell/module/skype/Test-CsMcxPushNotification)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

