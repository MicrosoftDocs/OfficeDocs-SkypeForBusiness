---
title: Configure live event settings in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 03/11/2019
ms.topic: article
ms.service: msteams
ms.reviewer: sonua
audience: admin
search.appverid: MET150
localization_priority: Normal
ms.collection: 
- M365-collaboration
- m365initiative-meetings
- enabler-strategic
description: Learn how to manage settings for Teams live events that are held in your organization.
f1.keywords:
- CSH
ms.custom:
- ms.teamsadmincenter.liveevents.settings
appliesto: 
  - Microsoft Teams
---

# Configure live event settings in Microsoft Teams

Use Teams live events settings to configure settings for live events that are held in your organization. You can set up a support URL and configure a third-party video distribution provider. These settings apply to all live events that are created in your organization.

You can easily manage these settings in the Microsoft Teams admin center. In the left navigation, go to **Meetings** > **Live events settings**.

![Screen shot of Teams live events settings](../media/teams-live-events-settings.png "Screen shot of Teams live events settings that you can configure in the Microsoft Teams admin center")

## Set up event support URL

This URL is shown to live event attendees. Add the support URL for your organization to give attendees a way to contact support during a live event.

### ![An icon showing the Microsoft Teams logo](../media/teams-logo-30x30.png) Using the Microsoft Teams admin center

1. In the left navigation, go to **Meetings** > **Live event settings**.
2. Under **Support URL**, enter your organization's support URL.

    ![Support URL setting for live events in the admin center](../media/teams-live-events-settings-supporturl.png "Screen shot of support URL setting for Teams live events")

### Using Windows PowerShell

Run the following:

```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -SupportURL “{your URL}”
```
For more information, see [Set-CsTeamsMeetingBroadcastConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingbroadcastconfiguration?view=skype-ps).
## Configure a third-party video distribution provider 

If you purchased and set up a software defined network (SDN) solution or enterprise content delivery network (eCDN) solution through a Microsoft video delivery partner, configure the provider for live events in Teams. 

### ![An icon showing the Microsoft Teams logo](../media/teams-logo-30x30.png) Using the Microsoft Teams admin center

1. In the left navigation, go to **Meetings** > **Live event settings**.
2. Under **Third-party video distribution providers**, complete the following: 

    ![Third-party video distribution provider settings in the admin center](../media/teams-live-events-settings-distribution-provider.png "Screen shot of the third-party video distribution provider settings for live events")

    - **Use a third-party distribution provider** Turn this on to enable the third-party video distribution provider.
    - **SDN provider name** Choose the provider you're using.
    - **Provider license key** Enter the license ID that you got from your provider contact.
    - **SDN API template URL** Enter the API template URL that you got from your provider contact.

### Using Windows PowerShell
Get the license ID or API token and API template from your provider contact, and then run one of the following, depending on the provider you're using:

**Hive** 
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName hive -SdnLicenseId {license ID GUID provided by Hive} -SdnApiTemplateUrl “{API template URL provided by Hive}”
```
**Kollective** 
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName kollective -SdnApiTemplateUrl "{API template URL provided by Kollective}" -SdnApiToken {API token GUID provided by Kollective}
```
**Riverbed** 
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName riverbed -SdnApiTemplateUrl "{API template URL provided by Riverbed}" -SdnApiToken {API token GUID provided by Riverbed}
```

For more information, see [Set-CsTeamsMeetingBroadcastConfiguration](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingbroadcastconfiguration?view=skype-ps).

> [!NOTE]
> If you plan to create live events using an external app or device, you'll also need to [configure your eCDN provider with Microsoft Stream](https://docs.microsoft.com/stream/network-caching). 

>[!Note]
> The change from using Microsoft Stream to [OneDrive for Business and SharePoint for meeting recordings](../tmr-meeting-recording-change.md) will be a phased approach. At launch you'll be able to opt-in to this experience, in November you'll have to opt-out if you want to continue using Stream, and some time in early 2021 we'll require all customers to use OneDrive for Business and SharePoint for new meeting recordings.

### Related topics
- [What are Teams live events?](what-are-teams-live-events.md)
- [Plan for Teams live events](plan-for-teams-live-events.md)
- [Set up for Teams live events](set-up-for-teams-live-events.md)
