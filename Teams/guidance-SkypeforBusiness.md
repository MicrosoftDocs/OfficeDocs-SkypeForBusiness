---
title: Enable Microsoft Teams side-by-side with Skype for Business 
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
description: Guidance for using Skype for Business and Microsoft Teams side by side.
Set_Free_Tag: Strat_MT_TeamsAdmin
---

Enable Microsoft Teams side-by-side with Skype for Business 
=============================================================

For organizations with existing deployments of Skype for Business Online, the recent introduction of Microsoft Teams presents an opportunity to evaluate the potential of Teams as a sole, communications and collaboration solution, and a challenge to tip the scale between the two solutions and how they can coexist in your environment.

If your business requirements can be met by Teams today, you can start adopting Teams to become your single communications and collaboration solution for your organization.

Teams is enabled by default, on all eligible tenants. Therefore, you need to decide on how to manage Teams side-by-side with Skype for Business, and continue to meet user expectations.

In general, there are two major side-by-side customer journeys. They are:

-   **Option 1:** Unmanaged side-by-side customer journey.

    IT does not actively control the side-by-side experience and, users are empowered to make the choice of preferred app.

-   **Option 2:** Managed side-by-side customer journey.

    IT controls the side-by-side experience, taking users through a journey of gradually introducing Teams to first introduce a new chat-based collaboration workspace, then meeting experiences, and finally chat and calling experiences in Teams.

![](media/guidance_SkypeforBusiness_image1.png)

Side-by-side benefits and considerations
----------------------------------------

Each journey has benefits and considerations to weigh when determining the right path forward based on your organization's profile. The table below provides the comparisons between managed and unmanaged side-by-side customer journeys.


<table>
<thead>
<tr class="header">
<th align="left">Migration Paths</th>
<th align="left">Unmanaged Side-by-Side</th>
<th align="left">Managed Side-by-Side</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>Organization profile</strong></td>
<td align="left"><ul>
<li>Typically, smaller organizations with no dedicated IT resources</li>
<li>IT allows user discretion in selecting right tools for their work</li>
<li>Primary Skype for Business usage is IM/P and meetings</li>
</ul></td>
<td align="left"><ul><li>Typically, mid-size to larger organizations</li>
<li>IT wants to control roll out of new tools more rigorously</li>
<li>Deeper adoption of Skype for Business today</li>
<li>Increased complexity in network and infrastructure</li>
<li>Multiple locations</p>
<li>Preference for single app with unique UC capabilities</li></ul></td>
</tr>
<tr class="even">
<td align="left"><strong>Benefits</strong></td>
<td align="left"><ul>
<li>Leverage capabilities in Teams that are not available in Skype for Business</li>
<li>Enhanced modern workplace within Office 365</li>
<li>Increased user flexibility</li>
<li>Enable all capabilities at once</li>
</ul></td>
<td align="left"><ul><li>Leverage capabilities in Teams that are not available in Skype for Business</li>
<li>Enhanced modern workplace within Office 365</li>
<li>Minimize user productivity impact</li>
<li>Reduce capability overlap</li>
<li>Streamline tool choice for UC scenarios</li>
<li>Empower IT and business to enable capabilities as appropriate in organization</li>
<li>Control the pace of change for users</li></ul></td>
</tr>
<tr class="odd">
<td align="left"><strong>Considerations</strong></td>
<td align="left"><ul>
<li>Multiple apps with similar, overlapping capabilities</li>
<li>Increased potential for user confusion which can lead to increased support calls, shadow IT, impacted productivity</li>
<li>Network planning and monitoring must take usage of two services into consideration</li>
<li>Increased and immediate change management efforts required—awareness, training, and support</li>
<li>Users may experience interoperability limitations between apps</li>
</ul></td>
<td align="left"><ul><li>IT has granular control, from licensing to user experiences, requiring additional cycles of planning and implementation</li>
<li>User education and action required to disable select capabilities in Teams</li>
<li>Change management efforts required to disable select capabilities in Teams</li>
<li>Network planning and monitoring must take usage of two services into consideration</li>
<li>Users may experience interoperability limitations between apps</li></ul></td>
</tr>
</tbody>
</table>

_Table 1: Side-by-Side benefits and considerations_

Unmanaged side-by-side customer journey
---------------------------------------

In an unmanaged side-by-side customer journey, Teams is introduced as a collaboration solution (chat-based workspace, channels, apps, integration with other Office 365 workloads, etc.) that involves client software and web client on desktop computers (PC or Mac) and mobile devices.

By default, Teams also presents overlapping capabilities with Skype for Business, these include private chat and calling, and scheduled meetings. This means Teams ends up providing complete communications and collaboration for the organization, while at the same time Skype for Business provides similar capabilities.

Teams supports interoperability with Skype for Business Online users, and users will be given an opportunity to choose their preferred chat and calling app when they launch Teams. If one user picks Teams as the preferred app, and another user hasn’t installed Teams or picked Skype for Business as the preferred chat and calling app, they can continue to chat and call each other through the interop capabilities that are part of Teams.

