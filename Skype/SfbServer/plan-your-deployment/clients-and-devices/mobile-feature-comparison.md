---
title: "Mobile client feature comparison for Skype for Business"
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
ms.assetid: b2c950c9-76a5-400a-b146-9b1a22790c12

description: "Summary: Review the feature support for the mobile client while planning for Skype for Business Server."
---

# Mobile client feature comparison for Skype for Business
 
**Summary:** Review the feature support for the mobile client while planning for Skype for Business Server.
  
This article compares the features and capabilities among Skype for Business mobile clients and the Skype for Business desktop client in the following categories:
  
- Sign-in, push notifications, and general features
    
- Enhanced presence
    
- Contacts and contact groups
    
- Instant messaging (IM)
    
- Skype for Business to Skype for Business audio and video
    
- Conferencing
    
- Telephony
    
- External users
    
- Archiving and compliance
    
-  Modern Authentication
    
The following tables list the features that are available to Skype for Business users in an on-premises deployment of Skype for Business Server. The same features are also available to Skype for Business Online and Microsoft Office 365 users, unless otherwise indicated in the table footnotes.
  
> [!NOTE]
> For online help and resources for end users, see [Discover Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=528686). 
  
> [!NOTE]
> To compare the features available in other Skype for Business clients, see [Desktop client feature comparison for Skype for Business](desktop-feature-comparison.md). 

> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
  
## Sign-in, push notifications, and general features

 
 | Feature/capability  | Skype for Business desktop client  | Windows Phone  | iOS  | Android |
|:-----|:-----|:-----|:-----|:-----|
|Skype for Business session remains signed in  <br/> |&#x2714;|&#x2714; &#x2776; |&#x2714; &#x2776; |&#x2714;|
|Support for push notifications  <br/> |&#x2714; &#x2778; |&#x2714;|&#x2714;|&#x2714;|
|Account information for multiple users can be cached on the same device  <br/> |&#x2714;||||
|Screen reader/voice over  <br/> |&#x2714;|&#x2714; &#x2777;           English only  <br/> |&#x2714;|&#x2714;|
|Use an external keyboard for accessibility  <br/> |&#x2714;||&#x2714;|&#x2714;|
|Microsoft Customer Experience Improvement Program support  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
   
 &#x2776;  On Windows Phone, Skype for Business signs out automatically after a period of inactivity, as follows:
  
- If the user has enabled push notifications, Skype for Business signs out after 10 days of inactivity.
    
- If the user has not enabled push notifications, Skype for Business signs out as soon as the user leaves the app.
    
On iOS devices, Skype for Business signs out automatically after the mobile client has not contacted the server for 10 days due to loss of network connectivity or other issues.
  
 &#x2777;  In app only.
  
 &#x2778;  Notifications are available when the app is running in the background.
  
## Enhanced presence support


 | Feature/capability  | Skype for Business desktop client  | Windows Phone  | iOS  | Android |
|:-----|:-----|:-----|:-----|:-----|
|Publish and view status  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|View status based on calendar free/busy information  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|View status notes and Out of Office messages  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Add a custom location  <br/> |&#x2714;||||
|Add a custom note  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Publish status based on calendar free/busy information  <br/> |&#x2714; &#x2776; ||||
|Set manual presence state (such as Busy, Do Not Disturb, and so on)  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
   
 &#x2776;  Skype for Business mobile clients do not update a user's presence based on the user's free/busy calendar information. If a mobile client user is also signed in to the Skype for Business desktop client, the desktop client updates the user's presence based on the user's free/busy calendar information. If the user is signed in to a mobile client only, the user's presence does not update based on free/busy calendar information.
  
## Contacts and contact groups support


 | Feature/capability  | Skype for Business desktop client  | Windows Phone  | iOS  | Android |
