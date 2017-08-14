---
title: Supported hybrid configurations for Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 5d456d6c-ad71-420c-b6d8-4d9cd0324f86
---



# Supported hybrid configurations for Skype for Business Server 2015
[] **Summary:** Learn about the hybrid configurations that are supported in Skype for Business Server 2015.
You can configure Skype for Business Server 2015 deployments for integration with Microsoft Exchange Server 2016, Microsoft Exchange Server 2013, Microsoft Exchange Server 2010, and SharePoint Server, both on-premises and online. The features listed in the following table are supported with all clients unless otherwise specified. For more information about client support, see  [Desktop client comparison tables for Skype for Business](desktop-client-comparison-tables-for-skype-for-business.md) and Skype for Business Online client comparison tables at [Clients for Skype for Business Online](https://go.microsoft.com/fwlink/p/?LinkId=281902).
  
    
    


## Integration with Exchange Server

The following table lists the features supported in a hybrid deployment when integrated with Microsoft Exchange Server. 
  
    
    


||**Exchange on-premises**|**Exchange Online**|
|:-----|:-----|:-----|
|**Skype for Business Server 2015 on-premises** <br/> | IM/Presence in Outlook <br/>  For more information, see [IM and Presence](http://technet.microsoft.com/library/6a93ae95-3b64-410b-ab72-74dea232f065.aspx) <br/>  Schedule and join online meetings through Outlook <br/>  For more information, see [Integrate Skype for Business Server 2015 with Exchange Server](integrate-skype-for-business-server-2015-with-exchange-server.md) <br/>  IM/Presence in Outlook Web App <br/>  For more information, see [Configure a hybrid environment in Skype for Business Server 2015](configure-a-hybrid-environment-in-skype-for-business-server-2015.md) <br/>  Schedule and join online meetings through Outlook Web App <br/>  IM/Presence in Mobile Clients <br/>  Join online meetings in Mobile clients <br/>  For more information, see [Deploying Mobility](http://technet.microsoft.com/library/f41e6b25-d2cd-43fd-a17b-22cfda8bcd4f.aspx) <br/>  Publish status based on Outlook calendar free/busy information <br/>  Contact List (via Unified Contact Store) <br/>  For more information, see [Configure Skype for Business Server 2015 to use the unified contact store](configure-skype-for-business-server-2015-to-use-the-unified-contact-store.md) <br/> > [!NOTE]>  Requires Exchange 2016 or Exchange 2013.>  A Lync 2013 or Skype for Business desktop client is required.           High-resolution Contact Photo in Lync 2013 client and Lync Web App. <br/>  For more information, see [Configure the use of high-resolution photos in Skype for Business Server 2015](configure-the-use-of-high-resolution-photos-in-skype-for-business-server-2015.md) <br/> > [!NOTE]>  Requires Exchange 2016 or Exchange 2013.           Meeting delegation <br/>  Supported only when both users are homed online in the same forest, or both are homed on-premises. <br/>  Missed Conversations history and Call Logs are written to user's exchange mailbox <br/>  Archiving Content (IM and Meeting) in Exchange <br/>  For more information, see [Deployment Checklist for Archiving](http://technet.microsoft.com/library/7479734d-be01-40d9-ad82-320a09d19d04.aspx) <br/> > [!NOTE]>  Requires Exchange 2016 or Exchange 2013.           Search archived content <br/> > [!NOTE]>  Requires Exchange 2016 or Exchange 2013.           Voice mail <br/>  For more information, see [Deploying On-Premises Exchange UM to Provide Lync Server 2013 Voice Mail](http://technet.microsoft.com/library/9673bd73-a3a3-425d-870f-04d801c6d0d5.aspx) <br/> | IM/Presence in Outlook <br/>  For more information, see [Configure integration between on-premises Skype for Business Server 2015 and Outlook Web App](configure-integration-between-on-premises-skype-for-business-server-2015-and-out.md) <br/>  Schedule and join online meeting through Outlook <br/>  IM/Presence in OWA <br/>  For more information, see [Configure integration between on-premises Skype for Business Server 2015 and Outlook Web App](configure-integration-between-on-premises-skype-for-business-server-2015-and-out.md) <br/>  Schedule and join online meeting from Outlook Web App <br/>  For more information, see [Configure integration between on-premises Skype for Business Server 2015 and Outlook Web App](configure-integration-between-on-premises-skype-for-business-server-2015-and-out.md) <br/>  IM/Presence in Mobile Clients <br/>  Join online meeting in Mobile clients <br/>  Publish status based on Outlook calendar free/busy information <br/>  Contact List (via Unified Contact Store). For more information, see [Configure Skype for Business Server 2015 to use the unified contact store](configure-skype-for-business-server-2015-to-use-the-unified-contact-store.md) <br/> > [!NOTE]>  Lync Server 2013 only. A Lync 2013 or Skype for Business desktop client is required.           High-resolution Contact Photo in Lync 2013 client, Skype for Business client, and Lync Web App. <br/>  For more information, see [Configure the use of high-resolution photos in Skype for Business Server 2015](configure-the-use-of-high-resolution-photos-in-skype-for-business-server-2015.md).  <br/>  Meeting delegation <br/>  Supported only when both users are homed online in the same forest, or both are homed on-premises. <br/>  Missed Conversations history and Call Logs are written to user's exchange mailbox <br/>  Archiving Content (IM and Meeting) in Exchange. <br/>  For more information, see [Deployment Checklist for Archiving](http://technet.microsoft.com/library/7479734d-be01-40d9-ad82-320a09d19d04.aspx) <br/>  Search archived content. For more information, see at [Configure Exchange for SharePoint eDiscovery Center](https://go.microsoft.com/fwlink/p/?LinkId=285448) <br/>  Voice mail. For more information, see [Providing Lync Server 2013 Users Voice Mail on Hosted Exchange UM](http://technet.microsoft.com/library/306d3fb5-231b-4f0b-b8d8-0d9083b5ed77.aspx) <br/> |
|**Skype for Business Online** <br/> | Presence in Outlook <br/>  Respond via IM, PSTN Call, Skype Call or Video Call from an Outlook email <br/>  Schedule and join online meetings through Outlook <br/>  IM/Presence in Mobile clients <br/>  Join online meetings in Mobile clients <br/>  Publish status based on Outlook calendar free/busy information <br/>  Missed Conversations history and Call Logs are written to user's exchange mailbox <br/>  High-resolution Contact Photo in Lync 2013 or Skype for Business client. <br/> > [!NOTE]>  Requires Exchange 2016 or Exchange 2013. This is not supported in Lync Web App when users are homed on Skype for Business Online.           Meeting delegation <br/>  Supported only when both users are homed online in the same forest, or both are homed on-premises. <br/>  Missed Conversations history and Call Logs are written to user's Exchange mailbox <br/>  Server Side Conversation History <br/> | IM/Presence in Outlook <br/>  Schedule and join online meetings through Outlook <br/>  IM/Presence in Outlook Web App <br/>  Schedule and join online meeting from Outlook Web App <br/>  IM/Presence in Mobile Clients <br/>  Join online meeting in Mobile clients <br/>  Publish status based on Outlook calendar free/busy information <br/>  Missed Conversations history and Call Logs are written to user's exchange mailbox <br/>  Contact List (via Unified Contact Store) <br/> > [!NOTE]>  Lync Server 2013 or Skype for Business client required           High-resolution Contact Photo in Lync 2013, Skype for Business client, and Lync Web App <br/>  Meeting delegation <br/>  Supported only when both users are homed online in the same forest, or both are homed on-premises. <br/>  Archiving Content (IM and Meeting) in Exchange <br/>  Search archived content <br/>  Voicemail <br/> |
   

## Integration with SharePoint

The following table lists the features supported in a hybrid deployment when integrated with SharePoint.
  
    
    


||**SharePoint on-premises**|**SharePoint Online**|
|:-----|:-----|:-----|
|**Skype for Business Server 2015 on-premises** <br/> | Skills search <br/>  Presence in SharePoint <br/> | Presence in SharePoint <br/> |
|**Skype for Business Online** <br/> | Presence in SharePoint <br/> | Presence in SharePoint <br/> |
   
