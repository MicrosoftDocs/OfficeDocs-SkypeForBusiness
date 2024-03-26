---
title: Cloud Video Interop for Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: conceptual
ms.service: msteams
audience: admin
search.appverid: MET150
ms.reviewer: naforer
ms.date: 01/10/2024
f1.keywords:
- NOCSH
description: Use Cloud Video Interop as an intermediate solution to allow third-party meeting room devices to join Microsoft Teams meetings.
ms.localizationpriority: medium
ms.collection: 
  - M365-voice
  - M365-collaboration
  - Tier1
  - m365initiative-meetings
ms.custom:
  - seo-marvel-apr2020
  - seo-marvel-mar2020
appliesto: 
  - Microsoft Teams
---

# Cloud Video Interop for Microsoft Teams

Cloud Video Interop (CVI) is a Microsoft Qualified third-party solution that enables third-party SIP and H.323 video room devices (VTCs) to join Microsoft Teams meetings.

With Microsoft Teams, you get rich online content collaboration in meetings that include audio, video, and content sharing. This can be enjoyed through the desktop and web client, as well as through many partner devices that integrate natively with Microsoft Teams. However, many customers have already invested in video communication devices, which can be expensive to upgrade. Cloud Video Interop provides an easy solution, which allows you to keep using your existing solutions until you're ready to upgrade.

With Cloud Video Interop, Microsoft Teams delivers a native meeting experience for all participants – in meeting rooms or inside of Teams clients.

### Is Cloud Video Interop for me?

Cloud Video Interop provides an intermediate service while you transition to a full native Microsoft Teams Solution, using Teams endpoints. The service provided should be part of your migration path.

Cloud Video Interop is intended for customers who meet the following criteria:

- Have a large deployment of meeting room devices and personal video devices deployment (50+ devices) that aren't qualified for direct integration with Microsoft Teams
- Are supported by one of our Cloud Video Interop partners
- Want to retain the value of their investment in their current meeting room devices and personal video devices during the migration to a native Microsoft Teams solution

While Cloud Video Interop provides a great intermediate solution, we encourage our customers to look into our native Teams Meeting solutions, such as Teams Rooms Systems, for the long term.

### Office 365 US Government and third-party services

Office 365 provides the ability to integrate third-party applications into SharePoint Online sites, Skype for Business, Teams, Office applications included in Microsoft 365 Apps for enterprise (such as Word, Excel, PowerPoint, and Outlook), and Outlook Web App. In addition, Office 365 supports integration with third-party service providers. These third-party applications and services might involve storing, transmitting, and processing your organization's customer data on
third-party systems that are outside of the Office 365 infrastructure and therefore aren't covered by the Office 365 compliance and data protection commitments. **It is recommended that you review the privacy and compliance statements provided by the third parties when assessing the appropriate use of these services for your organization.**

> [!NOTE]
> The Pexip Teams Connector must be hosted in the Arizona or Texas Azure regions for GCC High. The Virginia Azure region does not support the hosting of the Pexip Teams Connector for GCC High.

## Partners Certified for Microsoft Teams

The following partners have video interop solutions for Microsoft Teams. Your company may choose to work with any combination of these partners within your enterprise and choose the best support plan these partners offer for their CVI solution. 

> [!WARNING]
> Microsoft has only certified CVI partners (within the table below), for video interoperability within Teams meetings. Granting other 3rd parties with Graph API permissions which provide similar capabilities is not supported by Microsoft.

|Partner|Partner solution|
|----|---|
|![The logo representing Pexip Infinity.](media/pexip.png)| <a href="https://aka.ms/PexipInfinity" target="_blank">Pexip Infinity for Microsoft Teams</a> |
|![The logo representing Cisco CVI.](media/cisco.png)|<a href="https://aka.ms/CiscoCVI" target="_blank">Cisco Webex Video Integration for Microsoft Teams</a> |
|![The logo representing HP Poly CloudConnect.](media/hppoly.png) | <a href="https://aka.ms/PolyCloudConnect" target="_blank">HP Poly CloudConnect</a> |
|![The logo representing Poly RealConnect.](media/polycom.png) | <a href="https://aka.ms/PolyRealConnect" target="_blank">Poly RealConnect Service</a> |
|![The logo representing BlueJeans Gateway.](media/bluejeans.png)| <a href="https://aka.ms/BluejeansGateway" target="_blank">BlueJeans Gateway for Microsoft Teams</a> |

