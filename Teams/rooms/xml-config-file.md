---
title: Remotely manage Microsoft Teams Rooms device settings
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: henrikalim
ms.date: 08/22/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier2
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.assetid: df418e25-81fd-474d-be16-5cd1ac8145cc
ms.custom: 
  - seo-marvel-mar2020
description: Remote management of the default settings used by a Microsoft Teams Rooms device and creating a master settings file.
---

# Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file

This article discusses remote management of the default settings used by a Microsoft Teams Rooms device. It discusses how to create a master settings file and links to discussions of how to place them as needed on Teams Rooms.
  
It is possible for you to change default settings of Teams Rooms by updating a master XML file and sending copies to the remote Teams Rooms devices.

> [!NOTE]
> Some features are available only on Teams Rooms devices that have been assigned a Microsoft Teams Rooms Pro license. To see which features require Microsoft Teams Rooms Pro, see [Microsoft Teams Rooms licenses](rooms-licensing.md).

## Manage console settings with an XML configuration file

At startup, if a Microsoft Teams Rooms console finds an XML file named SkypeSettings.xml located at `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState`, it applies the configuration settings indicated by the XML file then deletes the XML file.
  
Depending on how many Microsoft Teams Rooms devices your enterprise has and how you choose to manage to configure them, there are several ways to place the XML configuration file. Once the file is pushed to the console, restart it to process the configuration changes. The XML configuration file is deleted after it is successfully processed. The management methods suggested for Microsoft Teams Rooms devices are discussed in:
  