Microsoft is continuously improving the interop experiences. In the beginning, there may be some cases whereby the interop experiences are not meeting user expectations. Since Skype for Business is still available to users, they can switch to Skype for Business for the capabilities that currently cannot be served by Teams.

Scheduled meetings in Teams is another overlapping capability that lets users schedule Teams meetings, or Skype for Business meetings. Each has its own advantages, and over time, when Teams meeting experience meets business requirements or surpasses the functionalities of Skype for Business meetings, we expect users to naturally switch to Teams meetings.

In this unmanaged side-by-side customer journey, prepare your helpdesk team to handle support calls from users when facing issues with interop capabilities. Or advise users when to choose Teams meetings over Skype for Business meetings, and vice versa.

This side-by-side customer journey may be applicable to your organization, whereby the users are more receptive to the nature of the unmanaged side-by-side experience, and the organization openly allows the users to pick the best communications and collaboration tools that suit their requirements.

Managed side-by-side customer journey
-------------------------------------

![](media/guidance_SkypeforBusiness_image2.png)

A managed side-by-side customer journey starts with organization wanting more control over how Teams is introduced.

-   The **first step** of this journey is a limited pilot of Teams scoped to modern collaboration requirements (chat-based workspace, channels, apps, integration with other Office 365 workloads, etc.). Ad-hoc channel meetings in Teams is also enabled to provide a chance for pilot users to evaluate the Teams meetings experience. Scheduled meetings and private chat and calling capabilities in Teams are disabled at this stage. To get started with a pilot, go to [Pilot Teams with Skype for Business](pilot-essentials.md).
    
-   The **second step** of this journey is by extending the rollout of Teams for modern collaboration throughout the organization. Scheduled meetings, and private chat and calling are continued to be disabled in Teams to avoid presenting users with overlapping capabilities with Skype for Business.

