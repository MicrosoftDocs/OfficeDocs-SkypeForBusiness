---
title: "Desktop client feature comparison for Skype for Business Server 2015"
ms.author: jambirk
author: jambirk
ms.reviewer: PhillipGarding
manager: serdars
ms.date: 2/16/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 16b14d59-7737-4f9d-aa4d-83765a18ea07
description: "Summary: Skype for Business Server 2015 or Skype for Business Online administrators can use these tables to understand what features are supported on which clients."
---

# Desktop client feature comparison for Skype for Business Server 2015
 
**Summary:** Skype for Business Server 2015 or Skype for Business Online administrators can use these tables to understand what features are supported on which clients.
  
 Before you deploy or upgrade to Skype for Business, check which clients are already in use in your organization. Use the tables below to understand the feature support impact on those clients. This can help you communicate changes to users, pace the roll-out process, and fully understand the benefits of upgrading to the latest client.
  
Some features available with Skype for Business Server 2015 are not available in Skype for Business Online, see [Online or Hybrid user account limitations](desktop-feature-comparison.md#Online-Hybrid) for specifics. Skype for Business Online Admins may want to refer to [Skype for Business Online Service Description](https://technet.microsoft.com/library/skype-for-business-online-service-description.aspx) for information on the different plans available to them.

See [Desktop client feature comparison for Skype for Business 2019](../../../SfBServer2019/plan/feature-comparison.md) for client support on Skype for Business Server 2019.
  
The following tables show the features that are available with each client that works with Skype for Business Server 2015 or Skype for Business Online. You may also want to refer to [Mobile client feature comparison for Skype for Business](mobile-feature-comparison.md) for smart phone and tablet client feature comparisons. The Client Access License or User Subscription License your organization purchases will also have an impact on which features are available to your users. Whether you deploy the Full or Basic client to users depends on the license or plan your organization chooses to buy. See the [Licensing Guide](https://products.office.com/en-us/skype-for-business/it-pros) for more details.
  
> [!IMPORTANT]
> Skype for Business Server 2015 and Skype for Business Online support the following previously released clients: Lync 2013, Lync 2010, Lync 2010 Mobile, Lync Phone Edition, and Lync 2010 Attendant. For information about these clients when used with other servers, see the [Client comparison tables for Lync Server 2013](https://technet.microsoft.com/en-us/library/gg425836%28v=ocs.15%29.aspx) and [Client comparison tables for Lync Server 2010](https://technet.microsoft.com/en-us/library/gg425836%28v=ocs.14%29.aspx). 
  
> [!NOTE]
> The **Lync 2010 Attendant** client is not supported in Skype for Business Online.
  
> [!NOTE]
> The Skype for Business Web App browser client and Skype Meetings App Windows 10 app only provide [Meetings support](desktop-feature-comparison.md#BKMK_Conferencing). Refer to [Plan for Meetings clients (Web App and Meetings App)](meetings-clients.md) for more about these clients.
  
## Enhanced Presence support
<a name="BKMK_EnhancedPresence"> </a>

This table covers the Enhanced Presence features that extend beyond a simple indication of whether a user is online, offline, busy, etc. 
  
|Feature/capability|Skype for Business 2015 or 2016 client|Skype for Business on Mac|Lync 2013 client|Lync Windows Store app|Lync 2010 | Lync 2010 Attendant|Lync Phone Edition|Communicator for Mac 2011|Lync for Mac 2011|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Publish status  <br/> |&#x2714;|&#x2714; &#x2776; |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714; &#x2776; |&#x2714;|&#x2714;|
|View status  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|View status notes and Out of Office messages  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Add a custom location  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;||||||
|Add a custom note  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;|&#x2714;|
|Use a photo from any public site for My Picture  <br/> (not available in Skype for Business Online)  <br/> |&#x2714;||&#x2714;|||||||

 &#x2776;  Does not support publishing status based on calendar free/busy information.
  
## Contacts and Contact Groups support
<a name="BKMK_Contacts"> </a>

This table covers the features relating to managing IM and Presence contacts. 
  

|Feature/capability|Skype for Business 2015 or 2016 client|Skype for Business on Mac | Lync 2013 client | Lync Windows Store app | Lync 2010 | Lync 2010 Attendant | Lync Phone Edition | Communicator for Mac 2011 | Lync for Mac 2011 | 
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Pre-populated Contacts list  <br/> |&#x2714;|||||||||
|View and Modify Contacts list  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Tag contacts for status change alerts  <br/> |&#x2714;|&#x2714;|&#x2714;||&#x2714;|&#x2714;||||
|Control privacy relationships  <br/> |&#x2714;||&#x2714;||&#x2714;|&#x2714;||||
|Search the corporate address book  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Search Microsoft Outlook contacts  <br/> |&#x2714;|&#x2714;|&#x2714;||&#x2714;|&#x2714;|&#x2714;||&#x2714;|
|Manage contact groups  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;|&#x2714;|
|Expand distribution groups and Office 365 Groups  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|||
|Search for Response Groups  <br/> (not available in Skype for Business Online)  <br/> |&#x2714;||&#x2714;||&#x2714;|&#x2714;||||
|Display recent contacts group  <br/> |&#x2714;||&#x2714;||&#x2714;|&#x2714;||||
|Display current conversations group  <br/> |&#x2714;|&#x2714;|&#x2714;||&#x2714;|&#x2714;|&#x2714;|||
|Display alternate contact views (for example, tile)  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|||&#x2714;|
|Sort contacts by Group, Relationship, or New (people who've added you to their Contacts list)  <br/> |&#x2714;||&#x2714;|Sort by group  <br/> |&#x2714;|&#x2714;||||
|Sort contacts by Status (availability)  <br/> |&#x2714;||&#x2714;||&#x2714;|&#x2714;|||&#x2714;|
|Search and add Exchange contacts  <br/> |&#x2714;||&#x2714;||||||&#x2714;|
   
## IM support
<a name="BKMK_IMSupport"> </a>

This table covers features related to IM support.
  

|Feature/capability | Skype for Business 2015 or 2016 client | Skype for Business on Mac | Lync 2013 client | Lync Windows Store app | Lync 2010 | Lync 2010 Attendant | Lync Phone Edition | Communicator for Mac 2011 | Lync for Mac 2011 | 
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Initiate IM with or email to a contact  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;|&#x2714;|
|Navigate among multiple IM conversations/Track multiple conversations in a single tabbed window  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;|&#x2714;|
|Log IM conversations in Outlook  <br/> |&#x2714;|&#x2714;If server side conversation history is turned on  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;||Saved in Communicator for Mac  <br/> |Saved in Lync for Mac  <br/> |
|Use prepared conversation templates  <br/> |||||&#x2714;|&#x2714;||||
|Check spelling  <br/> |&#x2714;|&#x2714;||&#x2714;|||||&#x2714;|
|Skill search (with SharePoint Server integration)  <br/> (On-premises Skype for Business Server and on-premises SharePoint 2013 are required for skill search.)  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;|&#x2714;||||
|Persistent Chat (Group Chat) integration  <br/> (not available for Skype for Business Online)  <br/> |&#x2714;||&#x2714;|||||||
|Escalate a Persistent Chat room to a Skype for Business Meeting with one click  <br/> (not available for Skype for Business Online)  <br/> |&#x2714;||&#x2714;|||||||
|Inline pictures of sender and receiver in IM window  <br/> |&#x2714;||&#x2714;|&#x2714;||||||
|Send ink messages  <br/> ||||&#x2714;||||||
|Receive ink messages  <br/> |&#x2714;||&#x2714;|&#x2714;||||||
|Set IM messages as high importance  <br/> |&#x2714;||&#x2714;|||||||
|Transfer files in peer-to-peer IM conversations<br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|||&#x2714;|
   
## Meetings support
<a name="BKMK_Conferencing"> </a>

This table covers features related to Meetings support.
  
> [!NOTE]
>  Skype for Business meeting features aren't available in Skype for Business Online Standalone Plan 1.  Plan 1 is being [retired](/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/skype-for-business-online-plan-1-retirement
).

In Skype-to-Skype sessions, a Skype for Business Online Plan 1 user can participate in desktop sharing and application sharing if they're invited by a user who has access to sharing features.   
For details, see the [Skype for Business Online Service Description](https://technet.microsoft.com/library/jj822172.aspx). 
  
|Feature/capability | Skype for Business 2016 client | Skype for Business on Mac | Skype for Business Web App | Skype for Business 2015 client | Lync 2013 client | Lync Windows Store app | Lync 2010 | Lync 2010 Attendant | Lync Phone Edition | Communicator for Mac 2011 | Lync for Mac 2011 | 
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Add computer audio  <br/> |&#x2714;|&#x2714;|&#x2714;(requires plug-in)  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Add video  <br/> |&#x2714;|&#x2714;|&#x2714;(requires plug-in)  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|||&#x2714;|&#x2714;|
|View multiparty video (gallery view)  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||||||
|Video-based screen sharing  <br/> |&#x2714;|&#x2714;|&#x2714;View-only  <br/> |||||||||
|Use in-meeting presenter controls  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||||&#x2714;|
|Access detailed meeting roster  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|||&#x2714;|
|Participate in multiparty IM  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;|&#x2714;|
|Share the desktop (if enabled)  <br/> |&#x2714;|&#x2714; &#x2776; |&#x2714; &#x2776; (requires plug-in)  <br/> |&#x2714;|&#x2714;||&#x2714;|||&#x2714; &#x2776; |&#x2714; &#x2776; |
|Share a program (if enabled)  <br/> |&#x2714;|View only  <br/> |&#x2714;(requires plug-in)  <br/> |&#x2714;|&#x2714;||&#x2714;||||View only  <br/> |
|Add anonymous participants (if enabled)  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;||||&#x2714;|
|Use dial-in audio meetings  <br/> |&#x2714; &#x2777; |&#x2714;|&#x2714; &#x2777; |&#x2714;|&#x2714; &#x2777; |&#x2714; &#x2777; |&#x2714;|&#x2714;|||&#x2714;|
|Initiate a Meet Now meeting  <br/> |&#x2714;|&#x2714;||&#x2714;|&#x2714;|&#x2714;|&#x2714;||||&#x2714;|
|Add and present Microsoft PowerPoint files  <br/> |&#x2714;| &#x2778; Annotations not available  <br/> |&#x2714;|&#x2714;|&#x2714;|Present only  <br/> |&#x2714;|||| &#x2778; View only, annotations not available  <br/> |
|Navigate Microsoft PowerPoint files  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||||&#x2714;|
|Add and edit OneNote meeting notes  <br/> |&#x2714;||Edit only (not add)  <br/> |&#x2714;|&#x2714;|||||||
|Use a whiteboard  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;||&#x2714;|||||
|Conduct polls  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;||&#x2714;|||||
|Upload files to share with others  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;||&#x2714;||||&#x2714;|
|Schedule a meeting or conference  <br/> |Outlook or Skype for Business Web Scheduler  <br/> |Outlook or Skype for Business Web Scheduler  <br/> |Skype for Business Web Scheduler  <br/> |Outlook or Skype for Business Web Scheduler  <br/> |Outlook or Lync Web Scheduler  <br/> |Outlook or Lync Web Scheduler  <br/> |Outlook  <br/> ||||Outlook  <br/> |
|Q&amp;A Manager  <br/> |&#x2714;|||||||||||
|Disable attendee video  <br/> |&#x2714;||&#x2714;|||||||||
|Disable meeting IM  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;|||||||
|Mute Audience  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||||||&#x2714;|
|Make everyone an attendee  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;||||||&#x2714;|
|Produce Skype Meeting Broadcast  <br/> |&#x2714;|||||||||||
|Delegate can schedule a meeting on behalf of delegator  <br/> |&#x2714;|&#x2714;|&#x2714;|||||||||
|Synchronize delegates between Skype for Business and Outlook  <br/> |&#x2714;||&#x2714;|||||||||
|Set Video Spotlight (lock video)  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;|
|Give/Take control of screen sharing  <br/> |&#x2714;||&#x2714;|||||||||
   
 &#x2776;  Participants can't control desktops that are shared by Skype for Business on Mac, Lync for Mac 2011, or Communicator for Mac 2011 users. Skype for Business on Mac, Lync for Mac 2011 and Communicator for Mac 2011 users can't control desktops shared by Windows users. This also won't work for Skype for Business Web App on Max OSX.
  
 &#x2777;  For Skype for Business Online, this feature requires Microsoft PSTN Conferencing, Exchange Unified Messaging, or a 3rd party audio conferencing provider.
  
 &#x2778;  The Lync for Mac 2011 client cannot view Microsoft Office 2013 PowerPoint presentations when they have been shared in a conference by the Skype for Business Web App.
  
## Voice (Telephony) support
<a name="BKMK_Telephony"> </a>

This table covers features related to voice services support.
  
> [!NOTE]
> Skype for Business Voice (Telephony) features are limited to certain Skype for Business Online subscription plans. > For details, see the [Skype for Business Online Service Description](https://technet.microsoft.com/library/jj822172.aspx). 
  
 | Feature/capability | Skype for Business 2015 or 2016 client | Skype for Business on Mac | Lync 2013 client | Lync Windows Store app | Lync 2010 | Lync 2010 Attendant | Lync Phone Edition | Communicator for Mac 2011 | Lync for Mac 2011 | 
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Initiate a call  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Click to call a contact  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Transfer a call  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;|
|Manage call forwarding  <br/> |&#x2714;|&#x2714;|&#x2714; &#x2776; |&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;|
|Manage team call settings  <br/> |&#x2714;||&#x2714; &#x2776; ||&#x2714;|&#x2714;||||
|Manage delegates  <br/> |&#x2714;|&#x2714;Requires Skype for Business Server 2015 CU4 or later  <br/> |&#x2714; &#x2776; ||&#x2714;||||&#x2714;|
|Initiate a call to a Response Group  <br/> |&#x2714;||&#x2714; &#x2776; ||&#x2714;|&#x2714;||||
|Support emergency services (E-911)  <br/> |&#x2714;|&#x2714;Requires Skype for Business Server 2015 CU6 or later  <br/> |&#x2714; &#x2776; ||&#x2714;|&#x2714;|&#x2714;||&#x2714;|
|IM notification to SIP URI(s) for E-911 call  <br/> |&#x2714;|&#x2714;|&#x2714;||&#x2714;|&#x2714;|&#x2714;||&#x2714;|
|IM notification to distribution list for E-911 call  <br/> |&#x2714;||&#x2714;||&#x2714;|&#x2714;|&#x2714;||&#x2714;|
|Connect to voice mail, set up or change greeting  <br/> |&#x2714;|&#x2714;|&#x2714; &#x2776; |&#x2714;|&#x2714;|&#x2714;|&#x2714;|||
|Missed call notification  <br/> |&#x2714;|&#x2714;|&#x2714; &#x2776; |&#x2714;|&#x2714;|&#x2714;|&#x2714;|||
|Make calls on behalf of another contact (manager/delegate scenario)  <br/> |&#x2714;|&#x2714;|&#x2714; &#x2776; ||&#x2714;|||||
|Handle another's calls if configured as a delegate  <br/> |&#x2714;|&#x2714;|&#x2714; &#x2776; ||&#x2714;|&#x2714;|&#x2714;|||
|Manage a high volumes of calls  <br/> |||||&#x2714;|&#x2714;||||
|Call park  <br/> |&#x2714;||&#x2714; &#x2776; |||||||
|Group call pickup  <br/> |&#x2714;||&#x2714; &#x2776; ||||&#x2714;|||
|Location-based routing  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;|
|Manage Response Group/Team call group  <br/> |&#x2714;||&#x2714;|||||||
   
 &#x2776;  This feature isn't available in Skype for Business Online.
  
## External users support
<a name="BKMK_ExternalUsers"> </a>

This table covers features related to support for external users homed on the PSTN.
  

|Feature/capability | Skype for Business 2015 or 2016 client | Skype for Business on Mac | Lync 2013 client | Lync Windows Store app | Lync 2010 | Lync 2010 Attendant | Lync Phone Edition | Communicator for Mac 2011 | Lync for Mac 2011 | 
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Initiate IM with a public contact  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;|&#x2714;|
|Initiate IM with a federated contact  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;||&#x2714;|&#x2714;|
|Conduct two-party or multiparty calls with external users  <br/> (not available in Skype for Business Online)  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
   
## Recording support
<a name="BKMK_Recording"> </a>

This table covers features related to support for recording meetings.
  
| Future/capability** | Skype for Business 2015 or 2016 client | Skype for Business on Mac | Lync 2013 client | Lync Windows Store app | Lync 2010 | Lync 2010 Attendant | Lync Phone Edition | Communicator for Mac 2011 | Lync for Mac 2011 | 
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Client-side recording of audio, video, application sharing, desktop sharing, and uploaded content  <br/> |&#x2714; &#x2776; ||&#x2714; &#x2776; ||&#x2714;|||||
|Client-side recording of file transfers, shared OneNote pages, and PowerPoint annotations  <br/> |&#x2714; &#x2777; ||&#x2714; &#x2777; ||&#x2714;|||||
|Select preferred recording resolution  <br/> |&#x2714;||&#x2714;|||||||
   
 &#x2776;  Recording is unavailable in certain Skype for Business Online standalone plans. Recording requires full Skype for Business client rights.
  
 &#x2777;  Recording of file transfers, shared OneNote pages, and PowerPoint annotations is unavailable in Skype for Business Online.
  
## Modern Authentication
<a name="BKMK_Recording"> </a>

This table covers features requiring support for modern authentication. 
  
Modern authentication also requires a topology described in [Skype for Business topologies supported with Modern Authentication](../../plan-your-deployment/modern-authentication/topologies-supported.md).
  

 | Feature/capability | Skype for Business 2015 or 2016 client | Skype for Business on Mac | Lync 2013 client | Lync Windows Store app | Lync 2010 | Lync 2010 Attendant | Lync Phone Edition | Communicator for Mac 2011 | Lync for Mac 2011 | 
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Modern Authentication  <br/> |&#x2714;|&#x2714;|&#x2714;|||||||
|Multi-factor Authentication  <br/> |&#x2714;|&#x2714;|&#x2714;|||||||
|Cert -Based Authentication  <br/> |&#x2714;(Domain-joined device only)  <br/> |&#x2714;|&#x2714;(Domain-joined device only)  <br/> |||||||
|Kerberos Authentication  <br/> |&#x2714;||&#x2714;|||||||
   
## Archiving, compliance, and logging support
<a name="BKMK_Archiving"> </a>

This table covers features related to support for archiving and logging functions.
  

 | Feature/capability | Skype for Business 2015 or 2016 client | Skype for Business on Mac | Lync 2013 client | Lync Windows Store app | Lync 2010 | Lync 2010 Attendant | Lync Phone Edition | **Communicator for Mac 2011** | Lync for Mac 2011 | 
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Archiving of IM conversations in Outlook Conversation History  <br/> |&#x2714; &#x2776; |&#x2714;If server side conversation history is enabled <br/> |&#x2714; &#x2776; |&#x2714; &#x2776; |&#x2714;|&#x2714;||Saved in Communicator for Mac  <br/> |Saved in Lync for Mac  <br/> |
|Client-side archiving of audio, video, application sharing, desktop sharing, and uploaded content  <br/> |&#x2714; &#x2776; ||&#x2714; &#x2776; ||&#x2714;|||||
|Client-side archiving of file transfers, shared OneNote pages, and PowerPoint annotations  <br/> (unavailable in Skype for Business Online)  <br/> |&#x2714;||&#x2714;||&#x2714;|||||
|Access sign-in logs from Skype for Business icon in the task bar  <br/> |&#x2714;||&#x2714;|||||||
   
 &#x2776;  For Skype for Business Online users, this feature requires Exchange Online and is controlled by the user's Exchange mailbox In-Place Hold attribute.
  
## Client limitations
<a name="Types"> </a>

### Basic client limitations
<a name="Full-Basic"> </a>

The features below are available using the Full client and are not available with the Basic client: 
  
- Manage team call settings
    
- Manage delegates
    
- Make calls on behalf of another contact (manager/delegate scenario)
    
- Handle another's calls if configured as a delegate
    
- Manage a high volume of calls
    
- Initiate a call to a Response Group
    
- Call park
    
- Change greeting
    
- Group call pickup

- Missed call notification emails are not generated when a user status is UM disabled and they are using a legacy Outlook Client (2013 or earlier)
    
### Online or Hybrid user account limitations
<a name="Online-Hybrid"> </a>

User accounts can exist either Online or On-premises, and that will affect the features available to that user. Users with accounts on Skype for Business Online will not have access to the following features, even with the Full client: 
  
- Enhanced Presence: Use a photo from any public site for My Picture
    
- Contacts: Search for Response Groups
    
- IM Support: Persistent Chat (Group Chat) integration
    
- IM Support: Escalate a Persistent Chat room to a Skype for Business Meeting with one click
    
- External Users: Conduct two-party or multiparty calls with external users
    
## See also
<a name="Types"> </a>

[Plan for clients and devices](clients-and-devices.md)

[Latest updates for versions of Skype for Business that use Windows Installer (MSI)](../../sfb-client-updates.md)