- [Configuring Group Policy for Microsoft Teams Rooms](rooms-operations.md#GroupPolicy)
- [Remote Management using PowerShell](rooms-operations.md#RemotePS) and [Configure a File Item](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772536(v=ws.11))

You can use any method you like so long as you can use it to transfer files and trigger a restart on the console device. The file must be readable, writable, and delete-able by the device's local user account. Preferably it is owned by, and has full privileges granted to, device's local user. If the file permissions are not set correctly, the software can fail to apply the settings, can fail to delete the file upon successful processing, and can even potentially crash.
  
## Create an XML configuration file

Any text editor can be used to create a settings file. The **XML Elements** table explains the elements shown in this sample SkypeSettings.xml (required file name) configuration file.
  
```XML
<SkypeSettings>
  <AutoScreenShare>1</AutoScreenShare>
  <HideMeetingName>0</HideMeetingName>
  <AutoExitMeetingEnabled>true</AutoExitMeetingEnabled>
  <AudioRenderDefaultDeviceVolume>50</AudioRenderDefaultDeviceVolume>
  <AudioRenderCommunicationDeviceVolume>50</AudioRenderCommunicationDeviceVolume>
  <UserAccount>
    <SkypeSignInAddress>username@microsoft.com</SkypeSignInAddress>
    <Password>Password!</Password>
  </UserAccount>
  <TeamsMeetingsEnabled>true</TeamsMeetingsEnabled>
  <SfbMeetingEnabled>false</SfbMeetingEnabled>
  <IsTeamsDefaultClient>true</IsTeamsDefaultClient>
  <RequirePasscodeForAllTeamsMeetings>false</RequirePasscodeForAllTeamsMeetings>
  <RequirePasscodeForAllPrivateTeamsMeetings>false</RequirePasscodeForAllPrivateTeamsMeetings>
  <WebExMeetingsEnabled>true</WebExMeetingsEnabled>
  <ZoomMeetingsEnabled>true</ZoomMeetingsEnabled>
  <BlueJeansMeetingsEnabled>true</BlueJeansMeetingsEnabled>
  <UseCustomInfoForThirdPartyMeetings>true</UseCustomInfoForThirdPartyMeetings>
  <CustomDisplayNameForThirdPartyMeetings>guestname</CustomDisplayNameForThirdPartyMeetings>
  <CustomDisplayEmailForThirdPartyMeetings>guest@microsoft.com</CustomDisplayEmailForThirdPartyMeetings>
  <BluetoothAdvertisementEnabled>true</BluetoothAdvertisementEnabled>
  <AutoAcceptProximateMeetingInvitations>true</AutoAcceptProximateMeetingInvitations>
  <AllowRoomRemoteEnabled>true</AllowRoomRemoteEnabled>
  <RoomQRcodeEnabled>true</RoomQRcodeEnabled>
  <QRCodeAutoAcceptProximateMeetingInvitations>true</QRCodeAutoAcceptProximateMeetingInvitations>
  <DualScreenMode>false</DualScreenMode>
  <DuplicateIngestDefault>true</DuplicateIngestDefault>
  <DisableTeamsAudioSharing>false</DisableTeamsAudioSharing>
  <EnableRoomCapacityNotification>true</EnableRoomCapacityNotification>
  <FrontRowEnabled>true</FrontRowEnabled>
  <FrontRowVideoSize>medium</FrontRowVideoSize>
  <FrontRowPanelDefaults>3,2</FrontRowPanelDefaults>
  <SingleFoRDefaultContentLayout>1</SingleFoRDefaultContentLayout>
  <DefaultFoRExperience>0</DefaultFoRExperience>
  <ShowMeetingChat>true</ShowMeetingChat>
  <OpenMeetingChatByDefault>true</OpenMeetingChatByDefault>
  <EnablePublicPreview>false</EnablePublicPreview>
  <NoiseSuppressionDefault>1</NoiseSuppressionDefault>
  <RoomLanguageSwitchEnabled>true</RoomLanguageSwitchEnabled>
  <SendLogs>
    <EmailAddressForLogsAndFeedback>username@microsoft.com</EmailAddressForLogsAndFeedback>
    <SendLogsAndFeedback>true</SendLogsAndFeedback>
  </SendLogs>
 <SendFeedbackToPMP>true</SendFeedbackToPMP>
 <Devices>
    <MicrophoneForCommunication>Device1</MicrophoneForCommunication>
    <SpeakerForCommunication>DeviceX</SpeakerForCommunication>
    <DefaultSpeaker>DeviceX</DefaultSpeaker>
    <ContentCameraId>Camera1</ContentCameraId>
    <ContentCameraEnhancement>true</ContentCameraEnhancement>
    <ContentCameraInverted>false</ContentCameraInverted>
  </Devices>
  <Theming>
       <ThemeName>Custom</ThemeName>
       <CustomBackgroundMainFoRDisplay>file name</CustomBackgroundMainFoRDisplay>
       <CustomBackgroundExtendedFoRDisplay>file name</CustomBackgroundExtendedFoRDisplay>
       <CustomBackgroundConsole>file name</CustomBackgroundConsole>
       <CustomThemeImageUrl>file name</CustomThemeImageUrl>
  </Theming>
  <TeamsRoomsNewExperience>true</TeamsRoomsNewExperience>
  <RemoveFoRCalendar>false</RemoveFoRCalendar>
  <CoordinatedMeetings enabled="true">
    <TrustedAccounts>username1@microsoft.com,username2@contoso.com</TrustedAccounts>
    <Settings>
      <Audio default="true" enabled="true"/>
      <Video default="true" enabled="true"/>
      <Whiteboard default="true" enabled="true"/>
    </Settings>
  </CoordinatedMeetings>
  <EnableResolutionAndScalingSetting>true</EnableResolutionAndScalingSetting> 
  <MainFoRDisplay> 
      <MainFoRDisplayResolution>1920,1080</MainFoRDisplayResolution> 
      <MainFoRDisplayScaling>100</MainFoRDisplayScaling> 
  </MainFoRDisplay> 
  <ExtendedFoRDisplay> 
      <ExtendedFoRDisplayResolution>1920,1080</ExtendedFoRDisplayResolution> 
      <ExtendedFoRDisplayScaling>100</ExtendedFoRDisplayScaling> 
  </ExtendedFoRDisplay>  
  <EnableDeviceEndToEndEncryption>false</EnableDeviceEndToEndEncryption>
  <SplitVideoLayoutsDisabled>false</SplitVideoLayoutsDisabled>
</SkypeSettings>
```

If a variable value is of the wrong type, elements are out of order, elements are unclosed, or another error is found, the XML file is *badly formed*. While processing a badly formed XML file, settings found up to the point where the error occurs are applied, then the rest of the file is ignored. Any unknown elements in the XML are ignored. If a parameter is omitted, it remains unchanged on the device. If a parameter value is invalid, its prior value remains unchanged.

**XML elements**

| Element | Type | Level | Usage |
|:--|:--|:--|:--|
| `<SkypeSettings>` | Container for all elements. |  | Required. |
| `<AutoScreenShare>` | Boolean &#x2777; | First &#x2776; | If true, a connected HDMI ingest will be automatically shared on the Front of Room display and when in a Teams Meeting it will be automatically shared to remote participants. If false, a connected HDMI ingest will be automatically shared on the Front of Room display in and out of a Teams meeting but it will not be shared to remote participants in the meeting automatically, users will need to select the share icon to shared content to remote participants. |
| `<HideMeetingName>` | Boolean &#x2777; | First &#x2776; | If true, meeting names are hidden. |
| `<UserAccount>` | Container | First &#x2776; | Container for credentials parameters. The sign-in address, Exchange address, or email address are usually the same, such as RainierConf<span></span>@contoso.com. |
| `<SkypeSignInAddress>` | String &#x2777; |  | The sign-in name for the console's SfB or Teams device account. |
| `<Password>` | String  &#x2778; |  | The password parameter is the same password used for the Skype for Business device account sign-in. |
| `<TeamsMeetingsEnabled>` | Boolean &#x2777; | First &#x2776; | Disabled by default. <br/> <br/> The XML file is considered badly formed if both `<SkypeMeetingsEnabled>` and`<TeamsMeetingsEnabled>` are disabled, but it's acceptable to have both settings enabled at the same time. |
| `<SfbMeetingEnabled>` | Boolean &#x2777; | First &#x2776; | Disabled by default. |
| `<IsTeamsDefaultClient>` | Boolean &#x2777; | First &#x2776; | Enabled by default. |
| `<RequirePasscodeForAllTeamsMeetings>` | Boolean &#x2777; | First &#x2776; | Disabled by default. <br/> <br/> If true, users are required to enter the correct meeting id and passcode to join all Teams meetings scheduled in the room with a Microsoft Teams Room Pro license.|
| `<RequirePasscodeForAllPrivateTeamsMeetings>` | Boolean &#x2777; | First &#x2776; | Disabled by default. <br/> <br/> If true, users are required to enter the correct meeting id and passcode to join all **private** Teams meetings scheduled in the room with a Microsoft Teams Room Pro license.|
| `<WebExMeetingsEnabled>` | Boolean &#x2777; | First &#x2776; | Disabled by default. <br/> <br/> If true, enables direct guest join experience for Cisco Webex meetings. |
| `<ZoomMeetingsEnabled>` | Boolean &#x2777; | First &#x2776; | Disabled by default. <br/> <br/> If true, enables direct guest join experience for Zoom meetings. |
| `<BlueJeansMeetingsEnabled>` | Boolean &#x2777; | First &#x2776; | Disabled by default. <br/> <br/> If true, enables direct guest join experience for BlueJeans meetings. |
| `<UseCustomInfoForThirdPartyMeetings>` | Boolean &#x2777; | First &#x2776; | Disabled by default and uses conference room account info to join third party meetings. <br/> <br/> If this value is set to true, you must specify both `<CustomDisplayNameForThirdPartyMeetings>`, `<CustomDisplayEmailForThirdPartyMeetings>` must be specified. |
| `<CustomDisplayNameForThirdPartyMeetings>` | String  &#x2778; | First &#x2776; | Specify guest name used to join third party meetings. Third party service will display this data in their experience and may store in their service. |
| `<CustomDisplayEmailForThirdPartyMeetings>` | String  &#x2778; | First &#x2776; | Specify guest email used to join third party meetings. Third party service will display this data in their experience and may store in their service. |
| `<BluetoothAdvertisementEnabled>` | Boolean &#x2777; | First &#x2776; | Enabled by default. |
| `<AutoAcceptProximateMeetingInvitations>` | Boolean &#x2777; | First &#x2776; | If true, proximity based meeting invitations via Bluetooth are automatically accepted. Enabled by default. |
| `<AllowRoomRemoteEnabled>` | Boolean &#x2777; | First &#x2776; | If true, room remote connections are allowed. Enabled by default. |
| `<RoomQRcodeEnabled>` | Boolean &#x2777; | First &#x2776; | If true, a QR code is shown on the home screen. Users can scan the QR code to quickly join meetings with the room system. Enabled by default. For more information, see [Join meetings with QR codes](/microsoftteams/rooms/teams-rooms-qr-codes).|
| `<QRCodeAutoAcceptProximateMeetingInvitations>` | Boolean &#x2777; | First &#x2776; | If true, proximity based meeting invitations via QR code are automatically accepted. Enabled by default. For more information, see [Join meetings with QR codes](/microsoftteams/rooms/teams-rooms-qr-codes).|
| `<AutoExitMeetingEnabled>` | Boolean &#x2777; | First &#x2776; | If true, device will automatically leave the meeting if it is the last participant remaining in the meeting before or after the meeting end time.  Disabled by default. |
| `<DualScreenMode>` | Boolean &#x2777; | First &#x2776; | If true, dual screen mode is enabled. Otherwise the device uses single screen mode. |
| `<DuplicateIngestDefault>` | Boolean &#x2777; | First &#x2776; | If true, content is shown on both screens in dual screen mode, when out of meeting. |
| `<DisableTeamsAudioSharing>` | Boolean &#x2777; | First &#x2776; | Set to true to disable HDMI audio sharing to meeting participants in Teams meeting. The default is false. |
| `<EnableCloudIntelliframe>` | Boolean &#x2777; | First &#x2776; | Enabled by default. If true, Cloud IntelliFrame will be enabled for the Team Room.|
| `<EnableRoomCapacityNotification>` | Boolean &#x2777; | First &#x2776; | Enabled by default to provide warnings to in room participants that the room has reached capacity (this requires the room capacity be set in Exchange and a camera capable of people counting). Set to false if you wish to disable these warnings. |
| `<FrontRowEnabled>` | Boolean &#x2777; | First &#x2776; | Enabled by default. If false, Front row is disabled. For more information, see [Set front row as the default layout](manage-front-row.md).|
| `<FrontRowVideoSize>` | String |  | Lets you set the size of Front row to provide more or less space for remote participant video and shared content. Possible values are `small`, `medium`, and `large`. The default value is `medium`. For more information, see [Set front row as the default layout](manage-front-row.md). |
| `<FrontRowPanelDefaults>` | String | | Lets you configure the position of the raise hand and chat components in the meeting panels to the left and right of meeting content on front-of-room displays.<br> <br>To manually configure the position of the raise hand and chat components, specify the numeric values of the component that should be shown in the left and right panels respectively, separated by a comma (for example, `3,1`).  Panels using the same component will be ignored except for <b>1</b> Hide the panel.<ul><li><b>1</b> Hide the panel.  </li><li><b>2</b> Show meeting chat.</li><li><b>3</b> Show raised hand list.</li></ul><br>If `FrontRowPanelDefaults` isn't specified in dual display mode, the raise hand component is shown in the left panel and chat component is shown in the right panel. In single display mode, the left panel isn't displayed by default for front-of-room displays narrower than 21:9.|
| `<DefaultFoRExperience>` | Boolean &#x2777; | First &#x2776; | Gallery view by default. Put 1 to change the default layout from Gallery view to Front row. For more information, see [Set front row as the default layout](manage-front-row.md). |
| `<EnableResolutionAndScalingSetting>` | Boolean &#x2777; | First &#x2776; | By default it is disabled. If you want to change your front-of-room's resolution and scaling, set it to true. If true, the display resolution and scale setting will be applied. This setting will affect both the main front-of-room display and extended front-of-room display once this setting is enabled. For more information, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](manage-front-room-scale-res.md).|
| `<MainFoRDisplay>` | Container | First &#x2776; | Use this container if your device is using single display mode.<br><br>In dual display mode, the main front-of-room display is the screen where the room calendar is shown. This screen is meant to be installed on the right-hand side.  `<MainFoRDisplayResolution>` and `<MainFoRDisplayScaling>` must be set together at the same time. If you only use either `<MainFoRDisplayResolution>` or `<MainFoRDisplayScaling>`, it will be ignored. For more information, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](manage-front-room-scale-res.md).|
| `<MainFoRDisplayResolution>` | String |  | Input numeric value of Width, Height (e.g. 1920,1080 or 3840,2160). It will be ignored if your front-of-room display does not support it. For more information, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](manage-front-room-scale-res.md).|
| `<MainFoRDisplayScaling>` | Number |  | Input numeric value of scaling. Valid values are 100 (recommended), 125, 150, 175, 200, 225, 250, and 300. If you input greater than and your front-of-room display only supports up to 300, it will be set to 300. For more information, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](manage-front-room-scale-res.md).|
| `<ExtendedFoRDisplay>` | Container | First &#x2776; | In dual display mode, the extended front-of-room display is the screen where the date, time, and room information are displayed. This screen is meant to be installed on the left-hand side.  `<ExtendedFoRDisplayResolution>` and `<ExtendedFoRDisplayScaling>` must be set together at the same time. If you only use either `<ExtendedFoRDisplayResolution>` or `<ExtendedFoRDisplayScaling>`, it will be ignored. For more information, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](manage-front-room-scale-res.md).|
| `<ExtendedFoRDisplayResolution>` | String |  | Input numeric value of Width, Height (e.g. 1920,1080 or 3840,2160). A value will be ignored if your front-of-room display not support it. For more information, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](manage-front-room-scale-res.md).|
| `<ExtendedFoRDisplayScaling>` | Number |  | Input numeric value of scaling. Valid values are 100 (recommended), 125, 150, 175, 200, 225, 250, and 300. If you input greater than 300 and your front-of-room display only supports up to 300, it will be set to 300. For more information, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](manage-front-room-scale-res.md).|
| `<SingleFoRDefaultContentLayout>` | String |  | In single display mode, you can set the default layout between Content+people and Content only:<br><ul><li><b>0</b> Content only</li><li><b>1</b> Content+people (default)</li></ul><br> For more information, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](manage-front-room-scale-res.md).|
| `<ShowMeetingChat>` | Boolean &#x2777; | First &#x2776; |Enabled by default. If disabled, meeting chat functionality (including chat bubbles and chat selection) isn't available in any meeting layout on the Teams Rooms device. |
|`<OpenMeetingChatByDefault>`| Boolean ❷ | First ❶ |Enabled by default. If disabled, chat panel will not show by default in meetings using Gallery view.|
| `<EnablePublicPreview>` | Boolean &#x2777; | First &#x2776; | Disabled by default. If true, public preview is enabled and end-users can access features in public preview on enabled Teams Rooms. See [Public preview for Microsoft Teams Rooms on Windows](../public-preview-doc-updates.md#public-preview-for-microsoft-teams-rooms-on-windows) for more information. |
| `<NoiseSuppressionDefault>` | String | First &#x2776; | Controls noise suppression levels in Teams.<br><ul><li><b>0</b> Off. Use OEM-provided noise suppression only.</li><li><b>1</b> High. Suppresses all background noises (stationary and non-stationary) that aren't speech.</li></ul> |
| `<SendLogs>` | Container | First &#x2776; |  |
|`<SendFeedbackToPMP>`| Boolean ❷ | First ❶ |Enabled by default. If true, when a user sends feedback through Report a problem from a room with a Teams Room Pro license, each feedback creates an event in the Teams Rooms Pro Management portal.|
| `<EmailAddressForLogsAndFeedback>` | String  &#x2778; |  | Sets an email address that receives logs and feedback submitted using Report a problem. |
| `<SendLogsAndFeedback>` | Boolean &#x2777; |  | Allows logs to be sent with feedback submitted using Report a problem. To ensure logs and feedback with larger sizes are delivered, adjust the message size restriction for your mailboxes on the Exchange admin center. |
| `<Devices>` | Container | First &#x2776; | The connected audio device names in the child elements are the same values listed in the Device Manager app. The configuration can contain a device that does not presently exist on the system, such as an A/V device not currently connected to the console. The configuration would be retained for the respective device. |
| `<MicrophoneForCommunication>` | String  &#x2778; |  | Sets the microphone used as the recording device in a conference. |
| `<SpeakerForCommunication>` | String  &#x2778; |  | Device to be used as speaker for the conference. This setting is used to set the speaker device used in a call. |
| `<DefaultSpeaker>` | String  &#x2778; |  | Device to be used to play the audio from an HDMI ingest source. |
| `<ContentCameraId>` | String  &#x2778; |  | Define the instance path for the camera configured in room to share analog whiteboard content in a meeting. See [Locate the Content camera USB instance path](#locate-the-content-camera-usb-instance-path). |
| `<ContentCameraInverted>` | Boolean &#x2777; |  | Specify if the content camera is physically installed upside down. For content cameras that support automatic rotation, specify false. |
| `<ContentCameraEnhancement>` | Boolean &#x2777; |  | When set to true (the default), the content camera image is digitally enhanced: the whiteboard edge is detected and an appropriate zoom is selected, ink lines are enhanced, and the person writing on the whiteboard is made transparent.  <br><br> Set to false if you intend to send a raw video feed to meeting participants for spaces where a whiteboard is not drawn on with a pen and instead the camera is used to show sticky notes, posters, or other media. |
| `<Theming>` | Container | First &#x2776; | One of the features that can be applied with an XML file is a Custom Theme for your organization. You are able to specify a theme name, background image, and color. |
| `<ThemeName>` | String  &#x2778; |  | Used to identify the theme on the client. The Theme Name options are ` Vivid Flag Default`, one of the provided preset themes, or `Custom`. <br/><br>  Custom theme names always use the name `Custom`. The client UI can be set at the console to the Default or one of the presets, but use of a custom theme must be set remotely by an Administrator. <br/>  Preset themes include: <br/>  `Vivid Flag Default`  </br>  `Summer Summit`  <br>  `Seaside Bliss`  </br>  `Into The Fold`  </br>  `Creative Conservatory`  <br/>  `Default`  <br/>  `Blue Wave`  <br/>  `Digital Forest` <br/>  `Dreamcatcher` <br/>  `Limeade` <br/>  `Purple Paradise` <br/>  `Pixel Perfect` <br/>  `Roadmap` <br/>  `Sunset` <br/>  To disable the current theme, use `No Theme` for the `<ThemeName>`. |
| `<CustomBackgroundMainFoRDisplay>` | String  &#x2778; |  | Used to specify the filename of the main/right custom background image on Teams Rooms version 4.17 and later with a Microsoft Teams Rooms Pro license. <br/><br> Required if `<ThemeName>` is set to `Custom`.<br/><br> For more information, see [Set up and manage Teams Rooms on Windows 4.17 and later custom backgrounds](/microsoftteams/rooms/custom-backgrounds?tabs=Enhanced). |
| `<CustomBackgroundExtendedFoRDisplay>` | String  &#x2778; |  | Used to specify the filename of the extended/left custom background image on Teams Rooms version 4.17 with a Microsoft Teams Rooms Pro license. <br/><br> Required if `<ThemeName>` is set to `Custom` **and** `<DualScreenMode>` is set to `true`.<br/><br> For more information, see [Set up and manage Teams Rooms on Windows enhanced custom backgrounds](/microsoftteams/rooms/custom-backgrounds?tabs=Enhanced).|
| `<CustomBackgroundConsole>` | String  &#x2778; |  | Used to specify the filename of the touch console custom background image on Teams Rooms version 4.17 and later  with a Microsoft Teams Rooms Pro license. <br/><br> Optional.<br/><br> For more information, see [Set up and manage Teams Rooms on Windows enhanced custom backgrounds](/microsoftteams/rooms/custom-backgrounds?tabs=Enhanced).|
| `<CustomThemeImageUrl>` | String  &#x2778; |  | Used to specify a custom theme image file name on Teams Rooms version 4.16 and earlier or on devices with a Teams Rooms Basic license. Input the file name only.   For more information on custom themes, see [Set up and manage Teams Rooms on Windows standard custom backgrounds](/microsoftteams/rooms/custom-backgrounds?tabs=Standard). <br><br>On Teams Rooms version 4.17 and later, we recommend you use the `<CustomBackgroundMainFoRDisplay>`, `<CustomBackgroundExtendedFoRDisplay>`, and `<CustomBackgroundConsole>` elements.  |
| `<TeamsRoomsNewExperience>`| Boolean &#x2777; |   | Enable or disable the refreshed home screen design on front-of-room displays and the console. Starting with version 4.17, the refreshed home screen design is enabled by default. For more information, see [Microsoft Teams Rooms home screen design refresh](mtr-home-refresh.md).  |
| `<RemoveFoRCalendar>`| Boolean &#x2777; |   | Remove the calendar on front-of-room displays. Disabled by default. For more information, see [Microsoft Teams Rooms home screen design refresh](mtr-home-refresh.md).  |
| `<CoordinatedMeetings>` | Boolean &#x2777; | First &#x2776; | Container for the configuration elements for Coordinated Meetings. This element has one attribute:<ul><li><b>enabled</b> Determines whether Teams is configured to participate in Coordinated Meetings with other devices.</li></ul> |
| `<TrustedAccounts>` | String |  | This is a comma-separated list of UPNs for each Teams Rooms device or Surface Hub that the device should accept meeting join requests from, or to which meeting join requests should be sent. |
| `<Settings>` | Container |  | Container for the configuration audio and video configuration elements for Coordinated Meetings. |
| `<Audio>` | Boolean &#x2777; |  | Controls audio configuration on a Teams Rooms device. This element has two attributes:<br><ul><li><b>default</b> Determines on which device the microphone will be active when a meeting starts. Only one device (typically a Teams Rooms device) can have this field set to `true` while the rest of the devices must have this field set to `false` to avoid audio echo and feedback.</li><li><b>enabled</b> Determines whether participants in a meeting can toggle the microphone on or off. Devices on which **Audio default** is set to `false` should have this setting set to `false` so that participants can't accidentally turn on a microphone and cause audio echo or feedback.<p>If **Audio default** is set to `true`, the **Audio enabled** setting is ignored and participants can mute or unmute the microphone.</li></ul> |
| `<Video>` | Boolean &#x2777; |  | Controls video configuration on a Teams Rooms device. This element has two attributes:<br><ul><li><b>default</b> Determines on which device the camera will be active when a meeting starts. For the best experience, we recommend that only the Teams Rooms device be set to `true` while all other devices are set to `false`.</li><li><b>enabled</b> Determines whether participants in a meeting can toggle the camera on or off. You can set this to `true` on any other devices in the event participants want to share different video perspectives (such as if a participant is using the Surface Hub whiteboard). If you don't want participants to turn a camera on or off on a device, set this to `false`.<p> If **Video default** is set to `true`, the **Video enabled** setting is ignored and participants can turn the camera on or off.</li></ul> |
| `<Whiteboard>` | Boolean &#x2777; |  | Controls whiteboard configuration on a Teams Rooms device. This element has two attributes:<br><ul><li><b>default</b> Determines on which device the whiteboard will be active when a meeting starts. For the best experience, we recommend that the Teams Rooms device be set to `false` and that you use the whiteboard on a Surface Hub.</li><li><b>enabled</b> Determines whether participants in a meeting can toggle the whiteboard on or off. If you don't want participants to turn the whiteboard on or off on a device, set this to `false`.<p> If **Whiteboard default** is set to `true`, the **Whiteboard enabled** setting is ignored and participants can turn the whiteboard on or off.</li></ul> |
| `<EnableDeviceEndToEndEncryption>` | Boolean &#x2777; |  | Default is `false`. Specify `true` to enable end-to-end encryption for one-to-one Teams calls. Both caller and recipient need to have end-to-end encryption enabled for this to work. |
| `<RoomLanguageSwitchEnabled>` | Boolean &#x2777; |  | Default is `true`. Specify `false` to block end users from changing the console language. |
| `<SplitVideoLayoutsDisabled>` | Boolean &#x2777; |  | Default is `false`. This setting is only applicable to dual-display rooms. Specify `true` to disable splitting video gallery across both screens. This will also disable Front row layout, and any settings associated with Front row layout. |

