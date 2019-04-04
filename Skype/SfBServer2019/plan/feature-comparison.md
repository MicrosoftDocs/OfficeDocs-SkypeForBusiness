---
title: "Desktop client feature comparison for Skype for Business Server 2019"
ms.author: jambirk
author: jambirk
ms.reviewer: PhillipGarding
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 16b14d59-7737-4f9d-aa4d-83765a18ea07
description: "Summary: Skype for Business Server 2019 or Skype for Business Online administrators can use these tables to understand what features are supported on which clients."
---

# Desktop client feature comparison for Skype for Business Server 2019

**Summary:** Skype for Business Server 2019 or Skype for Business Online administrators can use these tables to understand what features are supported on which clients.

 Before you deploy or upgrade to Skype for Business Server, check which clients are already in use in your organization. Use the tables below to understand the feature support impact on those clients. This can help you communicate changes to users, pace the roll-out process, and fully understand the benefits of upgrading to the latest client.

Some features available with Skype for Business Server 2019 are not available in Skype for Business Online; see [Online or Hybrid user account limitations](feature-comparison.md#Online-Hybrid) for specifics. Skype for Business Online Admins may want to refer to [Skype for Business Online Service Description](https://technet.microsoft.com/library/skype-for-business-online-service-description.aspx) for information on the different plans available to them.

The following tables show the features that are available with each client that works with Skype for Business Server 2019 or Skype for Business Online. You may also want to refer to [Mobile client feature comparison for Skype for Business](../../SfbServer/plan-your-deployment/clients-and-devices/mobile-feature-comparison.md) for smart phone and tablet client feature comparisons. The Client Access License or User Subscription License your organization purchases will also have an impact on which features are available to your users. Whether you deploy the Full or Basic client to users depends on the license or plan your organization chooses to buy. See the [Licensing Guide](https://products.office.com/en-us/skype-for-business/it-pros) for more details.

> [!IMPORTANT]
> Skype for Business Server 2019 and Skype for Business Online support the following previously released clients: Lync 2013, Skype for Business 2015, and Skype for Business 2016, as well as the Skype for Business 2019 client. For information about these clients when used with other servers, see the [Client comparison tables for Lync Server 2013](https://technet.microsoft.com/en-us/library/gg425836%28v=ocs.15%29.aspx) and [Desktop client feature comparison for Skype for Business 2015](../../SfbServer/plan-your-deployment/clients-and-devices/desktop-feature-comparison.md). 


> [!NOTE]
> The Skype for Business Web App browser client and Skype Meetings App Windows 10 app only provide [Meetings support](feature-comparison.md#BKMK_Conferencing). Refer to [Plan for Meetings clients (Web App and Meetings App)](../../SfbServer/plan-your-deployment/clients-and-devices/meetings-clients.md) for more about these clients.

## Enhanced Presence support
<a name="BKMK_EnhancedPresence"> </a>

This table covers the Enhanced Presence features that extend beyond a simple indication of whether a user is online, offline, busy, etc. 


| Feature/capability                                                                                  | Skype for Business 2015, 2016, or 2019 client | Skype for Business on Mac | Lync 2013 client |
|:----------------------------------------------------------------------------------------------------|:----------------------------------------------|:--------------------------|:-----------------|
| Publish status                                                                                      | &#x2714;                                      | &#x2714; &#x2776;         | &#x2714;         |
| View status                                                                                         | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| View status notes and Out of Office messages                                                        | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| Add a custom location                                                                               | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| Add a custom note                                                                                   | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| Use a photo from any public site for My Picture  <br/> (not available in Skype for Business Online) | &#x2714;                                      |                           | &#x2714;         |

 &#x2776;  Does not support publishing status based on calendar free/busy information.

## Contacts and Contact Groups support
<a name="BKMK_Contacts"> </a>

This table covers the features relating to managing IM and Presence contacts. 


| Feature/capability                                                                            | Skype for Business 2015, 2016, or 2019 client | Skype for Business on Mac | Lync 2013 client |
|:----------------------------------------------------------------------------------------------|:----------------------------------------------|:--------------------------|:-----------------|
| Pre-populated Contacts list                                                                   | &#x2714;                                      |                           |                  |
| View and Modify Contacts list                                                                 | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| Tag contacts for status change alerts                                                         | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| Control privacy relationships                                                                 | &#x2714;                                      |                           | &#x2714;         |
| Search the corporate address book                                                             | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| Search Microsoft Outlook contacts                                                             | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| Manage contact groups                                                                         | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| Expand distribution groups and Office 365 Groups                                              | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| Search for Response Groups  <br/> (not available in Skype for Business Online)                | &#x2714;                                      |                           | &#x2714;         |
| Display recent contacts group                                                                 | &#x2714;                                      |                           | &#x2714;         |
| Display current conversations group                                                           | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| Display alternate contact views (for example, tile)                                           | &#x2714;                                      | &#x2714;                  | &#x2714;         |
| Sort contacts by Group, Relationship, or New (people who've added you to their Contacts list) | &#x2714;                                      |                           | &#x2714;         |
| Sort contacts by Status (availability)                                                        | &#x2714;                                      |                           | &#x2714;         |
| Search and add Exchange contacts                                                              | &#x2714;                                      |                           | &#x2714;         |

## IM support
<a name="BKMK_IMSupport"> </a>

This table covers features related to IM support.

|Feature/capability | Skype for Business 2015, 2016, or 2019 client | Skype for Business on Mac | Lync 2013 client | 
|:-----|:-----|:-----|:-----|  
|Initiate IM with or email to a contact  |&#x2714;|&#x2714;|&#x2714;|  
|Navigate among multiple IM conversations/Track multiple conversations in a single tabbed window   |&#x2714;|&#x2714;|&#x2714;| 
|Log IM conversations in Outlook  |&#x2714;|&#x2714; If server-side conversation history is turned on   |&#x2714;|   
|Check spelling |&#x2714;|&#x2714;||   
|Skill search (with SharePoint Server integration)  <br/> (On-premises Skype for Business Server and on-premises SharePoint 2013 are required for skill search.)  |&#x2714;||&#x2714;|
|Persistent Chat (Group Chat) integration  <br/> (not available for Skype for Business Online)|&#x2714;||&#x2714;|  
|Escalate a Persistent Chat room to a Skype for Business Meeting with one click  <br/> (not available for Skype for Business Online) |&#x2714;||&#x2714;| 
|Inline pictures of sender and receiver in IM window |&#x2714;||&#x2714;| 
|Receive ink messages |&#x2714;||&#x2714;| 
|Set IM messages as high importance |&#x2714;||&#x2714;|

## Meetings support
<a name="BKMK_Conferencing"> </a>

This table covers features related to Meetings support.

> [!NOTE]
>  Skype for Business meeting features aren't available in Skype for Business Online Standalone Plan 1.  Plan 1 is being [retired](/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/skype-for-business-online-plan-1-retirement
).

In Skype-to-Skype sessions, a Skype for Business Online Plan 1 user can participate in desktop sharing and application sharing if they're invited by a user who has access to sharing features.
For details, see the [Skype for Business Online Service Description](https://technet.microsoft.com/library/jj822172.aspx). 

|Feature/capability | Skype for Business 2016 client | Skype for Business on Mac | Skype for Business Web App | Skype for Business 2015 client | Lync 2013 client | 
|:-----|:-----|:-----|:-----|:-----|:-----|  
|Add computer audio  |&#x2714;|&#x2714;|&#x2714;(requires plug-in)  |&#x2714;|&#x2714;| 
|Add video |&#x2714;|&#x2714;|&#x2714;(requires plug-in) |&#x2714;|&#x2714;| 
|View multiparty video (gallery view)  |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Video-based screen sharing    |&#x2714;|&#x2714;|&#x2714; View-only   ||| 
|Use in-meeting presenter controls |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;| 
|Access detailed meeting roster |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|  
|Participate in multiparty IM |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|  
|Share the desktop (if enabled)  |&#x2714;|&#x2714; &#x2776; |&#x2714; &#x2776; (requires plug-in) |&#x2714;| &#x2714;|
|Share a program (if enabled) |&#x2714;|View only   |&#x2714;(requires plug-in)  |&#x2714;|&#x2714;|   
|Add anonymous participants (if enabled) |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Use dial-in audio meetings  &#x2777;|&#x2714; |&#x2714;|&#x2714;  |&#x2714;|&#x2714;  |
|Initiate a Meet Now meeting|&#x2714;|&#x2714;||&#x2714;|&#x2714;|  
|Add and present Microsoft PowerPoint files |&#x2714;| &#x2778; Annotations not available   |&#x2714;|&#x2714;|&#x2714;| 
|Navigate Microsoft PowerPoint files |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;| 
|Add and edit OneNote meeting notes  |&#x2714;||Edit only (not add)  |&#x2714;|&#x2714;|
|Use a whiteboard |&#x2714;||&#x2714;|&#x2714;|&#x2714;|
|Conduct polls |&#x2714;||&#x2714;|&#x2714;|&#x2714;|
|Upload files to share with others |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Schedule a meeting or conference |Outlook or Skype for Business Web Scheduler  |Outlook or Skype for Business Web Scheduler |Skype for Business Web Scheduler |Outlook or Skype for Business Web Scheduler   |Outlook or Lync Web Scheduler |  
|Q&amp;A Manager |&#x2714;|||||
|Disable attendee video |&#x2714;||&#x2714;|||
|Disable meeting IM |&#x2714;||&#x2714;|&#x2714;|&#x2714;|
|Mute Audience |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Make everyone an attendee |&#x2714;||&#x2714;|&#x2714;|&#x2714;|
|Produce Skype Meeting Broadcast |&#x2714;|||||
|Delegate can schedule a meeting on behalf of delegator |&#x2714;|&#x2714;|&#x2714;|||
|Synchronize delegates between Skype for Business and Outlook |&#x2714;||&#x2714;|&#x2714;|| 
|Set Video Spotlight (lock video) |&#x2714;||&#x2714;|&#x2714;|&#x2714;| 
|Give/Take control of screen sharing  |&#x2714;||&#x2714;|||

 &#x2776;  Participants can't control desktops that are shared by Skype for Business on Mac, Lync for Mac 2011, or Communicator for Mac 2011 users. Skype for Business on Mac, Lync for Mac 2011 and Communicator for Mac 2011 users can't control desktops shared by Windows users. This also won't work for Skype for Business Web App on Max OSX.

 &#x2777;  For Skype for Business Online, this feature requires Microsoft PSTN Conferencing, Exchange Unified Messaging, or a third-party audio conferencing provider.

 &#x2778;  The Lync for Mac 2011 client cannot view Microsoft Office 2013 PowerPoint presentations when they have been shared in a conference by the Skype for Business Web App.

&#x2779;  For Skype for Business 2016 apps, you must be using Click-to-Run, build 16.0.4227 or later.

&#x2780;  For Skype for Business 2015 apps, you must have the September Update, build 15.0.4747 or later.

## Voice (Telephony) support
<a name="BKMK_Telephony"> </a>

This table covers features related to voice services support.

> [!NOTE]
> Skype for Business Voice (Telephony) features are limited to certain Skype for Business Online subscription plans. For details, see the [Skype for Business Online Service Description](https://technet.microsoft.com/library/jj822172.aspx). 

 | Feature/capability | Skype for Business 2015, 2016, or 2019 client | Skype for Business on Mac | Lync 2013 client |  
|:-----|:-----|:-----|:-----| 
|Initiate a call |&#x2714;|&#x2714;|&#x2714;|
|Click to call a contact |&#x2714;|&#x2714;|&#x2714;|
|Transfer a call |&#x2714;|&#x2714;|&#x2714;|  
|Manage call forwarding |&#x2714;|&#x2714;|&#x2714; &#x2776; | 
|Manage team call settings |&#x2714;||&#x2714; &#x2776; |
|Manage delegates |&#x2714;|&#x2714;   |&#x2714; &#x2776; |
|Initiate a call to a Response Group|&#x2714;||&#x2714; &#x2776; |
|Support emergency services (E-911) |&#x2714;|&#x2714; |&#x2714; &#x2776; |
|IM notification to SIP URI(s) for E-911 call |&#x2714;|&#x2714;|&#x2714;|
|IM notification to distribution list for E-911 call|&#x2714;|&#x2714;|&#x2714;|
|Connect to voice mail, set up or change greeting |&#x2714;|&#x2714;|&#x2714; &#x2776; | 
|Missed call notification |&#x2714;|&#x2714;|&#x2714; &#x2776; | 
|Make calls on behalf of another contact (manager/delegate scenario) |&#x2714;|&#x2714;|&#x2714; &#x2776; |
|Handle another's calls if configured as a delegate |&#x2714;|&#x2714;|&#x2714; &#x2776; | 
|Call park |&#x2714;||&#x2714; &#x2776; |
|Group call pickup |&#x2714;||&#x2714; &#x2776; |
|Location-based routing |&#x2714;|&#x2714;|&#x2714;| 
|Manage Response Group/Team call group |&#x2714;||&#x2714;|

 &#x2776;  This feature isn't available in Skype for Business Online.

## External users support
<a name="BKMK_ExternalUsers"> </a>

This table covers features related to support for external users homed on the PSTN.


|Feature/capability | Skype for Business 2015, 2016, or 2019 client | Skype for Business on Mac | Lync 2013 client |  
|:-----|:-----|:-----|:-----|  
|Initiate IM with a public contact |&#x2714;|&#x2714;|&#x2714;| 
|Initiate IM with a federated contact |&#x2714;|&#x2714;|&#x2714;| 
|Conduct two-party or multiparty calls with external users  <br/> (not available in Skype for Business Online)  |&#x2714;|&#x2714;|&#x2714;| 

## Recording support
<a name="BKMK_Recording"> </a>

This table covers features related to support for recording meetings.

| Feature/capability | Skype for Business 2015, 2016, or 2019 client | Skype for Business on Mac | Lync 2013 client |   
|:-----|:-----|:-----|:-----|  
|Client-side recording of audio, video, application sharing, desktop sharing, and uploaded content |&#x2714; &#x2776; ||&#x2714; &#x2776; |
|Client-side recording of file transfers, shared OneNote pages, and PowerPoint annotations| &#x2714; &#x2777; ||&#x2714; &#x2777; |
|Select preferred recording resolution  |&#x2714;||&#x2714;|

 &#x2776;  Recording is unavailable in certain Skype for Business Online standalone plans. Recording requires full Skype for Business client rights.

 &#x2777;  Recording of file transfers, shared OneNote pages, and PowerPoint annotations is unavailable in Skype for Business Online.

## Modern Authentication
<a name="BKMK_Recording"> </a>

This table covers features requiring support for modern authentication. 

Modern authentication also requires a topology described in [Skype for Business topologies supported with Modern Authentication](../../SfbServer/plan-your-deployment/modern-authentication/topologies-supported.md).


 | Feature/capability | Skype for Business 2015, 2016, or 2019 client | Skype for Business on Mac | Lync 2013 client | 
|:-----|:-----|:-----|:-----|  
|Modern Authentication |&#x2714;|&#x2714;|&#x2714;|
|Multi-factor Authentication|&#x2714;|&#x2714;|&#x2714;|
|Cert -Based Authentication |&#x2714;(Domain-joined device only) |&#x2714;|&#x2714;(Domain-joined device only)  |
|Kerberos Authentication |&#x2714;||&#x2714;|

## Archiving, compliance, and logging support
<a name="BKMK_Archiving"> </a>

This table covers features related to support for archiving and logging functions.


 | Feature/capability | Skype for Business 2015, 2016, or 2019 client | Skype for Business on Mac | Lync 2013 client |  
|:-----|:-----|:-----|:-----|  
|Archiving of IM conversations in Outlook Conversation History|&#x2714; &#x2776; |&#x2714; If server-side conversation history is turned on  |&#x2714; &#x2776; | 
|Client-side archiving of audio, video, application sharing, desktop sharing, and uploaded content  |&#x2714; &#x2776; ||&#x2714; &#x2776; |
|Client-side archiving of file transfers, shared OneNote pages, and PowerPoint annotations   (unavailable in Skype for Business Online)  |&#x2714;||&#x2714;|
|Access sign-in logs from Skype for Business icon in the task bar |&#x2714;||&#x2714;|

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

[Plan for clients and devices](../../SfbServer/plan-your-deployment/clients-and-devices/clients-and-devices.md)

[Latest updates for versions of Skype for Business that use Windows Installer (MSI)](../../SfbServer/sfb-client-updates.md)
