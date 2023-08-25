---
title: Set how you want to handle real-time media traffic for Teams meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: 
ms.date: 10/15/2018
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- NOCSH
ms.custom: 
  - ms.teamsadmincenter.meetingsettings.invitationurls
  - ms.teamsadmincenter.meetingsettings.network.ports
  - ms.teamsadmincenter.meetingsettings.overview
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier2
description: Learn how to enable QoS markers and set port ranges for each type of media traffic in Teams meetings.
---

# Set how you want to handle real-time media traffic for Teams meetings

<a name="bknetwork"> </a>

If you're using Quality of Service (QoS) to prioritize network traffic, you can enable QoS markers and set port ranges for each type of media traffic. Setting port ranges for different traffic types is only one step in handling real-time media; see [Quality of Service (QoS) in Teams](qos-in-teams.md) for much more detail.

> [!IMPORTANT]
> Apple-based systems: The only instance that we know of where Apple-based devices actually set the DSCP value is if all the following conditions are met:
> - iOS.
> - WiFi network.
> - Cisco switches.
> - The network administrator has added the app to the approved list.
>
> Android-based systems: There are no known limitations.
>
> If you enable QoS or change settings in the Microsoft Teams admin center for the Teams service, you'll also need to [apply matching settings to all user devices](QoS-in-Teams-clients.md) and all internal network devices to fully implement the changes to QoS in Teams.

  **Using the Microsoft Teams admin center**
1. Go to the [Teams admin center](https://admin.teams.microsoft.com).
2. In the left navigation, go to **Meetings** > **Meeting settings**.
3. Under **Network**, do the following:

    ![Screenshot of the network settings for meetings in the admin center.](media/meeting-settings-network.png "Screenshot of the network settings for Teams meetings in the Microsoft Teams admin center")

    - To allow DSCP markings to be used for QoS, turn on **Quality of Service (QoS) markers for real-time media traffic**. You only have the option of using markers or not; you can't set custom markers for each traffic type. See [Select a QoS implementation method](QoS-in-Teams.md#select-a-qos-implementation-method) for more on DSCP markers.

        > [!IMPORTANT]
        > Note that enabling QoS is only performed on the endpoints for tagging packets leaving the client. We still recommend applying matching QoS rules on all internal network devices for incoming traffic.
        
        > [!NOTE]
        > DSCP tagging is typically done via Source Ports and UDP traffic will route to Transport Relay with destination port of 3478 by default. If your company requires tagging on destination ports, please contact support to enable communication to the Transport Relay with UDP ports 3479 (Audio), 3480 (Video), and 3481 (Sharing).
    - To specify port ranges, next to **Select a port range for each type of real-time media traffic**, select  **Specify port ranges**, and then enter the starting and ending ports for audio, video, and screen sharing. Selecting this option is required to implement QoS. 
        > [!Note]
        > If **Quality of Service (QoS) markers for real-time media traffic** is on, then you have to manage your port settings. They aren't managed automatically.
        
        > [!IMPORTANT]
        > If you select **Automatically use any available ports**, available ports between 1024 and 65535 are used. Use this option only when not implementing QoS.
        >
        > Selecting a port range that is too narrow will lead to dropped calls and poor call quality. The recommendations below should be a bare minimum.

If you're unsure what port ranges to use in your environment, the following settings are a good starting point. To learn more, read [Implement Quality of Service (QoS) in Microsoft Teams](QoS-in-Teams.md). These are the required DSCP markings and the suggested corresponding media port ranges used by both Teams and ExpressRoute.

### Port ranges and DSCP markings

Media traffic type| Client source port range \* |Protocol|DSCP value|DSCP class|
|:---             |:---                         |:---    |:---      |:---      |
|Audio            | 50,000–50,019               |TCP/UDP |46        |Expedited Forwarding (EF)|
|Video            | 50,020–50,039               |TCP/UDP |34        |Assured Forwarding (AF41)|
|Application/Screen Sharing| 50,040–50,059      |TCP/UDP |18        |Assured Forwarding (AF21)|
| | | | |

\* The port ranges you assign can't overlap and should be adjacent to each other.

After QoS has been in use for a while, you'll have usage information on the demand for each of these three workloads, and you can choose what changes to make based on your specific needs. [Call Quality Dashboard](turning-on-and-using-call-quality-dashboard.md) will be helpful with that.
