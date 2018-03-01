---
title: "Manage a Skype Room Systems v2 console settings remotely with an XML configuration file"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: df418e25-81fd-474d-be16-5cd1ac8145cc
description: "This article discusses remote management of the default settings used by a Skype Room Systems v2 device, including applying a custom theme."
---

# Manage a Skype Room Systems v2 console settings remotely with an XML configuration file
 
This article discusses remote management of the default settings used by a Skype Room Systems v2 device, including applying a custom theme.
  
Updating a master XML file and sending copies to the consoles you manage makes it possible for you to change default settings for remotely managed devices. This article discusses how to create such a file, and links to discussions of how to place them as needed on the remotely managed devices. Using this method, you can also implement Custom Themes on your Skype Room Systems v2 consoles. 
  
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
             <AutoRotatePassword>1</AutoRotatePassword>
  </UserAccount>    
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

|**Element**|**Type**|**Level**|**Usage**|
|:-----|:-----|:-----|:-----|
|\<SkypeSettings\>  <br/> |Container for all elements.  <br/> ||Required.  <br/> |
| \<AutoScreenShare\> <br/> |Boolean 2 <br/> |First 1 <br/> | If true, auto screen share is enabled. <br/> |
|\<HideMeetingName\>  <br/> |Boolean 2 <br/> |First 1 <br/> |If true, meeting names are hidden.  <br/> |
|\<UserAccount\>  <br/> |Container  <br/> |First 1 <br/> |Container for credentials parameters.  <br/> The sign in address, Exchange address, or email address are usually the same, such as RanierConf@contoso.com.  <br/> |
|\<SkypeMeetingsEnabled\>  <br/> |Boolean 2 <br/> |First 1 <br/> |Enabled by default.  <br/> |
|\<TeamsMeetingsEnabled\>  <br/> |Boolean 2 <br/> |First 1 <br/> |Disabled by default.  <br/> The XML file is considered badly formed if both \<SkypeMeetingsEnabled\> and\<TeamsMeetingsEnabled\> are disabled, but it's acceptable to have both settings enabled at the same time.  <br/> |
|\<SkypeSignInAddress\>  <br/> |String 3 <br/> ||The sign in name for the console's Skype for Business device account.  <br/> |
|\<ExchangeAddress\>  <br/> |String 3 <br/> ||The sign in name for the console's Exchange device account.  <br/> If the ExchangeAddress is omitted, the SkypeSignInAddress will not automatically be re-used.  <br/> |
|\<DomainUsername\>  <br/> |String 3 <br/> ||The domain and user name of the console device, for example Seattle\RanierConf.  <br/> |
|\<Password\>  <br/> |String 3 <br/> || The password parameter is the same password used for the Skype for Business device account sign-in. <br/> |
| \<ConfigureDomain\> <br/> |String 3 <br/> ||You can list several domains, separated by commas.  <br/> |
|\<AutoRotatePassword\>  <br/> |Boolean 2 <br/> |||
| \<DualScreenMode\> <br/> |Boolean 2 <br/> |First 1 <br/> |If true, dual screen mode is enabled. Otherwise the device will use single screen mode.  <br/> |
|\<SendLogs\>  <br/> |Container  <br/> |First 1 <br/> ||
|\<EmailAddressForLogsAndFeedback\>  <br/> |String 3 <br/> ||This sets an optional email address that logs can be sent to when the "Give Feedback" window appears.  <br/> |
|\<SendLogsAndFeedback\>  <br/> |Boolean 2 <br/> || If true, logs are sent to the admin. If false, only feedback is sent to the admin (and not logs). <br/> |
| \<Devices\> <br/> |Container  <br/> |First 1 <br/> | The connected audio device names in the child elements are the same values listed in the Device Manager app. The configuration can contain a device that does not presently exist on the system, such as an A/V device not currently connected to the console. The configuration would be retained for the respective device. <br/> |
|\<MicrophoneForCommunication\>  <br/> |String 3 <br/> ||Sets the microphone that will be used as the recording device in a conference.  <br/> |
|\<SpeakerForCommunication\>  <br/> |String 3 <br/> ||Device to be used as speaker for the conference. This setting is used to set the speaker device that will be used hear the audio in a call.  <br/> |
|\<DefaultSpeaker\>  <br/> |String 3 <br/> ||Device to be used to play the audio from an HDMI ingest source.  <br/> |
| \<Theming\> <br/> |Container  <br/> |First 1 <br/> |One of the features that can be applied using an XML file is a Custom Theme for your organization. You will be able to specify a theme name, background image, and color.  <br/> |
|\<ThemeName\>  <br/> |String 3 <br/> || Used to identify the theme on the client. The Theme Name options are Default, one of the provided preset themes, or Custom. <br/>  Custom theme names should always use the name *Custom*  . The client UI can be set at the console to the Default or one of the presets, but applying a custom theme must be set remotely by an Administrator. <br/>  Preset themes include: <br/>  Default <br/>  Blue Wave <br/>  Digital Forest <br/>  Dreamcatcher <br/>  Limeade <br/>  Pixel Perfect <br/>  Roadmap <br/>  Sunset <br/>  To disable the current theme, use "No Theme" for the ThemeName. <br/> |
|\<CustomThemeImageUrl\>  <br/> |String 3 <br/> ||Required if using a custom theme, otherwise optional. See the [Custom Theme Images](xml-config-file.md#Themes) section below for more details on the custom theme image. <br/> |
|\<CustomThemeColor\>  <br/> |Container  <br/> ||Container for the \<RedComponent\>, \<GreenComponent\>, and \<BlueComponent\> values. These values are required if using a custom theme.  <br/> |
|\<RedComponent\>  <br/> |Byte (0-255)  <br/> ||Represents the red color component.  <br/> |
|\<GreenComponent\>  <br/> |Byte (0-255)  <br/> ||Represents the green color component.  <br/> |
|\<BlueComponent\>  <br/> |Byte (0-255)  <br/> ||Represents the blue color component.  <br/> |
   
1 All of the first-level elements are optional. If a first-level element is omitted, all of its child parameters remain unchanged on the device.
  
2 A boolean flag can be any of the following: true, false, 0, or 1. Boolean or numeric values left empty might render the XML malformed so there would be no changes to the settings.
  
3 If a string parameter is present, empty, and empty is a valid value, the parameter is cleared on the device.
  
## Manage console settings using an XML configuration file

At startup, if a Skype Room Systems v2 console finds an XML file named SkypeSettings.xml at the location ** C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState**, it will apply the configuration settings indicated by the XML file then delete the XML file.
  
Depending on how many Skype Room Systems v2 devices your enterprise has and how you choose to manage to configure them, there are a number of ways to place the XML configuration file. Once the file is pushed to the console, restart it to process the configuration changes. The XML configuration file is deleted after it is successfully processed. The management methods suggested for Skype Room Systems v2 devices are discussed in:
  
- [Configuring Group Policy for Skype Room Systems v2](skype-room-systems-v2.md#GroupPolicy)
    
- [Remote Management using PowerShell](skype-room-systems-v2.md#RemotePS) and[Configure a File Item](https://technet.microsoft.com/en-us/library/cc772536%28v=ws.11%29.aspx)
    
You are free to use any method you like so long as you can use it to transfer files and trigger a restart on the console device. The file must be readable, writable, and delete-able by the device's local user account (preferably, it should be owned by and have full privileges granted to that user). If the file permissions are not set correctly, the software may fail to apply the settings, may fail to delete the file upon successful processing, and could even potentially crash.
  
## Custom Theme Images
<a name="Themes"> </a>

The custom theme image file must be placed in **C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState**, just enter the file name and extension in the <CustomThemeImageUrl> variable.
  
The image file should be exactly 3840X1080 pixels and must be one of the following file formats: jpg, jpeg, png and bmp. If your organization wants a custom image, a graphic designer will find our [Custom Theme Photoshop Template](http://download.microsoft.com/download/9/0/D/90D4826A-9FD2-47D2-B911-97BF1737F4F7/SRS_ThemingTemplate_v1.2.psd) useful. It contains further detail on where to place various elements in a theme image and what areas appear on consoles and displays.
  
The XML configuration file must be updated at device startup to recognize the theme image. Once the new XML file is processed and deleted, the theme graphic file will be deleted from the directory.
  
## See also
<a name="Themes"> </a>

#### 

[Manage Skype Room Systems v2](skype-room-systems-v2.md)
#### 

[Configure a File Item](https://technet.microsoft.com/en-us/library/cc772536%28v=ws.11%29.aspx)

