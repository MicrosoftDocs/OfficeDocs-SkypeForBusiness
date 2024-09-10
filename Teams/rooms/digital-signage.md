---
title: Digital signage with Teams Rooms for Windows
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: henrikalim
ms.date: 9/06/2024
ms.topic: article
audience: admin
appliesto: 
  - Microsoft Teams
ms.service: msteams
ms.subservice: itpro-rooms
ms.collection: 
  - M365-collaboration
  - teams-rooms-consoles
  - Tier1
f1.keywords: 
  - NOCSH                           
search.appverid: MET150
ms.localizationpriority: medium
description: Learn more about how 
---
# Configure digital signage on Teams Rooms

This feature is only available for Technology Adoption Program (TAP) Preview and early adopter customers. 

Digital signage on Microsoft Teams Rooms expands organizational communications into your meeting spaces, enabling you to inform, connect, and engage your teams. When your Teams Rooms devices are not used for meetings or presentations, they can be configured to display dynamic content and relevant information like how to guides, company or organizational news, upcoming events, and more in signage mode. You can adjust when signage mode is activated and deactivated, including whether signage mode will adhere to the operating system's screen time-out setting. When your Teams Rooms devices are in signage mode, signage content appears in full screen on the front-of-room displays. You have the option to show the Teams Rooms banner so that users can see the room information and calendar preview alongside the signage content on the front-of-room displays. Tapping the touch console during signage mode seamlessly returns the user to the home screen.

:::image type="content" source="media/digital-signage/ds-meeting-enlarged-console.jpg" alt-text="Teasms Rooms homescreen." lightbox="media/digital-signage/ds-meeting-enlarged-console.jpg":::

## Prerequisites

Configuring digital signage for your tenant requires the following:

1. Teams Rooms on Windows version 5.1 or later installed on your Teams Rooms on Windows devices.
1. Teams Rooms Pro license assigned to resource accounts signed in to your Teams Rooms on Windows devices.
1. Teams Rooms Pro Management portal access for device configuration and management.

### Unsupported client and environments

Currently, digital signage isn't yet available on the following clients and environments:

- Teams Rooms on Android (MTR-A)
- Multi-tenant Management portal (MTMA)
- Government Community Cloud (GCC)
- Government Community Cloud High (GCC-H)
- Department of Defense (DoD)

## Set up and management

To enable digital signage for your Teams Rooms devices, you need to follow these steps:

1. Manage permissions for digital signage.
1. Enable digital signage for the tenant.
1. Add signage sources for the tenant, including enabling native third-party integrations as desired.
1. Assign a source and settings to rooms which will register rooms onto supported third-party content management systems (if applicable).

