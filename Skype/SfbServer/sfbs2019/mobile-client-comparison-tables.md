---
title: "Mobile client comparison tables for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: End User
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f3ba3379-afe4-4bc8-a038-9dff9dfd3bff

description: "In this articleSign-in, Push Notifications, and General FeaturesEnhanced Presence Support in Lync Mobile ClientsContacts and Contact Groups Support in Lync Mobile ClientsInstant Messaging Support in Lync Mobile ClientsLync-to-Lync Audio and VideoConferencing Support in Lync Mobile ClientsTelephony Support in Lync Mobile ClientsExternal User Support in Lync Mobile ClientsAddress Book IntegrationArchiving and Compliance Support in Lync Mobile Clients"
---

# Mobile client comparison tables for Lync Server 2013
[]
 **In this article**
  
[Sign-in, Push Notifications, and General Features](#sectionSection0)
  
[Enhanced Presence Support in Lync Mobile Clients](#sectionSection1)
  
[Contacts and Contact Groups Support in Lync Mobile Clients](#sectionSection2)
  
[Instant Messaging Support in Lync Mobile Clients](#sectionSection3)
  
[Lync-to-Lync Audio and Video](#sectionSection4)
  
[Conferencing Support in Lync Mobile Clients](#sectionSection5)
  
[Telephony Support in Lync Mobile Clients](#sectionSection6)
  
[External User Support in Lync Mobile Clients](#sectionSection7)
  
[Address Book Integration](#sectionSection8)
  
[Archiving and Compliance Support in Lync Mobile Clients](#sectionSection9)
  
The following tables compare the features and capabilities among Lync 2013 mobile clients and the Lync 2013 desktop client in the following categories:
  
- Sign-in, push notifications, and general features
    
- Enhanced presence
    
- Contacts and contact groups
    
- Instant messaging (IM)
    
- Lync-to-Lync audio and video
    
- Conferencing
    
- Telephony
    
- External users
    
- Archiving and compliance
    
These tables indicate the features that are available to Lync users in an on-premises deployment of Lync Server 2013. The same features are also available to Skype for Business Online and Microsoft Office 365 users, unless otherwise indicated in the table footnotes.
  
> [!NOTE]
>  Looking for the mobile client comparison tables for Skype for Business? See [Mobile client comparison tables for Skype for Business](https://technet.microsoft.com/en-us/library/dn951412.aspx). >  For online help and resources for end users, see [Microsoft Lync 2013 for Mobile Clients](https://go.microsoft.com/fwlink/?LinkId=286237). >  To compare the features available in other Lync 2013 clients, see [Desktop client comparison tables for Lync Server 2013](desktop-client-comparison-tables.md). >  Lync Server 2013 also supports Lync 2010 mobile apps. For details, see [Mobile Client Comparison Tables](https://go.microsoft.com/fwlink/p/?LinkID=234777) in the Lync Server 2010 documentation. 
  
## Sign-in, Push Notifications, and General Features
<a name="sectionSection0"> </a>

|**Feature/Capability**|**Lync 2013 desktop client**|**Windows Phone**|**iPhone**|**iPad**|**Android**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Lync session remains signed in  <br/> |●  <br/> |●<sup>1</sup> <br/> |●<sup>1</sup> <br/> |●<sup>1</sup> <br/> |●<sup>1</sup> <br/> |
|Support for push notifications  <br/> ||●  <br/> |<sup>4</sup>Not required  <br/> |<sup>4</sup>Not required  <br/> |<sup>4</sup>Not required  <br/> |
|Country code populates based on region settings  <br/> |||●  <br/> |●  <br/> ||
|Account information for multiple users can be cached on the same device  <br/> |●  <br/> |||||
|Screen reader/voice over  <br/> |●  <br/> |●<sup>2</sup>          English only  <br/> |●  <br/> |●  <br/> |●          English only  <br/> |
|Use an external keyboard with Lync  <br/> |||●<sup>3</sup> <br/> |●<sup>3</sup> <br/> |●  <br/> |
|Certificate and passive authentication support for mobile clients (Lync Server only)  <br/> ||●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Microsoft Customer Experience Improvement Program support  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> ||
   
<sup>1</sup> On Windows Phone, Lync signs out automatically if the user has not used the application for a period of time, as follows: 
  
- If the user has enabled push notifications, Lync signs out after 10 days of inactivity.
    
- If the user has not enabled push notifications, Lync signs out after 1 hour.
    
On iPhone and iPad, Lync signs out automatically if the user has not used the application for a period of time, as follows:
  
- If the mobile client has not contacted the server for 10 days due to loss of network connectivity or other issues.
    
<sup>2</sup> In app only. 
  
<sup>3</sup> Must be in VoiceOver mode. 
  
<sup>4</sup>iPhone, iPad, and Android don't require push notifications for receiving messages when an app is running in the background.
  
## Enhanced Presence Support in Lync Mobile Clients
<a name="sectionSection1"> </a>

|**Feature/Capability**|**Lync 2013 desktop client**|**Windows Phone**|**iPhone**|**iPad**|**Android**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Publish and view status  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|View status based on calendar free/busy information  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|View status notes and Out of Office messages  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Add a custom location  <br/> |●  <br/> |||||
|Add a custom note  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Publish status based on calendar free/busy information  <br/> |●<sup>1</sup> <br/> |||||
|Set manual presence state (such as Busy, Do Not Disturb, and so on)  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
   
<sup>1</sup> Lync mobile clients do not update a user's presence based on the user's free/busy calendar information. If a mobile client user is also signed in to the Lync desktop client, the desktop client updates the user's presence based on the user's free/busy calendar information. If the user is signed in to a mobile client only, the user's presence does not update based on free/busy calendar information. 
  
## Contacts and Contact Groups Support in Lync Mobile Clients
<a name="sectionSection2"> </a>

|**Feature/capability**|**Lync 2013 desktop client**|**Windows Phone**|**iPhone**|**iPad**|**Android**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|View Contacts list  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|View contact groups  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|View Frequent Contacts group  <br/> |●  <br/> |||||
|Modify Contacts list  <br/> |●  <br/> |||||
|Tag contacts for status change alerts  <br/> |●  <br/> |||||
|Control privacy relationships  <br/> |●  <br/> |||||
|Search the corporate address book  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Search Contacts list  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Manage contact groups  <br/> |●  <br/> |||||
|Expand distribution groups  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Search for Response Groups  <br/> |●<sup>1</sup> <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Display or hide contact photos  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Pin a contact to your home screen  <br/> ||●  <br/> ||||
   
<sup>1</sup> Not available to Skype for Business Online and/or Office 365 users. 
  
## Instant Messaging Support in Lync Mobile Clients
<a name="sectionSection3"> </a>

|**Feature/capability**|**Lync 2013 desktop client**|**Windows Phone**|**iPhone**|**iPad**|**Android**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Initiate instant messaging (IM) with a contact  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Participate in multiparty IM  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Invite others from within the conversation window  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> ||
|Display current conversations  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Navigate among multiple IM conversations  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Automatically log IM conversations in Exchange  <br/> |●  <br/> |||||
|Send an IM conversation as an email message  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Initiate an email to a contact  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|View missed IM invitations  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Vibrate with incoming IM  <br/> ||●<sup>1</sup> <br/> |●  <br/> |●  <br/> |●  <br/> |
   
<sup>1</sup> This device vibrates every time an IM is received even if the current message in the IM conversation is displayed 
  
## Lync-to-Lync Audio and Video
<a name="sectionSection4"> </a>

|**Feature/Capability**|**Lync 2013 desktop client**|**Windows Phone**|**iPhone**|**iPad**|**Android**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Lync-to-Lync voice  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Lync-to-Lync video  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
   
## Conferencing Support in Lync Mobile Clients
<a name="sectionSection5"> </a>

|**Feature/Capability**|**Lync 2013 desktop client**|**Windows Phone**|**iPhone**|**iPad**|**Android**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Click a link in the meeting reminder to join a meeting (public switched telephone network (PSTN))  <br/> |●  <br/> |●<sup>1</sup> <br/> |●<sup>1</sup> <br/> |●<sup>1</sup> <br/> |●<sup>1</sup> <br/> |
|Click a link in the meeting reminder to join a video or VoIP meeting  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Participate in multiparty IM  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Use dial-out conferencing (server calls the mobile device)  <br/> |●  <br/> |●<sup>2</sup> <br/> |●<sup>2</sup> <br/> |●<sup>2</sup> <br/> |●<sup>2</sup> <br/> |
|Use dial-in audio conferencing  <br/> |●<sup>3</sup> <br/> |||||
|View meeting video  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|View multiparty video (gallery view)  <br/> |●  <br/> |||●  <br/> ||
|Wait in meeting lobby  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Use in-meeting presenter controls  <br/> |●  <br/> |||||
|Access detailed meeting roster for audio conferences  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Access detailed meeting roster for IM conferences  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Share desktop or program  <br/> |●  <br/> |||||
|View shared desktop or program  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> ||
|View shared PowerPoint  <br/> |●  <br/> |●<sup>4</sup> <br/> |●<sup>4</sup> <br/> |●<sup>4</sup> <br/> ||
|Use meeting tools (present Microsoft PowerPoint files, use whiteboard, conduct polls, share files)  <br/> |●  <br/> |||||
|Navigate a list of your meetings  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Join a meeting even if you don't have a Lync account  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> ||
|View more information about meeting participants  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> ||
|Start an unscheduled group conversation with multiple participants directly from your client or device  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> ||
   
<sup>1</sup> For Office 365 users, this feature is available for audio conferencing provider (ACP)-enabled meetings only. 
  
<sup>2</sup> Not available to Office 365 users. 
  
<sup>3</sup> For Skype for Business Online and/or Office 365 users, this feature is available from third-party audio conferencing providers. 
  
<sup>4</sup>A PowerPoint presentation shared by Lync Web App cannot be viewed from Lync Mobile 2013. Annotations made on Lync 2013 Desktop clients are not viewable on mobile devices.
  
## Telephony Support in Lync Mobile Clients
<a name="sectionSection6"> </a>

|**Feature/Capability**|**Lync 2013 desktop client**|**Windows Phone**|**iPhone**|**iPad**|**Android**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|In Lync, tap the call icon to call a contact  <br/> |●<sup>1</sup> <br/> |●<sup>2</sup> <br/> |●<sup>2</sup> <br/> |●<sup>2</sup> <br/> |●<sup>2</sup> <br/> |
|Transfer a call  <br/> |●<sup>1</sup> <br/> |●  <br/> |●  <br/> |●  <br/> ||
|Manage call forwarding  <br/> |●<sup>3</sup> <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Manage team call settings  <br/> |●<sup>3</sup> <br/> |||||
|Manage delegates  <br/> |●<sup>3</sup> <br/> |||||
|Initiate a call to a Response Group  <br/> |●<sup>3</sup> <br/> |||||
|Support emergency services  <br/> |●<sup>4</sup> <br/> |||||
|Make calls on behalf of another contact (manager/delegate scenario)  <br/> |●<sup>3</sup> <br/> |||||
|Handle another contact's calls, if configured as a delegate  <br/> |●<sup>3</sup> <br/> |●<sup>3</sup> <br/> |●<sup>3</sup> <br/> |●<sup>3</sup> <br/> |●<sup>3</sup> <br/> |
|Use Call via Work (Lync Server 2013 places your outgoing calls so that the receiver's caller ID displays your work number instead of your mobile number)  <br/> ||●<sup>3</sup> <br/> |●<sup>3</sup> <br/> |●<sup>3</sup> <br/> |●<sup>3</sup> <br/> |
|Access voice mail  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Use the keypad in Lync  <br/> |●  <br/> |●<sup>3</sup> <br/> |●<sup>3</sup> <br/> |●<sup>3</sup> <br/> |●<sup>3</sup> <br/> |
   
<sup>1</sup> Lync Server 2013, Skype for Business Online, and Office 365 users may call other Lync users and Skype users by tapping the icon. Lync Server 2013 users may also place PSTN calls by tapping the icon. 
  
<sup>2</sup> For on-premises Lync Server 2013 users, on Windows Phone, iPhone, and iPad devices, the user taps the call icon in the contact card and accepts the callback from Lync Server 2013. For Office 365 users, on Windows Phone, iPhone, and iPad devices, when the user taps the call button, a dialog box opens asking the user to confirm that he or she wants to call the number. 
  
<sup>3</sup> Not available to Skype for Business Online and/or Office 365 users. 
  
<sup>4</sup> For Skype for Business Online and/or Office 365 users, this feature is supported by Microsoft partners. 
  
## External User Support in Lync Mobile Clients
<a name="sectionSection7"> </a>

|**Feature/Capability**|**Lync 2013 desktop client**|**Windows Phone**|**iPhone**|**iPad**|**Android**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Initiate IM with a public contact  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Initiate IM with a federated contact  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |●  <br/> |
|Conduct two-party calls with external users  <br/> |●  <br/> |||||
|Conduct multiparty calls with external users  <br/> |●  <br/> |||||
|Use Call via Work to reach a federated contact on their mobile phone by calling their published work number<sup>1</sup> <br/> ||●<sup>2</sup> <br/> |●<sup>2</sup> <br/> |●<sup>2</sup> <br/> |●<sup>2</sup> <br/> |
   
<sup>1</sup> By default, federated users are assigned the External Contacts privacy relationship. To be able to reach a federated contact on their mobile phone by calling their published work number, the federated contact must manually assign you the Colleagues privacy relationship. 
  
<sup>2</sup> Not available to Office 365 users. 
  
## Address Book Integration
<a name="sectionSection8"> </a>

|**Feature/Capability**|**Lync 2013 desktop client**|**Windows Phone**|**iPhone**|**iPad**|**Android**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Call address book contacts  <br/> |||||●  <br/> |
|Make Lync calls to contacts directly from address book  <br/> |||||●  <br/> |
   
## Archiving and Compliance Support in Lync Mobile Clients
<a name="sectionSection9"> </a>

|**Feature/Capability**|**Lync 2013 desktop client**|**Windows Phone**|**iPhone**|**iPad**|**Android**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Provide client-side archiving  <br/> |●  <br/> |||||
|Provide client-side recording  <br/> |●  <br/> |||||
   