&#x2776; All of the first-level elements are optional. If a first-level element is omitted, all of its child parameters remain unchanged on the device.
  
&#x2777; A boolean flag can be: true, false, 0, or 1. Leaving boolean or numeric values empty can render the XML malformed and prevent changes to the settings.
  
&#x2778; If a string parameter is present and empty, and empty is a valid value, the parameter is cleared on the device.
  

## Supported Meeting modes App version 4.9

**Skype for Business (default) and Microsoft Teams**

| XML Notation                | XML Value      |
|----------------------------|---------------|
| `<TeamsMeetingsEnabled>`     |   True         |
| `<SfbMeetingEnabled>`        |   True         |
| `<IsTeamsDefaultClient>`     |   False        |

**Skype for Business and Microsoft Teams (default)**

| XML Notation                | XML Value      |
|----------------------------|---------------|
| `<TeamsMeetingsEnabled>`    |   True         |
| `<SfbMeetingEnabled>`        |   True         |
| `<IsTeamsDefaultClient>`     |   True        |

**Skype for Business only**

| XML Notation                | XML Value      |
|----------------------------|---------------|
| `<TeamsMeetingsEnabled>`    |   False         |
| `<SfbMeetingEnabled>`        |   True         |
| `<IsTeamsDefaultClient>`     |   False        |