|:-----|:-----|:-----|:-----|:-----|
|View Contacts list  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|View contact groups  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|View Frequent Contacts group  <br/> |&#x2714;||||
|Modify Contacts list  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Tag contacts for status change alerts  <br/> |&#x2714;||||
|Control privacy relationships  <br/> |&#x2714;||||
|Search the corporate address book  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Search Contacts list  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Manage contact groups  <br/> |&#x2714;|||&#x2714;|
|Expand distribution groups  <br/> |&#x2714;|&#x2714;||&#x2714;|
|Search for Response Groups  <br/> |&#x2714; &#x2776; |&#x2714;||&#x2714;|
|Display or hide contact photos  <br/> |&#x2714;|&#x2714;|||
|Pin a contact to your home screen  <br/> ||&#x2714;|||
   
 &#x2776;  Not available to Skype for Business Online and/or Office 365 users.
  
## Instant Messaging support


 | Feature/capability  | Skype for Business desktop client  | Windows Phone  | iOS  | Android |
|:-----|:-----|:-----|:-----|:-----|
|Initiate instant messaging (IM) with a contact  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Participate in multiparty IM  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Invite others from within the conversation window  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Display current conversations  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Navigate among multiple IM conversations  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Automatically log IM conversations in Exchange  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Send an IM conversation as an email message  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Initiate an email to a contact  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|View missed IM invitations  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Vibrate with incoming IM  <br/> ||&#x2714; &#x2776; |&#x2714;|&#x2714;|
   
 &#x2776;  This device vibrates every time an IM is received even if the current message in the IM conversation is displayed
  
## Skype for Business to Skype for Business audio and video


 | Feature/capability  | Skype for Business desktop client  | Windows Phone  | iOS  | Android |
|:-----|:-----|:-----|:-----|:-----|
|Skype for Business-to-Skype for Business voice  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Skype for Business-to-Skype for Business video  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
   
> [!NOTE]
> Video on a mobile device requires a WiFi connection by default. 
  
## Conferencing support


 | Feature/capability  | Skype for Business desktop client  | Windows Phone  | iOS  | Android |
|:-----|:-----|:-----|:-----|:-----|
|Click a link in the meeting reminder to join a video or VoIP meeting  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Participate in multiparty IM  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Use dial-out conferencing (server calls the mobile device)  <br/> |&#x2714; &#x2776; |&#x2714; &#x2776; |&#x2714; &#x2776; |&#x2714; &#x2776; |
|Use dial-in audio conferencing  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|View meeting video  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|View multiparty video (gallery view)  <br/> |&#x2714;||||
|Wait in meeting lobby  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Use in-meeting presenter controls  <br/> |&#x2714;||||
|Access detailed meeting roster for audio conferences  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Access detailed meeting roster for IM conferences  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Share desktop or program  <br/> |&#x2714;||||
|View shared desktop or program (VbSS or RDP)  <br/> |&#x2714;|&#x2714; &#x2777; |&#x2714; &#x2777; |&#x2714; &#x2777; |
|View shared PowerPoint files  <br/> |&#x2714;|&#x2714; &#x2777; |&#x2714; &#x2777;&#x2778; |&#x2714; &#x2777; &#x2778;|
|Upload and present PowerPoint files  <br/> |&#x2714;||&#x2714; &#x2777; |&#x2714; &#x2777; |
|Use meeting tools (use whiteboard, conduct polls, share files)  <br/> |&#x2714;||||
|Navigate a list of your meetings  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Join a meeting even if you don't have a Skype for Business account  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|View more information about meeting participants  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Start an unscheduled group conversation with multiple participants directly from your client or device  <br/> |&#x2714;|&#x2714;|&#x2714;||
   
 &#x2776;  For Office 365 users, this feature requires Enterprise Voice, which is part of the E5 license.
  
 &#x2777;  Requires a WiFi connection by default.
 
 &#x2778;  Viewing embedded video in PowerPoint presentations is not supported.
  
## Telephony support


 | Feature/capability  | Skype for Business desktop client  | Windows Phone  | iOS  | Android |
