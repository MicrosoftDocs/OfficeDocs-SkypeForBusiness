---
title: 'Frequently Asked Questions: Provisioning Lync Server for Skype connectivity'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: 'Frequently Asked Questions: Provisioning Lync Server for Skype connectivity'
ms:assetid: 4d1b2bfc-780b-4b8c-afd5-11c2e59203b5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn440172(v=OCS.15)
ms:contentKeyID: 57793362
ms.date: 12/29/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Frequently Asked Questions: Provisioning Lync Server 2013 for Skype connectivity

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2019-03-22_

Beginning in April 2019, we will stop the collection and retention of contact information for customers who are provisioned for Skype Federation via the pic.lync.com website. This change is being made to ensure that the pic.lync.com provisioning system adheres to Microsoft privacy policies. 
 
Once this change goes live, we will no longer be able to provide email updates on pending provisioning changes. PIC provisioning changes typically complete within 24-48 hours after being entered. If you are still experiencing Skype Federation issues 48 hours after submitting a provisioning request, please engage Microsoft Technical Support to investigate further.

> [!IMPORTANT]
> As part of this change, all previously entered contact information will be purged from our system by the end of April, 2019.


**Q: What features are supported between Microsoft Lync and Skype?**

**A:** With Skype now part of the Microsoft family, new possibilities open up for extending unified communications scenarios to the hundreds of millions of people who use Skype. This combination will enable Lync customers to connect and collaborate with suppliers, customers, and partners, relying on the richness of Lync and the reach of Skype.

  - Instant Message and Audio and Video Calls—Federated audio and video calling and instant messaging between Lync and Skype users

  - Presence Sharing— Exchange presence information between federated contacts

  - Simple Administration—Settings and controls to configure federated communications in accordance with your organization’s policies and standards

**Q: How do I qualify to connect my Lync deployment with Skype?**

**A:** You are licensed for Skype connectivity if you have either:

  - Lync Server (2010 or 2013) plus Lync Server Standard Client Access Licenses (“CALs”; 2010 or 2013) for the users and/or devices in your organization that will connect to Skype. 

  - Lync Online (as standalone licenses or as part of an Office 365 suite).  However, this service (pic.lync.com) is only for provisioning Lync Server and hybrid Lync Server and Lync Online deployments.  Lync Online PIC provisioning is done in Lync Online Control Panel (LOCP).

**Q: What must Lync end users do to connect to Skype contacts?**

**A:** After a domain is activated and the features are enabled by an organization’s Lync administrator, Lync users can add Skype contacts to their contact lists within the Lync client.

**Q: What must Skype end users do to connect to Lync contacts?**

**A:** All Skype users wishing to connect to a Lync user must have a Microsoft Account associated with their Skype IDs and sign in using the Microsoft Account.  This can be enabled within the Skype client.

**Q: Is federation with Windows Live still available?**

**A:** Beginning in October, 2012, Microsoft started helping Windows Live Messenger (WLM) users move to Skype, en route to eventually retiring WLM. Lync will continue to support federation with WLM as long as WLM is in market, but no additional Windows Live domain activations will be allowed. The movement of WLM users is enabled by the Skype 6.0 for Mac and Windows (released October 25, 2012) which allows signing in with a Microsoft Account (i.e., the same credentials as WLM). After simply signing in to Skype, WLM buddy lists automatically populate into Skype, and users can take advantage of Skype’s expanded communication capabilities such as calling landlines and mobiles, screen sharing, group video calling, and support for a wide variety of devices. Moreover, WLM users’ federated Lync contacts follow the transition into Skype with the rest of their buddy lists, and IM between Skype and Lync for these contacts will be available immediately. Lync customers do not need to do anything to enable this continuity of service.

**Q: Is federation with Yahoo\! or AOL still available?**

**A:**No. Federation with Yahoo\! and AOL were contingent upon support from Yahoo\! and AOL. For both Yahoo\! and AOL, the service ended on June 30, 2014. 

**Q: Can I trial Skype connectivity before purchasing Lync?**

**A:** Skype connectivity is not offered on a trial basis. In place of a trial, Lync customers with eligible licenses are encouraged to simply sign up for the service to test.

**Q: What information is required for provisioning?**