> [!NOTE]
> Both BlueJeans and Poly (RealConnect Service) are no longer on-boarding additional customers, their respective services are now in maintenance only mode.

## Cloud Video Interop Release Notes

Microsoft continues to work with Cloud Video Interop (CVI) partners to make meetings between Microsoft Teams and other services more seamless for users. The table below details which features are available or planned.

|Release Date| Feature Name|Feature Description|Microsoft Status|*BlueJeans|Cisco|Pexip|*Poly|
| -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- |
|CY22Q3|PowerPoint Notifications|CVI participants are notified when PowerPoint is being shared via Teams participants|Delivered to CVI Partners|Available|TBD|Available|TBD|
|CY22Q4|CVI Telemetry|Enable identification of CVI calls within Call Quality Dashboard (CQD) metrics|Delivered to CVI Partners|TBD|Available|TBD|Available|
|CY22Q4|Alignment of lobby between CVI and Teams meetings|Alignment of CVI Lobby with Teams Meeting Scheduling, specifically: "People who were invited" and "Only me and co-organizers", now ensures VTC is held in lobby even when VTC lobby bypass is configured. **Note:** *as a result of this change VTCs (used within Teams live events as a presenter) must be admitted via the lobby*|Delivered to CVI Partners|Available|Available|Available|Available|
|CY22Q4|Support for Long Term Reference Frame (LTRF)|Improved support for video packet loss recovery within CVI|Delivered to CVI Partners|TBD|TBD|TBD|N/A|
|CY22Q4|Support for Microsoft Teams Premium, "Watermark Feature"|Phase 1: Notification for Watermark-enabled meeting with both video and content blocked|Delivered to CVI Partners|TBD|TBD|N/A - will launch Phase 2|N/A - will launch Phase 2|
|CY23Q1|Support for Microsoft Teams Premium, "Watermark Feature"|Phase 2: Full Watermark support, CVI Partners will create Watermark overlay with both video and content displayed. **Note:** *at this time Teams meetings only support Watermark for trusted VTCs i.e. Lobby Bypass must be enabled*|Delivered to CVI Partners|TBD|TBD|Planned|Available|
|CY23Q2|SIP Guest Join|The ability to join Teams Meetings with VTCs when CVI coordinates aren't present within the invite|Delivered to CVI Partners|TBD|TBD|Available|TBD|
|CY23Q3|Point-to-Point (P2P) calling between Teams Rooms on Windows and VTCs|Teams Rooms Pro calling feature which creates the ability to perform bi-directional calling between Teams Rooms on Windows and VTC devices|Delivered to CVI Partners|TBD|TBD|Available|TBD|

*Both BlueJeans and Poly CVI solutions are in maintenance only mode, no new customers are being on-boarded.

### Cloud Video Interop overview

Cloud Video Interop is a third-party service that is offered by our partners to provide interoperability between existing video conferencing and personal video device solutions on premises, and Microsoft Teams.

The solutions offered by our partners consist of components that can be deployed either fully cloud based or partially/fully on premises. 
     
The following diagram shows the high-level architecture of our partner solutions.

![Diagram describing a Teams Cloud Video Interop partner solution.](media/teams-cloud-video-interop-partner-solution.png)


## Deploy Cloud Video Interop

When deploying a Cloud Video Interop solution, it's important to understand that you're deploying a partner solution. The general steps you should take to deploy Cloud Video Interop are listed in the following diagram.

![Diagram describing deploying CVI in your organization.](media/deploying-cvi.png)

