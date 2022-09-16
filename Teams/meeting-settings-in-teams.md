---
title: Manage meeting settings
ms.author: mabond
author: mkbond007
manager: serdars
ms.reviewer: sonua
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.meetingsettings.invitationurls
  - ms.teamsadmincenter.meetingsettings.network.ports
  - ms.teamsadmincenter.meetingsettings.overview
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
description: Learn how to manage settings for Teams meetings that users schedule in your organization.
---

# Manage meeting settings in Microsoft Teams

As an admin, you use Teams meetings settings to control whether anonymous users can join Teams meetings, customize meeting invitations, and if you want to enable Quality of Service (QoS), set port ranges for real-time traffic. These settings apply to all Teams meetings that users schedule in your organization. You manage these settings from **Meetings** > **Meeting settings** in the Microsoft Teams admin center.

Through a per-organizer policy setting, admins now can control whether specific users or groups of users can let anonymous users join the meetings they organize. The per-organizer and organization-wide policy settings both control anonymous join, and the more restrictive takes effect.

> [!Important]
 > **-DisableAnonymousJoin** is the organization-wide policy setting. It will be deprecated in the future, and then the per-organizer policy will be the only way to control anonymous join.

## Allow anonymous users to join meetings

With anonymous join, anyone can join the meeting as an anonymous user by clicking the link in the meeting invitation. To learn more, see [Join a meeting without a Teams account](https://support.office.com/article/join-a-meeting-without-a-teams-account-c6efc38f-4e03-4e79-b28f-e65a4c039508). You can control anonymous users' ability to join meetings either at your organization level, or per meeting organizer by using two different policy settings.

 ### Using the Microsoft Teams admin center to configure organization-wide policy

You must be a Teams admin to make these changes. See [Use Teams administrator roles to manage Teams](./using-admin-roles.md) to read about getting admin roles and permissions.

1. Go to the [Teams admin center](https://admin.teams.microsoft.com).

2. In the left navigation, go to **Meetings** > **Meeting settings**.

3. Under **Participants**, turn on **Anonymous users can join a meeting**.

    ![Screenshot of participants settings for meetings in the admin center.](media/meeting-settings-participants.png "Screenshot of participants settings for Teams meetings in the Microsoft Teams admin center")

> [!CAUTION]
> If you don't want anonymous users to join meetings scheduled by users in your organization, turn off this setting.

### Using PowerShell to configure per-organizer policy

Admins can now control whether specific users or groups of users can let anonymous users join the meetings they organize. This new per-organizer policy is controlled by using the **-AllowAnonymousUsersToJoinMeeting** parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy). This comes with Teams PowerShell version 2.6.0 and later.

You can use either policy, organization-wide or per-organizer, to manage anonymous join. We recommend that you implement the per-organizer policy. The organization-wide policy setting will be deprecated in the future and the per-organizer policy will be the only way to control anonymous join.

Since both the organization-wide and per-organizer policies control anonymous join, the more restrictive setting will be effective. For example, if you don't allow anonymous join at the organization level, that will be your effective policy regardless of what you configure for the per-organizer policy. Therefore, in order to allow anonymous users to join meetings, you must configure both policies to allow anonymous join by setting the following values:

- **-DisableAnonymousJoin** set to **$false**
- **-AllowAnonymousUsersToJoinMeeting** set to **$true**

Any other combination of values will prevent anonymous users from joining meetings.
> [!NOTE]
> To learn more about managing meeting policies, see [Manage meeting policies in Microsoft Teams](/microsoftteams/meeting-policies-overview).

### Blocking anonymous join for specific client types

When anonymous users are allowed to join meetings, they can use either the Teams client or a custom client built using [Azure Communication Services](/azure/communication-services/). Admins can block selected client types using the **-BlockedAnonymousJoinClientTypes** parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).

The possible values are:
- Null (default). All client types are allowed.
- Acs. Blocks custom clients built using [Azure Communication Services](/azure/communication-services/).
- Teams. Blocks the Teams client.

## Allow anonymous users to interact with apps in meetings

Anonymous users will now inherit the user-level global default permission policy. This control will then allow anonymous users to interact with apps in Teams meetings as long as the user-level permission policy has enabled the app. Note that anonymous users can only interact with apps that are already available in a meeting and cannot acquire and/or manage these apps. 

> [!IMPORTANT]
> By default, the setting to allow anonymous users to interact with apps in meetings is enabled.

 **Using the Microsoft Teams admin center**

You must be a Teams service admin to access this setting. See [Use Teams administrator roles to manage Teams](./using-admin-roles.md) to read about getting admin roles and permissions.

1. Go to the [Teams admin center](https://admin.teams.microsoft.com).

2. In the left navigation, go to **Meetings** > **Meeting settings**.

3. Under **Participants**, the setting for **Anonymous users can interact with apps in meetings** can be changed.

> [!CAUTION]
> If you don't want anonymous users to interact with apps in meetings scheduled by users in your organization, turn off this setting.

## Customize meeting invitations

You can customize Teams meeting invitations to meet your organization's needs. You can add your organization's logo and include helpful information, such as links to your support website and legal disclaimer, and a text-only footer.

### Tips for creating a logo for meeting invitations  

1. Create an image that's no more than 188 pixels wide by 30 pixels tall (it's quite small).
2. Save the image in JPG or PNG format.
3. Store the image in a location that everyone receiving the invitation can access, such as a public website.

    Now you can add it to your meeting invitations. See the next steps.

### Customize your meeting invitations

 **Using the Microsoft Teams admin center**

1. Go to the [Teams admin center](https://admin.teams.microsoft.com).
2. In the left navigation, go to **Meetings** > **Meeting settings**.
3. Under **Email invitation**, do the following:

    ![Screenshot of the meeting invitation settings you can customize.](media/meeting-settings-invitation.png "Screenshot of the meeting invitation settings that you can customize for Teams meetings")

    - **Logo URL** Enter the URL where your logo is stored.
    - **Legal URL** If your organization has a legal website that you want people to go to for any legal concerns, enter the URL here.
    - **Help URL** If your organization has a support website that you want people to go to if they run into issues, enter the URL here.
    - **Footer** Enter text that you want to include as a footer.
4. Click **Preview invite** to see a preview of your meeting invitation.
5. When you're done, click **Save**.
6. Wait an hour or so for the changes to propagate. Then schedule a Teams meeting to see what the meeting invitation looks like.  

## Set how you want to handle real-time media traffic for Teams meetings

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
