---
title: Roll out Microsoft Teams First 
author: LaszloSomi
ms.author: lsomi
manager: swerth
audience: Admin
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
ms.reviewer: lsomi
ms.localizationpriority: medium
search.appverid: MET150
description: Use this guidance to roll out Microsoft Teams as your first Microsoft 365 or Office 365 workload.
ROBOTS: NOINDEX, NOFOLLOW
appliesto: 
  - Microsoft Teams
---

# Roll out Microsoft Teams First

Microsoft Teams can help your employees stay connected and collaborate with each other, especially in the current unprecedented time where remote work is a reality of employees around the world. Being able to chat, do video meetings and collaborate on Office documents within Teams can help companies stay productive. Whether you are a small business, a non-profit or a large organization, you can get started with Teams as the first workload within Microsoft 365 or Office 365 suite before deploying any other Office app or service.

This article details the considerations you must make with the "Teams First" approach.

> [!IMPORTANT]
> While Teams can be your organization's first cloud deployed workload, deploying Teams should be part of your overall cloud deployment strategy.

If you have already rolled out other Microsoft 365 or Office 365 services and Teams is your next workload to roll out (instead of the first), start with [How to roll out Teams](./deploy-overview.md).

## Start here

To get started with your Teams First deployment you will need to meet at minimum some pre-requisites. The following list will show what you must have in place for your organization before Teams can be enabled:

1.  A Microsoft 365 or Office 365 organization configured with your domain name

2.  Azure Active Directory connectivity (AAD connect) or similar cloud identity sync solution – with all required attributes synched with your tenant  
    To understand the attributes synchronized with AAD sync, read [Azure AD Connect sync: Attributes synchronized to Azure Active Directory](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)

3.  Appropriate user licenses assigned for Teams  
    To understand Teams licensing, read [Microsoft Teams service description](/office365/servicedescriptions/teams-service-description).

