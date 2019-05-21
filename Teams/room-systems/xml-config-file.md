---
title: "Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file"
ms.author: v-lanac
author: lanachin
ms.reviewer: davgroom
manager: serdars
ms.date: 1/31/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: df418e25-81fd-474d-be16-5cd1ac8145cc
ms.collection: M365-voice
description: "This article discusses remote management of the default settings used by a Microsoft Teams Rooms device, including applying a custom theme."
---

# Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file
 
This article discusses remote management of the default settings used by a Microsoft Teams Rooms device, including applying a custom theme.
  
Updating a master XML file and sending copies to the consoles you manage makes it possible for you to change default settings for remotely managed devices. This article discusses how to create such a file, and links to discussions of how to place them as needed on the remotely managed devices. Using this method, you can also implement Custom Themes on your Microsoft Teams Rooms consoles. 
  
## Creating an XML configuration file

The table below explains the elements shown in this sample SkypeSettings.xml (this is a required file name) configuration file. 
  
```
<SkypeSettings>
  <AutoScreenShare>true</AutoScreenShare>
  <HideMeetingName>true</HideMeetingName>
  <UserAccount>
             <SkypeSignInAddress>RanierConf@contoso.com</SkypeSignInAddress>
             <ExchangeAddress>RanierConf@contoso.com</ExchangeAddress>
             <DomainUsername>Seattle\RanierConf</DomainUsername>
             <Password>password</Password>
             <ConfigureDomain>domain1, domain2</ConfigureDomain>
  </UserAccount>    
  <IsTeamsDefaultClient>false</IsTeamsDefaultClient>
  <BluetoothAdvertisementEnabled>true</BluetoothAdvertisementEnabled>
  <SkypeMeetingsEnabled>false</SkypeMeetingsEnabled> 
  <TeamsMeetingsEnabled>true</TeamsMeetingsEnabled> 
  <DualScreenMode>true</DualScreenMode>
  <SendLogs>                           
             <EmailAddressForLogsAndFeedback>RanierConf@contoso.com</EmailAddressForLogsAndFeedback>
	            <SendLogsAndFeedback>true</SendLogsAndFeedback>
  </SendLogs>
  <Devices>
              <MicrophoneForCommunication>Microsoft LifeChat LX-6000</MicrophoneForCommunication>
              <SpeakerForCommunication>Realtek High Definition Audio</SpeakerForCommunication>
              <DefaultSpeaker>Polycom CX5100</DefaultSpeaker>
  </Devices>
  <Theming> 
    <ThemeName>Custom</ThemeName>
	   <CustomThemeImageUrl>folder path</CustomThemeImageUrl>
      <CustomThemeColor>
	       <RedComponent>100</RedComponent>
	       <GreenComponent>100</GreenComponent>
	       <BlueComponent>100</BlueComponent>
 	     </CustomThemeColor>
  </Theming>
</SkypeSettings>
```

If the XML file is badly formed (meaning a variable value is of the wrong type, elements are out of order, elements are unclosed, and so on), settings found up to the point where the error is found are applied, then the rest of the file is ignored during processing. Any unknown elements in the XML are ignored. If a parameter is omitted, it remains unchanged on the device. If a parameter's value is invalid, its prior value remains unchanged.
  
**XML elements**
 