**A:** To submit a provisioning request under a qualified license, you need the following:

  - Microsoft agreement number:
    
      - Microsoft Volume Licensing Support: Microsoft Volume Licensing Agreement number
    
      - Microsoft Partner Network: Headquarter partner ID
    
      - Service Provider Licensing Agreement: Initial enrollment number
    
      - High Volume Services: Product enrollment number

  - Fully qualified domain names (FQDNs) for the Access Edge service.
    
      - FQDN for at least one Access Edge service is required.
    
      - If your organization has more than one server running the Access Edge service, specify the FQDNs for each additional Access Edge service. Important: If you previously specified an FQDN for the Access Edge service and want to change it, provisioning for the change can take several days to complete and can result in a disruption in service. To prevent service disruption, we recommend that you maintain the previously specified FQDN of the Access Edge service.

  - Session Initiation Protocol (SIP) domain(s). This is the domain suffix of the SIP URI that users currently use for instant messaging. If your organization has more than one SIP domain, specify the domain suffix for each domain used for instant messaging. For example, for user1@contoso.com, specify contoso.com for the SIP domain; for user1@example.fabrikam.com, specify example.fabrikam.com as the SIP domain.
    
    <div>
    

    > [!NOTE]
    > Specify only the domain suffix for the SIP domain. Do not specify any FQDNs, including the FQDN for the Access Edge service, for the SIP domain.

    
    </div>

  - Contact information. Specify an e-mail address for the administrator of each SIP domain that you specify.

**Q: How do I enable Lync-Skype Connectivity in a split-domain scenario?**

**A:**If you have a Lync Online 2013 and Lync Server on-premise split-domain scenario (with users on both online and on-premise using the same SIP domain), enable Lync-Skype Connectivity by doing these two steps in the following order

1.  Set up on-premise Lync-Skype Connectivity as explained in the PIC Provisioning Guide.

2.  Wait until you see confirmation that your domain has been provisioned by Microsoft.

3.  After you see the confirmation, use the Lync admin center to turn on “external communications”. For more information, see [http://office.microsoft.com/en-us/support/configure-external-communications-HA102817865.aspx?CTT=5\&origin=HA102817356](http://office.microsoft.com/en-us/support/configure-external-communications-ha102817865.aspx?ctt=5%26origin=ha102817356)

This order is important.  You must set up the on-premise connectivity before you enable the communications in Lync Online. If the order is reversed, the information entered for on-premise in <https://pic.lync.com> will not go through. If you have already set up Lync Online for external communications with this domain, you must turn it off, wait for 24 hours, and start again, first by entering your on-premise information at <https://pic.lync.com> and then turning on external communications for Lync Online.

**Q: Can I provision multiple Access Edge service FQDNs for Skype connectivity?**

**A:** You can provision only one access edge FQDN for one or more domains. You can provision multiple access edge FQDNs, up to 10 per request, if they have distinct domains.

**Q: Can I obtain the list of Microsoft Account e-mail addresses that you find for the organization requesting provisioning?**

**A:** No. These addresses are considered personally identifiable information and are not shared.

**Q: How do I add a Windows Live Messenger contact that has an ID containing a domain other than those supported by Windows Live?**

**A:** If you are adding a Windows Live Messenger user with an account or ID with a non-Windows Live domain, enter the address in the following format: \<user name\>(\<domain name\>)@msn.com, where \<domain name\> is the domain name in the e-mail address of the user. For example, if you wanted to add ted@contoso.com, you would use the following format: ted(contoso.com)@msn.com. For a list of domains that are administered by Windows Live, see the Supported Domains section in “Known Issues That Occur with Public Instant Messaging After You Install Live Communications Server Service Pack 1” at http://support.microsoft.com/?kbid=897567.

**Q: How long does the provisioning process take?**

**A:** Provisioning can take up to 30 days.

**Q: How will I know when provisioning is complete?**

**A:** Microsoft will send e-mail notification when provisioning is complete.

**Q: How can I update the configuration or contact details that I submit?**

**A:** You can update your information at the same web site that you used to request provisioning, after provisioning is complete. Enter your agreement number, and then click Update service.

</div>

<span> </span>

</div>

</div>

</div>

