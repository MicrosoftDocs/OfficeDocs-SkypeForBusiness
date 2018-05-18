---
title: "Configure Cloud Voicemail"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 5/9/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for implementing cloud-based voicemail for users homed on Skype for Business Server."
---

# Configure Cloud Voicemail Service
<!-- PM Roy Kunz  See [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US) for alternate example. -->

[!INCLUDE [disclaimer](../disclaimer.md)]

## Overview 
See the [Plan Cloud Voicemail Service](plan-cloud-voicemail.md) article for an overview of Cloud Voicemail functionality.
 <!--See [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US) for alternate example. -->

### Prerequisites
The following configurations need to happen before the Cloud Voicemail feature can be configured:
- [Deploy Enterprise Voice in Skype for Business Server 2015](../../SfbServer/deploy/deploy-enterprise-voice/deploy-enterprise-voice.md)
- [Deploy Edge Server in Skype for Business Server](../../SfbServer/deploy/deploy-edge-server/deploy-edge-server.md)
- [Configure hybrid connectivity between Skype for Business Server and Skype for Business Online](configure-hybrid-connectivity.md)
- [Integrate Skype for Business Server with Exchange Server](../../SfbServer/deploy/integrate-with-exchange-server/integrate-with-exchange-server.md) or <BR> [Configure integration between on-premises Skype for Business Server 2015 and Exchange Online Web App](../../SfbServer/deploy/integrate-with-exchange-server/outlook-web-app.md) 

**(We don't seem to have any other article for integrating SfB and Exch Online (without Exch UM), is https://blogs.technet.microsoft.com/nexthop/2016/03/29/integrate-on-premise-lync-or-skype-for-business-with-office-365-unified-messaging-um/  or https://blogs.technet.microsoft.com/nagshettykadwadi/2017/10/18/integrate-skype-for-business-server-with-exchange-online-unified-messaging-in-hybrid-scenario/ in the general area? Both refer to integration with Exchange UM, is that different in any way from integrating with Exchange without UM?) <br> We don't know the line between integration with and without UM.**

## Configure Azure Cloud voicemail as the Hosting Provider on the edge server 

```
New-CsHostingProvider -Identity "Exchange Online" -Enabled $True -EnabledSharedAddressSpace $True -HostsOCSUsers $False -ProxyFqdn "exap.um.outlook.com" -IsLocal $False -VerificationLevel UseSourceVerification
```
**Questions:**
- Replace -Identity "Exchange Online" with ? 
- Replace -ProxyFqdn "exap<span></span>.um.outlook.com" with ?
- Is this the only command in integrating with exchange OL, or is this specific to UM?

## Enable a User for Cloud Voicemail

To enable a user’s voice mail calls to be routed to  Cloud voicemail, you must run the **[Set-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/set-csuser?view=skype-ps)** cmdlet to set the value of the HostedVoiceMail parameter. This parameter also signals Skype for Business Server 2019 to light up the “call voice mail” indicator.

- The following example enables Pilar Ackerman’s user account for Cloud Voicemail: \
     `Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $True`

    The cmdlet verifies that a Cloud Voicemail policy (global, site-level or per-user) applies to this user. If no policy applies, the cmdlet fails.
- The following example disables Pilar Ackerman’s user account for hosted voice mail:  \
    `Set-CsUser -Identity "Pilar Ackerman" -HostedVoiceMail $False`


The cmdlet verifies that no hosted voice mail policy (global, site-level or per-user) applies to this user. If a policy does apply, the cmdlet fails.

**QUESTIONS:**
- Verify: are we still using the HostedVoiceMail parameter for Set-CsUser , or is there a new parameter not yet public?<br> 
- If the user is already on hosted exchange UM is this part needed?<br> 
- What about migrating users from hosted EXCH UM to Cloud VM?<br> 
- This approach is one at a time.  Is there a bulk mechanism?<br> 
- It would make sense if there was another command in which we defined who or where the Host is, if not Exchange UM than the new Cloud voicemail provider. Is there something like this?