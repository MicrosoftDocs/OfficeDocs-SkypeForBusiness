---
title: Enterprise content delivery networks for streaming Microsoft Teams events
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
ms.reviewer: asteele
ms.date: 10/01/2023
search.appverid: MET150
f1.keywords:
- NOCSH
localization_priority: medium
appliesto: 
  - Microsoft Teams
ms.custom:
description: Learn about scale video delivery and enterprise content delivery networks (eCDNs) for Microsoft Teams streaming events.
---

# Enterprise content delivery networks for streaming Microsoft Teams events

**APPLIES TO:** ✔️Meetings ✖️Webinars ✔️Town halls ✔️Live events

Teams streaming events can use enterprise content delivery networks (eCDNs), including the Microsoft eCDN and eCDNs from Microsoft partners. Teams streaming events include:

- Town halls
- Live events
- Meetings with more than 1,000 participants

Playback of videos from Microsoft Teams events use adaptive bitrate streaming (ABR) delivered as a unicast stream. This means that every viewer is getting their own video stream from the internet. For events or videos sent out to large portions of your organization, there could be a significant amount of network and internet bandwidth consumed by viewers.

Organizations may want to understand and reduce this network traffic for events and popular videos. If so, Teams can be enabled to integrate with trusted Microsoft partners that offer enterprise content delivery network (eCDN) solutions that include self-managing delivery technologies, real-time monitoring, and in-depth network analytics. These eCDN platforms let organizations monitor, scale, and optimize the distribution of video streams (and sometimes other content types) across your enterprise network.

## Acquire and set up your eCDN solution outside of Teams

Get expert help with monitoring and scaling video delivery by teaming up with trusted Microsoft eCDN partners.

Before you can enable an eCDN solution to be used with Teams, you must purchase and set up that eCDN solution outside and separate from Teams. To ensure that the solution meets your needs, some partners provide free trials of their content delivery and network analytics technologies.

Several eCDN solutions are pre-integrated and can be enabled for use with Teams. See information from the providers below.

> [!IMPORTANT]
> Teams Premium features require the Microsoft eCDN. Streaming events organized by people with a Teams Premium license always use the Microsoft eCDN even if you've configured a different option.

### Microsoft eCDN (Teams Premium)

**Microsoft eCDN** solves the network congestion problem that occurs during large corporate virtual events such as all-hands meetings. This is the only eCDN option for Teams Premium town hall organizers. Microsoft eCDN forms a mesh network over the LAN, which reduces the load by 95% and eliminates network issues. Microsoft eCDN is the first eCDN to use WebRTC as its foundation, which means no software or hardware installation is needed. Fortune 500 customers mitigate networking issues and trust Peer5 for their biggest corporate events.

- Zero-setup network configuration for Microsoft eCDN ensures that remote workers and/or heavy video traffic won't strain your network nor oblige you to invest in costly infrastructure. It includes automatic site detection, automatic VPN detection, and automatic NAT/firewall traversal. Learn more at [How to enable Microsoft eCDN](/ecdn/how-to/enable-microsoft-ecdn-for-your-tenant).
- Silent Testing with Microsoft eCDN allows IT admins to simulate large events on their corporate network, permitting thorough and non-disruptive testing and troubleshooting before a real event. Learn more at [Perform a silent test](/ecdn/how-to/perform-silent-test).
- Industry-leading analytics from Microsoft eCDN provide granular analyses and allow admins to quickly find the root cause for any streaming issue. Your toolkit includes delivery and UX metrics, advanced drilldowns, per-user analytics, and a back-end API. Learn more at [Analytics](/ecdn/technical-documentation/analytics).

### Hive Streaming

The **Hive Streaming Video Experience Platform** comprises three core products:

- **Hive Video Optimization** is based on a patented software-only, zero-configuration algorithm. Optimization automatically maximizes the quality and reach of live and on-demand video (VOD) for the whole organization.
- **Hive Video Analytics** helps customers understand trends in live event and on-demand video performance to improve viewer engagement over time. As engagement improves, so does video adoption across the company.
- **Hive Video Operations** provides powerful capabilities aiming to proactively secure streaming video success before and during live video events. The operational tools empower your video streaming and UC teams to find and correct problems before they happen.