### Plan

During the plan phase, you should identify the devices that you won't replace with a native Teams device, and find a Cloud Video Interop partner that can support these devices.  

It's also important to understand that you'll need a license for each user who will schedule meetings in which you want a Cloud Video Interop-enabled device to join. Note that exact licensing requirements can be obtained from the Cloud Video Interop partner. Ensure that this is clear before you start your deployment.

### Configure

The partner that you have chosen for your CVI deployment will provide you with a full deployment document that consists of all the steps needed to deploy successfully within your organization. This will include firewall ports and IP ranges, configuration changes for your devices, and other settings that need to change.

### Provision  

During the provision phase, you'll assign licenses to the appropriate users according to the partner configuration guide. You'll also need to go through the Azure Consent process to provide the partner access to your Teams environment. See [Permissions and consent in the Microsoft identity platform endpoint](/azure/active-directory/develop/v2-permissions-and-consent) for more information about the Azure consent process.

### Schedule

After a user is enabled for Cloud Video Interop, any meeting scheduled using the Teams Meeting Add-in for Outlook, the Teams Client or Outlook Web Access (OWA) will have the appropriate additional information automatically added into the Teams meeting so that Cloud Video Interop-compatible devices can join these meetings.

### Join

Depending on the partner solution, there are several ways to join a Cloud Video Interop-enabled meeting. Exact meeting join scenarios will be provided by your Cloud Video Interop partner. We've listed some examples below:

- IVR (Interactive Voice Response) 

   - You can dial in to the partner's IVR using the tenantkey@domain.
   - When you're in the partner IVR, you'll be prompted to enter the VTC conferenceId, which will then connect you to the Teams meeting.
      
- Direct dial 

   - You can directly dial in to the Teams meeting without interacting with the partner's IVR by using the direct dial feature, using the full string of tenantkey.VTC ConferenceId@domain.
- One-touch dial 
   - If you have integrated the VTC room calendar, you can use the one-touch dial capabilities offered by your partner (without needing to type any dial string).
            
## Manage Cloud Video Interop
   
After Cloud Video Interop is deployed, you can manage the devices using the solutions provided by our partners. Each partner will provide you with an administrative interface that will include both license and device management. 

Reporting is also available directly from the partner administrative interface. For more information on reporting capabilities, contact the partner of your choice.

### Troubleshooting Cloud Video Interop
   
Cloud Video Interop is a partner-provided service. If you're experiencing issues, the first step is to connect a device that has the Teams Client installed and connect it to the same segment as the Cloud Video Interop device that is causing problems. 

If Teams functions correctly on this segment, and you have also followed all the networking and configuration guidelines the partner has provided, you'll need to contact the partner for further troubleshooting. 

## PowerShell for Cloud Video Interop
   

The following PowerShell cmdlets are available for you to (partially) automate the Cloud Video Interop deployment.

- **Get-CsTeamsVideoInteropServicepolicy**: Microsoft provides preconstructed policies for each of our supported partners that allow you to designate which partner(s) to use for Cloud Video Interop.<br>This cmdlet allows you to identify the preconstructed policies that you can use in your organization. You can assign this policy to one or more of your users by leveraging the Grant-CsTeamsVideoInteropServicePolicy cmdlet.
      
- **Grant-CsTeamsVideoInteropServicePolicy**: This cmdlet allows you to assign a preconstructed policy for use in your organization or assign the policy to specific users.
- **New-CsVideoInteropServiceProvider**: Use this cmdlet to specify information about a supported CVI partner that your organization would like to use.
- **Set-CsVideoInteropServiceProvider**: Use this cmdlet to update information about a supported CVI partner that your organization uses.
- **Get-CsVideoInteropServiceProvider**: Use this cmdlet to get all of the providers that have been configured for use within the organization.
- **Remove-CsVideoInteropServiceProvider**: Use this cmdlet to remove all provider information about a provider that your organization no longer uses.








