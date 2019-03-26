---
title: 'Lync Server 2013: Configuring Microsoft Exchange Server 2013 Unified Messaging for Lync Server 2013 voice mail'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring Exchange Server 2013 Unified Messaging for Lync Server 2013 voice mail
ms:assetid: 1be9c4f4-fd8e-4d64-9798-f8737b12e2ab
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ687983(v=OCS.15)
ms:contentKeyID: 49733573
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Microsoft Exchange Server 2013 Unified Messaging for Microsoft Lync Server 2013 voice mail

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-04_

Microsoft Lync Server 2013 enables you to have voicemail messages stored in Microsoft Exchange Server 2013; those voicemail messages will then appear as email messages in your users' Inboxes. This capability was also found in the 2010 editions of Lync Server and Exchange; however, the process of configuring this "unified messaging" has been simplified in the 2013 editions thanks to the introduction of the UM Call Router component. This component is installed on the Exchange 2013 Client Access server, and all calls to Exchange unified messaging (such as a voicemail) are first routed through the Call Router and then are redirected to the appropriate Mailbox server.

If you have already configured server-to-server authentication between Lync Server 2013 and Exchange 2013 then you are ready to setup unified messaging. To do so, you must first create and assign a new unified messaging dial plan on your Exchange server. For example, these two commands (run from within the Exchange Management Shell) configure a new 3-digit dial plan for Exchange:

    New-UMDialPlan -Name "RedmondDialPlan" -VoIPSecurity "Secured" -NumberOfDigitsInExtension 3 -URIType "SipName" -CountryOrRegionCode 1
    Set-UMDialPlan "RedmondDialPlan" -ConfiguredInCountryOrRegionGroups "Anywhere,*,*,*" -AllowedInCountryOrRegionGroups "Anywhere"

In the first command in the example, the VoIPSecurity parameter, and the parameter value "Secured" indicate that the signaling channel is encrypted by using Transport Layer Security (TLS). The URIType "SipName" indicates that messages will be sent and received using the SIP protocol, and the CountryOrRegionCode of 1 indicates that the dial plan applies to the US.

In the second command, the parameter value passed to the ConfiguredInCountryOrRegionGroups parameter specifies the in-country groups that can be used with this dial plan. The parameter value "Anywhere,\*,\*,\*" sets the following:

  - Group name ("Anywhere")

  - AllowedNumberString (\*, a wildcard character indicating that any number string is allowed)

  - DialNumberString (\*, a wildcard character indicating that any dialed number is allowed)

  - TextComment (\*, a wildcard character indicating that any text command is allowed)

<div>


> [!NOTE]  
> Creating a new dial plan will also create a Default Mailbox Policy.



</div>

After creating and configuring the new dial plan you must add the new dial plan to your unified messaging server and then modify the startup mode of that server; in particular, you must set the startup mode to "Dual". You can perform both of these tasks from within the Exchange Management Shell:

    Set-UmService -Identity "atl-exchangeum-001.litwareinc.com" -DialPlans "RedmondDialPlan" -UMStartupMode "Dual"

After the unified messaging server has been configured you should next run the Enable-ExchangeCertificate cmdlet to ensure that your Exchange certificate is applied to the unified messaging service:

    Enable-ExchangeCertificate -Server "atl-umserver-001.litwareinc.com" -Thumbprint "EA5A332496CC05DA69B75B66111C0F78A110D22d" -Services "SMTP","IIS","UM"

After the certificate has been correctly assigned you must then stop and restart the MsExchangeUM service on the unified messaging server. This service must be stopped and restarted any time you change the startup mode.

After finishing configuration of the unified messaging server you can then configure the UM Call Router:

    Set-UMCallRouterSettings -Server "atl-exchange-001.litwareinc.com" -UMStartupMode "Dual" -DialPlans "RedmondDialPlan" 
    Enable-ExchangeCertificate -Server "atl-umserver-001.litwareinc.com" -Thumbprint "45BAA32496CC891169B75B9811320F78A1075DDA" -Services "IIS","UMCallRouter"

Because the startup mode has changed you must stop and restart the MsExchangeUMCR service on the computer hosting the UM Call Router.

To complete the unified messaging setup, you then need to create a UM mailbox policy and then use that policy to enable users for unified messaging. You can create a mailbox policy by using a command similar to this:

    New-UMMailboxPolicy -Name "RedmondMailboxPolicy" -AllowedInCountryOrRegionGroups "Anywhere"

And you can enable a user for unified messaging by using a command similar to this:

    Enable-UMMailbox -Extensions 100 -SIPResourceIdentifier "kenmyer@litwareinc.com" -Identity "litwareinc\kenmyer" -UMMailboxPolicy "RedmondMailboxPolicy"

In the preceding command, the Extensions parameter represents the telephone extension number for the user. In this example, the user has the extension number 100.

After you have enabled his mailbox, the user kenmyer@litwareinc.com should be able to use Exchange unified messaging. You can verify that the user can connect to Exchange UM by running the [Test-CsExUMConnectivity](https://docs.microsoft.com/powershell/module/skype/Test-CsExUMConnectivity) cmdlet from within the Lync Server Management Shell:

    $credential = Get-Credential "litwareinc\kenmyer"
    
    Test-CsExUMConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

If you have a second user who has been enabled for unified messaging you can use the [Test-CsExUMVoiceMail](https://docs.microsoft.com/powershell/module/skype/Test-CsExUMVoiceMail) cmdlet to verify that this second user can leave a voicemail message for the first user.

    $credential = Get-Credential "litwareinc\pilar"
    
    Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $credential

</div>

<span> </span>

</div>

</div>

</div>

