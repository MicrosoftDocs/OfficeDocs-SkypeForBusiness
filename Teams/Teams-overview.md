---
title: Overview of Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
ms.reviewer: 
description: Learn about Microsoft Teams, its infrastructure, and using Teams with Office 365.
localization_priority: Normal
search.appverid: MET150
ms.custom:
- NewAdminCenter_Update
MS.collection: Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
---

Overview of Microsoft Teams
===========================

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=ccf507a4-4ec4-4d61-9fb0-c86b5f1fc2a6&AutoPlayVideo=false] 


Microsoft Teams brings together the full breadth and depth of Office 365, to provide a true chat-based hub for teamwork and give customers the opportunity to create a more open, fluid, and digital environment. Microsoft Teams is built on existing Microsoft technologies woven together by Office 365 Groups. 

Out of the box, Teams leverages identities stored in Azure Active Directory (Azure AD) and integrates with the other services within Office 365, to create a SharePoint online site and an Exchange Online group mailbox for each team created.

Anyone with a business or consumer email account, such as Outlook, Gmail, or others, can participate as a guest in Teams. All guests in Teams are covered by the same compliance and auditing protection as the rest of Office 365, and guests can be managed securely within Azure AD. Admins can centrally manage how guests participate within their Office 365 environment and easily view, add, or revoke a guest’s access to the host tenant.

Teams provides a persistent chat capability, calling and meetings, easy access to other components of Office 365 as well as a robust extensibility story.  This provides a hub for teamwork that is appropriate for enterprise companies, small organizations and everyone in between.  

To extend Teams capabilities, use Connectors, Tabs, and Bots - available as [Apps](https://go.microsoft.com/fwlink/?linkid=854629), to bring external information, content, and intelligent bot interactions to Teams.  

Microsoft Teams infrastructure
------------------------------

Teams is built on existing Microsoft technologies, woven together by Office 365 Groups. Powered by the Microsoft cloud, organizations can expect excellent performance and reliability when leveraging Teams as part of their collaboration story.

Out of the box, a team created in Teams will create an Office 365 Group, a SharePoint Online site (complete with a document library), and an Exchange Online group mailbox, which will be used by Teams to store information such as meeting invites. A team can be created using existing Office 365 Groups, allowing existing group memberships, and contents stored in SharePoint Online and Exchange Online to be ported to Teams.

To complement the Teams capability as a persistent chat board where informal, real-time conversations take place, Teams also provides a calling and meeting experience built on the next generation cloud-based infrastructure that is also used by Skype and Skype for Business. These technology investments include Azure-based cloud services for media processing and signaling, H.264 video codec, SILK and Opus audio codec, network resiliency, telemetry, and quality diagnostics.

Office 365 Groups leverage identities stored in Azure Active Directory (Azure AD) and as such, all authentication and authorization capabilities in Azure AD, such as support for multi-factor authentication (MFA), are readily available for use by Teams.

> [!NOTE]
> Based on customer feedback, new Office 365 Groups generated as a result of creating a team in Microsoft Teams will no longer show in Outlook by default. For customers that want to continue with the existing behavior of showing these groups in Outlook, an Exchange Online PowerShell cmdlet will be provided which can enable the group for the Outlook experience. Groups created through Outlook and then later enabled for Teams will continue to show in both Outlook and Teams. This update will gradually roll out across Outlook and Teams in the coming months.


Microsoft Teams and Office 365
------------------------------

Different groups have various needs, based on their functional role and workstyle. Office 365 is designed for the unique workstyle of every group and includes purpose-built, integrated applications, including:

-   Outlook for enterprise-grade email, now with groups functionality

-   SharePoint for sites and portals, intelligent content services, business process automation and enterprise search

-   Yammer for driving company-wide connections

-   Skype for Business as the backbone for enterprise voice and video

-   And now, Microsoft Teams, the new chat-based workspace in Office 365

Here are common use cases for each application in Office 365. For detailed usage guidance, visit the [FastTrack Productivity Library](https://go.microsoft.com/fwlink/?linkid=854630).

![Microsoft Teams icon.](media/Overview_of_Microsoft_Teams_image1.png)

-   Leveraged by users and teams who are looking to collaborate in real-time with the same group of people.

-   Helps teams looking to iterate quickly on a project while sharing files and collaborating on shared deliverables.

-   Allows users to connect a wide range of tools into their workspace (such as Planner, Power BI, GitHub, etc.).

![Microsoft Outlook icon.](media/Overview_of_Microsoft_Teams_image2.png)

-   Leveraged by users who prefer to collaborate in the familiar environment of email and/or a more formal, structured manner.

-   Provides specific business processes that require email usage to transmit documents and information inside and outside corporate boundaries.

-   Communicates and connects with users who are outside of immediate workgroups or organizations.

![Yammer icon.](media/Overview_of_Microsoft_Teams_image3.png)

-   Leveraged to help connect users across the organization to organize around communities of practice and share best practices.

-   Improves cross-functional workflows through an open and transparent feed-based platform

-   Fosters executive-employee engagement with two-way conversations between leadership and the wider employee base

-   Ignites your frontline workforce to share and receive knowledge and expertise

![Skype for Business icon.](media/Overview_of_Microsoft_Teams_image4.png)

-   Leveraged for real-time communication and collaboration both internally and externally with customers/partners.

-   Provides meetings with audio, video and content with small or large teams (including Town Halls with up to 10,000 participants).

-   Offers enterprise telephony functionality.


![Microsoft SharePoint icon.](media/Overview_of_Microsoft_Teams_image5.png)

-   Leveraged for sites and portals (e.g. company news & announcements, search, and document collaboration).

-   Implements business process automation on document libraries and lists of information by integrating Microsoft Flow and PowerApps.

-   Full-powered SharePoint team site automatically provisioned for every Microsoft Team for file storage, team news, pages, lists and more.

-   See [How SharePoint Online and OneDrive for Business interact with Teams](SharePoint-OneDrive-interact.md)

## [Teams known issues](Known-issues.md)

## [Teams client release notes](https://support.office.com/article/Release-notes-for-Microsoft-Teams-d7092a6d-c896-424c-b362-a472d5f105de)