> [!IMPORTANT]
> Before you enable and set up digital signage, consider your privacy and compliance requirements. See [Adding an external signage source](#step-3---adding-an-external-signage-source) for more information.
The following sections show you how to complete each step.

## Step 1 - Managing permissions for digital signage

By default, Microsoft 365 Global Admins and Teams Rooms Pro Managers have the digital signage *tenant* management and digital signage *room* management permissions which grants the ability to perform the following actions respectively:

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

- Digital signage *tenant* management permission
  - Enable, disable, and reset digital signage for the tenant.
  - Add and delete signage sources.
  - Assign signage source and settings to any rooms and/or room groups in the tenant.
  - Set default signage source and settings for the tenant.
  
- Digital signage *room* management permission
  - Enable and disable digital signage for a room.
  - Select an existing signage source from the list of sources that has been added to the tenant for a room.
  - Modify signage settings for a room.
  
Microsoft 365 Global Admins and Teams Rooms Pro Managers can assign additional users with digital signage tenant management and/or digital signage room management permissions using the role-based access control:

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

1. Log in to **Teams Rooms Pro Management** portal > go to **Settings** > **Roles** > select **Create** **role** > enter a unique name and description for the role > select **Next**.
1. Under **Role permissions**, select **Digital signage tenant management: View, Modify** and/or **Digital signage room management: Modify** as desired > select **Next** > enter a name and description for the assignment > select **Next**.
1. Under **Assign members**, search and/or select user(s) and/or security group(s) that will be part of this role with the selected permissions > select **Next**.
1. Under **Assign scope**, search and/or select room(s) and/or room group(s) that this role can manage > select **Next** > **Add new role**.

> [!IMPORTANT]
> The **digital signage** ***tenant*** **management: modify** permission grants the ability to apply signage source and settings to all rooms in the tenant. Any room or room group specified under the assign scope step will only apply to the **digital signage** ***room*** **management: modify** permission and other permissions that are selected in the wizard.

## Step 2 - Enabling digital signage

To enable digital signage for your tenant, log in to **Teams Rooms Pro Management** portal > go to **Settings** > **Digital signage** > toggle On **Digital signage** on the digital signage tenant management page.

Next, you'll need to add a signage source. You can add multiple signage sources for your tenant and assign a different source per room or room group. Supported signage sources include third-party digital signage providers and web URLs. Native integrations with the following trusted third-party digital signage providers are available:

- [Appspace](https://www.appspace.com/microsoft-teams-rooms/)

- [XOGO](https://www.xogo.io/xogo-for-microsoft-teams-rooms)

> [!NOTE]
> To add a supported third party content management system as a signage source, a separate subscription to the provider is needed. Contact the provider directly for information on pricing and packages.

## Step 3 - Adding an external signage source

To enable a third party integration, from the digital signage tenant management page, select **Add source** > enter a unique name and description for this source > select **Next** > choose the third party system of your choice > enter a valid integration ID that you must obtain from the third-party system > select **Validate** > **Next** > acknowledge terms of use > select **Next** > review and finish > select **Submit**.

If you don’t use any of the supported third party providers, you can set web URLs as a signage source. To ensure the web application loads successfully on your Teams Rooms device, the URL must meet the following requirements:

- Has a valid web URL format.
- Begins with "https".
- Accessible within a browser InPrivate window without requiring authentication or permission from the resource account.
- Loads within an iframe that runs in sandbox="allow-scripts allow-same-origin" environment. For more information, see [CSP: frame-ancestors - HTTP | MDN (mozilla.org)](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors).

To add a web URL as signage source, from the digital signage tenant management page, select **Add source** > enter a unique name and description for this source > select **Next** > choose **Custom**> enter a web URL that meets the requirements above > select **Next** > acknowledge terms of use > select **Next** > review and finish > select **Submit**.

> [!NOTE]
> SharePoint and OneDrive for Business URLs aren't supported for the custom option.

> [!IMPORTANT]
> By adding a signage source to your tenant, you accept full responsibility for all signage content that is displayed in your rooms and acknowledge that Microsoft isn't responsible for the signage content that is displayed nor the data that may be transferred out of our system to the external signage source. 
> Supported third party providers will receive the name and email of the specific rooms where they have been assigned as the signage source, allowing seamless integration.

## Step 4 - Assigning a signage source and settings

Once you've added signage source(s) for your tenant, you can now assign a signage source and settings to your rooms. If you're assigning one of the trusted third party providers as a signage source to a room, this step automatically registers that specific room onto the third-party content management system. You can assign a signage source and settings for multiple rooms or room groups at the tenant level or for individual rooms at a room level:

- Tenant-level - from the digital signage tenant management page, choose a signage source > select **Assign to rooms** > confirm the pre-selected source that you intend to assign > select **Next** > review or modify signage settings > select **Next** > search or select room(s) and/or room group(s) where you'd like to assign your chosen source and settings > select **Next** > review and finish > select **Submit**.
- Room-level - navigate to the specific room's settings. Go to **Rooms** > choose a specific room > select **Settings** > **Digital signage** > toggle ON **Digital signage** > modify signage settings as desired > choose a signage source from any of the sources added to the tenant > select **Apply**.

> [!NOTE]
> Settings will only be applied during the maintenance window. To find the setting application results, go to **Rooms** > select **Export** **all** and filter through the rooms and settings in the CSV file.
Once settings have been applied, rooms are now registered with the third party provider. You can manage and update the content that plays in the room directly from the third party content management system.

> [!TIP]
> When designing signage content, avoid placing texts or images on the top 15% of the screen height to avoid being obstructed by the Teams Rooms banner.

> [!WARNING]
> Make sure that there is signage content assigned to your room from the third party service. If there isn't signage content from the third party service available for your room, signage mode won't activate even when configured to do so to avoid showing blank screens on front-of-room displays.

## Modifying default source and settings

While each room or room group can be assigned with a unique configuration, you can set your preferred default signage settings for your tenant, including the default source, signage mode user interface, and display period. To do so:

- **Signage source** - from the digital signage tenant management page, choose a source > select **Set as default.**
- **Signage mode user interface** - from the digital signage tenant management page, select **Preferences** > toggle On or Off **Show Teams Rooms banner** as desired. Turn On to show room information including room name and calendar preview alongside signage content. Turn Off to hide room information in signage mode.
- **Display period** - from the digital signage tenant management page, select **Preferences** >
  - **Activation timer** - enter the number of minutes (between 1 to 100) that a device has been idle before signage mode activates.
  - **Deactivation** **timer** - enter the number of minutes (between 0 to 100) before a scheduled meeting starts when signage mode deactivates and returns to the home screen.
  - **Screen timeout** - toggle On or Off **Allow screen timeout when device is idle** as desired. Turn On to adhere to the operating system's screen timeout settings (i.e., the screen light goes out regardless of when signage mode is activated). Turn Off to bypass the operating system's screen timeout settings (i.e., the screen remains lit up on idle devices when signage mode is activated).
  
> [!NOTE]
> If you add video content in your signage playlist, the screen timeout setting might not consistently honored due to underlying operating system behavior for video playback.

> [!TIP]
> To maximize the visibility of signage mode and ensure your teams see signage content when walking into a room, passing by a room, or lingering in a room after a meeting ends, set the activation and deactivation timers to the lowest possible values and extend the operating system's screen timeout timer or bypass the screen timeout settings by turning Off **Allow screen timeout when device is idle**.

## Monitoring and insights (coming soon)

When using a supported third party digital signage provider as the signage source of a room, you can proactively monitor the health of digital signage in the room using the new digital signage health signal when you expand the display signal. To view the digital signage health signal: go to **Rooms** > choose the specific room > select **Status** > toggle On **Show all signals** > expand **Display** > select **Digital signage**. Alternatively, go to **Incidents** > expand **Display** > select **Digital** **signage**.

When there is an issue with the third party player or signage content, the issue description, and actions you can take to resolve the issue (if applicable) will be visible in the messages. Depending on the nature of the issue, the Teams Rooms experience will vary:

- If there is no signage content available to play in a room whether caused by a system error (i.e., server error, offline) or human error (i.e., no content assigned to the room, no cached content), signage mode will remain deactivated until the issue is resolved at the next device restart. The room will remain on the home screen to avoid showing error messages or empty screens on front-of-room displays. Alerts will be provided on the Teams Rooms Pro Management portal and the third party content management system as appropriate.
- If there is signage content available to play in a room (i.e., cached content) despite an error, signage mode will continue to activate per the activation timer. Any applicable alerts will still be provided on the Teams Rooms Pro Management portal and/or the third party content management system.

> [!NOTE]
> The digital signage health signal is not available for rooms with a web URL (custom option) signage source.

### Help and support

If you have issues with configuring signage settings on your Teams Rooms device using the Teams Rooms Pro Management portal, you can contact Microsoft support. For issues specific to the signage content displayed in your rooms, supported third party providers must be contacted first for assistance. If your digital signage provider determines that the underlying issue requires Microsoft's attention, they can route the issue to Microsoft on your behalf or advise you to open a ticket directly with Microsoft.

## Known issues and limitations

|Issue or limitation|Workaround|
| -------- | -------- |
|Settings are only applied during the maintenance window.|There is no way to immediately apply the settings.|
|Regardless of the signage source, the digital signage health signal isn't available.|If digital signage has been enabled but signage mode isn't activated after the maintenance window, submit an issue using **Report a problem**.|

