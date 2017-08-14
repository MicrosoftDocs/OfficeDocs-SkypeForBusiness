---
title: Plan for Web downloadable clients
ms.prod: SKYPEFORBUSINESS
ms.assetid: 31e95e16-f79f-46c6-b123-973fa56a824e
---


# Plan for Web downloadable clients
[] **Summary:** Review the support requirements for the Skype for Business Web App and Skype Meetings App while planning for Skype for Business.
Whenever a user clicks a meeting URL but does not have the Skype for Business client installed, the user is presented with the option to join the meeting by using Skype for Business Web App. The default server behavior is to interact with a user to download and install Skype for Business Web App to join the meeting. Starting with CU5, Skype Meetings App is available as a replacement for Skype for Business Web App. Skype Meetings App offers a simplified browser experience for downloading and installing the app and joining meetings, including one-click join for users of Internet Explorer. Skype Meetings App also has many improvements over theSkype for Business Web App for reliability and the meeting experience. 
  
    
    

If Skype Meetings App is enabled, users will download the latest version of the app from the online Content Delivery Network (CDN) rather than from your Skype for Business server.
Skype for Business Server 2015 works with the Skype for Business Web App by default. The Skype for Business Web App is stored on the Front End Server and gets sent to the meeting attendee.
  
    
    


> [!NOTE]
>  A browser plug-in is required for certain Skype for Business Web App features, including computer-based voice, video, sharing, and viewing of ongoing screen sharing. A meeting attendee can install the sharing plug-in either when they join the meeting or when they initiate one of these features.1>  Office 365 users can use Internet Explorer 10 or later with Skype for Business.
  
    
    