|:-----|:-----|:-----|:-----|:-----|
|In Skype for Business, tap the call icon to call a contact  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Transfer a call  <br/> |&#x2714;|&#x2714;|&#x2714;||
|Consultative Transfer  <br/> |&#x2714; &#x2778; ||||
|Manage call forwarding  <br/> |&#x2714; &#x2776; |&#x2714;|&#x2714;|&#x2714;|
|Manage team call settings  <br/> |&#x2714; &#x2776; ||||
|Manage delegates  <br/> |&#x2714; &#x2776; ||||
|Initiate a call to a Response Group  <br/> |&#x2714; &#x2776; ||||
|Support emergency services  <br/> |&#x2714; &#x2777; ||||
|Make calls on behalf of another contact (manager/delegate scenario)  <br/> |&#x2714; &#x2776; ||||
|Handle another contact's calls, if configured as a delegate  <br/> |&#x2714; &#x2776; |&#x2714; &#x2776; |&#x2714; &#x2776; |&#x2714; &#x2776; |
|Use Call via Work  <br/> |&#x2714; &#x2776; |&#x2714;|&#x2714;||
|Access voice mail  <br/> |&#x2714;|&#x2714;|&#x2714;||
|Use the keypad in Skype for Business  <br/> |&#x2714; &#x2776; |&#x2714;|&#x2714;||
   
 &#x2776;  Available to Skype for Business Online and/or Office 365 E5 users, and users homed on Skype for Business Server or Lync Server 2013 with Enterprise Voice enabled.
  
 &#x2777;  For Skype for Business Online and/or Office 365 users, this feature is supported by Microsoft partners.
  
 &#x2778;  Windows Desktop client only.
  
## External user support


 | Feature/capability  | Skype for Business desktop client  | Windows Phone  | iOS  | Android |
|:-----|:-----|:-----|:-----|:-----|
|Initiate IM with a public contact  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Initiate IM with a federated contact  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Conduct two-party calls with external users  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Conduct multiparty calls with external users  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Use Call via Work to reach a federated contact on their mobile phone by calling their published work number  &#x2776;            <br/> ||&#x2714;|&#x2714;|&#x2714;|
   
 &#x2776;  By default, federated users are assigned the External Contacts privacy relationship. To be able to reach a federated contact on their mobile phone by calling their published work number, the federated contact must manually assign you the Colleagues privacy relationship.
  
## Address book integration


 | Feature/capability  | Skype for Business desktop client  | Windows Phone  | iOS  | Android |
|:-----|:-----|:-----|:-----|:-----|
|Call device address book contacts  <br/> ||&#x2714;|&#x2714;|&#x2714;|
|Make Skype for Business calls to contacts directly from device address book  <br/> ||||&#x2714;|
   
## Archiving and compliance support


 | Feature/capability  | Skype for Business desktop client  | Windows Phone  | iOS  | Android |
|:-----|:-----|:-----|:-----|:-----|
|Provide client-side archiving  <br/> |&#x2714;||||
|Provide client-side recording  <br/> |&#x2714; &#x2776; ||||
   
 &#x2776;  Not available to Skype for Business Online and/or Office 365 users.
  
## Modern Authentication

This table covers features requiring support for modern authentication.
  
Modern authentication also requires a topology described in [Skype for Business topologies supported with Modern Authentication](../../plan-your-deployment/modern-authentication/topologies-supported.md).
  

 | Feature/capability  | Skype for Business desktop client  | Windows Phone  | iOS  | Android |
|:-----|:-----|:-----|:-----|:-----|
|Modern Authentication  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Multi-factor Authentication  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Cert -Based Authentication  <br/> |&#x2714;(Domain-joined device only)  <br/> ||&#x2714;|&#x2714;|
|Mobile Application Management (via Intune)  <br/> |||&#x2714;|&#x2714;|
   

