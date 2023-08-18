---
title: What is Microsoft Intelligent camera
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: vishnuna
ms.date: 08/18/2023
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-voice
  - Teams_ITAdmin_Devices
  - Tier1
ms.topic: reference
search.appverid: MET150
description: Learn how to install and use the Microsoft Teams Intelli Camera for hybrid meetings.
---

# What is Microsoft Intelligent Camera?

Microsoft Teams AI Camera is a platform, which allows users to inspire and share engaging experiences for remote users.

The IntelliCamera provides an immersive audio and video experience for remote users through better meeting understanding. It allows for identifying the active speaker and their role, whiteboard content capture, transcription and translation, and an O365 Graph for remote and hard of hearing users at a low cost easy deployment.

## Getting started

The getting started kit for IntelliFrame provides Microsoft Teams certified camera, which includes loudspeaker and microphones. The intelligent camera can produce multiple video stream, AI powered active speaker tracking by recognizing facial movements and gestures.

### What is in the box?

- A device installation printed guide.
- Yealink SmartVision 60 camera.
- Two USB A to C cables of 3 feet and 10 feet.
- A power adapter
- 3M sticky pads to secure the camera to the table.
- A tool kit to screw/unscrew the cable covers.

### Prerequisites

- Microsoft Windows Teams Room (MTR) device.
- MTR Pro license:
  - MTR with Pro or Premium license is required to enable IntelliFrame, and people recognition features on MTR.
  - Basic license won't enable IntelliFrame or people recognition. If you have Basic, the camera will show active speaker and panoramic views.
  - Check the [Teams devices](../rooms/license-check.md#check-the-license-of-a-couple-teams-rooms-devices) to determine if you have the right license.
- Set policy for [People Recognition and Enrollment](#enabling-enrollment-option-and-people-recognition).
- Configure MTR for log collection and Feedback for bug filing.

## Device provisioning

### Supported cameras

The Microsoft Teams Room device supports the following cameras for IntelliFrame and people recognition.

- Yealink SmartVision 60
- Jabra Panacast 50 (launching soon)

### Placing and fixing SmartVision 60 to conference room table

SmartVision 60 camera is a "Center of room" 360-degree camera. It's meant to be placed at the center of the meeting room table where there's a clear view between camera and meeting attendees.

> [!Note]
> We recommend the device to be placed at the center of the table, but no more than 10 feet from
the Microsoft Teams Room (MTR) console.

After placing the camera on the table, use the supplied 3M sticky pads to adhere the device to the table and ensure that the device is firmly placed and isn't movable. Ensure the arrow on the device is pointing to the monitor, as the orientation of the device is critical to its functioning.

### Connecting device to your Microsoft Teams Room

Connect the USB C cable to A cable with the USB-C port inserted into the SmartVision 60 and USB-A port on MTR.

> [!Note]
> Ensure the cable is not pulled tightly or pinched for ideal data transmission and connectivity.

Log in to the MTR as Admin User and change the settings as shown in the
image.

:::image type="content" source="../media/ConnectDevice_MTR.png" alt-text="Screenshot that shows connecting device to MTR.":::

## Firmware update and enable device log collection

### Enable device log collection

To enable device log collection for feedback log filing:

1. Launch an Admin command prompt in Microsoft Teams Room that the camera connects.
1. Run [plazacfg.bat]{.underline} released with this document to config the log collection and windows driver update endpoint settings properly.
1. Reboot the Microsoft Teams Room for changes to take effect.

### Update device firmware

Once you are connected to Microsoft Teams Room (MTR), the Device Firmware must be updated.

To ensure you have the latest Firmware, sign in to MTR from the Admin mode, and do a **Windows update** to receive the latest firmware.

## Calibrate to Ignore room monitors

You must calibrate the device to avoid camera detecting faces on monitors and rendering them on IntelliFrame.

1. To complete the calibration process (Automatic and Manual), [download the application](https://agent.rooms.microsoft.com/files/agent/plaza/builds/prod/IntelligentIgnore.zip).
1. Sign in to MTR with Admin privilege, right select **install.bat** and run as administrator. The app starts the installation.

1. Open Windows Device Manager and look for Yealink camera entry under the Cameras node.

> [!Note]
> If the list of Yealink cameras dosen't appear under the Cameras section within 2 minutes of plugging in the device, check the USB cable or power supply and ensure that they are firmly connected.

1. Locate and double click on **IntelligentIgnore** icon from the desktop.

1. The Calibration App opens a window and you can **automatically** or **manually** select any region in the room to be ignored for face detection.
   - Manual mode: You can manually adjust the area using the upper and lower sliders that should be ignored by the camera for face detection.
   
     :::image type="content" source="../media/set_ignore_region.png" alt-text="Screenshot that shows the monitor ignore region.":::
   
   - Detect monitor mode: It automatically detects the monitor to be ignored.
   -  :::image type="content" source="../media/Detect_monitor_mode.png" alt-text="Screenshot that shows the detect monitor mode.":::

> [!Note]
> Ensure monitor(s) are connected to MTR.

After you set the ignore region, it will force the SmartVision 60 to reboot and apply the changes.

Steps 1 through 5 complete the installation process and set the ignore region. If reconfiguration is required, you can launch the calibration app from the MTR settings.

:::image type="content" source="../media/callibration_reconfig.png" alt-text="Screenshot that shows the reconfiguration.":::

Once the ignore region is configured, meeting attendees can walk through the ignore space, or even sit in this space and will continue to be recognized. Ignore logic applies to faces on monitors.
  
### Unsupported Ignore regions

- **Glass walls**: Some meeting rooms may have glass walls, which allow outside people to be visible to the camera. In such cases there's a possibility of accidentally capturing their faces, which negatively impact the meeting experience. We recommend frosting and other methods of covering the glass walls to reduce faces outside the meeting room from being detected. This helps in reducing or even eliminating the issue.

- **Pictures of people:** The camera only detects live people. If there is wind or other unexpected camera movement, or pictures of the people on the wall, it may be recognized as a person transiently. This can have a negative affect in the meeting. Report these cases to Microsoft using the feedback link provided.

> [!Note]
> We are constantly improving our detection mechanisms and tools, any feedback you provide will help us expedite the fixes.

## Enabling enrollment option and people recognition

You can prepare SmartVision 60 to recognize people's faces and voices in meetings by enabling [Face enrollment](#enabling-face-enrollment) and [People recognition](#enabling-people-recognition).

### Enabling Face Enrollment

 An Intelligent camera uses Face and Voice profile information of an enrolled user to recognize who is speaking from the intelligent camera room to enable the following features:

- Name labels on room participant stage videos.
- Roster entry under call room participants.
- Live transcription with recognition (who said what).

This step requires CsTeamsMeetingPolicy **enrollUserOverride** tenant policy to be **Enabled**. When an Admin applies the policy, face enrollment option shows up under **Recognition** tab along with voice enrollment.

> [!CAUTION]
>
> - Face Enrollment and People Recognition is not intended for use in Illinois. Please do not install an intelligent camera in a meeting room in Illinois.
> - You are responsible for compliance with local laws and regulations when you install an intelligent camera and use Face Enrollment and People Recognition in a particular jurisdiction, including with respect to obligations around notice, consent, and data retention.
> - Please install appropriate signage outside any meeting room, where you install an intelligent camera, advising people about the People Recognition, Face Enrollment, and Voice Recognition features.
> - You must first enroll for Voice recognition before you can enroll for Face recognition.

`enrollUserOverride` = {Disabled | Enabled} 
**Enabled**- Policy value allows Enrollment tab to be seen on individual Teams user accounts for registering voice and face profiles.  
**Disabled** – No enrollment tab option. This is default.

*This policy should already be enabled if tenant has allowed voice enrollment.
   :::image type="content" source="../media/enroll_user_override.png" alt-text="Screenshot that shows the voice recognition.":::

### Enabling People Recognition

People Recognition can't be used in the following states: X, Y, and Z.

This requires the tenant CsTeamsMeetingPolicy **roomPeopleNameUserOverride** to be "**On**" and **roomAttributeUserOverride** to be **Attribute** for allowing individual voice and face profiles to be used for recognition in meetings.

`roomPeopleNameUserOverride` = {On | Off}  
**On** - Policy value allow **People recognition** option on Microsoft Teams Room under call control bar.  
**Off** – No People Recognition option on Microsoft Teams Room. This is default.

`roomAttributeUserOverride` = {Attribute | Off}
**Attribute** - Policy value allow **Voice identification** option on Microsoft Teams Room if transcription is started for the meeting.  
**Off** – No Voice identification option on Microsoft Teams Room. This is default.

For more on information on setting meeting policies, refer to [Tenant administration control](../rooms/voice-recognition.md) and [Microsoft Teams PowerShell](../teams-powershell-overview.md).

PowerShell cmdlet sample for changing CsTeamsMeetingPolicy

```powershell
Import-Module MicrosoftTeams
$credential = Get-Credential   // Enter your admin’s email and password 
Connect-MicrosoftTeams –Credential $credential

New-CsTeamsMeetingPolicy    // enter identity name and use it in next steps 
Set-CsTeamsMeetingPolicy -identity {identity_name} –RoomPeopleNameUserOverride On 
Get-CsTeamsMeetingPolicy -identity {identity_name} // to confirm the changed value.

New-CsTeamsMeetingPolicy // enter identity name and use it in next steps.
Set-CsTeamsMeetingPolicy -identity {identity_name} –RoomAttributeUserOverride Attribute
Get-CsTeamsMeetingPolicy -identity {identity_name} // to confirm the changed value. 
```

## Filing and sending feedback to Microsoft

To provide feedback and description of the issue, you must send [feedback to Microsoft](#sending-the-feedback-to-microsoft). The feedback must contain all the relevant logs for proper triage.

### Sending the feedback to Microsoft

#### Report a problem from Microsoft Teams Room

Follow the steps to report a problem via MTR.

1. During the meeting, use the **"..."** section as shown in the picture and select "Report a problem".

   :::image type="content" source="../media/report_problem_mtr.png" alt-text="Screenshot that shows the report from MTR.":::

1. Enter the description: You see two categories, select **meetings** from the drop-down under **What is this related to?** section.

1. Enter the details that best describe your experience under **What are you seeing? Has it always been that way?** section.

   ![Screenshot that shows the details](/Teams/media/description_feedback.png)

### Report a problem from the desktop client

- During the meeting, you find the **"..."** selection. Select it to show **Report a problem** and select it to enter the next window.
   ![Screenshot that shows how to report a problem](/Teams/media/report_problem_desktop.png)
- In the next window, you'll see options to select the category. Select the category from the drop-down that best represents your experience or issues.
   ![Screenshot that shows the description for desktop client](/Teams/media/description_desktop.png)

>[!Note]
 > To report a problem using the desktop client, you must be on a meeting window to send the correct diagnostics logs.
 > For accurate diagnostics, provide feedback from both Microsoft Teams Room and Desktop client. We recommend sending two bugs for each issue you encounter.

## Scheduling a meeting

When you schedule a meeting, both room and users who wish to be identified must be invited to experience IntelliFrame and People Recognition upon enrollment. Else, users will only be identified as "Guest".
An example of a meeting invite is shown below.

:::image type="content" source="../media/demo_meeting.png" alt-text="Screenshot that shows the demo meeting schedule.":::

>[!Note]
> Adhoc meetings won't have face identifications, where there is no Outlook appointment with a list of participants.
> 1:1 meeting will not have IntelliFrame or identification.
> Always schedule a meeting to use SmartVision 60 features like IntelliFrame and People recongnition.

## Known issues

| # | Behavior | Mitigation |
|---|----------|------------|
| 1 | When the view from the room is an Active speaker view and not IntelliFrame view, the **Name** label is missing on the participant video. | N/A |
| 2 | Intermittently room participants fail to get added to the Roster. | Option 1: Close and open the camera lid. Option 2: Restart device |
| 3 | The purple bounding box around the room is always highlighted even when there's no voice or sound from the Room. | N/A |
| 4 | Time taken to switch from IntelliFrame to Active speaker, after IntelliFrame toggle, and for **Name** labels to appear/disappear after people recognition toggle is five to seven seconds. | N/A |
| 5 | For people Identification, the Outlook invite supports a total of 64 users. This includes users attending online, and 12 concurrent users in the room for **Name** labels. | N/A |
| 6 | Room participants get identified: <br><li> If they're part of the outlook meeting invite <br><li> If the meeting invite was forwarded to a participant before 30 minutes of the meeting. | N/A |
| 7 |  New Teams 2.1 app isn't supported. | Don't select the **Try the new Teams** toggle. |

## FAQ

**What is the recommended Cable type?**

   Yealink provides a 3-meter USB cable along with the camera device. User must use this cable to connect camera to MTR. If you require a longer cable, you can contact Yealink to order. Yealink has two cables available for order at 15-meters and 30-meters. These cables of 3-meter, 15-meter, and 30-meter are particularly for camera at USB3 speed.

**How do I contact Microsoft support if I have any questions regarding the provisioning or Microsoft Intelligent camera?**

If you have any questions, you can reach out to [Microsoft support team](https://support.microsoft.com/en-us/contactus).