> [!NOTE]
> As of Skype for Business Server 2015 CU5 or later, meetings held using Skype for Business Online will no longer send a clientless user the Skype for Business Web App, they will instead be sent Skype Meetings App. As of Skype for Business Server 2015 CU5 or later, if you  [Enable Skype Meetings App to replace Skype for Business Web App (Optional)](deploy-web-downloadable-clients-in-skype-for-business-server-2015.md#SMA_Enable), clientless users will be sent Skype Meetings App instead of Skype for Business Web App. 
  
    
    


## Software requirements
<a name="OS-Browser"> </a>

To use the Skype for Business Web App, a user must have one of the following supported operating system and browser combinations. 
  
    
    

**Operating System and browser support for Skype for Business Web App**

|
|
|**Operating system**|**Edge**|**32- and 64-bit Internet Explorer 11**|**32-bit Internet Explorer 10**|**64-bit Internet Explorer 10**|**32-bit Internet Explorer 9**|**64-bit Internet Explorer 9**|**32-bit Version of Firefox 12.X**|**64-bit Versions of Safari 5.X, 6.X, 7.X**|**32-bit Version of Chrome 18.X**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Windows 10  <br/> |Yes  <br/> |Yes  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |Yes  <br/> |N/A  <br/> |Yes4 <br/> |
| Windows 8.11 <br/> |N/A  <br/> |Yes  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |Yes  <br/> |N/A  <br/> |Yes4 <br/> |
| Windows 8 (Intel based)1 <br/> |N/A  <br/> |N/A  <br/> |Yes  <br/> |Yes  <br/> |N/A  <br/> |N/A  <br/> |Yes  <br/> |N/A  <br/> |Yes4 <br/> |
|Windows 7 with SP12 <br/> |N/A  <br/> |Yes  <br/> |No  <br/> |No  <br/> |No  <br/> |No  <br/> |Yes  <br/> |No  <br/> |Yes4 <br/> |
|Windows Server 2008 R2 with SP12 <br/> |N/A  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |Yes4 <br/> |
|Mac OS X 10.8 and later (Intel-based)2 <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |Yes  <br/> |Yes  <br/> |Yes4 <br/> |
   
1 On Windows 8, and Windows 8.1, the plug-in required to use computer-based audio, video, application viewing, application sharing, desktop viewing, and desktop sharing can be installed only if you're running Internet Explorer 10 or Internet Explorer 11 for the desktop. These features are not available with non-desktop versions of Internet Explorer 10 and 11.
  
    
    
2 On supported Windows 7, Windows Server 2008 R2, and Macintosh operating systems, all features are available including computer-based voice, video, application viewing, application sharing, desktop viewing, and desktop sharing. To use these features, you must install a plug-in when prompted. Note that Mac OS X version 10.7 is no longer supported.
  
    
    
3 On supported Windows Server 2008 operating systems, computer-based voice and video are not available. Application viewing, application sharing, desktop viewing, and desktop sharing are available.
  
    
    
4 Accessing the Web App from Chrome will launch an small program which loads the Web App in an embedded Internet Explorer frame. This program requires one of the supported versions of Internet Explorer be installed for the Web App to load properly.
  
    
    

### Skype Meetings App

The Skype Meetings App runs as an app on computers using Windows 10, Windows 8.1, Windows 8, or Windows 7 operating systems. There are no browser dependencies.
  
    
    
For any other dependencies, refer to  [Supported platforms for Skype Meetings App](https://support.office.com/en-US/client/results?Shownav=true&amp;lcid=1033&amp;ns=SKFBWA&amp;version=15&amp;omkt=en-US&amp;ver=15&amp;HelpID=SfBWebApp4001)
  
    
    

## Hardware requirements
<a name="OS-Browser"> </a>

Computer hardware requirements are determined by the operating system and browser. Voice and telephony features require a microphone and speakers, headset with microphone, or equivalent device compatible with the computer. Video features require a video device compatible with the computer. For detailed information about video hardware support and expected video quality, see  [Skype for Business client video requirements](skype-for-business-client-video-requirements.md).
  
    
    

## Network requirements
<a name="Network"> </a>

In order for an individual to use Skype for Business Web App or Skype Meetings App, their organization's network infrastructure will still need to be configured to support Office 365 as described in  [Office 365 URLs and IP address ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US). This is the case whether the meeting was created by a user of Skype for Business Online or Skype for Business Server 2015. If the user is on a network not configured as described, app features may or may not work.
  
    
    

## Supported Meetings features
<a name="BKMK_Conferencing"> </a>

This table compares the Meetings features available to users of the Skype for Business client, Skype for Business Web App, Skype Meetings App, and Lync Web App. Lync Web App is listed for feature comparison purposes: a user would only be downloading and using Lync Web App if the meeting was hosted on a Lync 2013 server.
  
    
    
.
  
    
    

|
|
|****Feature/capability****|****Skype for Business 2016** client**|****Skype Meetings App****|****Skype for Business Web App****|****Lync Web App****|
|:-----|:-----|:-----|:-----|:-----|
|Add computer audio  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)(requires plug-in)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)(requires plug-in)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)(requires plug-in)  <br/> |
|Add video  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)(requires plug-in)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)(requires plug-in)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)(requires plug-in)  <br/> |
|View multiparty video (gallery view)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|
|Video-based screen sharing  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)(View-only)  <br/> |||
|Use in-meeting presenter controls  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|
|Access detailed meeting roster  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|
|Participate in multiparty IM  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|
|Share the desktop (if enabled)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)![read footnote 1](images/817e529d-a5e1-4969-a195-f3ba3c6a2e7f.png)(requires plug-in)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)![read footnote 1](images/817e529d-a5e1-4969-a195-f3ba3c6a2e7f.png)(requires plug-in)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)![read footnote 1](images/817e529d-a5e1-4969-a195-f3ba3c6a2e7f.png)(requires plug-in)  <br/> |
|Share a program (if enabled)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)(requires plug-in)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)(requires plug-in)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)(requires plug-in)  <br/> |
|Add anonymous participants (if enabled)  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|
|Use dial-in audio meetings  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)![read footnote 2](images/e366e0ee-8e3f-4e83-8009-2e7eb5674a18.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)![read footnote 2](images/e366e0ee-8e3f-4e83-8009-2e7eb5674a18.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)![read footnote 2](images/e366e0ee-8e3f-4e83-8009-2e7eb5674a18.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)![read footnote 2](images/e366e0ee-8e3f-4e83-8009-2e7eb5674a18.png)|
|Initiate a Meet Now meeting  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)||||
|Add and present Microsoft PowerPoint files  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|
|Navigate Microsoft PowerPoint files  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|
|Add and edit OneNote meeting notes  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|Edit only (not add)  <br/> |Edit only (not add)  <br/> |Edit only (not add)  <br/> |
|Use a whiteboard  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|
|Conduct polls  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|
|Upload files to share with others  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|
|Schedule a meeting or conference  <br/> |Outlook or Skype for Business Web Scheduler  <br/> |Skype for Business Web Scheduler  <br/> |Skype for Business Web Scheduler  <br/> |Skype for Business Web Scheduler  <br/> |
|Q&amp;A Manager  <br/> |![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|![checklist check-off](images/d551a87b-3ffe-4d16-b190-352a2042f65d.png)|
   

  
    
    
![read footnote 1](images/817e529d-a5e1-4969-a195-f3ba3c6a2e7f.png)
  
    
    
 Participants can't control desktops that are shared by Lync for Mac 2011 or Communicator for Mac 2011 users. Lync for Mac 2011 and Communicator for Mac 2011 users can control desktops shared by Windows users. This also won't work for Skype for Business Web App on Max OSX.
  
    
    

  
    
    
![read footnote 2](images/e366e0ee-8e3f-4e83-8009-2e7eb5674a18.png)
  
    
    
 For Skype for Business Online, this feature requires Microsoft PSTN Conferencing, Exchange Unified Messaging, or a 3rd party audio conferencing provider.
  
    
    

  
    
    
![read footnote 3](images/f58a4c2c-e4b3-4954-9eee-1d5f7a89da53.png)
  
    
    
 The Lync for Mac 2011 client cannot view Microsoft Office 2013 PowerPoint presentations when they have been shared in a conference by the Skype for Business Web App.
  
    
    

## See also
<a name="BKMK_Conferencing"> </a>


#### 


  
    
    
 [Deploy Web downloadable clients in Skype for Business Server 2015](deploy-web-downloadable-clients-in-skype-for-business-server-2015.md)
#### 


  
    
    
 [Supported platforms for Skype Meetings App](https://support.office.com/en-US/client/results?Shownav=true&amp;lcid=1033&amp;ns=SKFBWA&amp;version=15&amp;omkt=en-US&amp;ver=15&amp;HelpID=SfBWebApp4001)