4.  Organization's network prepared for Teams  
    To understand network preparation, read [Prepare your organization's network for Teams](prepare-network.md).

5.  Allow network access to Exchange, SharePoint, and OneDrive for Business in Microsoft 365 or Office 365: [Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges).

> [!NOTE]
> Tenants created after September 1, 2019 are provisioned in Teams Only mode.
> 
> [!IMPORTANT]
> If you have Skype for Business Server deployed, and your tenant was provisioned AFTER September 1, 2019, please contact support to enable coexistence capabilities for Teams. Make sure your 'Organization wide upgrade policy' is set to 'Island mode' <span class="underline">before</span> you assign any Teams licenses to a user.

## Migration Starting points

Your journey to Microsoft 365 or Office 365 and features available in Teams depending on your starting point and the existence of on premises Skype for Business or Lync server. The following sections will detail basic capabilities and configuration options in addition to the pre-requisites above. We have broken down the starting point scenarios to the following topics:

**Tenant Teams Configuration**: Tenant and user modes are used to control the recipient's behavior. These settings can be assigned on the tenant level or the user level in an organization. To learn more, read [Coexistence with Skype for Business](coexistence-chat-calls-presence.md).

**Chat / External communication in Teams**: Chat services refer to peer to peer or group chat conversations within and organization or externally to the organization. External communication is also referred to as federation in Skype for Business.

**Create and view meetings in Teams**: A user can always create online meetings via the Outlook Teams add-in and PSTN dial-in is available in all scenarios once the user is licensed. Teams and Skype for Business store calendaring information in the user's Exchange mailbox. On premises Exchange server must be Exchange Server 2016 CU3 or above for the Teams client to be able to interact with the user's mailbox. Without Exchange mailbox access the Calendar icon in Teams will not appear and they user will not be able to view, create or modify meetings in the Teams client.

**Calling features VoIP / PSTN in Teams**: Calling can be Voice over IP (VoIP) or Public Switched Telephone Network (PSTN). VoIP connectivity happens natively between Teams clients, while PSTN connectivity happen when a user dials an outside phone number.  

Teams support two types of PSTN connectivity. Microsoft Calling Plan, when Microsoft provides telephony infrastructure including the phone number for a user, or Direct Routing configuration, where the customer provides the telephony connectivity over a Session Border Controller (SBC) for the Teams user.  
To learn more, read [Which Calling Plan is right for you?](calling-plan-landing-page.md) and [Phone System Direct Routing](direct-routing-landing-page.md).

**Teams and Channels collaboration in Teams**: In Teams, teams are groups of people brought together for work, projects, or common interests. Teams are made up of channels. Each channel is built around a topic, like "Team Events," a department name, or just for fun. Channels are where you hold meetings, have conversations, and work on files together. During collaboration

**OneDrive for Business (P2P file sharing) in Teams**: Outside of Teams and Channels, Teams users can share files peer-to-peer using OneDrive for business or other P2P sharing file programs such as Citrix Files, DropBox, Box and Google Drive. For OneDrive for business a user must have SharePoint Online license assigned.

**Application Platform**: Apps provide out-of-the-box tools for your organization to get more out of Teams. These apps combine the functionality of tabs, messaging extensions, connectors, and bots provided by Microsoft, built by a third-party, or by developers in your organization.

**Security and Compliance features:** Teams has a wide range of information to help you with compliance areas, including retention policies, data loss prevention (DLP), eDiscovery and legal hold for channels, chats and files, audit log search. To learn more, read [Security and compliance in Microsoft Teams](security-compliance-overview.md).  

> [!NOTE]
> Advance eDiscovery features require E5 licensing.

[Compare licensing options](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans).

Read [How Exchange and Microsoft Teams interact](exchange-teams-interact.md) to learn which compliance features are available in your scenario.

## Organizations **<span class="underline">without</span>** Skype for Business or Lync Server

This starting point assumes that your organization does not utilize Skype for Business or Lync Server currently and Teams will be your first application in Microsoft 365 or Office 365. The following table details high level configuration and end user capabilities for Teams for core services.

<table>
<thead>
<tr class="header">
<th>Item</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Tenant Teams configuration</td>
<td>Teams Only mode, all chat and calling features are in Teams Only.</td>
</tr>
<tr class="even">
<td>Chat / External Communication in Teams</td>
<td><p>Internal (intra Microsoft 365 or Office 365 organization) and external chat communication possible from Teams.</p>
<p><em>Note: DNS entries must be configured for external access. Skype for Business DNS records are needed even though you don't have Skype for Business on-premises, or in Microsoft 365 or Office 365, to allow federation with Lync and Skype for Business environments:<br />
<a href="/office365/enterprise/external-domain-name-system-records">External Domain Name System records</a></em></p></td>
</tr>
<tr class="odd">
<td>Create and view Meetings in Teams</td>
<td><p>Able to create internal and external meetings via Outlook add-in.</p>
<p>PSTN Dial in and Dial out capability is available with the Audio Conferencing licenses.</p>
<p>Teams calendar access requires Exchange 2016 CU3+ on-premises deployed with Exchange hybrid established: <a href="/exchange/hybrid-deployment/deploy-hybrid">Create a hybrid deployment with the Hybrid Configuration wizard.</a> </p>

In addition to Exchange hybrid configuration, establish Exchange OAuth authentication: [Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help). 

</p></td>
</tr>
<tr class="even">
<td>Calling Features<br />
VoIP / PSTN in Teams</td>
<td><p>VoIP internally and externally to the tenant is available.</p>
<p>PSTN services can be configured via Microsoft Phone System, plus adding a Microsoft Calling Plan or Direct Routing.</p></td>
</tr>
<tr class="odd">
<td>Teams and Channels collaboration in Teams</td>
<td><p>For full experience, including compliance features, a SharePoint Online license need to be assigned to the user.</p>
<p>Migration of existing on-premises SharePoint sites is not required.</p></td>
</tr>
<tr class="even">
<td>OneDrive for Business (P2P file sharing)</td>
<td>OneDrive for Business requires a user to have a SharePoint Online license assigned. Without this license peer-to-peer file sharing will not be possible.</td>
</tr>
<tr class="odd">
<td>Application platform</td>
<td>Users will be able to use the apps that are designated available for them according to your company policies.<br />
Learn more here: <a href="/microsoftteams/admin-settings">Admin settings for apps in Teams</a></td>
</tr>
<tr class="even">
<td>Security and Compliance features</td>
<td><ul>
<li><p>Retention policies are available.</p></li>
<li><p>eDiscovery and Legal Hold for compliance on channel messages is supported.</p></li>
<li><p>Data loss prevention policies (DLP) are available.</p></li>
</ul>
<p>Full feature set available with Exchange Online; Exchange on-premises supports most of these features. For a full list, see <a href="/MicrosoftTeams/exchange-teams-interact">How Exchange and Teams interact</a>.</p></td>
</tr>
</tbody>
</table>

### Enablement steps for organizations without Skype for Business or Lync Server

1.  Meet pre-requisites detailed in the Start Here section above

2.  Switch tenant into Teams Only mode (for existing tenants only): [Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md).

3.  Configure your tenant in accordance with your company's business/company policies: [Manage Microsoft Teams settings for your organization](enable-features-office-365.md).

4.  Deploy the Teams client to your users: [Get clients for Teams](get-clients.md)

5.  Drive your adoption program  
    [Adopt Microsoft Teams](adopt-microsoft-teams-landing-page.md)
    
    [Microsoft Teams adoption quick start checklist](teams-adoption-quick-start-checklist.md)

6.  Begin planning moving other workloads to Microsoft 365 or Office 365

## Organizations **<span class="underline">with</span>** Skype for Business or Lync server

This starting point assumes that your organization utilizes Skype for Business 2019 or 2015+ or Lync 2013+ server on premises. We already have extensive guidance for organizations migrating from on premises servers to Teams and it should be followed for these scenarios. This guidance is specific to the scenario that Teams is the first application you utilize in Microsoft 365 or Office 365. The following table details high level configuration and end user capabilities for Teams for core services.

<table>
<thead>
<tr class="header">
<th>Item</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Tenant Teams configuration</td>
<td>Islands mode.</td>
</tr>
<tr class="even">
<td>Chat / External Communication in Teams</td>
<td>Internal within your own tenant only, external communication (federation) is via your Skype for Business or Lync server deployment.</td>
</tr>
<tr class="odd">
<td>Create and view Meetings in Teams</td>
<td><p>Able to create internal and external meetings via Outlook add-in.</p>
<p>PSTN Dial in and Dial out capability is available with the Audio Conferencing licenses.</p>
<p>Teams calendar access requires Exchange 2016 CU3+ on-premises deployed with Exchange hybrid established:<br />
<a href="/exchange/hybrid-deployment/deploy-hybrid">Create a hybrid deployment with the Hybrid Configuration wizard.</a></p>
<p>Administrator can control the Skype for Business Outlook add-in via the Teams meeting policy’s PreferredMeetingProviderForIslandsMode attribute:<a href="/powershell/module/skype/set-csteamsmeetingpolicy">
set-csteamsmeetingpolicy</a>.</p> 
</td>
</tr>
<tr class="even">
<td>Calling Features<br />
VoIP / PSTN in Teams</td>
<td><p>VoIP internally to the tenant is available.</p>
<p>PSTN or Calling Plan services are not available until the user is moved to Teams Only experience.</p></td>
</tr>
<tr class="odd">
<td>Teams and Channels collaboration in Teams</td>
<td><p>For full experience, including compliance features, a SharePoint Online license need to be assigned to the user.</p>
<p>Migration of existing on-premises SharePoint sites is not required.</p></td>
</tr>
<tr class="even">
<td>OneDrive for Business (P2P file sharing)</td>
<td>OneDrive for Business requires a user to have a SharePoint Online license assigned. Without this license per-to-peer file sharing will not be possible.</td>
</tr>
<tr class="odd">
<td>Application platform</td>
<td>Users will be able to use the apps that are designated available for them according to your company policies.<br />
Learn more here: <a href="/microsoftteams/admin-settings">Admin settings for apps in Teams</a></td>
</tr>
<tr class="even">
<td>Security and Compliance features</td>
<td><ul>
<li><p>Retention policies are available.</p></li>
<li><p>eDiscovery and Legal Hold for compliance on channel messages is supported.</p></li>
<li><p>Data Loss Prevention policies (DLP) are available.</p></li>
</ul>
<p>Full feature set available with Exchange Online; Exchange on-premises supports most of these features. For a complete list, see 
<a href="/MicrosoftTeams/exchange-teams-interact">How Exchange and Teams interact.</a></p>
<ul>
</ul></td>
</tr>
</tbody>
</table>

### Enablement steps for organizations with Skype for Business Server  

1.  Meet pre-requisites detailed in the Start Here section above.

2.  Switch tenant into Islands mode (for tenants provisioned AFTER 9/1/2019, please contact support to make this change)  
    [Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md)

3.  Configure your tenant in accordance with your company's business/company policies  
    [Manage Microsoft Teams settings for your organization](enable-features-office-365.md)

4.  Deploy the Teams client  
    [Get clients for Teams](get-clients.md)

5.   Drive your adoption program  
    [Adopt Microsoft Teams](adopt-microsoft-teams-landing-page.md)<br/>
    [Microsoft Teams adoption quick start checklist](teams-adoption-quick-start-checklist.md)

6.  Begin planning moving other workloads to Microsoft 365 or Office 365

7.  Establish Skype for Business hybrid and follow the recommended upgrade paths for Skype for Business and Lync servers  
    [Upgrade from Skype for Business on-premises to Teams](upgrade-to-teams-execute-skypeforbusinesshybridonprem.md)

## Closing statement

Microsoft Teams can be an enabler for your organization to bring all the employees, information workers and Frontline workers, together on a single platform. You can [get started](https://products.office.com/microsoft-teams/group-chat-software) today. You can keep in touch with all our latest announcements and monthly product updates [here](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/bg-p/MicrosoftTeamsBlog).

Additionally, as companies around the world are managing the current COVID-19 situation, we have created a series of content that will help you utilize Teams for the maximum impact in your organization.

  - Our [commitment to customers during COVID-19](https://www.microsoft.com/en-us/microsoft-365/blog/2020/03/05/our-commitment-to-customers-during-covid-19/)

  - [2 weeks in: what we've learned about remote work](https://www.microsoft.com/en-us/microsoft-365/blog/2020/03/18/making-the-switch-to-remote-work-5-things-weve-learned/)

  - [Delivering online meetings and events](https://www.microsoft.com/en-us/microsoft-365/blog/2020/03/17/delivering-online-meetings-events/)

  - [Helping small and medium-sized businesses work remotely with Teams](https://www.microsoft.com/en-us/microsoft-365/blog/2020/03/17/helping-smb-customers-work-remotely-microsoft-teams/)

  - [Digital transformation of live events: Bob Bejan's observations from the frontline](https://www.microsoft.com/en-us/microsoft-365/blog/2020/03/13/digital-transformation-live-events-bob-bejans-observations-frontline/)

  - [The top 9 ways Microsoft IT is enabling remote work for its employees](https://www.microsoft.com/en-us/microsoft-365/blog/2020/03/12/top-9-ways-microsoft-it-enabling-remote-work-employees/)

  - [Work remotely, stay secure—tips for CISOs](https://www.microsoft.com/en-us/microsoft-365/blog/2020/03/12/work-remotely-stay-secure-ciso-tips/)

  - [Helping teachers and students make the switch to remote learning](https://www.microsoft.com/en-us/microsoft-365/blog/2020/03/11/helping-teachers-students-switch-remote-learning/)

  - [Staying productive while working remotely with Microsoft Teams](https://www.microsoft.com/en-us/microsoft-365/blog/2020/03/10/staying-productive-while-working-remotely-with-microsoft-teams/)

## Support Services reference

Teams relies on Exchange Online, SharePoint Online, OneDrive for Business and Microsoft 365 Groups to provide your users with a fully integrated Microsoft 365 or Office 365 experience. As noted above, Teams will work without full deploying these services – with limited capabilities. You can read more about Teams and its pre-requisites here: [Welcome to Teams](teams-overview.md).

For specifics on each of the services listed above, please follow the links below:

  - Exchange Online is used for calendaring features and storing peer to peer messages in Teams. To learn more, read [How Exchange and Teams interact](exchange-teams-interact.md)

> [!IMPORTANT]
> For Teams interop with Exchange on-premises, you must configure the new Exchange OAuth authentication protocol as described in [Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help).

  - SharePoint is used for file sharing in channels, while /OneDrive for Business is used for file sharing in 1:1 or group chat. To learn more, read [How SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md).

  - [Microsoft 365 Groups](office-365-groups.md) are used for team and channel creation/management.


## Related topics

[Microsoft Teams IT architecture and telephony solutions posters](teams-architecture-solutions-posters.md#teams-as-part-of-microsoft-365)

[Plan hybrid connectivity between Skype for Business Server and Office 365](/SkypeForBusiness/hybrid/plan-hybrid-connectivity)

[Support remote workers using Teams](support-remote-work-with-teams.md)

[Work remotely with Microsoft 365](https://aka.ms/remote-work)
