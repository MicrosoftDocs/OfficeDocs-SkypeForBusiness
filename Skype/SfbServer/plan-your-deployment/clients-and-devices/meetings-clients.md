---
title: "Plan for Meetings clients (Web App and Meetings App)"
ms.author: v-lanac
author: lanachin
ms.reviewer: PhillipGarding
manager: serdars
ms.date: 2/16/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 31e95e16-f79f-46c6-b123-973fa56a824e
description: "Summary: IT Professionals should review the support requirements for the Skype for Business Web App and Skype Meetings App while planning for Skype for Business Server. This article is not intended for the users of these apps."
---

# Plan for Meetings clients (Web App and Meetings App)
  
 >[!IMPORTANT]
 >On April 5th, 2019, the Skype for Business Web App and Skype Meetings App have been replaced by the Skype for Business desktop app for Mac users. For more information, please see [Skype for Business desktop app on Mac to replace Skype Meetings App (web)](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Skype-for-Business-desktop-app-on-Mac-to-replace-Skype-Meetings/ba-p/357958).
 
**Summary:** IT Professionals should review the support requirements for the Skype for Business Web App and Skype Meetings App while planning for Skype for Business Server. This article is not intended for the users of these apps.
  
Once you've implemented Skype for Business Server, your organization's users will presumably have the Skype for Business client installed as part of the deployment process. 
  
Later on, those users may create meetings and invite users from outside the organization, and those meeting invitees may not have any version of the Skype for Business client. When those users click the URL for the meeting invite, the lack of a client will be detected and the invitee without a Skype for Business client will be asked to download and install a lightweight, meetings-only client so they can join the meeting.
  
