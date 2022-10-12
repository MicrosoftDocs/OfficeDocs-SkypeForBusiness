---
title: Scale video delivery in Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
ms.reviewer: asteele
search.appverid: MET150
f1.keywords:
- NOCSH
description: This article will discuss scale video delivery and enterprise content delivery networks (eCDNs) for Microsoft Teams streaming events.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Scale video delivery and monitor network traffic by using eCDNs with Microsoft Teams

Playback of videos from Microsoft Teams and "External app or device" live events (formerly known as "External Encoder" productions) use adaptive bitrate streaming (ABR) delivered as a unicast stream. This means that every viewer is getting their own video stream from the internet. For live events or videos sent out to large portions of your organization, there could be a significant amount of network and internet bandwidth consumed by viewers.

Organizations may want to understand and reduce this network traffic for live events and popular videos. If so, Teams can be enabled to integrate with trusted Microsoft partners that offer enterprise content delivery network (eCDN) solutions that include self-managing delivery technologies, real-time monitoring, and in-depth network analytics. These eCDN platforms let organizations monitor, scale, and optimize the distribution of video streams (and sometimes other content types) across your enterprise network.

## Acquire and set up your eCDN solution outside of Teams

Get expert help with monitoring and scaling video delivery by teaming up with trusted Microsoft eCDN partners.

Before you can enable an eCDN solution to be used with Teams, you must purchase and set up that eCDN solution outside and separate from Teams. To ensure that the solution will meet your needs, some partners provide free trials of their content delivery and network analytics technologies.

Several eCDN solutions are pre-integrated and can be enabled for use with Teams. See information from the providers below.

### Hive Streaming

The **Hive Streaming Video Experience Platform** comprises three core products:

- **Hive Video Optimization** is based on a patented software-only, zero-configuration algorithm. Optimization automatically maximizes the quality and reach of live and on-demand video (VOD) for the whole organization.
- **Hive Video Analytics** helps customers understand trends in live event and on-demand video performance to improve viewer engagement over time. As engagement improves, so does video adoption across the company.
- **Hive Video Operations** provides powerful capabilities aiming to proactively secure streaming video success before and during live video events. The operational tools empower your video streaming and UC teams to find and correct problems before they happen.