**Microsoft Teams only**

| XML Notation                | XML Value      |
|----------------------------|---------------|
| `<TeamsMeetingsEnabled>`    |   True         |
| `<SfbMeetingEnabled>`        |   False         |
| `<IsTeamsDefaultClient>`     |   True        |


## Supported Meeting modes App version 4.8 or lower

**Skype for Business (default) and Microsoft Teams**

| XML Notation                | XML Value      |
|----------------------------|---------------|
|  `<TeamsMeetingsEnabled>`     |   True         |
|  `<IsTeamsDefaultClient>`     |   False        |

**Skype for Business and Microsoft Teams (default)**

| XML Notation                | XML Value      |
|----------------------------|---------------|
|  `<TeamsMeetingsEnabled>`     |   True         |
|  `<IsTeamsDefaultClient>`     |   True         |

**Skype for Business only**

| XML Notation                | XML Value      |
|----------------------------|---------------|
|  `<TeamsMeetingsEnabled>`     |   False         |
|  `<IsTeamsDefaultClient>`     |   False         |

## Locate the Content camera USB instance path

To locate the instance path:

1. Go into Windows settings on the Microsoft Teams Rooms console.
2. Enter the admin password.
3. From a Command Prompt, type `devmgmt.msc` to bring up Device Manager.
4. In **Device Manager**, look in the **Imaging devices** node and  locate the content camera.
5. Right-click the camera, and open **Properties**.
6. Select the **Details** tab, and locate the **Device instance path** property in the drop-down.
7. The value shown is the device instance path to set in the XML configuration file. When specifying the path in XML, replace the ampersand (&) with `&amp;`.

## See also

[Content cameras](content-camera.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)

[Configure a File Item](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772536(v=ws.11))