-   The **third step** of the managed side-by-side customer journey starts when the organization decides that Teams meeting experience and capabilities meet their business requirements. With scheduled private and channel meetings enabled in Teams, users will be presented with options to schedule both Teams meetings and Skype for Business meetings, and it is expected that over time users will naturally switch to Teams meetings given the continued innovations in Teams. To be successful in steering usage from Skype for Business to Teams, implement a robust change management program inclusive of training, support and communications that explains the value-add that Teams offers to the user, with clear guidance on how to get started with Teams. Leverage our [User Readiness](http://aka.ms/UserReadiness) resources to help design your awareness campaign.


-   The **last step** of the managed side-by-side customer journey is when private chat and calling in Teams are enabled. Teams interoperability capabilities will feature heavily in this step to ensure a seamless side-by-side experience. Ideally, to enforce the use of Teams for private chat and calling, Teams is set as the default chat and calling app. Similar to the introduction of scheduled meetings in Teams, specific users adoption campaign featuring Teams private chat and calling experience will be required to steer usage to Teams.

Over time, potentially the whole organization can rely solely on Teams to meet communications and collaboration requirements. To see when new features are coming in Teams, see the [Office 365 Roadmap](http://aka.ms/TeamsRoadmap). 

Managing side-by-side experience
--------------------------------

Microsoft Teams is enabled, by default, for organizations with eligible Office 365 subscriptions, and if your organization fits the profile for unmanaged side-by-side customer journey, we highly recommend you keep it as-is to foster organic adoption of Microsoft Teams.

Teams is accessible via modern Web browsers and desktop client installation and requires no IT administrative privilege (applicable to PC only) and mobile client.

All capabilities in Teams, from private chat and calling, ad-hoc and scheduled meetings, and apps are enabled by default, allowing users to experiment and use the capabilities that suit their needs. First run experience in Teams guides users to pick their preferred chat and calling application (Microsoft Teams or Skype for Business).

Should your organization require a more controlled release of new tools such as Teams, the following options can be considered for your managed side-by-side customer journey, they are:

-   Pilot and rollout of Teams for collaboration. See [Pilot Teams with Skype for Business](pilot-essentials.md).

-   Rollout of Teams for meetings

-   Rollout of Teams for chat and calling

### Pilot and rollout of Teams for collaboration

At its core, Microsoft Teams was built around persistent chat and integration with Office 365 by enhancing Office 365 Groups.

Since by default everybody in your organization with an eligible Office 365 subscription license is enabled for Teams, a limited pilot of Teams will involve disablement of Teams license for all users that are outside of the pilot group.

To focus the release of Teams as a collaboration solution, and to avoid user confusion due to overlapping capabilities with Skype for Business, the following settings can be configured at the Tenant level from their default values.

<table>
<thead>
<tr class="header">
<th align="left">Section</th>
<th align="left">Setting</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>General</strong></td>
<td align="left"><p>Use Skype for Business for recipients who don’t have Microsoft Teams: <strong>Off</strong></p></td>
<td align="left"><p>Disabling this setting disables interoperability between Microsoft Teams and Skype for Business Online</p></td>
</tr>
<tr class="even">
<td align="left"><strong>Calls and meetings</strong></td>
<td align="left"><p>Allow scheduling for private meetings: <strong>Off</strong></p><p>Allow scheduling for channel meetings: <strong>Off</strong></p><p>Allow private calling: <strong>Off</strong></p></td>
<td align="left"><p>Disabling this setting prevents users from scheduling private meetings</p><p>Disabling this setting prevents users from scheduling channel meetings</p><p>Disabling this setting prevents users from making private calls (audio and video)</p></td>
</tr>
<tr class="odd">
<td align="left"><strong>Messaging</strong></td>
<td align="left"><p>Allow users to chat privately: <strong>Off</strong></p></td>
<td align="left"><p>Disabling this setting prevents users from chatting privately with other Microsoft Teams’ users</p></td>
</tr>
</tbody>
</table>

_Table 2: Teams for collaboration tenant settings_

<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/guidance_SkypeforBusiness_image3.png" /></p>
<p>Note</p></td>
<td align="left">You need to disable private calling and private chat to both Business and Enterprise users, and Guest users (if Guest Access is applicable to your organization).</td>
</tr>
</thead>
<tbody>
</tbody>
</table>

With this configuration, users can be introduced to how meetings work in Teams by advocating the use of ad-hoc channel meetup, enabling the use of voice, video, and screen sharing as part of the modern collaboration experience.

A successful pilot of Teams for collaboration can be followed up with broad rollout throughout the organization by enabling Teams license for all users.

### Rollout of Teams for meetings

As users are getting accustomed to collaborating using Microsoft Teams, scheduled meetings can be considered as the next capability to be enabled in the organization.

<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/guidance_SkypeforBusiness_image3.png" /></p>
<p>Note</p></td>
<td align="left">The organizers of scheduled meetings must have their mailboxes in Exchange Online multi-tenant (or Exchange Online Dedicated vNext).</td>
</tr>
</thead>
<tbody>
</tbody>
</table>

The following settings can be configured at the tenant level to enable scheduled meetings in Teams, and the settings are applicable to Business and Enterprise users only.

<table>
<thead>
<tr class="header">
<th align="left">Section</th>
<th align="left">Setting</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>Calls and meetings</strong></td>
<td align="left"><p>Allow scheduling for private meetings: <strong>On</strong></p><p>Allow scheduling for channel meetings: <strong>On</strong></p></td>
<td align="left"><p>Enabling this setting allows users to schedule private meetings</p><p>Enabling this setting allows users to schedule channel meetings</p></td>
</tr>
</tbody>
</table>

_Table 3: Teams for meetings tenant settings_

Scheduled meetings can be organized via the Teams desktop client, a browser, or via Microsoft Outlook using the meeting add-in for Microsoft Teams. Once scheduled meetings in Teams is enabled, we recommend you start educating users to create new Teams meetings or update existing Skype for Business meetings to Teams meetings.

### Rollout of Teams for chat and calling

Private chat and calling are the capabilities in Microsoft Teams that will be continuously developed, and over time provide a compelling replacement to Skype for Business. When your organization considers that Teams private chat and calling capabilities meet key business requirements, the following settings can be configured at the tenant level to enable private chat and calling in Teams. The Calls and Meetings, and Messaging settings need to be applied to both Business and Enterprise users, and Guest users (if Guest Access is applicable to your organization).

<table>
<thead>
<tr class="header">
<th align="left">Section</th>
<th align="left">Setting</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>General</strong></td>
<td align="left"><p>Use Skype for Business for recipients who don’t have Microsoft Teams: <strong>On</strong></p></td>
<td align="left"><p>Enabling this setting allows interoperability between Microsoft Teams and Skype for Business Online for both chat and calling </p></td>
</tr>
<tr class="even">
<td align="left"><strong>Calls and meetings</strong></td>
<td align="left"><p>Allow private calling: <strong>On</strong></p></td>
<td align="left"><p>Enabling this setting allows users to place private calls (audio and video)</p></td>
</tr>
<tr class="odd">
<td align="left"><strong>Messaging</strong></td>
<td align="left"><p>Allow users to chat privately: <strong>On</strong></p></td>
<td align="left"><p>Enabling this setting allows users to chat with other users privately</p></td>
</tr>
</tbody>
</table>

_Table 4: Teams for chat and calling_

At this stage, all users must be instructed to choose Teams as the preferred chat and calling app.

With the enablement of private chat and calling, Teams will deliver all capabilities currently provided by Skype for Business, and users can start using Teams client to fulfill their communications and collaboration requirements.


<table>
<thead>
<tr class="header">
<td align="left"><p><img src="media/pilot_essentials_image2.png" /></p></td>
<td align="left">
<p><strong>Next Action:</strong> Once Teams is up and running side-by-side with Skype for Business, [Drive Value through user adoption of Teams](continue-journey.md), while continuing your journey from Skype for Business to Teams.</td>
</tr>
</thead>
<tbody>
</tbody>
</table>