|Element|Type|Level|Usage|
|:--- |:--- |:--- |:--- |
|\<SkypeSettings\>   |Container for all elements.   ||Required.   |
| \<AutoScreenShare\>  |Boolean &#x2777;  |First &#x2776;  | If true, auto screen share is enabled.  |
|\<HideMeetingName\>   |Boolean &#x2777;  |First &#x2776;  |If true, meeting names are hidden.   |
|\<UserAccount\>   |Container   |First &#x2776;  |Container for credentials parameters.   The sign in address, Exchange address, or email address are usually the same, such as RanierConf<span></span>@contoso.com.   |
|\<SkypeMeetingsEnabled\>  |Boolean &#x2777;  |First &#x2776;  |Enabled by default.   |
|\<SkypeSignInAddress\>   |String  &#x2778;  ||The sign in name for the console's Skype for Business device account.   |
|\<ExchangeAddress\>   |String  &#x2778;  ||The sign in name for the console's Exchange device account.   If the ExchangeAddress is omitted, the SkypeSignInAddress will not automatically be re-used.   |
|\<DomainUsername\>   |String  &#x2778;  ||The domain and user name of the console device, for example Seattle\RanierConf.   |
|\<Password\>   |String 3  || The password parameter is the same password used for the Skype for Business device account sign-in.  |
| \<ConfigureDomain\>  |String  &#x2778;  ||You can list several domains, separated by commas.   |
|\<TeamsMeetingsEnabled\>   |Boolean &#x2777;  |First &#x2776;  |Disabled by default. <br/> <br/> The XML file is considered badly formed if both \<SkypeMeetingsEnabled\> and\<TeamsMeetingsEnabled\> are disabled, but it's acceptable to have both settings enabled at the same time.   |
|\<IsTeamsDefaultClient> |Boolean &#x2777;  |First &#x2776;  |Disabled by default. |
|\<BluetoothAdvertisementEnabled> |Boolean &#x2777;  |First &#x2776;  |Enabled by default. |
|\<DualScreenMode\>  |Boolean &#x2777;  |First &#x2776;  |If true, dual screen mode is enabled. Otherwise the device will use single screen mode.   |
|\<SendLogs\>   |Container   |First &#x2776;  ||
|\<EmailAddressForLogsAndFeedback\>   |String  &#x2778;  ||This sets an optional email address that logs can be sent to when the "Give Feedback" window appears.   |
|\<SendLogsAndFeedback\>   |Boolean &#x2777;  || If true, logs are sent to the admin. If false, only feedback is sent to the admin (and not logs).  |
| \<Devices\>  |Container   |First &#x2776;  | The connected audio device names in the child elements are the same values listed in the Device Manager app. The configuration can contain a device that does not presently exist on the system, such as an A/V device not currently connected to the console. The configuration would be retained for the respective device.  |
|\<MicrophoneForCommunication\>   |String  &#x2778;  ||Sets the microphone that will be used as the recording device in a conference.   |
|\<SpeakerForCommunication\>   |String  &#x2778;  ||Device to be used as speaker for the conference. This setting is used to set the speaker device that will be used hear the audio in a call.   |
|\<DefaultSpeaker\>   |String  &#x2778;  ||Device to be used to play the audio from an HDMI ingest source.   |
| \<Theming\>  |Container   |First &#x2776;  |One of the features that can be applied using an XML file is a Custom Theme for your organization. You will be able to specify a theme name, background image, and color.   |
|\<ThemeName\>   |String  &#x2778;  || Used to identify the theme on the client. The Theme Name options are Default, one of the provided preset themes, or Custom. <br/>  Custom theme names should always use the name *Custom*  . The client UI can be set at the console to the Default or one of the presets, but applying a custom theme must be set remotely by an Administrator. <br/>  Preset themes include: <br/>  Default <br/>  Blue Wave <br/>  Digital Forest <br/>  Dreamcatcher <br/>  Limeade <br/>  Pixel Perfect <br/>  Roadmap <br/>  Sunset <br/>  To disable the current theme, use "No Theme" for the ThemeName.  |
|\<CustomThemeImageUrl\>   |String  &#x2778;  ||Required if using a custom theme, otherwise optional. See the [Custom Theme Images](xml-config-file.md#Themes) section below for more details on the custom theme image.  |
|\<CustomThemeColor\>   |Container   ||Container for the \<RedComponent\>, \<GreenComponent\>, and \<BlueComponent\> values. These values are required if using a custom theme.   |
|\<RedComponent\>   |Byte (0-255)   ||Represents the red color component.   |
|\<GreenComponent\>   |Byte (0-255)   ||Represents the green color component.   |
|\<BlueComponent\>   |Byte (0-255)   ||Represents the blue color component.   |
| | | |
   
&#x2776; All of the first-level elements are optional. If a first-level element is omitted, all of its child parameters remain unchanged on the device.
  
&#x2777; A boolean flag can be any of the following: true, false, 0, or 1. Boolean or numeric values left empty might render the XML malformed so there would be no changes to the settings.
  
 &#x2778; If a string parameter is present, empty, and empty is a valid value, the parameter is cleared on the device.
  
## Manage console settings using an XML configuration file

At startup, if a Microsoft Teams Rooms console finds an XML file named SkypeSettings.xml at the location **C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState**, it will apply the configuration settings indicated by the XML file then delete the XML file.
  
Depending on how many Microsoft Teams Rooms devices your enterprise has and how you choose to manage to configure them, there are a number of ways to place the XML configuration file. Once the file is pushed to the console, restart it to process the configuration changes. The XML configuration file is deleted after it is successfully processed. The management methods suggested for Microsoft Teams Rooms devices are discussed in:
  
- [Configuring Group Policy for Microsoft Teams Rooms](room-systems-v2-operations.md#GroupPolicy)
    
- [Remote Management using PowerShell](room-systems-v2-operations.md#RemotePS) and [Configure a File Item](https://technet.microsoft.com/library/cc772536%28v=ws.11%29.aspx)
    
You are free to use any method you like so long as you can use it to transfer files and trigger a restart on the console device. The file must be readable, writable, and delete-able by the device's local user account (preferably, it should be owned by and have full privileges granted to that user). If the file permissions are not set correctly, the software may fail to apply the settings, may fail to delete the file upon successful processing, and could even potentially crash.
  
## Custom Theme Images
<a name="Themes"> </a>

The custom theme image file must be placed in **C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState**, just enter the file name and extension in the \<CustomThemeImageUrl\> variable.
  
The image file should be exactly 3840X1080 pixels and must be one of the following file formats: jpg, jpeg, png and bmp. If your organization wants a custom image, a graphic designer will find our [Custom Theme Photoshop Template](https://go.microsoft.com/fwlink/?linkid=870441) useful. It contains further detail on where to place various elements in a theme image and what areas appear on consoles and displays.
  
The XML configuration file must be updated at device startup to recognize the theme image. Once the new XML file is processed and deleted, the theme graphic file will be deleted from the directory.
  
## See also


[Manage Microsoft Teams Rooms](skype-room-systems-v2.md)

[Configure a File Item](https://technet.microsoft.com/library/cc772536%28v=ws.11%29.aspx)
