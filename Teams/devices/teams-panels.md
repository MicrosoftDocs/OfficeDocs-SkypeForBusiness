---
title: "Microsoft Teams panels"
ms.author: v-mdhiman
author: ManikaDhiman
manager: serdars
ms.reviewer: weizxue
ms.topic: reference
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-voice
search.appverid: MET150
localization_priority: Normal
description: "This article provides an overview of and features supported by Microsoft Teams panels."
---

# Microsoft Teams panels

Microsoft Teams panels are the compact touch screen devices that are mounted right outside of your meeting spaces, typically next to entrances. Teams panels provide you the ability to view location and meeting details, at a glance, and reserve an available meeting space on the fly. With rich, large text and color-coded indicators, you can see the meeting space’s availability even from a distance. 

Teams panels and dedicated Microsoft Teams devices that display meeting details scheduled via Teams or Outlook 365 calendaring applications. With meeting details prominently displayed, attendees can easily confirm they’re in the right room, at the right time, and for the right meeting.

This article provides an overview of Teams panels and can help you plan, deliver, and manage Teams panels devices in your organization.

<!--Add a link to the SMC topic. To learn more, check out [Get started with Teams panels](https://support.microsoft.com/office/get-started-with-teams-displays-ff299825-7f13-4528-96c2-1d3437e6d4e6).-->

## Features supported by Teams panels

Teams panels support the following features:

- **Dedicated display of meeting space and meeting details** You get at-a-glance details about a meeting space, including its location and availability status. For a reserved meeting space, you can see key meeting details, such as the meeting name, meeting schedule, and meeting organizer.
- **Reserve available meeting spaces for ad hoc meetings** Using the touch-screen panel, you can reserve an available meeting space on the fly for an ad hoc meeting, and _join_ this Teams meeting in the in-room Microsoft Teams Rooms or Surface Hub devices.
- **Color-coded indicators for space availability status** You can see room availability at-a-glance from afar and up close with vibrant LED and Home screen indicators. Green indicates that the meeting space is available, and if required you can reserve it on the fly right from the panel itself. Red or purple indicates that the meeting space is reserved.
- **Customize background and reserved state indicator** Admins have the ability to change the default look of the panels through settings. For example, admins can change the background wallpaper, or change the color of the busy state indicator.

## Partners certified for Teams panels
You can acquire your Teams panels devices from one of the following partners:
- Crestron
- Yealink

## Teams panels requirements
The following section lists the physical, software, and network requirements of Teams panels. These requirements may vary depending on which Teams panels device you are using. Refer to the Original Equipment Manufacturer (OEM) documentation to know what's required for your set of devices.

<!--Reviewers: Please include any additional requirements-->

**Physical requirements**
- Microsoft Teams certified device
- Power over Ethernet (PoE) cable of appropriate length
<!--Reviewers: Add LED indicators?-->

**Software requirements**
- Microsoft Teams
<!--Reviewers: Should the firmware requirement be listed here?-->

**Network requirements**
- Access to a server that can provide an IP address using DHCP
- Wired network connection to assure you will have reliable connectivity
- Proxy bypass is strongly recommended for real-time traffic

## License requirement

To use Teams panels, you need [Microsoft Teams Rooms Standard License](https://docs.microsoft.com/en-us/MicrosoftTeams/rooms/rooms-licensing).

> [!Note]
> For a meeting space with the Microsoft Teams Rooms system deployed, you do not need additional license for Teams panels devices.

## Deploy Teams panels devices

The following section is intended for people tasked with planning, deploying, and managing Teams panels devices. This section is not intended for the end users of Teams panels.

Deployment of Teams panels devices can be broken down into the following tasks:

- [Meeting space inventory and capability planning](#inventory-sites-and-meeting-spaces): Create an inventory of your organization’s sites and meeting spaces where you will deploy Teams panels devices.
- [Procurement](#procurement): Procure the devices from your selected device partner.  
- [Site readiness](#site-readiness): Confirm that your deployment locations (meeting spaces) meet the deployment requirements.
- [Configuration and deployment](#configuration-and-deployment): Create resource accounts and assign them to the devices.

## Inventory sites and meeting spaces
Take an inventory of the existing bookable meeting spaces in your organization. Identify the sites and meeting spaces that are in scope for deploying Teams panels. Work with your facilities and audio-visual teams to determine where and how to install the Teams panels devices, and if any additional hardware is needed for mounting the panels.

## Procurement
Based on the number of meeting spaces that are in scope for deploying Teams panels, procure the devices from one of the [partners certified for Teams panels](#partners-certified-for-teams-panels). Visit the partners’ websites to learn more about the devices and procurement options. 

The installation harware requirements for the devices may not be the same for every meeting space in your organization. Depending on the meeting space specifications, such as layout and wall surface material, you might need to procure additional installation hardware. For example, the installation hardware requirement for mounting the device on a glass wall may be different from mouting it on a plaster surface or a wood paneling. Refer to the device partner's documentation for available mouting options.

Depending on your deployment scale and approach, you might decide to have the Teams panels devices and
any additional components shipped to a central location for initial configuration and assignment. This might
be a good approach for a staged rollout across many sites. Or, you might choose to ship the bundles directly to
your sites.

## Site readiness
While the ordered devices are being delivered to your organization, work with your networking, facilities, and audio-visual teams to make sure that deployment requirements are met and each site and meeting space is ready in terms of power and networking.

Our recommendations for Teams panels sites are:

- Dedicated resource accounts
- Ethernet cabling
- Quality of Service (QoS) enabled on the network for Microsoft Teams media

For physical installation considerations, see the OEM's documentation and, if you have one, leverage the experience of your audio-visual team before you install and mount devices and run cabling.

## Configuration and deployment
Planning for configuration and deployment covers the following key areas:

- Resource account provisioning
<!--Check if we have details about Teams panels configuration profiles-->
- Testing

### Resource account provisioning

Every Teams panels device requires a Microsoft 365 resource account. This is the account that signs in to Microsoft Teams app on the Teams panels device. You can create resource accounts and assign them to the Teams panels devices using the Microsoft 365 admin center.

To set up a Microsoft 365 resource account for Teams panels, you'll need to purchase a [Microsoft Teams Rooms Standard license](#license-requirement). This license includes a resource mailbox that enables people in your organization to book the meeting space via Outlook or Teams.

When you create a resource account, you can choose whether to let the account automatically accept or decline meeting requests, allow recurring meetings, specify how far in advance people can book the resource, and so on.

> [!NOTE]
>- If you already have a resource mailbox account set up for the meeting space where you're installing Teams panels device, you can change that resource account into a device account. After that's done, all you need to do is add the device account to the Teams panels device. However, make sure that the resource account has the Microsoft Teams Rooms Standard license assigned to it to use it as Teams panels device resource account.   
>
>- If you already have a Microsoft Teams Rooms system deployed in the meeting space where you're installing Teams panels device, then the resource account already has the [Microsoft Teams Rooms license](../rooms/rooms-licensing). In such cases, you don't need to purchase a separate Microsoft Teams Rooms Standard license for deploying Teams panels device.

> [!TIP]
> It is recommended to create the resource account well in advance of the actual Teams panels installation.
> Consider using naming conventions for the Teams panels resource account. Make the display names for your Microsoft 365 resource accounts descriptive and easy to understand. These are the names that users will see when they search meeting spaces while scheduling meetings in Outlook or Teams calendars.

See [Create a resource account using the Microsoft 365 admin center](resource-account-ui.md) for information on how to create a resource account and assign a license to it.

### Testing
After the Teams panels devices are deployed, it is recommended that you test the device. Check that all the [features supported by Teams panels](#features-supported-by-teams-panels) are working on the deployed device. Try creating a number of meetings for various time slots via Teams app or Outlook 365 on your computer. Check if the panels device correctly shows the meeting details and the room availability status for the scheduled meetings. Additionally, try using the **Reserve** button to check if you can reserve an available meeting space right from the device.

## Manage Teams panels in your organization
To manage your Teams panels devices, in the left navigation of the Microsoft Teams admin center, go to **Devices** > **Teams panels**. From here, you can change the device configuration profile, manage updates, restart devices, add and remove device tags, and more. For more information, see [Manage your devices in Teams](device-management.md).

## Next steps
[How to use Microsoft Teams panels devices](use-teams-panels.md)

## See also
<!--Add a link to the Techcommunity blog here. [Introducing Microsoft Teams panels]-->

<!--Add a link to the marketplace here [Teams Marketplace](https://office.com/teamsdevices)-->

<!--Add a link to the Get started topic on SMC here-->