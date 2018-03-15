---
title: "Steps to prepare and deploy Lync Server 2013 hybrid environment"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
ms.custom: httpsfix
ms.assetid: a50d4f7b-63f4-4663-af63-56ca87e4e3e7

description: "The following table lists the steps required to prepare your environment for a hybrid deployment with Skype for Business Online and Microsoft Office 365."
---

# Steps to prepare and deploy Lync Server 2013 hybrid environment
[]
The following table lists the steps required to prepare your environment for a hybrid deployment with Skype for Business Online and Microsoft Office 365.
  
|**Completed?**|**Step**|**Description**|
|:-----|:-----|:-----|
||Create a tenant account for Office 365 and enable Lync Online  <br/> |Learn about Office 365 and Lync Online at [Office 365](https://go.microsoft.com/fwlink/p/?LinkId=254980).  <br/> To make sure that your environment is ready for Office 365, see the [System Requirements](https://go.microsoft.com/fwlink/p/?LinkId=401408).  <br/> For details about setting up Office 365, see [Getting Started with Office 365](https://go.microsoft.com/fwlink/p/?LinkId=254982) and [Set Up Office 365](http://go.microsoft.com/fwlink/p/?LinkId=254979).  <br/> |
||Add your domain and verify ownership  <br/> |Your domain is sometimes also referred to as your vanity domain. You must add your domain to your Office 365 tenant, and then follow the steps to validate the domain with Office 365. This is to confirm that you are the owner of the domain.  <br/> To add your domain to your Office 365 tenant, follow the steps described at [Add your domain to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=254983).  <br/> Complete all of the steps in each section in the topic, including "Edit DNS records for your Office 365 services."  <br/> |
||Verify environment readiness  <br/> |You can use the Office 365 Setup Assistant to help you deploy Office 365. For more information, see [Use Setup Assistant to determine Office 365 readiness](https://go.microsoft.com/fwlink/p/?LinkId=254985).  <br/> For details about using the tool and deploying Office 365, see [Office 365 deployment guide](https://go.microsoft.com/fwlink/p/?LinkId=257337).  <br/> |
||Prepare for Active Directory synchronization  <br/> |Active Directory synchronization keeps your on-premises Active Directory continuously synchronized with Office 365. This lets you create synchronized versions of each user account and group, and also enables global address list (GAL) synchronization from your local Microsoft Exchange Server environment to Microsoft Exchange Online.  <br/> > [!IMPORTANT]> You need to synchronize the AD accounts for all Lync users in your organization between your on-premises and online Lync deployments, even if users are not moved to Lync Online. If you do not synchronize all users, communication between on-premises and online users in your organization may not work as expected.           To prepare your environment for Active Directory synchronization, follow the steps described in [Directory synchronization Roadmap](https://go.microsoft.com/fwlink/p/?LinkId=254988), including setting up single sign-on.  <br/> |
||Create certificates for Active Directory Federation Services (AD FS)  <br/> |You will need to create the certificates that are used for identity federation with Office 365. For more information, see the "Federation server certificates" section of the Plan for and deploy AD FS for use with single sign-on topic at [Checklist: Use AD FS to implement and manage single sign-on](https://go.microsoft.com/fwlink/p/?LinkId=285376).  <br/> |
||Assign certificates for AD FS  <br/> |After you create the certificates that are used for identity federation with Office 365, you must install and assign them.  <br/> |
||Move pilot users to Skype for Business Online  <br/> |After you have completed the steps to prepare and configure your environment for Skype for Business Online, you can start moving pilot users to Lync Online.  <br/> See [Move users to Lync Online in Lync Server 2013](move-users-to-lync-online.md).  <br/> |
||Administering users in a hybrid deployment  <br/> |For details about how to administer users in a hybrid deployment, see [Administering users in a hybrid Lync Server 2013 deployment](administering-users-in-a-hybrid-deployment.md).  <br/> |
   

