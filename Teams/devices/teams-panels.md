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

Microsoft Teams panels are the compact touch screen devices that are mounted right outside of your meeting spaces to streamline space management. Teams panels provides you the ability to view location and meeting details at a glance, and reserve an available meeting space on the fly. With rich, large text and color-coded indicators, you can see the meeting space’s current availability even from afar.

Teams panels are dedicated Teams devices that are pre-integrated with Microsoft Outlook 365 and Teams calendar and display meeting details scheduled through these calendar applications.

This article provides an overview of Teams panels and can help you plan, deliver, and manage Teams panels in your organization.

<!--To learn more, check out [Get started with Teams displays](https://support.microsoft.com/office/get-started-with-teams-displays-ff299825-7f13-4528-96c2-1d3437e6d4e6).-->

## Features supported by Teams panels

Teams panels support the following features:

- **Dedicated display of meeting space and meeting details** You can—at a glance—get information about a meeting space, including its location and availability status. For a reserved meeting space, you can see meeting details, such as the meeting name, meeting schedule, and meeting organizer.
- **Reserve available room for ad hoc meetings** Using the touch-screen panel, you can reserve an available room for an ad hoc meeting on the fly. Tap the **Reserve** button on the Home screen and select the meeting end time.
- **Color-coded indicators for space availability status** Identify, even from a distance, if a meeting space is available or resserved by just looking at the color displayed on the panels. Green indicates the space is available and you can reserve it on the fly right from the panel. If the color displayed is red or purple, the meeting space is already reserved.
- **Customize background and reserved state indicator** Admins have the ability to change the default look of the panels through settings. For example, admins can change the background wallpaper, or change the color of the Reserved state indicator.  

## Teams panels requirements
The following section lists the physical, software, and network requirements of Teams panels.

**Physical requirements**
- Microsoft Teams panel device
- Power over Ethernet (PoE) cable of appropriate length

**Software requirements**
- Microsoft Teams

**Network requirements**
- Access to a server that can provide an IP address using DHCP
- Wired network connection to assure you will have reliable connectivity
- Proxy bypass is strongly recommended for real-time traffic
- Panels certified for Microsoft Teams

**License requirement**

To use Teams panels, you need [Microsoft Teams Rooms Standard License](https://docs.microsoft.com/en-us/MicrosoftTeams/rooms/rooms-licensing). For a meeting space with the Microsoft Teams Room system, you do not need additional license to deploy Teams panels.

## Partners certified for Teams panels
You can acquire your Teams panels devices from one of the following partners:
- Crestron
- Yealink

## Deploy Teams panels devices

The following section is intended for people tasked with planning, deploying, and managing Teams panels devices. This section is not intended for the end users of Teams panels.

Deployment of Teams panels devices can be broken down into the following tasks:

- Meeting space inventory and capability planning: Create an inventory of your organization’s sites and meeting spaces where you will deploy Teams panels.
- Device partner selection: Select the partner from one of the [partners certified for Teams panels](#partners-certified-for-teams-panels) to procure the devices.
- Procurement: Procure the devices from your selected device partner.  
- Site readiness: Confirm that your deployment locations (meeting spaces) meet the deployment requirements.
- Service readiness: Create resource accounts and assign them to the devices ([see Create a resource account using the Microsoft 365 admin center](resource-account-ui.md)).
- Configuration and deployment: Set up Teams panels 

### Inventory sites and meeting spaces
Take an inventory of the existing bookable meeting spaces in your organization. Identify the sites and meeting spaces that are in scope for deploying Teams panels. Work with your facilities and audio-visual teams to determine where and how to install the Teams panels devices, and if any additional hardware is needed for mounting the panels.

### Device partner selection
Determine your preferred device partner to procure the Teams panels devices from one of the [partners certified for Teams panels](#partners-certified-for-teams-panels). Visit the partners’ websites to learn more about the devices and procurement options.

### Procurement
Based on the number of rooms that are in scope for deploying Teams panels, procure the devices from the selected device partners. Select your preferred device partner to procure the Teams panels devices. Visit the partners’ websites to learn more about the devices and procurement options. 

Depending on your meeting space's wall surface on which the device will be mounted, you might need additional installation hardware. For example, mounting the device on a glass wall might need different harware than mouting it on a plaster surface or a wood paneling. Refer to the device partner's documentation for available mouting options.

Depending on your deployment scale and approach, you might decide to have the Teams panels devices and
any additional components shipped to a central location for initial configuration and assignment. This might
be a good approach for a staged rollout across many sites. Or, you might choose to ship the bundles directly to
your sites.

### Site readiness
While the ordered devices are being delivered to your organization, work with your networking, facilities, and audio-visual teams to make sure that deployment requirements are met and each site and room is ready in terms of power and networking.

Our recommendations for Teams panels sites are:

- Dedicated resource accounts
- Ethernet cabling
- Quality of Service (QoS) enabled on the network for Microsoft Teams media

For physical installation considerations, see the manufacturer's documentation and, if you have one, leverage the experience of your audio-visual team before you install and mount screens and run cabling.

> [!TIP]
> Be sure to check out [Prepare your network for Teams](../prepare-network.md) for bandwidth planning and assessing your network’s suitability for real-time traffic.
>
> We don't recommend placing proxy servers between Teams devices and the Internet. For more information about proxy servers and Teams, check out [Proxy servers for Teams](../proxy-servers-for-skype-for-business-online.md).

### Configuration and deployment

Planning for configuration and deployment covers the following key areas:

- Resource account provisioning
- Device deployment
- Collaboration bars for Microsoft Teams application and peripheral device configuration
- Testing
- Asset management

#### Resource account provisioning

Every Teams panels device requires its unique resource account. This is the account that signs in to Teams panels. Depending on your organization's environment, this account can be an Active Directory or Azure Active Direcory account. It is recommended to create the account well in advance of the actual Teams panels installation. You can create resource accounts and assign them to the Teams panels devices using the Microsoft 365 admin center. [See Create a resource account using the Microsoft 365 admin center](resource-account-ui.md) for more information. 

To set up a Microsoft 365 resource account, you'll need to purchase a Meeting Room license for it. The Meeting Room license includes a resource mailbox that enables people in your organization to book the meeting room via Outlook or Teams.

When you create a resource account, you can choose whether to let the account automatically accept or decline meeting requests, allow recurring meetings, specify how far in advance people can book the resource, and so on.

> [!TIP]
> Consider using naming conventions for the Teams panels resource account. Make the display names for your Microsoft 365 resource accounts descriptive and easy to understand. These are the names that users will see when searching for and adding Microsoft Teams panels to meetings.

## Manage Teams panels in your organization

To manage your Teams panels devices, in the left navigation of the Microsoft Teams admin center, go to **Teams panels**. From here, you can change the device configuration profile, manage updates, restart devices, add and remove device tags, and more. For more information, see [Manage your devices in Teams](device-management.md).

## Get started with Teams panels
The following section is indented for Teams panels end users and describes how to use it. The Personalize your Teams panels Home screen is intended for admins only.

### Teams panel Home screen
The Teams panels Home screen is the visual interface that is displayed on your Teams panels. It displays details about the meeting space, such location and room availability status, and details about the scheduled meeting. 
- The top left pane displays the current day, date, and time, and the meeting space name where the device is mounted.
- The top right tile displays availability status of the meeting space.
  - If the room is reserved, the tile appears either in red or purple, and displays meeting details, including meeting name, meeting schedule, and meeting organizer. With meeting details prominently displayed, attendees can easily confirm they’re in the right room, at the right time, and for the right meeting. 
  - If the room is available, the tile appears in green and displays a **Reserve** button. You can tap the **Reserve** button to schedule an ad-hoc meeting. 

### Reserve an available meeting space
You can reserve an available meeting space, indicated by the green color on the Home screen, on the fly for an ad-hoc meeting. 

To reserve an available meeting space:
1. On the Home screen, tap the **Reserve** button.
2. Choose the meeting end time from the available slots.
  > [!NOTE]
  >  The start time for such meetings is always the current time.
3. Tap **Reserve**.
  Confirmation for reservation appears and the tile color on the Home screen changes to red or purple indicating that the room is now reserved. 

If the meeting space that you just reserved is a Microsoft Teams Room, you can use the touch controller (Microsoft Teams Rooms console) to add your meeting attendees and immediately start a meeting.


### Personalize your Teams panels Home screen
The 


## Frequently asked questions
Find answers to frequently asked questions about Teams panels.



## See also

<!--Add a link to the Techcommunity blog here. [Introducing Microsoft Teams panels]-->

<!--Add a link to the marketplace here [Teams Marketplace](https://office.com/teamsdevices)-->

<!--Add a link to the Get started topic on SMC here-->

For an MTR, do we need to create a resource account for the panels? If no, how to add panels to the MTR resource account?
SMC-side documentation?
Is the resource account also the admin account of Teams panels? the account used to sign in to panels?