All of them work to create full-scope video experiences—from planning to execution and analysis. Maximizing the experience of streaming video communication is crucial for employee engagement and alignment on your company mission. To learn more, check out [Hive Streaming](https://www.hivestreaming.com/partners/microsoft).

### Kollective

**Kollective Technology** is a cloud-based, content distribution platform that utilizes intelligent peering to deliver live and on-demand enterprise video, providing 100% video quality and 100% engagement at just 1% of the bandwidth. Kollective’s integration with Teams events allows globally dispersed employees to easily consume video, improving employee communication, boosting overall engagement, and increasing training and retention opportunities.

**Kollective IQ** is a sophisticated, user-friendly analytics platform for Microsoft Stream. With customizable reporting, visualizations and dashboards, it's easy to quantify and digest both user experience and engagement across complex global enterprise networks. Communication Managers and Network Administrators can watch real-time events and network activity, so bottlenecks can be addressed quickly, insuring peak network performance.

To learn more about these options, check out [Kollective eCDN for Microsoft](https://kollective.com/microsoft-live-events/).

### Ramp

**Ramp eCDN** reduces network bandwidth consumption by 90% or more when streaming events and video on demand (VOD). Use Ramp to mix and match any combination of eCDN technologies—multicast, caching, and peer-to-peer networking. With centralized management, monitoring, and insightful analytics, you gain visibility and control over network performance to create the highest-quality viewer experience.

- **Ramp Multicast+** is the most efficient way to stream live video. Using the multicast protocol, you only consume the bandwidth required for one viewer, whether you have 100, 10,000, or 100,000 viewers. Learn more at [Ramp Multicast+](https://www.rampecdn.com/altitudecdn/multicast/).
- **Ramp OmniCache™** is video-specific caching software that uses local caches to serve live and VOD video to nearby audiences, drastically reducing the number of video streams traveling across your internet connections and WAN links. Learn more at [Ramp OmniCache](https://www.rampecdn.com/altitudecdn/video-cache/).
- **Ramp Peer-to-Peer (P2P)** lets you optimize bandwidth even at locations with limited infrastructure. P2P builds a peer network of client devices watching the same content to redistribute the video streams from one viewing device to another. Learn more at [Ramp P2P](https://www.rampecdn.com/altitudecdn/p2p/).

> [!NOTE]
> Your chosen eCDN solution is subject to the selected partner eCDN provider’s terms of service and privacy policy, which will govern your use of the eCDN provider’s solution. Your use of the eCDN provider’s solution will not be subject to the Microsoft volume licensing terms or Online Services Terms. If you don't agree to the 3rd party provider’s terms, then don't enable the eCDN solution in Microsoft Teams.

## Configure Stream encoder type events for your eCDN solution

After purchasing and setting up your eCDN solution, you can enable it for use with Microsoft Stream, including Stream encoder events that are created through Microsoft Teams or Yammer.

1. Open the Teams admin center as a Microsoft 365 Global admin or a Teams admin and navigate to the [events settings](https://admin.teams.microsoft.com/broadcasts/settings) page.
1. Toggle the **Video distribution provider** to **On**.
1. Choose an **eCDN/SDN provider** from the **Video distribution provider** dropdown list.
1. Fill out the other fields as directed by your solution provider (Not all fields are used by all solution providers).
1. Select **Save**.
1. To check if your setup is correct, select **Verify setup**.
    - Search for any video in your organization to validate with.
    - If your eCDN provider is set up correctly, you'll see a **Success** message on the verify setup tool.
    - If you aren't set up correctly, you'll see a **Failure** message. Copy the event message to share with your provider for troubleshooting.

After you configure Teams for an eCDN solution, any video or live event that is played in Teams will take advantage of that solution automatically.

## Configure Teams production type events through Teams and Yammer for your eCDN solution

If you plan to create Teams events through Teams or Yammer, you'll need to [configure your eCDN provider to be integrated with Microsoft Teams](teams-live-events/what-are-teams-live-events.md#enterprise-content-delivery-network-ecdn) as well.

### Get to video analytics reports for your eCDN solution

As noted above, some eCDN solutions also provide analytics reports that give deeper information about playback sessions, viewers, and quality of service. If your provider gave you an analytics report URL template to configure when you set up the provider in the Teams admin center, then owners of videos or events can easily get to the analytics report for a specific video or event.

Owners of videos will see an Analytics tab directly under the video. On this tab, there will be a link for owners to access the analytics report for this specific video in the eCDN provider's system.

If you're a Teams admin, you can also elevate your access to see the Analytics tab and get to the eCDN analytics report link, even if you aren't an owner of the live event or video.

1. As a Teams admin, go to the video player page.
1. Select **Settings**.
1. Select **View in admin mode**.
1. Select the **Analytics** tab.

## Troubleshooting issues

Make sure that your eCDN solution is set up correctly in your network and that you've properly configured Teams to enable the provider per their instructions and specific configuration strings. If you're still having issues, some of the information below might help.

### Verify setup tool

If you're having issues with your eCDN solution, you can always come back and run the **Verify setup** tool. The eCDN provider event messages shown for your test video can give you and your eCDN provider more information on what's not working.

- Go to **Settings** > **Admin Settings** > **eCDN provider** > **Verify setup**

### Disable eCDN for a specific session via URL query string

To determine if an issue you're seeing is with the eCDN solution or with Teams, you can easily disable the eCDN solution for a specific playback session via query string.

- If your playback URL already has a question mark, **?**, in it, then add **&disableSDN=true**.
- If your playback URL doesn't have a question mark, **?**, in it then add **?disableSDN=true**.

### View eCDN info in browser console

If your eCDN solution provider supports it, they may print debug information during initialization of playback through their solution. This extra info may be helpful in determining what is going wrong. You can enable extra console debug messages via the query string.

- If your playback URL already has a question mark, **?**, in it, then add **&isSDNDebug=true**.
- If your playback URL doesn't have a question mark, **?**, in it then add **?isSDNDebug=true**.

Select **F12** on your keyboard when your browser is active and switch to the **Console** tab to see all the information printed during the loading of the page with the isSDNDebug=true query string set on the playback URL.

## Configure a third-party video distribution provider

If you purchased and set up a software defined network (SDN) solution or enterprise content delivery network (eCDN) solution through a Microsoft video delivery partner, configure the provider for events in Teams.

### Using the Microsoft Teams admin center

1. In the left navigation, go to **Meetings** > **Live event settings**.
2. Under **Third-party video distribution providers**, complete the following:

    ![Third-party video distribution provider settings in the admin center.](media/teams-live-events-settings-distribution-provider-new.png "Screen shot of the third-party video distribution provider settings for live events")

    - **Third-party distribution provider** Turn this ON to enable the third-party video distribution provider.
    - **SDN provider name** Choose the provider you're using.
    - **SDN Configuration** Enter SDN Configuration details.

### Using Windows PowerShell

Get the license ID or API token and API template from your provider contact, and then run one of the following, depending on the provider you're using:

**Microsoft eCDN**
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName microsoft
```
**Hive** 
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName hive -SdnLicenseId {license ID GUID provided by Hive} -SdnApiTemplateUrl “{API template URL provided by Hive}”
```
**Kollective** 
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName kollective -SdnApiTemplateUrl "{API template URL provided by Kollective}" -SdnApiToken {API token GUID provided by Kollective}
```
**Ramp** 
```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName ramp -SdnRuntimeConfiguration "{Configuration provided by RAMP}"
```

For more information, see [Set-CsTeamsMeetingBroadcastConfiguration](/powershell/module/skype/set-csteamsmeetingbroadcastconfiguration?view=skype-ps&preserve-view=true).

>[!Note]
> Your chosen eCDN solution is subject to the selected 3rd party provider’s terms of service and privacy policy, which will govern your use of the eCDN provider’s solution. Your use of the eCDN provider’s solution will not be subject to the Microsoft volume licensing terms or Online Services Terms. If you don't agree to the 3rd party provider’s terms, then don't enable the eCDN solution in Microsoft Teams.