> [!NOTE]
> The Skype for Business Web App and Skype Meetings App are only available when trying to log in to a meeting without having Skype for Business. User help for these apps is at [https://aka.ms/smahelp](https://aka.ms/smahelp). 
  
> [!NOTE]
> You can't pre-install either the Skype for Business Web App or Skype Meetings App, but [smart phone](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-1) and [tablet](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-2) users may be able to install inexpensive mobile clients they can use to attend meetings.
  
By default, the server hosting the meeting will direct the user to download and install Skype for Business Web App to join the meeting. The Skype for Business Web App is stored on the Front End Server and gets sent to the meeting attendee. 
  
For Skype for Business Server, Skype Meetings App (on Windows) and Skype for Business for Mac (on Mac) are available as replacements for Skype for Business Web App beginning with CU5, but providing the replacement apps requires the additional configuration described in [Enable Skype Meetings App to replace Skype for Business Web App (Optional)](../../deploy/deploy-clients/deploy-web-downloadable-clients.md#SMA_Enable).  If Skype for Business for Mac is enabled, users will download the latest version of the app from the Office 365 Content Delivery Network (CDN) rather than from your Skype for Business server. For Skype for Business Server 2019, using Skype for Business for Mac is the only option.
  
Skype Meetings App offers a simplified browser experience for downloading and installing the app and joining meetings, including one-click join for users of Internet Explorer. Skype Meetings App also has many improvements over the Skype for Business Web App for reliability and the meeting experience. 
  
> [!NOTE]
> As of Skype for Business Server 2015 CU5 or later, meetings held using Skype for Business Online will no longer send a clientless user the Skype for Business Web App, they will instead be sent Skype Meetings App (on Windows) or Skype for Business for Mac (on Mac). As of Skype for Business Server 2015 CU5 or later, if you [Enable Skype Meetings App to replace Skype for Business Web App (Optional)](../../deploy/deploy-clients/deploy-web-downloadable-clients.md#SMA_Enable), clientless users will be sent Skype Meetings App or Skype for Business for Mac instead of Skype for Business Web App. 
  
## Software requirements
<a name="OS-Browser"> </a>

To use the Skype for Business Web App, a user must have one of the following supported operating system and browser combinations. 
  
**Operating System and minimum browser support for Skype for Business Web App**

| Operating system | Edge | 32- and 64-bit Internet Explorer 11 or later | 32- and 64-bit Internet Explorer 10 or later | 32- and 64-bit Internet Explorer 9 or later | 32- and 64-bit Version of Safari 6.2.8 - 11.X | 32- and 64-bit Version of Chrome 18.X or later |
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Windows 10  <br/> |Yes  <br/> |Yes  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |Yes &#x2778; <br/> |
|Windows 8.1 &#x2776; <br/> |N/A  <br/> |Yes  <br/> |N/A  <br/> |N/A  <br/> |N/A <br/> |Yes &#x2778; <br/> |
|Windows 8 (Intel based) &#x2776; <br/> |N/A  <br/> |N/A  <br/> |Yes  <br/> |N/A <br/> |N/A  <br/> |Yes &#x2778; <br/> |
|Windows 7 with SP1 &#x2777; <br/> |N/A  <br/> |Yes  <br/> |No  <br/> |No  <br/> |N/A <br/>|Yes &#x2778; <br/> |
|Windows Server 2008 R2 with SP1 &#x2777; <br/> |N/A  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |N/A <br/>|Yes &#x2778; <br/> |
   
&#x2776; The Skype for Business Web App browser plug-in requires a specific sharing plugin to use computer-based voice, video, sharing, and viewing of ongoing screen sharing and other features. A meeting attendee is given the option to install the sharing plug-in either when they join the meeting or when they initiate one of these features. On Windows 8, and Windows 8.1, the sharing plug-in can be installed only if you're running Internet Explorer 10 or Internet Explorer 11 for the desktop. These features are not available with non-desktop versions of Internet Explorer 10 and 11. Note that Firefox is no longer supported.
  
&#x2777; On supported Windows 7 and Windows Server 2008 R2 systems, all features are available including computer-based voice, video, application viewing, application sharing, desktop viewing, and desktop sharing. To use these features, you must install a plug-in when prompted.
  
&#x2778; Accessing the Web App from Chrome on Windows will launch a small program which loads the Web App in an embedded Internet Explorer frame. This program requires one of the supported versions of Internet Explorer be installed for the Web App to load properly.
  
> [!NOTE]
> Office 365 users can use Internet Explorer 10 or later with Skype for Business. 
  
### Skype Meetings App

Skype Meetings App runs as an app on computers using Windows 10, Windows 8.1, Windows 8, Windows 7, with 32- and 64-bit Internet Explorer 11 or later installed. 
  
For any other dependencies, refer to [Supported platforms for Skype Meetings App](https://support.office.com/en-US/client/results?Shownav=true&amp;lcid=1033&amp;ns=SKFBWA&amp;version=15&amp;omkt=en-US&amp;ver=15&amp;HelpID=SfBWebApp4001)
  
### Skype for Business for Mac

Skype for Business for Mac runs on computers using macOS version 10.8 or later. 

## Hardware requirements
<a name="OS-Browser"> </a>

Computer hardware requirements are determined by the operating system and browser. Voice and telephony features require a microphone and speakers, headset with microphone, or equivalent device compatible with the computer. Video features require a video device compatible with the computer. For detailed information about video hardware support and expected video quality, see [Skype for Business client video resolutions](video-resolutions.md).
  
## Network requirements
<a name="Network"> </a>

If a user of Skype for Business Web App or Skype Meetings App experiences meeting connection issues, chances are their organization's network infrastructure is not configured to support Office 365 as described in [Office 365 URLs and IP address ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US). This is the case whether the meeting was created by a user of Skype for Business Online or Skype for Business Server. 
  
If the user is on a network not configured as described, many app features may or may not work and they may not be able to connect to the meeting at all.
  
## Supported Meetings features
<a name="BKMK_Conferencing"> </a>

This table compares the Meetings features available to users of the Skype for Business client, Skype for Business Web App, Skype Meetings App, and Lync Web App. Lync Web App is listed for feature comparison purposes: a user would only be downloading and using Lync Web App if the meeting was hosted on a Lync 2013 server.

| Feature/capability | Skype for Business 2016 or 2019 client | Skype for Business on Mac client | Skype Meetings App | Skype for Business Web App | Lync Web App |
|:-----|:-----|:-----|:-----|:-----|:-----|
|Add computer audio  <br/> |&#x2714;|&#x2714;|&#x2714; (requires plug-in)  <br/> |&#x2714; (requires plug-in)  <br/> |&#x2714; (requires plug-in)  <br/> |
|Add video  <br/> |&#x2714;|&#x2714;|&#x2714; (requires plug-in)  <br/> |&#x2714; (requires plug-in)  <br/> |&#x2714; (requires plug-in)  <br/> |
|Switch audio to a phone for authenticated participants  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Switch audio to a phone for guest participants  <br/> |&#x2714;|&#x2714;|&#x2714;|||
|View multiparty video (gallery view)  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Video-based screen sharing  <br/> |&#x2714;|&#x2714; <br/> |&#x2714;(View-only)  <br/> |||
|Use in-meeting presenter controls  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Access detailed meeting roster  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Participate in multiparty IM  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Set IM messages as high importance  <br/> |&#x2714;|||||
|Share the desktop (if enabled)  <br/> |&#x2714;|&#x2714;|&#x2714; (requires plug-in)  <br/> |&#x2714; (requires plug-in)  <br/> |&#x2714; (requires plug-in)  <br/> |
|Share a program (if enabled)  <br/> |&#x2714;||&#x2714;(requires plug-in)  <br/> |&#x2714;(requires plug-in)  <br/> |&#x2714;(requires plug-in)  <br/> |
|Take control of another user's shared desktop or program  <br/> |&#x2714;||&#x2714; (&#x2776; requires plug-in)  <br/> |&#x2714; (&#x2776; requires plug-in)  <br/> |&#x2714; (&#x2776; requires plug-in)  <br/> |
|Let another user take control of your shared desktop or program  <br/> |&#x2714;|||||
|Add anonymous participants (if enabled)  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Invite participants by name  <br/> |&#x2714;|&#x2714;||||
|Invite participants by phone number  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Invite participants by email  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;|
|Use dial-in audio meetings  <br/> |&#x2714; &#x2777; |&#x2714; &#x2777; |&#x2714; &#x2777; |&#x2714; &#x2777; |&#x2714; &#x2777; |
|Initiate a Meet Now meeting  <br/> |&#x2714;|&#x2714;||||
|Record a meeting  <br/> |&#x2714;|||||
|Add and download attachments  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;|
|Add and present Microsoft PowerPoint files  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Navigate Microsoft PowerPoint files  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Add and edit OneNote meeting notes  <br/> |&#x2714;||Edit only (not add)  <br/> |Edit only (not add)  <br/> |Edit only (not add)  <br/> |
|Use a whiteboard  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;|
|Conduct polls  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;|
|Upload files to share with others  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;|
|Schedule a meeting or conference  <br/> |Outlook or Skype for Business Web Scheduler  <br/> |Outlook or Skype for Business Web Scheduler  <br/> |Skype for Business Web Scheduler  <br/> |Skype for Business Web Scheduler  <br/> |Skype for Business Web Scheduler  <br/> |
|Q&amp;A Manager  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;|
|Disable attendee video  <br/> |&#x2714;|||||
|Disable meeting IM  <br/> |&#x2714;||&#x2714;|&#x2714;|&#x2714;|
|Mute audience  <br/> |&#x2714;|&#x2714;|&#x2714;|&#x2714;|&#x2714;|
|Make everyone an attendee  <br/> |&#x2714;|||||
|Produce Skype Meeting Broadcast  <br/> |&#x2714;|||||
   
 &#x2776;  Participants can't control desktops that are shared by Skype for Business for Mac, Lync for Mac 2011 or Communicator for Mac 2011 users.
  
 &#x2777;  For Skype for Business Online, this feature requires Microsoft PSTN Conferencing, Exchange Unified Messaging, or a 3rd party audio conferencing provider.
  
## Known issues and troubleshooting
<a name="BKMK_Conferencing"> </a>

For End-users, the [online help](https://aka.ms/smahelp) for these apps is readily available. IT Professionals should be aware of the following issues:
  
- If the user is on a network not configured to meet the [Network requirements](meetings-clients.md#Network), many app features may or may not work and they may not be able to connect to the meeting at all.
    
- Some users may have corporate-administered computers with disabled permission to install apps. for those users, neither app is an option, but [smart phone](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-1) and [tablet](https://products.office.com/en-us/skype-for-business/download-app?tab=tabs-2) users may be able to install inexpensive mobile clients they can use to attend meetings.
    
    Other installation issues are also covered in the [help topics](https://support.office.com/en-us/article/Trouble-installing-the-Skype-for-Business-Web-App-plug-in-958fc5f1-2d6f-42e3-815d-a9516c591274?ui=en-US&amp;rs=en-US&amp;ad=US). 
    
- Users may see a firewall warning the first time they run the meetings app. They may be prompted to open ports to optimize the experience, and this may require Admin privileges on the machine they may not have. The app should still function and the user can safely decline to open the requested ports. 
    
- You must have [ActiveX enabled without filtering](https://support.office.com/en-us/article/Turn-off-ActiveX-filtering-for-Skype-for-Business-Web-App-b6de8ff6-ac7e-4e2f-b18c-2f13db643c41?ui=en-US&amp;rs=en-US&amp;ad=US) in Internet Explorer, even if IE is not your default browser. In Skype for Business Web App, an ActiveX control—a small module that adds additional features to a web app or other program—is required for audio, video, and screen sharing.
    
- For some features of Skype for Business Web App to work correctly, you must allow your browser to [save cookies](https://support.office.com/en-us/article/Allow-cookies-for-Skype-Meetings-App-Skype-for-Business-Web-App-2108276b-b5c3-484b-bf2b-dac6eeba4c93) on your computer or device.
    
- You may need to [turn on JavaScript](https://support.office.com/en-us/article/Turn-on-JavaScript-for-Skype-Meetings-App-Skype-for-Business-Web-App-3d997bf9-637c-4fe6-8ee3-9e62bfda52cd) support in your browser for some Skype for Business Web App features to work as expected.
    
### AES Support 

As of Skype for Business Server 2015 CU5, AES is not supported for ASP.NET 4.6 and this may cause Skype Meetings App to fail to start. [Cryptographic requirements due to ASP .NET 4.5](../security/user-and-client-authentication.md#cryptographic-requirements-due-to-asp-net-45) has more details.
  
## See also
<a name="BKMK_Conferencing"> </a>

[Deploy Web downloadable clients in Skype for Business Server](../../deploy/deploy-clients/deploy-web-downloadable-clients.md)

[Supported platforms for Skype Meetings App](https://support.office.com/en-US/client/results?Shownav=true&amp;lcid=1033&amp;ns=SKFBWA&amp;version=15&amp;omkt=en-US&amp;ver=15&amp;HelpID=SfBWebApp4001)