All of them work to create full-scope video experiences—from planning to execution and analysis. Maximizing the experience of streaming video communication is crucial for employee engagement and alignment on your company mission. To learn more, check out [this link](https://www.hivestreaming.com/partners/microsoft).

### Kollective

**Kollective Technology** is a cloud-based, content distribution platform that utilizes intelligent peering to deliver live and on-demand enterprise video, providing 100% video quality and 100% engagement at just 1% of the bandwidth. Kollective’s integration with Teams Live Events allows globally dispersed employees to easily consume video, improving employee communication, boosting overall engagement, and increasing training and retention opportunities.

**Kollective IQ** is a sophisticated, user-friendly analytics platform for Microsoft Stream. With customizable reporting, visualizations and dashboards, it is easy to quantify and digest both user experience and engagement across complex global enterprise networks. Communication Managers and Network Administrators can watch real-time events and network activity, so bottlenecks can be addressed quickly, insuring peak network performance.

To learn more about these options, check out [this link](https://kollective.com/microsoft-live-events/).

### Peer5

**Peer5** solves the network congestion problem that occurs during large corporate virtual events such as all-hands meetings. Peer5 forms a mesh network over the LAN which reduces the load by 95% and eliminates network issues. Peer5 is the first eCDN to use WebRTC as its foundation, which means no software or hardware installation is needed. Fortune 500 customers mitigate networking issues and trust Peer5 for their biggest corporate events.

- **Zero-setup network configuration** for Peer5 ensures that remote workers and/or heavy video traffic won't strain your network nor oblige you to invest in costly infrastructure. It includes automatic site detection, automatic VPN detection, and automatic NAT/firewall traversal. Learn more at [this link](https://blog.peer5.com/how-to-configure-your-vpn-to-ensure-successful-corporate-video-events/).
- **Silent Testing** with Peer5 allows IT admins to simulate large live events on their corporate network, permitting thorough and non-disruptive testing and troubleshooting before a real event. Learn more at [this link](https://www.peer5.com/product/silent-tester).
- **Industry-leading analytics** from Peer5 provide granular analyses and allow admins to quickly find the root cause for any streaming issue. Your toolkit includes delivery and UX metrics, advanced drilldowns, per-user analytics, and a back-end API. Learn more at [this link](https://blog.peer5.com/peer5-analytics-tools/).

### Ramp

**Ramp eCDN** reduces network bandwidth consumption by 90% or more when streaming live events and video on demand (VOD). Use Ramp to mix and match any combination of eCDN technologies—multicast, caching, and peer-to-peer networking. With centralized management, monitoring, and insightful analytics, you gain visibility and control over network performance to create the highest-quality viewer experience.

- **Ramp Multicast+** is the most efficient way to stream live video. Using the multicast protocol, you only consume the bandwidth required for one viewer, whether you have 100, 10,000, or 100,000 viewers. Learn more at [this link](https://www.rampecdn.com/altitudecdn/multicast/).
- **Ramp OmniCache™** is video-specific caching software that uses local caches to serve live and VOD video to nearby audiences, drastically reducing the number of video streams traveling across your internet connections and WAN links. Learn more at [this link](https://www.rampecdn.com/altitudecdn/video-cache/).
- **Ramp Peer-to-Peer (P2P)** lets you optimize bandwidth even at locations with limited infrastructure. P2P builds a peer network of client devices watching the same content to redistribute the video streams from one viewing device to another. Learn more at [this link](https://www.rampecdn.com/altitudecdn/p2p/).

### Riverbed

**Riverbed**, the industry standard in network optimization, has extended its acceleration solutions to Teams. Microsoft 365 customers can confidently accelerate Microsoft 365 traffic, including Teams, along with a wealth of other leading enterprise SaaS services to increase workforce productivity from anywhere. Teams acceleration can be enabled through an effortless setup that comes with all the assurance of Riverbed’s world-class support and ongoing investment. Learn more at [this link](https://www.riverbed.com/office365).

> [!NOTE]
> Your chosen eCDN solution is subject to the selected partner eCDN provider’s terms of service and privacy policy, which will govern your use of the eCDN provider’s solution. Your use of the eCDN provider’s solution will not be subject to the Microsoft volume licensing terms or Online Services Terms. If you don't agree to the 3rd party provider’s terms, then don't enable the eCDN solution in Microsoft Teams.

## Configure Yammer and Microsoft Teams "External app or device" production type events for your eCDN solution

After purchasing and setting up your eCDN solution, you can enable it for use with Microsoft Stream, including "External encoder" live events that are created through Microsoft Teams or Yammer.

1. Sign in to Teams as an Microsoft 365 Global Admin or a Teams admin.
1. Go to the **Settings** icon > **Admin settings** > **eCDN provider**.
1. Toggle the **Enable 3rd party eCDN provider** to **On**.
1. Choose an eCDN provider from the dropdown list.
1. Fill out the other fields as directed by your solution provider (Not all fields are used by all solution providers).
1. Click **Save**.
1. To check if your setup is correct, click **Verify setup**.
    - Search for any video in your organization to validate with.
    - If your eCDN provider is set up correctly, you'll see a "Success" message on the verify setup tool.
    - If you aren't set up correctly, you'll see a "Failure" message. Copy the event message to share with your provider for troubleshooting.

After you configure Teams for an eCDN solution, any video or live event that is played in Teams will take advantage of that solution automatically.

## Configure Teams production type events through Teams and Yammer for your eCDN solution

If you plan to create Teams live events through Teams or Yammer, you'll need to [configure your eCDN provider to be integrated with Microsoft Teams](teams-live-events/what-are-teams-live-events.md#enterprise-content-delivery-network-ecdn) as well.

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
